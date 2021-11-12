---
title: Rendering and converting
description: 
published: true
date: 2021-11-12T13:15:35.408Z
tags: 
editor: markdown
dateCreated: 2021-09-02T02:05:52.949Z
---

It is common for authors to render their documents into a different format to make them easier to read, or to convert to another format for use in another tool. 

# Rendering RFCXML
There are three main ways to render RFCXML:
1. Use the [Author Tools](/https://author-tools.ietf.org) web service
1. Install [xml2rfc]() and run directly
1. Use [rfc2629xslt](https://greenbytes.de/tech/webdav/rfc2629xslt/rfc2629xslt.html) with any XSLT processor

The following table shows the output formats supported by each tool.

| Tool | Supported output formats ||||||||
|    | Plain text | HTML | HTMLised<sup>1</sup> | PDF | EPUB | Nroff | CHM<sup>2</sup> | DOCX |
| :- | :--------- | :--- | :------------------- | :-- | :--- | :---- | :-------------- |
| [Author Tools](/https://author-tools.ietf.org) | Yes | Yes | Yes | Yes | Yes | Yes | No | No |
|  [xml2rfc]() | Yes | Yes | Yes | Yes | Yes | Yes | No | No |
| [rfc2629.xslt](https://greenbytes.de/tech/webdav/rfc2629xslt/rfc2629xslt.html) | Yes | Yes | No | Yes | Yes | No | Yes | No |
| [xml2docx](https://github.com/evyncke/xml2docx) | No | No | No | No | No | No | No | Yes |

Notes:
<sup>1</sup> **HTMLised** is the plain text version with an HTML wrapper and the references and table of contents turned into links.
<sup>2</sup> **CHM** is Microsoft's Compiled Help Module.


# Rendering plain text
There are three main ways to render RFCXML:
1. Use the [Author Tools](/https://author-tools.ietf.org) web service
1. Install [xml2rfc]() and run directly
1. Install [id2xml]() and use that to convert your plain text to RFCXML and then follow the instructions for rendering RFCXML above


# Rendering other formats
If you want to convert from a different source format then you should first convert to RFCXML or Plain Text and follow the instructions above.