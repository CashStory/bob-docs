---
title: Blog 
description: 
published: true
date: 2020-06-12T10:15:28.012Z
tags: 
editor: markdown
---

![blog-page.png](/blog-page.png =700x350){.align-center}

The blog page contains two elements  :
- Banner
- Tabs
- Article cards

The blog page code is in the blog folder in the index.vue file :
**pages/_lang/blog/index.vue**

The tabs allow you to find an article by a tag . You can add tags in each articles in json translation files in the **/locale** folder:

```json
tags: ['#treasury', '#finance'],
```


Articles are displayed in cards with a cover picture , a main title, subtitle and the author. When you click on a card you are redirected to the article.  

For more infos about how to create a new blog article check  [how to](https://docs.cashstory.com/landing/howto)  documentation.