---
title: Drafting in WYSIWYG editors
description: 
published: true
date: 2021-10-10T22:20:32.677Z
tags: 
editor: markdown
dateCreated: 2021-08-18T10:58:56.227Z
---

WYSIWYG is used here to mean the class of tools where the author uses a GUI with no visibility of the underlying document format. 

## WYSIWYG toolchains
The toolchains listed here support WYSIWYG editing.

### 1. MS Word with RFC 5385 template and tool
The [Template for Internet-Drafts and RFCs for WinXP MS Word 2000+](https://www.strayalpha.com/tools/) comprises an MS Word template and a Perl script for converting your resulting .docx file into RFC XML.  This is fully documented in [RFC 5385](https://datatracker.ietf.org/doc/html/rfc5385).

### 2. MS Word with RFC Tool
[RFC Tool](https://github.com/hallambaker/PHB-Build-Tools/tree/master/DocTools/rfctool) converts .docx files from MS Word into RFC XML.  This is documented in [draft-hallambaker-rfctool](https://datatracker.ietf.org/doc/html/draft-hallambaker-rfctool).

## Other WYSIWYG
In addiiton to the toolchains listed above, a number of the [XML toolchains](/drafting-in-xml) support near-WYSIWYG drafting.

Other WYSIWYG editors, such as LibreOffice, are not listed because there is no support for exporting or converting to RFC XML, though that can be used for Plain Text drafting.