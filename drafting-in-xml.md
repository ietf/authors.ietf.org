---
title: Drafting in XML
description: 
published: true
date: 2022-03-01T03:16:19.800Z
tags: 
editor: markdown
dateCreated: 2021-08-18T10:56:56.326Z
---

# Introduction
For an introduction to RFCXML see the [RFCXML overview and background](/rfcxml-overview) and for detailed documentation on each element and attribute see the [RFCXML vocabulary reference](/rfcxml-vocabulary).

Modern XML toolchains include advanced features that support XML editing including schema validation and schema-aware editing.  The templates provided at [Templates and schemas](/templates-and-schemas) contain the necessary code to make this work.

## Quick start guide
1. Choose your RFCXML toolchain from the list below
1. Clone or download the [RFCXML template repository](https://github.com/ietf-authors/rfcxml-templates-and-schemas).
1. Edit the [Standard](https://authors.ietf.org/en/templates-and-schemas#draft-rfcxml-general-template-standard-00xml) (or [Annotated](https://authors.ietf.org/en/templates-and-schemas#draft-rfcxml-general-template-annotated-00xml)) template.
1. If you require automated builds then consider the [Github workflow](https://github.com/martinthomson/i-d-template/blob/main/doc/TEMPLATE.md).
1. Process your edited I-D using the [IETF Author Tools web service](https://author-tools.ietf.org).


# RFCXML toolchains
The following XML toolchains have been reported as in use by IETF community members.  These are all interactive XML editors. 

## Emacs editor in nXML Mode
The popular open source editor Emacs includes [nXML Mode](https://www.gnu.org/software/emacs/manual/html_mono/nxml-mode.html), which enables validation and schema-sensitive editing when you use an RNC schema. 

## OxygenXML
[Oxygen XML Editor](https://www.oxygenxml.com/xml_editor.html) is a commercial XML editor.  This tool comes in different versions with a number of different licensing options, though all versions support RELAX NG validation and some support syntax highlighting and intelligent auto-completion. The premium version also supports collaborative edIting, including tracked changes and comment review.

The same company also makes [Oxygen Content Fusion](https://www.oxygenxml.com/content_fusion.html), which support web-based collaborative editing and document review.
  
## XMLmind XML Editor (XXE) with xml2rfc-xxe
[XMLmind XML Editor (XXE)](https://www.xmlmind.com/xmleditor/) is a commercial near-WYSIWYG XML editor with a free edition for personal use.  XXE supports RNC schema validation and context-sensitive editing.

A community developed configuration for XXE, [xml2rfc-xxe](https://github.com/wkumari/xml2rfc-xxe/) is available, providing additional context-sensitive editing features, however this does not support the latest version of RFCXML and is unsupported.

## Text editor wtih xmllint
IETF community members report using a range of text editors with varying support for XML editing, and and validating the RFCXML externally using [xmllint](http://xmlsoft.org/xmllint.html), a common open source, command line tool.

# Supporting tools
Authors writing in XML may find the following tools helpful:

## Add XML tags for RFC2119 keywords
This [script](https://strayalpha.com/software/rfcxml/lookback-bcp-fix.pl) adds `<bcp14>` tags around RFC 2119 keywords in XML source.

## bibtex2rfc
[bibtex2rfc](https://github.com/yaronf/bibtex2rfc) converts BibTeX citations into BibXML references. See [References in RFCXML](/references-in-rfcxml) for more details.

## i-d-template
[Drafting in Markdown](/drafting-in-markdown#h-3-internet-draft-template-and-i-d-template) describes the use of the [i-d-template](https://github.com/martinthomson/i-d-template) and [internet-draft-template](https://github.com/martinthomson/internet-draft-template) projects for managing I-Ds.  These tools can be used to manage RFCXML I-Ds, with most of the same [automation features](https://github.com/martinthomson/i-d-template/blob/main/doc/FEATURES.md#automation-features).
