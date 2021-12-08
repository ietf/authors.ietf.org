---
title: Collaborative editing
description: 
published: true
date: 2021-12-08T17:58:32.371Z
tags: 
editor: markdown
dateCreated: 2021-08-25T04:21:06.810Z
---

Collaborative editing is generally the hardest part of authoring an I-D as you will need to keep on top of multiple changes from multiple sources.

### 1. Comparing two I-Ds with rfcdiff
[rfcdiff](https://tools.ietf.org/rfcdiff) is a web service that provides a side-by-side comparison of two documents.  It is generally used to show the differences between two version of the same I-D to see what has changed, or between a submitted I-D and a working draft.

### 2. Using GitHub with i-d-template and internet-draft-template
GitHub is commonly used for collaborative editing of I-Ds.  Two community tools have been written to support this:
* [i-d-template](https://github.com/martinthomson/i-d-template) uses GitHub to automate multiple aspects of the authoring process.
* [internet-draft-template](https://github.com/martinthomson/internet-draft-template) is a GitHub repository template that works with i-d-template by creating a GitHub repository, which includes all of the automation of i-d-template. This newly created repository includes a template Markdown file.