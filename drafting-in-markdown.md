---
title: Drafting in Markdown
description: 
published: true
date: 2022-03-01T03:38:59.420Z
tags: 
editor: markdown
dateCreated: 2021-08-18T10:57:57.022Z
---

# Introduction
Markdown is a lightweight markup language that is widely supported.  While Markdown is significantly easier to use than XML it is also less powerful and is less standardised.  Consequently the Markdown toolchains are very popular but the tools are not interchangeable as they use different syntaxes.

## Quick start guide

1.  Choose a Markdown toolchain from the list below
1.  The chosen toolchain will normally include its own template, which you then edit with your choice of text editor.
1. If you require automated builds then consider the [Github workflow](https://github.com/martinthomson/i-d-template/blob/main/doc/TEMPLATE.md).
1. Process your edited I-D using the [IETF Author Tools web service](https://author-tools.ietf.org).

# Markdown toolchains
The following Markdown toolchains have been reported in common use by I-D authors.

## kramdown-rfc
[kramdown-rfc](https://github.com/cabo/kramdown-rfc) is an open source text processor that converts files written in its proprietary markdown syntax into RFCXML. This is by far the most commonly used Markdown toolchain for I-Ds.

The [Author Tools](https://author-tools.ietf.org) web service supports kramdown-rfc as one of its backend processors.

## mmark
[mmark](https://mmark.miek.nl) is an open source text processor that converts files written in its proprietary markdown syntax into RFCXML.

The [Author Tools](https://author-tools.ietf.org) web service supports mmark as one of its backend processors.

## internet-draft-template and i-d-template
[internet-draft-template](https://github.com/martinthomson/internet-draft-template) and [i-d-template](https://github.com/martinthomson/i-d-template) are a pair of tools that work together together to provide an automated Markdown I-D build system in GitHub.  Behind the scenes, they use [kramdown-rfc](https://github.com/cabo/kramdown-rfc) as the Markdown processor but can be configured to use [mmark](https://mmark.miek.nl) or even an RFCXML processor.

To use these tools you start by [creating a new repository](https://github.com/martinthomson/i-d-template/blob/main/doc/TEMPLATE.md) using [internet-draft-template](https://github.com/martinthomson/internet-draft-template/generate).  The new created repository includes a template Markdown file and the [automation features](https://github.com/martinthomson/i-d-template/blob/main/doc/FEATURES.md#automation-features) of i-d-template.

# Supporting tools
Authors writing in Markdown may find the following tools helpful:

## bibxml2md
[bibxml2md](https://github.com/yaronf/bibxml2md) converts BibXML references into Markdown.  See [References in RFCXML](/references-in-rfcxml) for more details.

## draftr
[draftr](https://ipv.sx/draftr-js/) provides a live on-screen conversion using kramdown-rfc.  This tool is no longer maintained.


