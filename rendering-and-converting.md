---
title: Rendering and converting
description: 
published: true
date: 2021-11-12T11:56:17.549Z
tags: 
editor: markdown
dateCreated: 2021-09-02T02:05:52.949Z
---

It is common for authors to render their documents into a different format to make them easier to read, or to convert to another format for use in another tool. 

This page explains the conversion options from the two supported source formats of RFCXML and Plain Text into other formats.  If you want to convert from a different source format then you should first convert to one of these two formats.

# Rendering RFCXML
The two main tools for this are [xml2rfc]() and [rfc2629xslt]()

and then refer to this table.

| Output     | Input ||
|            | RFC XML | Plain Text |
| ---------- | :-----: | :--------: |
| **RFC XML**    | - | id2xml |
| **Plain Text** | [xml2rfc]() _or_ [rfc2629.xslt](https://greenbytes.de/tech/webdav/rfc2629xslt/rfc2629xslt.html) | - |
| **HTML**       | [xml2rfc]() _or_ [rfc2629.xslt](https://greenbytes.de/tech/webdav/rfc2629xslt/rfc2629xslt.html) | [xml2rfc]() _or_ [rfcmarkup](https://tools.ietf.org/tools/rfcmarkup/) |
| **HTMLised**<sup>1</sup>   | [xml2rfc]() | [xml2rfc]() |
| **PDF**        | [xml2rfc]() _or_ [rfc2629.xslt](https://greenbytes.de/tech/webdav/rfc2629xslt/rfc2629xslt.html) | [xml2rfc]() |
| **EPUB**       | [xml2rfc]() _or_ [rfc2629.xslt](https://greenbytes.de/tech/webdav/rfc2629xslt/rfc2629xslt.html) | [xml2rfc]() |
| **Nroff**      | [xml2rfc]() | [xml2rfc]() |
| **CHM**<sup>2</sup>        | [rfc2629.xslt](https://greenbytes.de/tech/webdav/rfc2629xslt/rfc2629xslt.html) | - |
| **DOCX**       | [xml2docx](https://github.com/evyncke/xml2docx) | - |

Notes:
<sup>1</sup> **HTMLised** is the plain text version with an HTML wrapper and the references and table of contents turned into links.
<sup>2</sup> **CHM** is Microsoft's Compiled Help Module.


