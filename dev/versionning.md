---
title: Semantic Versioning
description: 
published: true
date: 2020-03-12T09:57:48.316Z
tags: 
---

# Semantic Versioning

## Overview

Semantic versioning is a formal convention for specifying compatibility using a three-part version number: major version; minor version; and patch. The patch number is incremented for minor changes and bug fixes which do not change the software's application programming interface (API).

## How it works

In sequence-based software versioning schemes, each software release is assigned a unique identifier that consists of one or more sequences of numbers or letters. This is the extent of the commonality; schemes vary widely in areas such as the quantity of sequences, the attribution of meaning to individual sequences, and the means of incrementing the sequences.

Semantic Versioning is a 3-component number in the format of X.Y.Z, where :

- X stands for a major version.
- Y stands for a minor version.
- Z stands for a patch.

![semanticc.png](/semanticc.png)

Cashstory versioning uses a sequence of three digits (Major.Minor.Patch) Breaking changes are indicated by increasing the major number (high risk), new non-breaking features increment the minor number (medium risk) and all other non-breaking changes increment the patch number (lowest risk).

## Advantages of Semantic Versioning :

- You can keep track of every transition in the software development phase.
- Versioning can do the job of explaining the developers about what type of changes have taken place and the possible updates that should take place in the software.
- It helps to keep things clean and meaningful.
- It helps other people who might be using your project as a dependency.
