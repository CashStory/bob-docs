---
title: Google Lib
description: 
published: true
date: 2020-07-01T13:51:41.194Z
tags: 
editor: markdown
---

# Google spreadsheet lib

This lib contains function to get data from a google spreadsheet file. 

### Functions

``` python
def __init__(self, spreadsheet_id=None, sheet_name=None, credentials_json=None)
```
Init the google spreadsheet class.

| Parameter       | Type   | Description                                 |
| --------------- | ------ | ------------------------------------------- |
| spreadsheet_id  | string | Id of your google sheet file                |
| sheet_name      | string | Name of the sheet you want to get data from |
| credential_json | String | Credentials of the google account           |

``` python
def get_google_sheet(self, title, sheet_name)
```
Gets data from a google spreadsheet. You need to have a client_secret.json file from the account who created the sheet. And you need to share your  google spreadsheet with this emails : 

- connector@skypebot.iam.gserviceaccount.com

- cs-googlesheet@cashstory.iam.gserviceaccount.com

| Parameter   | Type   | Description                                 |
| ----------- | ------ | ------------------------------------------- |
| title*      | string | Title of your google sheet file             |
| sheet_name* | string | Name of the sheet you want to get data from |

