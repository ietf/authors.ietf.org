---
title: Drafting in other markup languages
description: 
published: true
date: 2021-12-14T20:45:17.733Z
tags: 
editor: markdown
dateCreated: 2021-08-19T09:01:14.498Z
---

There are many other lightweight text markup languages with their own processing systems. Those listed here are supported by a toolchain that produces either a plaintext or an RFCXML Internet-Draft.

Most of these toolchains are not widely used and in some cases rely on tools that are unmaintained. 

# AsciiDoc
[AsciiDoc](https://asciidoc.org) is a text document format similar to Markdown.

## AsciiRFC with metanorma-ietf
[AsciiRFC](https://datatracker.ietf.org/doc/html/draft-ribose-asciirfc) is an AsciiDoc syntax for writing IETF documents.  The [metanorma-ietf](https://github.com/metanorma/metanorma-ietf) tool converts documents in AsciiRFC into RFCXML.  

# LaTeX
[LaTeX](https://www.latex-project.org) is an open source typesetting system designed for the production of technical and scientific documentation. An out of date [LaTeX template](https://www.rfc-editor.org/materials/2-latex.template.txt) is available.

## Lyx with lyx2rfc
[Lyx](https://www.lyx.org) is an open source what-you-see-is-what-you-mean (WYSIWYM) GUI editor for LaTeX documents. [lyx2rfc](https://github.com/nicowilliams/lyx2rfc) is a plugin to Lyx that converts LyX XHTML output to RFC XML.

lyx2rfc is unmaintained and was last updated in 2014.

# nroff format
nroff is a text formatting program that produces output suitable for fixed-width files. An out of date [Nroff template](https://www.rfc-editor.org/materials/3-nroff.template) is available with a similarly out of date [tutorial](https://www.rfc-editor.org/materials/nroff.html).
  
## Emacs editor in nroff mode
The popular open source editor Emacs includes [Nroff mode](https://www.gnu.org/software/emacs/manual/html_node/emacs/Nroff-Mode.html).

## nroff with Nroff Edit
[nroff Edit](https://aaa-sec.com/nroffedit/) is a Java based WYSIWYG editor for writing and editing Internet-Drafts in nroff. The nroff based Internet-Draft file is edited in the left window while the resulting compiled text version is instantly shown in the right Window as a result of any edit changes.

Nroff Edit is unmaintained and was last updated in 2015.

## nroff with nroff2xml
[nroff2xml](https://github.com/tomaszmrugalski/nroff2xml) is a Python script that converts a file in nroff format into v2 RFCXML.  

nroff2xml is unmaintained and was last updated in 2013.

# Org Mode
Org is a highly flexible structured plaintext file format that is used mainly in the Emacs editor in [Org Mode](https://orgmode.org).

## Org Mode RFC XML Exporter
[Org Mode RFC XML Exporter](https://github.com/choppsv1/org-rfc-export) is an Emacs plugin that exports Org Mode files to RFCXML.



