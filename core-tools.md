---
title: xml2rfc and the Author-Tools web service
description: 
published: true
date: 2021-12-09T04:12:36.522Z
tags: 
editor: markdown
dateCreated: 2021-11-12T12:37:54.926Z
---

# xml2rfc
[xml2rfc](https://github.com/ietf-tools/xml2rfc) is the core tool for validating and transforming RFCXML files.  It can be installed locally for command line (CLI) access, or as part of an automated build system, or in a web service.

# Author Tools web service
The [Author Tools](https://author-tools.ietf.org) web service supports a range of common tasks, thereby reducing the need for authors to install and maintain key tools locally.  These tasks include:
* Validating I-Ds
* Converting from one format to another 

Behind the scenes, this service uses [xml2rfc](https://github.com/ietf-tools/xml2rfc), [kramdown-rfc](https://github.com/cabo/kramdown-rfc2629), [id2xml](https://github.com/ietf-tools/id2xml), [idnits](https://github.com/ietf-tools/idnits-mirror) and other tools.  The service accepts files in a number of different formats and automatically chains tools as needed to perform the chosen task.  This allows this service to support a greater range of one-stop processes than the individual tools themselves.  For example, the service will accept a Markdown file and generate an EPUB by first running [kramdown-rfc](https://github.com/cabo/kramdown-rfc2629) to generate the RFCXML and then [xml2rfc](https://github.com/ietf-tools/xml2rfc) to generate the EPUB.

The Author Tools web service is regularly enhanced and suggestions for new tasks to support are welcome.

