---
title: Profile
description: 
published: true
date: 2020-04-01T09:12:43.931Z
tags: 
---

# User profile
Your profile page is where your personal account details are stored. User account details are configured in a json file.  

Some of the user informations can be updated from his profile page (name, email, company, password ...). You can also log out or delete your account from the "danger zone" tab. 

![profile.png](/profile.png =700x370)
## Overview
Users are represented by a json object :
 ``` json
[
  {
    "_id": "5c11e6g91dd500000484270a",
    "email": "bob@cashstory.com",
    "password": "password",
    "firstName": "bob",
    "lastName": "user",
    "company": {
      "name": "CashStory",
      "size": "1-10people",
      "whatUse": "Work",
      "kind": "Financial Services"
    },
    "manager": "Yes",
    "userRole": "Program/Project Management",
    "tmpAccount": false,
    "phoneNumber": null,
     "workspaceCurrent": {
      "id": "5e0004842a6824c478266e2h",
      "section": 1,
      "box": "5ka8700f502d6c0e366aa67k"
    },
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
    "services": {
      "dkApi": {
        "authMethod": "dkApi",
        "login": {
          "username": "",
          "password": ""
        }
      }
    }
  }
]
 ```
To access the full user template click <a href="/templates/create-user.json" target="_blank">here</a>
## Main properties

> ⚠️ Properties with a \* are mandatory
{.is-warning}

| Property          | Type    | Description                                                  |
| ----------------- | ------- | ------------------------------------------------------------ |
| _id*              | String  | Unique user id                                               |
| email*            | string  | Email adress of the user                                     |
| password*         | string  | Password of the user that will be used to login              |
| firstname*        | string  | Firstname of the user                                        |
| lastname*         | string  | Lastname of the user                                         |
| company*          | object  | Contains the user company properties decribed down below.    |
| manager*          | string  | "Yes" if the user is manager , "No" if is not.               |
| userRole*         | string  | User function in the company                                 |
| tmpAccount*       | boolean | Temporary account true/false                                 |
| phoneNumber*      | string  | Phone number of the user                                     |
| workspaces*       | object  | Workspaces id this user has access to. Properties are decribed down below. You can find workspaces properties in the [home page](https://docs.cashstory.com/getting_started/home_page) documentation. |
| workspaceCurrent* | object  | Contains current workspace properties described below        |
| services*         | object  | Name of the services you want to enable for this user. Properties decribed down below. |
| role*             | string  | Empty by default , "admin" to have admin access              |

**```company``` object properties**

| Property | Type   | Description                             |
| -------- | ------ | --------------------------------------- |
| name*    | string | Name of the company                     |
| size*    | string | Number of people working in the company |
| whatUse* | string | What is the use for this company        |
| kind*    | string | Kind of company                         |

**```workspaceCurrent``` object properties**

| Property | Type   | Description                 |
| -------- | ------ | --------------------------- |
| id*      | string | Id of the current workspace |
| section  | number | Number of the section       |
| box      | string | Id of the box               |
| name     | string | Name of this workspace      |
| logo     | string | Logo of this workspace      |

**```services``` object properties**

| Property    | Type   | Description                       |
| ----------- | ------ | --------------------------------- |
| authMethod* | string | Name of the service use for login |
| login*      | object | username and password             |




