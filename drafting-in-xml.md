---
title: Drafting in XML
description: 
published: true
date: 2021-10-10T21:03:25.287Z
tags: 
editor: markdown
dateCreated: 2021-08-18T10:56:56.326Z
---

## Introducing RFC XML
RFC XML, also called 'The "xml2rfc" vocabulary', is an XML markup language that has been used as the canonical format for published RFCs since RFC 8650 in November 2019.  

The current version of RFC XML, v3, is formally defined in a RELAX NG Compact Syntax (RNC) schema as documented and explained in [RFC 7991](https://www.rfc-editor.org/info/rfc7991). Since the publication of RFC 7991, a number of changes have been made to the schema that are currently documented in the [implementation notes for RFC 7991](https://datatracker.ietf.org/doc/html/draft-levkowetz-xml2rfc-v3-implementation-notes-11).

The previous version of RFC XML, v2, is still actively used as some of the tools that process RFC XML do not fully support v3 or still default to v2. RFC XML v2 is documented and explained in [RFC 7749](https://www.rfc-editor.org/info/rfc7749).

A small [library](https://tools.ietf.org/tools/templates/) of RFC XML templates is available though these are under review and likely to be updated and moved.

Published RFCs go through a 'prep' process that makes multiple changes to the RFC XML in order to support the long time archival nature of RFCs.  While RFCs validate with the same schema, using an XML RFC as a template for an Internet-Draft is not recommended. 

## What to look for in an XML toolchain
There are two key features to look for in an XML toolchain:
1. RNC schema validation. This ensures that your document is valid RFC XML as you type it.
1. RNC aware editing support. 

To take advantage of these features your XML code must include an [`<?xml-model ...>`](https://www.w3.org/TR/xml-model/) processing instruction as found in the [schema aware templates]() below.

## RFC XML toolchains
The following XML toolchains have been reported as in use by IETF community members.  These are all interactive XML editors. 

### 1. Emacs editor in nXML Mode
The popular open source editor Emacs includes [nXML Mode](https://www.gnu.org/software/emacs/manual/html_mono/nxml-mode.html), which enables validation and schema-sensitive editing when you use an RNC schema. 

### 2. XMLmind XML Editor (XXE) with xml2rfc-xxe
[XMLmind XML Editor (XXE)](https://www.xmlmind.com/xmleditor/) is a commercial near-WYSIWYG XML editor with a free edition for personal use.  XXE supports RNC schema validation and context-sensitive editing.

A community developed configuration for XXE, [xml2rfc-xxe](https://github.com/wkumari/xml2rfc-xxe/) is available, providing additional context-sensitive editing features. 

### 3. Oxygen XML Editor
[Oxygen XML Editor](https://www.oxygenxml.com/xml_editor.html) is a commercial XML editing tool that comes in different versions with a number of different licensing options. All versions support RELAX NG validation and some support syntax highlighting and intelligent auto-completion. The premium version also supports collaborative edIting, including tracked changes and comment review.

The same company also makes [Oxygen Content Fusion](https://www.oxygenxml.com/content_fusion.html), which support web-based collaborative editing and document review.

## Supporting tools
Authors writing in XML may find the following tools helpful:

### 1. Add XML tags for RFC2119 keywords
This [script](https://strayalpha.com/software/rfcxml/lookback-bcp-fix.pl) adds `<bcp14>` tags around RFC 2119 keywords in XML source.

### 2. bibtex2rfc
[bibtex2rfc](https://github.com/yaronf/bibtex2rfc) converts BibTeX citations into BibXML references. The IETF publishes a [library of BibXML references](https://xml2rfc.tools.ietf.org), which should be checked first.

## TODO
- DTDs
