---
title: Monitoring
description: How to monitor the OS?
published: true
date: 2020-03-12T15:16:40.338Z
tags: 
---

## How Cashstory health Works

Each check in <a href="https://health.cashstory.com/" target="_blank">My Checks</a>  page has a unique "ping" URL. Whenever you make a HTTP request to this URL, Cashstory health records the request and updates the "Last Ping" value of the corresponding check.

When a certain, configurable amount of time passes since last received ping, the check is considered "late". Cashstory health then waits for additional time (configured with the "Grace Time" parameter) and, if still no ping, sends you an alert.

As long as the monitored service sends pings on time, you receive no alerts. As soon as it fails to check in on time, you get notified. It is a simple idea.

![capture_d’écran_2020-03-11_à_17.15.04.png](/capture_d’écran_2020-03-11_à_17.15.04.png =650x280)
## Signalling a Success

At the end of your batch job, add a bit of code to request your ping URL.

- HTTP and HTTPS protocols both work. Prefer HTTPS, but on old systems you may need to fall back to HTTP.
- Request method can be GET, POST or HEAD
- Both IPv4 and IPv6 work
- For HTTP POST requests, you can include additional diagnostic information for your own reference in the request body. If the request body looks like a UTF-8 string, Cashstory health will log the first 10 kilobytes of the request body, so you can inspect it later.

The response will have status code "200 OK" and response body will be a short and simple string "OK".

## Signalling a Failure

Append /fail to a ping URL and use it to actively signal a failure. Requesting the /fail URL will immediately mark the check as "down". You can use this feature to minimize the delay from your monitored service failing to you getting a notification.

Below is a skeleton code example in Python which signals a failure when the work function returns an unexpected value or throws an exception:

``` python
import requests
URL = "https://health.cashstory.com/ping/your-uuid-here"

def do_work():
    # Do your number crunching, backup dumping, newsletter sending work here.
    # Return a truthy value on success.
    # Return a falsy value or throw an exception on failure.
    return True

success = False
try:
    success = do_work()
finally:
    # On success, requests https://health.cashstory.com/ping/your-uuid-here
    # On failure, requests https://health.cashstory.com/ping/your-uuid-here/fail
    requests.get(URL if success else URL + "/fail")
```

## Measuring Job Execution Time

Append /start to a ping URL and use it to signal when a job starts. After receiving a start signal, Cashstory health will show the check as "Started". It will store the "start" events and display the job execution times. The job execution times are calculated as the time gaps between adjacent "start" and "complete" events.

Signalling a start kicks off a separate timer: the job now must signal a success within its configured "Grace Time", or it will get marked as "down".

Below is a code example in Python:
``` python
import requests
URL = "https://health.cashstory.com/ping/your-uuid-here"


# "/start" kicks off a timer: if the job takes longer than
# the configured grace time, the check will be marked as "down"
try:
    requests.get(URL + "/start", timeout=5)
except requests.exceptions.RequestException:
    # If the network request fails for any reason, we don't want
    # it to prevent the main job from running
    pass


# TODO: run the job here
fib = lambda n: n if n < 2 else fib(n - 1) + fib(n - 2)
print("F(42) = %d" % fib(42))

# Signal success:
requests.get(URL)
```

## Examples

### Crontab

When using cron, probably the easiest is to append a curl or wget call after your command. The scheduled time comes, and your command runs. If it completes successfully (exit code 0), curl or wget runs a HTTP GET call to the ping URL.

``` http
# m h dom mon dow command
  8 6 *   *   *   /home/user/backup.sh && curl -fsS --retry 3 https://health.cashstory.com/ping/your-uuid-here > /dev/null
```

With this simple modification, you monitor several failure scenarios:

- The whole machine has stopped working (power outage, janitor stumbles on wires, VPS provider problems, etc.)
- cron daemon is not running, or has invalid configuration
- cron does start your task, but the task exits with non-zero exit code
- Either way, when your task doesn't finish successfully, you will soon know about it.

The extra options to curl are meant to suppress any output, unless it hits an error. This is to prevent cron from sending an email every time the task runs. Feel free to adjust the curl options to your liking.

|   |   |
|---|---|
| **&&**  |  Run curl only if ```/home/user/backup.sh``` succeeds |
| **-f, --fail** | Makes curl treat non-200 responses as errors |
|  **-s, --silent** |  Silent or quiet mode. Don't show progress meter or error messages.|
| **-S, --show-error**	 |  	When used with -s it makes curl show error message if it fails. |
| **--retry `<num>`** | If a transient error is returned when curl tries to perform a transfer, it will retry this number of times before giving up. Setting the number to 0 makes curl do no retries (which is the default). Transient error means either: a timeout, an FTP 4xx response code or an HTTP 5xx response code.  |
| **> /dev/null** | Redirect curl's stdout to /dev/null (error messages go to stderr,)  |

### Cron Syntax Cheatsheet

Cashstory health understands most of the traditional cron syntax features. Under the hood, it uses the croniter package to parse and interpret cron expressions. Below is a showcase of supported syntax features.

Pro-tip! On Unix-like operating systems, you can also easily access cron syntax documentation by typing man 5 crontab in shell.

![capture_d’écran_2020-03-11_à_13.39.48.png](/capture_d’écran_2020-03-11_à_13.39.48.png =350x310) ![capture_d’écran_2020-03-11_à_13.39.59.png](/capture_d’écran_2020-03-11_à_13.39.59.png =350x310)

## When Alerts Are Sent
Each check has a configurable Period parameter, with the default value of one day. For periodic tasks, this is the expected time gap between two runs.

Additionally, each check has a Grace parameter, with default value of one hour. You can use this parameter to account for run time variance of tasks. For example, if a backup task completes in 50 seconds one day, and completes in 60 seconds the following day, you might not want to get alerted because the backups are 10 seconds late.

Each check can be in one of the following states:

![tablehealth.png](/tablehealth.png =690x310)
