---
title: Workspaces
description: 
published: true
date: 2020-04-01T08:53:15.952Z
tags: 
---

# Workspaces

In CashStory OS, each user has is own workspace configured.

We can configure :
- Logo and name of the workspace
- Menu and section and  [boxes](https://docs.cashstory.com/getting_started/boxes) 



Workspaces are to be configured in json format.

## Overview

This json configuration file defines the properties of a workspace :
```json
{
  "_id": "5f4b37c6r7e7160003c780e0",
  "logo": {
    "url": ".../../../assets/logo/logo.png",
    "name": "testUpload"
  },
  "name": "default",
  "menu": [
    {
      "title": "Data Story",
      "icon": "eye",
      "sectionId": 1
     },
     {
       "title": "Activity Manager",
       "icon": "tasks",
       "sectionId": 2
     }
  ],
  "sections": [
    {
        "box": [],
        "id": 1,
        "title": "Stories",
        "description": "Follow your financial & extra-financial performance"
    }
  ],
  "creatorId": "5c41bf7b800fe50004ca65e9"
}
​
```
To access the full workspace template click <a href="/templates/create-workspace.json" target="_blank">here</a>

## Configuration

To create a new workspace you need to access the workspace smart table on <a href="https://bob.cashstory.com/" target="_blank">cashstory</a>
(you need admin authorization to access it).

![capture_d’écran_2020-03-03_à_15.58.49.png](/capture_d’écran_2020-03-03_à_15.58.49.png)

You can go on the "+" button to add a new workspace, this will generate a new json configuration file.  

**Top level properties**

> ⚠️ Properties with a \* are mandatory
{.is-warning}

| Property   | Type   | Description                                   |
| ---------- | ------ | --------------------------------------------- |
| _id*       | string | Workspace unique id                           |
| logo*      | object | Contains logo properties described below.     |
| name*      | string | The name of this workspace                    |
| menu*      | object | Contains menu properties described below.     |
| sections*  | object | Contains sections properties described below. |
| creatorId* | string | Id of the creator of this workspace           |

**```logo``` object properties**

| Property | Type   | Description                                                  |
| -------- | ------ | ------------------------------------------------------------ |
| url*     | string | URL of the logo you want to display in the header of the workspace. |
| name*    | string | Name for this logo                                           |
Json:
```json
"logo": {
    "url": ".../../../assets/logo/logo.png",
    "name": "logo"
}
```
**```menu``` object properties**

| Property   | Type   | Description                                                  |
| ---------- | ------ | ------------------------------------------------------------ |
| title*     | string | Title of the menu                                            |
| icon*      | string | Icon of the menu. You need to use a <a href="https://fontawesome.com/" target="_blank">Font awesome</a> icon name. |
| sectionId* | number | Id of the section in which the menu will be                  |
Json:
```json
  "menu": [
    {
      "title": "Data Story",
      "icon": "eye",
      "sectionId": 1
     }
  ]
```
**```section``` object properties**

| Property     | Type   | Description                                                  |
| ------------ | ------ | ------------------------------------------------------------ |
| id*          | number | Number of the section                                        |
| title*       | string | Title of the section                                         |
| description* | string | Short description in relation with this section              |
| box*         | array  | Contains the boxes config, check [boxes](https://docs.cashstory.com/getting_started/boxes) documentation for more infos. |


