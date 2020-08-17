---
title: Landing
description: 
published: true
date: 2020-06-18T14:52:13.116Z
tags: 
editor: markdown
---



# Overview
To go to the Cashstory landing follow this link : https://cashstory.com/en/

The sections available in the landing are : 
- Header
- Sign in 
- Free account  
- Features
- Clients
- Feedbacks
- Partners
- Register 
- Footer
- Blog 
- Privacy 

The website is available in 3 languages : 
- English 
- French 
- Spanish 

## Header

![landingheader.png](/landingheader.png =700x50)

The header is at the top of all pages and stay fixed on scroll.  You can find it in the code in the folder component : **components/Header.vue**

![landingfiles.png](/landingfiles.png =300x100)

To display it on all pages the header component  is called in the **layouts/default.vue** file.

The header contains the following elements: 
- Cashstory logo
- Sign in button
- Free account button
- Lang selector (english, french, spanish)

Each element is link to a function that can be modified in the script section  (under the html of page) :
- Cashstory logo :  ```:href="linkLocal('/')"```
- Sign in button :  ```@click="goToLogin()"```
- Free account button :  ```:href="linkLocal('/#account')"```
- Lang selector : ```@click="selectLang('lang')”```

## Footer

![landindfooter.png](/landindfooter.png =700x110)

The footer is displayed at the bottom of all pages. You can find it in the code in the folder component : **components/Footer.vue**

![landingfiles.png](/landingfiles.png =300x100)

To display it on all pages the footer component  is called in the **layouts/default.vue** file.

The footer contains five links that redirects you on other pages: 
- Blog:  **/blog**
- Legal:  **/legal**
- Privacy:  **/legal#privacy**
- Contact

Then you have some social medias buttons with svg logos: 
- Twitter
- Facebook
- Linkedin
- Youtube
- Github

The path of link and buttons is in the **components/Footer.vue** file.

## Register

You can find the register (account creation pipeline) directly in cashstory’s landing page.

The informations required during that phase are : 
- Email : “name@company.com” 
- Full Name 
- Mobile
- Password
- Token (6 digits)

![landingregister.png](/landingregister.png =700x400)

It can also be accessible through bob login page  by clicking on “Register”.

In the project code you can find the register pipe in the components folder : **components/Register.vue**

![capture_d’écran_2020-03-19_à_09.27.30.png](/capture_d’écran_2020-03-19_à_09.27.30.png =250x110)

Each information you enter in the input is pushed into the database when you click on the next step.  Each step is triggered with a function in the script section in the html. 

The vuejs form validation is used in the code to validate the email (https://fr.vuejs.org/v2/cookbook/form-validation.html). 

## Multi-languages translation 

The module works with the vue-i18n plugin that we installed on the project with npm.  
This is the doc used to install the plugin :
https://medium.com/@allenhwkim/multiple-language-with-nuxt-vuejs-efc3dad45eac

You can find the plugin configuration in this files : 
- **plugins/i18n.js** (sets up VueI18n plugin)
- **store/index.js** (what language is currently in use)
- **middleware/i18n.js** (handle different languages)

There is a translation file for each languages in the locales folder: 
- **locales/en.json**
- **locales/fr.json**
- **locales/es.json**

![landingcode.png](/landingcode.png =700x400)

The json translation files structure looks like this : 
```json
"pagename": {
   "section_1": {
     "element_1": "text",
     "element_2": "text"
   },
   "section_2": {
     "element_1": "text",
     "element_2": "text"
   },
 }
```

First we have the page name and then for each section of the page we have the different paragraphs in an element. 

The json files are generated with a python script in **landing/notebook**. The script gets the translation from a google sheet. To updade the text you need to change it in the google sheet and then run the script in Jupyter to push the changes on GitHub.

To display the text in the html pages you need to call the variable like this : 
``` 
{{ $t('pagename.section_1.element_1') }} 
```

The button to select your language is in the header component. 
