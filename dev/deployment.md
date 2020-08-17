---
title: Deployment
description: 
published: true
date: 2020-03-02T06:53:04.056Z
tags: 
---

# Installation requirements
**Hardware requirements**
Resources’ needs are defined by different elements:

CPU: directly depends on the maximum number of users connected at the same time, the complexity of the preprocessing scripts, if all services are hosted on the same server…
Memory: size of all data that will be crunched during each update (our recommendation is three times this amount to allow preprocessing scripts to pivot and compute extra data)
Storage: a typical installation uses around 1GB, but additional space for the database, data sources files and assets should be planned
For single projects, our recommendation and typical configuration are:

CPU: Intel® Xeon® E3 1245 v5 (4C/8T @3.5 Ghz)
Memory: 32 GB DDR4 ECC
Storage: 250 GB SSD
Of course the right sizing will directly depends of your data and usage

**Software requirements**
OS
Toucan Toco requires a GNU/Linux 64 bits architecture. We currently support

Ubuntu (from Xenial - v16.04)
Debian (from Jessie - v8.0)
CentOS (from v7.0)
RedHat (from 7.0)


**Packages**
Python 3
Ansible v2.7.x (on any machine that has access to the target machine, or alternatively on the target machine itself) because all our deployment scripts are using it you need to be able to install official packages from the distribution repositories or mirrors
Network requirements
The installation (and upgrade) process requires an Internet access to a given domains list during the whole installation or upgrade procedure.

The On-Premise node needs to be able to reach the following domains on port 80 (HTTP) and 443 (HTTPS):

get-package.toucantoco.com
galaxy.ansible.com
pypi.org
pypi.python.org
www.python.org
files.pythonhosted.org
repo.mongodb.org
www.mongodb.org
deb.nodesource.com (for Debian OS family only)
rpm.nodesource.com (for RedHat OS family only)
github.com
codeload.github.com
raw.githubusercontent.com
keyserver.ubuntu.com (for Debian OS family only)
registry.npmjs.com
registry.npmjs.org
*.s3.amazonaws.com
bower.herokuapp.com
registry.yarnpkg.com
nodejs.org
storage.googleapis.com
packages.microsoft.com (when using Azure Microsoft SQL Server only)
This permission has a real restricted area in time and domains and could be disable just after the installation.

Please note if you choose to configure the Toucan Toco backend to send mails (like reset password) via Sendgrid, you will also need to permantly whitelist api.sendgrid.com on ports 80 and 443.
Docker requirements

TBD

# Kubernetes

## Helm charts

- mongodb: https://hub.helm.sh/charts/stable/mongodb-replicaset
- redis: https://hub.helm.sh/charts/stable/redis-ha
- postgres: https://hub.helm.sh/charts/bitnami/postgresql-ha
- prometheus: https://hub.helm.sh/charts/stable/prometheus
- grafana: https://hub.helm.sh/charts/stable/grafana
- weave-scope: https://hub.helm.sh/charts/stable/weave-scope
- jupyter: https://jupyterhub.github.io/helm-chart/
- healthchecks: In house (will add link to github)
- mongodump: In house (will add link to github)
- tools: In house (will add link to github)
- galaxy: In house (will add link to github)