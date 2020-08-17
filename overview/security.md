---
title: Security
description: 
published: true
date: 2020-03-04T16:48:47.646Z
tags: 
---

# Introduction

With Cashstory, apps are secure by default. Apps are completely partitioned from the native OS – and each other – with sandboxing. Preventing vulnerabilities that can compromise the end user’s desktop and eliminating the need for never-ending security reviews that draw out deployment timelines.

Conventional wisdom has it that slow change equals security. But Google alone delivers major new versions of Chromium every 6 weeks and additional security fixes in between. Cashstory’s engineering team does the hard work of keeping up with Google, making it easy for you to instantly push security fixes and to ensure backward compatibility of your apps.

## Update

Cashstory eliminates Update issues that are common in native desktop development. Long deployment schedules affect not only the developer, but the end user as well. 

**With CashStory, developers can:**

* Eliminate long deployment schedules thanks to technology that allows immediate updates and remote debugging
* Seamlessly deploy to thousands of desktops at once
* Deploy anywhere, at anytime and choose when to update, even on a customer’s desktop

There are also plenty of ways to deploy. Whether it’s a single app or an entire enterprise of apps that need to be deployed, CashStory has a solution.

# Overview 

CashStory is a security first, JavaScript/HTML5 runtime environment built on top of Kubernet  project that also incorporates [Docker](https://www.docker.com/). However, with the use of Docker as part of CashStory OS, we take the following precautions:

1.  Maintain the fidelity of the Docker Security model
2.  Use SSL X.509 by default for all public communication
3.  Prohibit exposure of any Docker API (private or public) to a third party website

In addition, CashStory provides Group Policy controls around all APIs that can access  
sensitive resources, such as the file system.

# Core Principles

CashStory organizes its security philosophy around these core principles:  
• Leverage the Docker security team’s great work  
• Strongly limit vulnerability to Cross Site Scripting  
• All applications must be signed  
• Any code that sits on the filesystem must be checksummed/signed and validated prior to loading  
• Expose full process isolation for application owners to use

>“Gartner asserts that applications deployed in containers are more secure than applications deployed on the bare OS” because even if a container is cracked “they greatly limit the damage of a successful compromise because applications and users are isolated on a per-container basis so that they cannot compromise other containers or the host OS”.
{.is-success}


# InterApplication Messaging
 
CashStory applications uses a private networking interface (PNI) to expose the URL location from which they are loaded as well as the protocol used. This means that one can validate that an application was securely loaded from a specific domain and thus be sure of its identity. Applications that are running outside of the CashStory Runtime (web applications) but that are connected to the PNI, expose their SSL signing signatures so that their identity can also be validated. 

# Encryption / Signing

All Cashstory binaries and libraries are signed by Let’s Encrypt CA. All Cashstory code loaded from the filesystem is checksummed, signed and validated prior to running. Signatures for application assets are exposed via the API for applications to validate.
