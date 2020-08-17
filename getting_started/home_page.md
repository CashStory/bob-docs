---
title: Home page
description: 
published: true
date: 2020-03-12T14:48:53.470Z
tags: 
---

# Home page

## Overview
When you login in your Cashstory workspace you arrive on your home page. This page regroups two elements , the news feed and your favorites. This two elements are configured in the user configuration file in json format. 

![homepage.png](/homepage.png =650x350)


## Configuration

The ```workspaces``` object is used to configure the user news and favorite elements of the workspace. This object is used inside the [user](https://docs.cashstory.com/getting_started/profile) configuration.

``` json
    "workspaces": [
      "5cs4dg2b6214322f2915282f": {
        "news": {
          "sources": [],
          "categories": [],
          "name": "News",
          "lang": "en"
        },
        "favorites": {
          "boxes": [
            {
              "_id": "5d92000c5g009e0114ddehhh",
              "name": "Tutoriel",
              "description": "Welcome Bob",
              "attachement": "https://www.youtube.com/embed/7u7vcrKDphg",
              "attachement_type": "video",
              "target": "https://www.youtube.com/watch?v=9QGMz9beIL0",
              "target_type": "external",
              "column": 12
            }
          ],
        	"name": "Fav"
     	  },
      	"name": "demo"
      }
    ],
  ``` 

**Top level properties**

| Property   | Type   | Description                           |
| ---------- | ------ | ------------------------------------- |
| name*      | string | Name of the workspace                 |
| news*      | object | Contains properties for the news      |
| favorites* | object | Contains properties for the favorites |

**```news``` object properties**

| Property   | Type   | Description                       |
| ---------- | ------ | --------------------------------- |
| name*      | string | Name of the news part             |
| lang       | string | Language use                      |
| class      | string | Give a class to this news element |
| sources    | array  | Choose a source for the news      |
| categories | array  | Add categories                    |
​
**```favorites``` object properties**

| Property | Type   | Description                       |
| -------- | ------ | --------------------------------- |
| name*    | string | Name of the news part             |
| class    | string | Language use                      |
| boxes    | object | Give a class to this news element |

**favorite ```boxes``` object properties**

| Property         | Type   | Description                                                  |
| ---------------- | ------ | ------------------------------------------------------------ |
| _id              | string | Id of the favorite box                                       |
| name*            | string | Name of this favorite                                        |
| description*     | string | Description of this favorite box                             |
| attachement      | string | Url of the attachement for this favorite                     |
| attachement_type | string | Type of the attachement, can be: 'image' / 'video' /'iframe' |
| target           | string | Link where you are redirected when you click on the favorite |
| wp               | object | Check workspaceCurrent properties for this object properties |
| target_type      | string | Type of the target between : 'internal' / 'external'/ 'external_same' |
| column*          | number | Number of column between 1 to 12                             |

