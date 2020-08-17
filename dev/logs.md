---
title: Log Management
description: 
published: true
date: 2020-03-18T13:42:58.688Z
tags: 
---

# Log management
## Overview
In Cashstory events done by the user like login are send to the logs. Application logging allows applications to have their own, separate logs that can be retrieved for later use by the App Provider. Anything logged by the app will go to a separate folder and file in the Cashstory database.

Logs are in json format : 
```json
 {
    "creatorId": "5da886a8918b2b1ffscchh4",
    "action": "login",
    "prevData": {},
    "newData": {},
    "context": {},
    "collectionName": "auth"
  }
```

## Log properties

| Property       | Type   | Description                               |
| -------------- | ------ | ----------------------------------------- |
| creatorId      | string | Creator id of the user for this log       |
| action         | string | Type of action logged                     |
| prevData       | object | Previous data object                      |
| newData        | object | New data object                           |
| context        | object | Context data object                       |
| collectionName | string | Name of the database collection concerned |

## Values loged

Here is a list of the values logged: 

| Value      | Description   | 
| -------------- | ------ | 
| login     | user login in cashstory | 
| login-with-saml         | string | 
| getAll      | get all users | 
| count        | count data | 
| insert       | insert data |
| get | read some data | 
| update      | update of data | 
| delete       | delete data | 
| upload       | upload data in the database | 
| getFile        | read file | 
| sendFile        | send a file |
| create | create user | 
| getMe      | read my user informations | 
| deleteMe       | delete my user account | 
| event       | event on data | 
| addFav        | add favorite in user config | 
| deleteFav        | delete a favorite |
| login-jwt | login | 
| login-basic | basic auth login | 




## Blockchain log

ProvenDB uses Blockchain technology to create the world’s first genuinely trustworthy database. ProvenDB bridges the gap between database systems and Blockchain, providing you with a proven data storage solution.

You can know more about blockchain log on <a href="https://provendb.com/homepage//" target="_blank">ProvenDB</a>