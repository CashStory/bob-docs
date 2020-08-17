---
title: bob
description: 
published: true
date: 2020-02-11T18:27:02.543Z
tags: 
---

# Intro
Your content here

## Stack

Bob is generated with [Angular CLI](https://github.com/angular/angular-cli). 

This project uses the [MEAN stack](https://en.wikipedia.org/wiki/MEAN_(software_bundle)):
* [**A**ngular 8+](https://angular.io): frontend framework

Other tools and technologies used:
* [Bootstrap](http://www.getbootstrap.com): layout and styles
* [Font Awesome Pro](http://fontawesome.io): icons
* [JSON Web Token](https://jwt.io): user authentication
* [Angular 2 JWT](https://github.com/auth0/angular2-jwt/tree/v1.0): JWT helper for Angular
* [stylelint](https://github.com/stylelint/stylelint): style linter
* [htmllint](https://github.com/htmllint/htmllint): html linter

## Dev Prerequisites
1. From project root folder install all the dependencies: `npm i`

## Run
### Development mode with local backend
`npm start`: [nps](https://github.com/kentcdodds/nps#readme) Angular build, TypeScript compiler.

A window will automatically open at [localhost:4200](http://localhost:4200). Angular files are being watched. Any change automatically creates a new bundle and reload your browser.

### Development mode with prod backend
`npm start live.prod`: [nps](https://github.com/kentcdodds/nps#readme) Angular build, TypeScript compiler.

A window will automatically open at [localhost:4200](http://localhost:4200). Angular files are being watched. Any change automatically creates a new bundle and reload your browser.

### Production mode
`npm start serve.prod`: run the project with a production bundle and AOT compilation listening at [localhost:3000](http://localhost:3000) 

## Running linters
Run `npm start lint` to execute all lint

Run `npm start lint.front` to execute the frontend TS linting via [TSLint](https://github.com/palantir/tslint).

Run `npm start lint.html` to execute the frontend HTML linting via [HTMLHint](https://github.com/htmlhint/HTMLHint).

Run `npm start lint.style` to execute the frontend SCSS linting via [SASS-Lint](https://github.com/sasstools/sass-lint).

## Further help
To get more help on the `angular-cli` use `ng --help` or go check out the [Angular-CLI README](https://github.com/angular/angular-cli/blob/master/README.md).

### Author
* [Martin donadieu](https://github.com/riderx)
