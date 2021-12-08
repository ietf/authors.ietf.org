---
title: Drafting in Markdown
description: 
published: true
date: 2021-12-08T20:45:53.330Z
tags: 
editor: markdown
dateCreated: 2021-08-18T10:57:57.022Z
---

Markdown is a lightweight markup language that is widely supported.  While Markdown is significantly easier to use than XML is also less powerful and is less standardised.  Consequently the Markdown toolchains are very popular but the tools are not interchangeable as they use different syntaxes.

# Markdown toolchains
The following Markdown toolchains have been reported in common use by I-D authors.

## 1. kramdown-rfc2629
[kramdown-rfc2629](https://github.com/cabo/kramdown-rfc2629) is an open source text processor that converts files written in its proprietary markdown syntax into RFCXML. 

The [Author Tools](https://author-tools.ietf.org) web service supports kramdown-rfc2629 as one of its backend processors.

[draftr](https://ipv.sx/draftr-js/) provides a live on-screen conversion using kramdown-rfc2629.

## 2. mmark
[mmark](https://mmark.miek.nl) is an open source text processor that converts files written in its proprietary markdown syntax into RFCXML.

The [Author Tools](https://author-tools.ietf.org) web service supports mmark as one of its backend processors.

## 3. internet-draft-template and i-d-template
[internet-draft-template](https://github.com/martinthomson/internet-draft-template) and [i-d-template](https://github.com/martinthomson/i-d-template) are a pair of tools that work together together to provide an automated Markdown I-D build system in GitHub.  Behind the scenes, they use [kramdown-rfc2629](https://github.com/cabo/kramdown-rfc2629) as the Markdown processor.

To use these tools you start by [creating a new repository](https://github.com/martinthomson/internet-draft-template/generate) using internet-draft-template.  The new created repository includes a template Markdown file and the automation features of i-d-template.

# Supporting tools
Authors writing in Markdown may find the following tools helpful:

## 1. bibxml2md
[bibxml2md](https://github.com/yaronf/bibxml2md) converts BibXML references into Markdown.  The IETF publishes a [library of BibXML references](https://xml2rfc.tools.ietf.org).