---
title: Bob lib
description: 
published: true
date: 2020-07-09T14:40:17.300Z
tags: 
editor: markdown
---

Bob lib is the python library CashStory is building to make data scripting easy to any Finance or IT professional that would like to enhance their skillset !

# How to create a new lib

Here are the steps you need to follow to add a new function in Bob lib repository. 

### Create your function in a jupyter notebook

First connect to your jupyter lab and create your function in a jupyter notebook. 

![jupyter-notebook.png](/jupyter-notebook.png =740x400)

### Create a new lib in bob brain repo 

In the bob brain repository create a new lib in the **bob** folder using the template example file. Import the new lib in the **__init__.py** file. 

![new-lib.png](/new-lib.png =740x400)

### Add your function in bob brain lib 

Add your imports and function in your new lib. If you have installed modules add the name and version of the module in the **requirements.txt** .

### Create a driver notebook for your lib 

Create a new notebook to be used as a driver. You can use the template_driver.ipynb in bob repository.  In your driver show an example of how to use your function with bob. 

### Add your driver notebook in bob brain repo 

Download your driver file and add it in the bob brain repository in **shared/drivers**. Push your code on dev branch.

![driver-code.png](/driver-code.png =740x400)

### New version of bob lib in jupyter

After building , bob brain code needs to be manually deployed to be available in jupyter lab. Then you have to restart your jupyter server to have the last version.