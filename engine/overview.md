---
title: Overview
description: 
published: true
date: 2020-06-18T14:50:50.576Z
tags: 
editor: markdown
---

# Introduction

Bob brain is a modern, cloud-based data pipeline. Use it to import data from any of a huge number of inputs, perform mapping and transformation if/as necessary, and then load that data into your output or "data destination" (a data warehouse such as Amazon Redshift, Google BigQuery, Microsoft Azure, Snowflake, or cloud-based data store such as Amazon S3) for analysis.

Bob brain is created with Jupyter notebook. Arround it there is a FTP service which helps you to get files and functions.

Bob lib the python library CashStory is building to make data scripting easy to any Finance or IT professional that would like to enhance their skillset !

As simple as a series of Excel formulas, Bob's library will blow your mind.

We will here explain here what you can do with it.

## Getting started

Bob brain makes it easy to get data from your data source to your data destination.

The process looks like this:

1. Create an output ("Where will your data live after extraction?").
2. Create an input ("What is your data source or stream?").
3. That's it! Your data starts to flow from your input(s) to your output right away.

The schema mapping is done automatically (but you can easily customize that via the mapper). If you want to do any transformation of your data prior to loading, use our powerful Code Engine. If anything unexpected happens, don't worry. Any events that fail to load are captured.

When you log in Jupyter, you arrive at the notebook page. This is a graphical representation of your data pipeline setup — data flows from your inputs on the left, through the Code Engine, then the Mapper, and then into your Output (also known as the Data Destination). From the notebook page you can access any part of the process: Input, Code Engine, Mapper, Restream Queue, and Output. Also, this is where you go to add new Inputs.

# Jupyter

Bob brain uses JupyterLab environement: https://datascience.cashstory.com/

<a href="https://jupyter.org/" target="_blank">JupyterLab</a> is a web-based interactive development environment for Jupyter notebooks, code, and data. JupyterLab is flexible: configure and arrange the user interface to support a wide range of workflows in data science, scientific computing, and machine learning. Jupyter is extensible and modular: write plugins that add new components and integrate with existing ones.

![jupyter-notebook.png](/jupyter-notebook.png =750x400)

## Create user 

This uses GitHub OAuth to authenticate users.
It requires that you create and register on GitHub first by filling out a form on the GitHub site.

To create a jupyter user we use a notebook in JupyterLab : **add_user_jupyter.ipynb**
It create a new user with an email and password and check that this user does not already exist.
# FTP
The **File Transfer Protocol** (**FTP**) is a standard network protocol used for the transfer of computer files between a client and server on a computer network.

FTP is built on a client-server model architecture using separate control and data connections between the client and the server. FTP users may authenticate themselves with a clear-text sign-in protocol, normally in the form of a username and password.

## Create user 

To create a new ftp user we use a JupyterLab notebbok : **add_user_ftp.ipynb**
The user is created with an email and password. In this notebook you can also see the user info on service ftp. 