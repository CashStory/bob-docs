---
title: Architecture
description: 
published: true
date: 2020-03-04T13:45:16.877Z
tags: 
---

# Architecture

Cashstory is an environment that sits on top of an existing desktop operating system to provide additional functionality to web applications. Each app is web-deployed and uses a standard web app server. Apps are not hosted with Cashstory. The developer is in control of the app development process and how apps and Cashstory resources are hosted.

Cashstory's main architectural components are divided into two sections:

- Cashstory Desktop processes
- Cashstory Cloud processes

These components work together to launch and manage the lifecycle of an application. Below is a diagram of the lifecycle of an application from start event to launch. The information below the diagram is organized by Desktop or Cloud Process to help you better understand how all components work together to launch an application in Cashstory.

## Desktop
When a desktop user clicks on the Cashstory desktop icon or a link is clicked on, it invokes the Cashstory OS to complete a sequence of startup events for web app launch. The RVM launches the Runtime by version or realm which is responsible loading the app URL. If the application is an external app using an Cashstory adapter, upon app launch the adapter will invoke the RVM to launch the Runtime.

## Cloud

Once this startup sequence is complete, the Runtime launches and begins to render the app into a window. If the app manifest declares Cashstory Services, the app will request these services and enable service functionality upon app launch.

Cashstory resources for apps can either be hosted through Cashstory Cloud or on-premise. The benefit of Cashstory Cloud is that there is no maintenance required for the customer and it ensures everyone is able to access the latest data instantly from any location without requiring VPN access. It is highly recommended to use Cashstory Cloud over on-premise hosting for Cashstory resources as Cashstory Cloud has built-in security features to protect data and meet compliance requirements.

Cashstory Cloud uses the Amazon Web Services Cloud Front Content Delivery Network (CDN) to host container-related resources for fast, distributed delivery across the globe. Apps using this resource-hosting method still host their app in their own app server. However, Cashstory resources are hosted in Cashstory Cloud to be easily retrieved by the RVM.

Resources hosted in the cloud include logs, icon assets, service configs, and licensing information. The RVM is responsible for managing these resources for the Runtime by delivering logs, fetching and caching app config icon assets and services configs, and reporting licensing and app usage.


![azure.png](/azure.png =330x160) ![aws.jpg](/aws.jpg =330x160)