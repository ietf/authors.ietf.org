---
title: Adding diagrams
description: 
published: true
date: 2021-11-18T10:06:05.493Z
tags: 
editor: markdown
dateCreated: 2021-11-17T10:06:49.972Z
---

# Introduction
If you are [drafting in XML](/drafting-in-xml) then your diagrams need to be provided in SVG format and optionally also in ASCII for use when the I-D is rendered in plain text.  The SVG can be generated in one of a number of ways:
1. Using an interactive diagramming tool that generates SVG
1. Using a diagramming language that generates SVG
1. Converting a diagram in another format into SVG
1. Hand-coding the SVG

If you are [drafting in Markdown](/drafting-in-markdown) or [another lightweight markup language](/drafting-in-other-firmats) then your options depend on the tool you use:
1. Some tools allow you to specify an external SVG file
1. Some tools support embedded diagramming languages and manage the conversion of those into SVG
1. Some tools do not support SVG diagrams requiring you to use ASCII diagrams or add the SVG manually after the I-D has been converted to RFCXML

For I-Ds that are submitted in plain text, any diagrams need to be included in ASCII inline in the text.