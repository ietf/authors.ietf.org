---
title: Drafting in word processors
description: 
published: true
date: 2021-12-14T20:45:40.623Z
tags: 
editor: markdown
dateCreated: 2021-08-18T10:58:56.227Z
---

# Word processor toolchains
A number of community members use word processors for I-D authoring because they are familiar with them and because they have good support for collaborative editing.

## MS Word with RFC 5385 template and tool
The [Template for Internet-Drafts and RFCs for WinXP MS Word 2000+](https://www.strayalpha.com/tools/) comprises an MS Word template and a Perl script for converting your resulting .docx file into RFCXML.  This is fully documented in [RFC 5385](https://datatracker.ietf.org/doc/html/rfc5385).

## MS Word with RFC Tool
[RFC Tool](https://github.com/hallambaker/PHB-Build-Tools/tree/master/DocTools/rfctool) converts .docx files from MS Word into RFCXML.  This is documented in [draft-hallambaker-rfctool](https://datatracker.ietf.org/doc/html/draft-hallambaker-rfctool).

# Supporting tools

## xml2docx
[xml2docx](https://github.com/evyncke/xml2docx) generates an Office Open XML (.DOCX) format document from an RFCXML document.