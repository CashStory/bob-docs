---
title: How to
description: 
published: true
date: 2020-07-09T14:37:03.807Z
tags: 
editor: markdown
---

# How to update a blog article in the landing ? 

## Step 1: Get the article from Google doc or any other source 

The article should contain : 
- The main picture
- The main title
- Author name
- Subtitle 
- Body of the article
- Tags and hashtags

## Step 2: Create your article body in markdown

Write your article content in markdown in the markdown editor Typora. 
You can download it here : https://typora.io/

## Step 3: Add article in google sheet

Open the landing google sheet (you need authorization to acess it): https://docs.google.com/spreadsheets/d/1Cbtb__YqcdPiOhWsG74UpyZlDzWbz3yR3w2TkIZAJIg/edit#gid=208569976

![landing-gsheet.png](/landing-gsheet.png =700x350)

Then add the new article in the sheet "BLOG" and use the same template than the other articles . There is three columns, one for each language.

## Step 4: Launch script in jupyter

Log in your JupyterLab and go to the landing github project. In the folder **notebook** open the script **landing.ipynb**. When you run the script the landing json translation files are updated with the google sheet values.

Before running the script fill the config with your GitHub username and password , and choose the branch were you want to push the new article:

```
sheet_name = "SITE"
config = {
            'username':'',
            'password':'',
            'github_url':'https://github.com/CashStory/landing.git',
            'branch':'dev',
            'target_folder':'website',
            'action':'push',
            'commit_message':'language'
        }
path = "locales"
blog_sheet_name = "BLOG"
```
- title - name of work book
- sheet_name - name of sheet
- config -  git crendentials
- path - path inside git repository where langague files belongs to 
- blog_sheet_name - name of sheet where blogs written 

You should have a message of sucess after you run the script to tell that the code is pushed. 

## Step 4: Add images

To add images for your article , go in the folder **website** (you need to run the script once to have this folder) . Add your images in **website/static/articles**. Then run the script to push them. 


## Additional informations 

Meta are automatically created for each article in  **pages/_lang/blog/_article.vue**. 

```js
    meta: [
       {
         hid: 'image',
         name: 'image',
         content: this.article.image
       },
       {
         hid: 'description',
         name: 'description',
         content: this.article.description
       },
       {
         hid: 'og:title',
         property: 'og:title',
         content: this.article.title
       },
      
 
 
      {
         hid: 'og:image',
         property: 'og:image',
         content: this.article.image
       },
       {
         hid: 'og:description',
         property: 'og:description',
         content: this.article.description
       },
       { property: 'og:url', content: `${this.host}${this.$route.path}` }
     ]

```

