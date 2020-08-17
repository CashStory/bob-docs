---
title: API's & Drivers
description: 
published: true
date: 2020-08-17T16:57:35.603Z
tags: 
editor: markdown
---

# Overview
CASHSTORY offers APIs and adapters that are easy to integrate with any standard web application. Gain key Cashstory functionality by connecting these APIs and/or adapters to your application. Setup varies by use case. Here are some further details on how to use each API.

# Darkknight CashStory Api 

## Introduction
Darknight is our backend coded in nodejs

## Dev Stack
Whole stack in <a href="https://www.typescriptlang.org" target="_blank">Typescript</a>.

This project uses the <a href="https://en.wikipedia.org/wiki/MEAN_(software_bundle)" target="_blank">MEAN stack</a> :
* <a href="http://www.mongoosejs.com" target="_blank">Mongoose.js</a> (<a href="https://www.mongodb.com" target="_blank">MongoDB</a>): database
* <a href="http://expressjs.com" target="_blank">Express.js</a>: backend framework 
* <a href="https://nodejs.org" target="_blank">Node.js</a>: runtime environment

Other tools and technologies used:
* <a href="https://jwt.io" target="_blank">JSON Web Token</a>: user authentication
* <a href="https://github.com/dcodeIO/bcrypt.js" target="_blank">Bcrypt.js</a>: password encryption

## Prerequisites
1. Install <a href="https://nodejs.org" target="_blank">Node.js</a> and <a href="https://www.mongodb.com" target="_blank">MongoDB</a>
2. From project root folder install all the dependencies: `npm i`
3. Init env file `npm start init.env`
3. Edit `.env` file with theses vars
```
MONGODB_URI=mongodb://URLOFYOURMONGO
MAX_WORKER=1
WEKAN_URI=https://task.cashstory.com
FRONT_URI=https://bob.dev.cashstory.com
FTP_URI=https://ftp.cashstory.com
FTP_AUTH_TOKEN=APIKEY
JUPYTER_URI=https://datascience.cashstory.com
JUPYTER_AUTH_TOKEN=APIKEY
BACK_URI=https://darkknight.dev.cashstory.com
SECRET_TOKEN=RANDOMTOKEN
TWILIO_NUMBER=TWIOLIOMOBILE
TWILIO_SID=TWIOLIOSID
TWILIO_TOKEN=TWIOLIOTOKEN
EMAIL_HOST=SMTPSERVER
EMAIL_PORT=465
EMAIL_SECURE=true
EMAIL_USER=EMAIL
EMAIL_PASSWORD=PASS
EMAIL_FROM=EMAIL
EMAIL_ADMIN=EMAIL1, EMAIL2
SLACK_WEBHOOK=WEBHOOKURL
SLACK_NAME=NAME
SLACK_CHANNEL=#CHANNEL
API_KEY_CLOCKIFY=APIKEY
API_KEY_WAKATIME=APIKEY
CRON_RECURRENCE=CRON
DIALOGFLOW_ID=ID
DIALOGFLOW_PRIVATE_KEY=APIKEY
DIALOGFLOW_CLIENT_EMAIL=EMAIL
TZ=Europe/Paris
DK_ENV=dev
WORKSPACEDEFAULT=5cb5dc2b6314346f2915222d
DEBUG=true
NODE_ENV=production
```

## Run

### Development mode
`npm start`: <a href="https://github.com/kentcdodds/nps#readme" target="_blank">nps</a> execute TypeScript compiler and Express server.

Express files are being watched. Any change automatically creates a new bundle, restart Express server.

### Production mode
`npm start serve.prod`: run the project with a production bundle at <a href="http://localhost:3000" target="_blank">localhost:3000</a>

## Deploy (with docker)
1. Exemple using docker-compose and image cashstory/node-git:latest
``` 
version: '3'

services:
  darkknight:
    image: registry.gitlab.com/bobcashstory/darkknight:dev
    container_name: darkknight-dev
    restart: always
    networks:
      - galaxy_cs-tier
    environment:
      - MONGODB_URI=URI
      - SECRET_TOKEN=TOKEN
      - PORT=8080
      - SLACKTEE_TOKEN=TOKEN
      - SLACK_NAME=NAME
      - SLACK_CHANNEL=#CHANNEL
      - WEKAN_URI=https://task.cashstory.com
      - FRONT_URI=https://bob.dev.cashstory.com
      - FTP_URI=https://ftp.cashstory.com
      - FTP_AUTH_TOKEN=TOKEN
      - CS_DATABASE=darkknight-dev
      - EMAIL_HOST=HOST
      - EMAIL_PORT=PORT
      - EMAIL_SECURE=true
      - EMAIL_USER=apikey
      - EMAIL_PASSWORD=PASS
      - EMAIL_FROM=bob@cashstory.com
      - EMAIL_ADMIN=bob@cashstory.com, jeremy.ravenel@cashstory.com
      - DIALOGFLOW_ID=ID
      - DIALOGFLOW_PRIVATE_KEY=KEY
      - DIALOGFLOW_CLIENT_EMAIL=EMAIL
      - JUPYTER_URI=https://datascience.cashstory.com
      - JUPYTER_AUTH_TOKEN=TOKEN
      - CRON_RECURRENCE=58 12 * * *
      - DK_ENV=dev
      - API_KEY_CLOCKIFY=APIKEY+g5t
```
## Running linters
Run `npm start lint` to execute all lint

## Technical documentation
<iframe frameborder="0" width="100%" height="1500px" scrollable="no" src="https://api.cashstory.co/docs"></iframe>

# Bob CashStory Front

## Introduction
Bob is the frontend of our workspace https://bob.cashstory.com/

## Dev stack

The frontend is generated with <a href="https://github.com/angular/angular-cli" target="_blank">Angular CLI</a> . 

This project uses the <a href="https://en.wikipedia.org/wiki/MEAN_(software_bundle)" target="_blank">MEAN stack</a> :
* [**A**ngular 7+](https://angular.io): frontend framework

Other tools and technologies used:
* <a href="https://cli.angular.io" target="_blank">Angular CLI</a>: frontend scaffolding
* <a href="http://www.getbootstrap.com" target="_blank">Bootstrap</a>: layout and styles
* <a href="http://fontawesome.io" target="_blank">Font Awesome Pro</a>: icons
* <a href="https://jwt.io" target="_blank">JSON Web Token</a>: user authentication
* <a href="https://github.com/auth0/angular2-jwt/tree/v1.0" target="_blank">Angular 2 JWT</a>: JWT helper for Angular
* <a href="https://github.com/stylelint/stylelint" target="_blank">stylelint</a>: style linter
* <a href="https://github.com/htmllint/htmllint" target="_blank">htmllint</a>: html linter

## Prerequisites
From project root folder install all the dependencies: `npm i`

## Run
### Development mode with local backend
`npm start`: <a href="https://github.com/kentcdodds/nps#readme" target="_blank">nps</a>  Angular build, TypeScript compiler.

A window will automatically open at [localhost:4200](http://localhost:4200). Angular files are being watched. Any change automatically creates a new bundle and reload your browser.

### Development mode with prod backend
`npm start live.prod`: <a href="https://github.com/kentcdodds/nps#readme" target="_blank">nps</a>  Angular build, TypeScript compiler.

A window will automatically open at  <a href="http://localhost:4200" target="_blank">localhost:4200</a>. Angular files are being watched. Any change automatically creates a new bundle and reload your browser.

### Production mode
`npm start serve.prod`: run the project with a production bundle and AOT compilation listening at <a href="http://localhost:3000" target="_blank">localhost:3000</a>

## Running linters
Run `npm start lint` to execute all lint

Run `npm start lint.front` to execute the frontend TS linting via <a href="https://github.com/palantir/tslint" target="_blank">Tslint</a>.

Run `npm start lint.html` to execute the frontend HTML linting via <a href="https://github.com/htmllint/htmllint" target="_blank">Htmllint</a>.

Run `npm start lint.style` to execute the frontend SCSS linting via <a href="https://github.com/sasstools/sass-lint" target="_blank">SASS-Lint</a>.

## Further help
To get more help on the `angular-cli` use `ng --help` or go check out the <a href="https://github.com/angular/angular-cli/blob/master/README.md" target="_blank">Angular-CLI README</a>.

# License
You agree to the Developer License to download, use, test, or build with any CASHSTORY Technology. The code in each individual API section is covered by the CASHSTORY Developer License. If you have any questions, please contact support@cashstory.com.