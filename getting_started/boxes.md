---
title: Boxes
description: 
published: true
date: 2020-04-01T09:04:54.606Z
tags: 
---

# Boxes

In CashStory OS, everything the user interact with is a "Box". Boxes are linked to sections (from the left hand panel, see [workspaces](https://docs.cashstory.com/getting_started/workspaces))

![box.png](/box.png =650x380)

This "box-based" configuration enable a huge flexibility of configuration. We can configure : 

- Apps that are already in the OS
- Custom apps that are not in the OS
- Other types of elements like : documentation, spreadsheet, etc... as long as they have an url to give. 

Boxes are to be configured in json format. 

## Overview

Boxes are represented by a json object :

```json
 "box": [
      {
        "hideElements": [],
        "_id": "5da846a8918b2b1ffsccdg4",
        "name": "Name of my app",
        "iframe": true,
        "autoExpand": true, 
        "url": "https://task.cashstory.com/",
        "urlBg":"https://myimage.png",
        "smartTable": {
          "database": "darkknight",
          "collection": "workspaces",
          "model": "workspace",
          "rights": [
            "POST",
            "GET",
            "PUT",
            "DELETE"
          ],
          "settings": {
            "columns": {
              "_id": {
                "title": "id"
              },
              "name": {
                "title": "Name"
              }
            }
          }
        },
        "authMethod": "name",
        "login": {
          "username": "test",
          "password": "test"
        },
        "buttons": {
          "openNewWindow": true,
          "backTo": true,
          "expandCollapse": false
        }
      }
    ],
```

To access the full workspace template click <a href="/templates/create-workspace.json" target="_blank">here</a>

## Mandatory properties

> ⚠️ Properties with a \* are mandatory
{.is-warning}

| Property     | Type    | Description                                                  |
| ------------ | ------- | ------------------------------------------------------------ |
| hideElements | array   | Ask iframe to automatically hide elements list in this property |
| _id*         | string  | The unique id of the box                                     |
| name*        | string  | The name of the box depending on what is inside              |
| iframe       | boolean | Integrate the service inside the app in an iframe            |
| urlBg*       | string  | URL of the background image of the box                       |
| url          | string  | URL of the service you want to enter                         |
| autoExpand   | boolean | Open the box automatically when you click on the section     |
| smartTable   | object  | Contains the smartTable config, check [smartTables](https://docs.cashstory.com/getting_started/smarttable) documentation for more informations. |
| authMethod   | string  | Name of the authentification service in the box              |
| login        | object  | Contain login properties described below                     |
| buttons      | object  | Contain properties of buttons described below                |

## Optional properties

**```login``` object properties**

| Property  | Type   | Description           |
| --------- | ------ | --------------------- |
| username* | string | Username use to login |
| password* | string | Password use to login |
Json:
```json
"login": {
	"username": "",
  "password": ""
}
```
**```buttons``` object properties**

![box-buttons.png](/box-buttons.png =750x40)

| Property       | Type    | Description                                      |
| -------------- | ------- | ------------------------------------------------ |
| notebookUrl | string | Url that calls for a jupyter notebook            |
| expandCollapse* | boolean | Show button to expand the box iframe             |
| openNewWindow*  | boolean | Show button to open the box link in a new window |
| backTo*         | boolean | Show button to go back to the section page       |
Json:
```json
"buttons": {
  "notebookUrl": "http://jupyter-bob_40cashstory_2Ecom:5000/start/10a61b541d901cbded8eb41d766d0824c351989a96f1c32dc94a8d3e51ba",
	"openNewWindow": true,
  "backTo": true,
  "expandCollapse": true
}
```

## Configuration example : 

Here are some boxes configuration examples : 

**Toucan app**
```json
"box": [
  {
  	"hideElements": [],
     "_id": "5e4a71f1e4e7448572b777bc",
     "name": "Toucan Toco",
     "urlBg": "https://task.cashstory.com/cfs/files/attachments/J3xwxdJEJprH3ijW8/toucantoco.png?token=eyJhdXRoVG9rZW4iOiJ5VGxYS3FUYjVvVlhrZVRtMTQ0UFBrRzdJSlFqaDZTek5TSkpna1o5Z0ZCIn0%3D",
     "url": "https://cashstory.toucantoco.com/",
     "iframe": true,
     "autoExpand": false,
     "authMethod": "toucan",
     "login": {
      "username": "",
      "password": ""
    }
   }
]
```
**Jupyter**
```json
"box": [
  {
  	"hideElements": [],
    "_id": "5dt8c6cf57f7aeb29ecdc689",
    "name": "Jupyter Notebook",
    "iframe": true,
    "urlBg": "https://jupyter.org/assets/nav_logo.svg",
    "url": "https://datafactory.cashstory.com/hub/login",
    "autoExpand": false,
    "authMethod": "jupyter",
    "login": {
      "username": "",
      "password": ""
    }
   }
],
```
**Wekan**
```json
"box": [
  {
    "hideElements": [],
    "_id": "5da87aef502d6c401f3aa725",
    "name": "Wekan",
    "urlBg": "https://api.dev.cashstory.com/api/v1/files/672962-1583441620716.png",
    "url": "https://task.cashstory.com/",
    "iframe": true,
    "autoExpand": false
   }
],
```
**Spreadsheet**
```json
"box": [
	{
  	 "hideElements": [],
     "_id": "5da555a8918b2c1ffbauaec4",
     "name": "Spreadsheet",
     "iframe": false,
     "urlBg": "https://task.cashstory.com/cfs/files/attachments/wSLEFmNa9T6EYQumT/googlespreadsheet.png?token=eyJhdXRoVG9rZW4iOiJya1VOekdoeE1sUEpsY1JCNHhyNXl6TTEyZjZTMlNKdndXUTcyOEhrUzRWIn0%3D",
     "url": "https://docs.google.com/spreadsheets/u/0/?tgif=d",
     "autoExpand": false
     "login": {
       "username": "",
       "password": ""
     }
   }
],
```

**PowerBI**

```json
"box": [
	{
  	"hideElements": [],
    "_id": "5e133000f63ccf76708917d5",
    "name": "Power BI",
    "urlBg": "https://task.cashstory.com/cfs/files/attachments/YWxSdbjcgHJ6yAywb/power%20bi.png?token=eyJhdXRoVG9rZW4iOiJjOGxZUmlJWm5lb3NyUE1DRGtWMzhmM3lrTE9neUM4ZzdqUnR5d2VMZmJLIn0%3D",
    "url": "https://app.powerbi.com/home",
    "iframe": true,
    "autoExpand": false
   }
],
```

**Excel**

```json
"box": [
	{
  	"hideElements": [],
    "_id": "5ea87b07702c6c73483aa0b4",
    "name": "Excel",
    "iframe": false,
    "urlBg": "https://task.cashstory.com/cfs/files/attachments/jkNctAoiZrBkPdGeP/excel.png?token=eyJhdXRoVG9rZW4iOiJya1VOekdoeE1sUEpsY1JCNHhyNXl6TTEyZjZTMlNKdndXUTcyOEhrUzRWIn0%3D",
    "url": "https://products.office.com/en/excel",
    "autoExpand": false
   },
],
```

**Trello**

```json
"box": [
	{
  	"hideElements": [],
    "_id": "5ddddafa90b583d6f6c64807",
    "name": "Trello",
    "iframe": false,
    "urlBg": "https://task.cashstory.com/cfs/files/attachments/3AH68hmRM6XQYM9Xd/trello.png?token=eyJhdXRoVG9rZW4iOiJya1VOekdoeE1sUEpsY1JCNHhyNXl6TTEyZjZTMlNKdndXUTcyOEhrUzRWIn0%3D",
    "url": "https://trello.com/login",
    "autoExpand": false
	},
],
```

**Gmail**

```json
"box": [
	{
  	"hideElements": [],
    "_id": "5dcde69793c7844d70d64776",
    "name": "Gmail",
    "iframe": false,
    "urlBg": "https://task.cashstory.com/cfs/files/attachments/xMtphHNZxtXDSW8eS/gmail.png?token=eyJhdXRoVG9rZW4iOiJya1VOekdoeE1sUEpsY1JCNHhyNXl6TTEyZjZTMlNKdndXUTcyOEhrUzRWIn0%3D",
    "url": "https://mail.google.com/mail/u/0/#inbox",
    "autoExpand": false
  },
],
```

**Slack**

```json
"box": [
	{
  	"hideElements": [],
    "_id": "5dcae47897b573c297d74555",
    "name": "Slack",
    "iframe": false,
    "urlBg": "https://task.cashstory.com/cfs/files/attachments/57Br5HYja2bgZxff2/slack.png?token=eyJhdXRoVG9rZW4iOiJya1VOekdoeE1sUEpsY1JCNHhyNXl6TTEyZjZTMlNKdndXUTcyOEhrUzRWIn0%3D",
    "url": "https://slack.com/signin",
    "autoExpand": false
  },
],
```








