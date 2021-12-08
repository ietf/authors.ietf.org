---
title: Rendering and converting
description: 
published: true
date: 2021-12-08T20:26:17.903Z
tags: 
editor: markdown
dateCreated: 2021-09-02T02:05:52.949Z
---

It is common for authors to render (convert) their documents into a different format to make them easier to read, or to convert to another format for use in another tool. 

# Rendering RFCXML into other formats
There are three main ways to render RFCXML:
1. Use the [Author Tools](/https://author-tools.ietf.org) web service.  
1. Install [xml2rfc](https://github.com/ietf-tools/xml2rfc) and run it directly.
1. Use [rfc2629xslt](https://greenbytes.de/tech/webdav/rfc2629xslt/rfc2629xslt.html) with any XSLT processor (including those embedded in web browsers). This allows those using XML editors to directly render output from that editor and in some editors, to see the results in real time. It also allows viewing the document directly in a browser without a prior conversion step.

The following table shows the output formats supported by each tool.

| Tool | Supported output formats ||||||||
|    | Plain text | HTML | HTMLised<sup>1</sup> | PDF | EPUB | Nroff | DOCX |
| :- | :--------- | :--- | :------------------- | :-- | :--- | :---- | :-------------- |
| [**Author Tools**](/https://author-tools.ietf.org) | Yes | Yes | Yes | Yes | Yes | No | No |
|  [**xml2rfc**](https://github.com/ietf-tools/xml2rfc) | Yes | Yes | Yes | Yes | Yes | Yes<sup>2</sup> | No |
| [**rfc2629xslt**](https://greenbytes.de/tech/webdav/rfc2629xslt/rfc2629xslt.html) | Yes | Yes | No | Yes | Yes | No | No |
| [**xml2docx**](https://github.com/evyncke/xml2docx) | No | No | No | No | No | No | Yes |

Notes:
<sup>1</sup> **HTMLised** is the plain text version with an HTML wrapper and the references and table of contents turned into links.
<sup>2</sup> **nroff** output is onlu supported for RFCXML v2 input files.


# Rendering plain text into other formats
There are three main ways to render plain text:
1. Use the [Author Tools](/https://author-tools.ietf.org) web service.  This takes I-Ds in a number of formats, including Markdown, and directly renders an output document.
1. Install [xml2rfc](https://github.com/ietf-tools/xml2rfc) and run directly
1. Install [id2xml](https://github.com/ietf-tools/id2xml) and use that to convert your plain text to RFCXML and then follow the instructions for rendering RFCXML above


# Rendering other formats
If you want to convert from a different source format then you should first convert to RFCXML or Plain Text and follow the instructions above.