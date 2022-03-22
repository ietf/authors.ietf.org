---
title: Author Tools web service
description: 
published: true
date: 2021-12-11T22:32:36.367Z
tags: 
editor: markdown
dateCreated: 2021-11-12T12:37:54.926Z
---

The [Author Tools](https://author-tools.ietf.org) web service supports a range of common tasks, thereby reducing the need for authors to install and maintain key tools locally.  These tasks include:
* Validating I-Ds
* Converting from one format to another 

Behind the scenes, this service uses [xml2rfc](https://github.com/ietf-tools/xml2rfc), [kramdown-rfc](https://github.com/cabo/kramdown-rfc), [id2xml](https://github.com/ietf-tools/id2xml), [idnits](https://github.com/ietf-tools/idnits-mirror) and other tools.  The service accepts files in a number of different formats and automatically chains tools as needed to perform the chosen task.  This allows this service to support a greater range of one-stop processes than the individual tools themselves.  For example, the service will accept a Markdown file and generate an EPUB by first running [kramdown-rfc](https://github.com/cabo/kramdown-rfc) to generate the RFCXML and then [xml2rfc](https://github.com/ietf-tools/xml2rfc) to generate the EPUB.

The Author Tools web service is regularly enhanced and suggestions for new tasks to support are welcome.

