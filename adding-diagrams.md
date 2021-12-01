---
title: Adding diagrams
description: 
published: true
date: 2021-12-01T02:19:57.587Z
tags: 
editor: markdown
dateCreated: 2021-11-17T10:06:49.972Z
---

# Introduction
Your options for adding diagrams depends on your choice of authoring format:

## Drafting in XML
If you are [drafting in XML](/drafting-in-xml) then your diagrams need to be provided in SVG format and optionally also in ASCII for use when the I-D is rendered in plain text.  The SVG can be generated in one of a number of ways:
1. Using an interactive diagramming tool that generates SVG
1. Using a diagramming language that generates SVG
1. Converting a diagram in another format into SVG
1. Hand-coding the SVG

## Drafting in Markdown or another lightweight markup language
If you are [drafting in Markdown](/drafting-in-markdown) or [another lightweight markup language](/drafting-in-other-formats) then your options depend on the toolchain you use:
    1. Some tools allow you to specify an external SVG file
    1. Some tools support embedded diagramming languages and manage the conversion of those into SVG
    1. Some tools do not support SVG diagrams requiring you to use ASCII diagrams and/or add the SVG manually after the I-D has been converted to RFCXML.

## Drafting in plain text
For I-Ds that are submitted in plain text, any diagrams need to be included in ASCII inline in the text.

# Accepted SVG - SVG 1.2 RFC
Your SVG diagrams must conform to the SVG profile "SVG 1.2 RFC" as documented in RFC 7996 (which is in turn a subset of SVG Tiny 1.2) that has the following restrictions compared to standard SVG:
* No animation
* No interactivity
* No scripting or other extensibility
* No colour or grayscale, only black and white
* Only 'serif', 'sans-serif', and 'monospace'generic font families from the WebFonts facility
* Only ASCII links

See [Document Validation](/document-validation) for details of how to validate your SVG.

# Tools that generate SVG

The following tools are known to be used to generate SVG:

## Inkscape
## {.tabset}
### Details


### Community tips
#### Nevil Brownlee, July 2018
Of the Open Source packages, in my opinion Inkscape is the best of them. It's a big package, though, with many features, so there's a big learning curve to go through. Fortunately there's a lot of tutorial material on the web, for example: [Inkscape tutorial](http://tavmjong.free.fr/INKSCAPE/MANUAL/html/QuickStart.html) Note, however, that SVG 1.2 RFC only allows objects that are part of black-and-white line drawings.

Again, Inkscape uses markers for line-end symbols (even if you create your own markers using Object → Objects to Marker). That means, if you want arrowheads at the end of lines, you have to draw them in yourself. The simplest way to do that is to make an arrowhead with two lines grouped together, draw your lines, then copy your arrowhead at the end(s) of them.

Another nice feature of Inkscape is that its 'Resize page to content' lets you resize your svg drawing to trim the white space around its edges before you save it as 'Plain SVG'. See the example [SVG flowchart diagram](https://www.rfc-editor.org/rse/wiki/lib/exe/fetch.php?media=inkscape-drawn-arrows.svg) produced in this way.

## LibreOffice Draw
## {.tabset}
### Details


### Community tips
#### Nevil Brownlee, July 2018
This is good if you're used to LibreOffice, and your drawing is fairly simple.

Create your drawing using Draw, group it into a single object, then export it. (For me, that makes an SVG diagram that emacs and Inkscape display properly, but Firefox donesn't - however, check-svg.py's rewritten SVG diagram displays properly in Firefox, with Draw's arrowheads displayed properly.)

## Dia
## {.tabset}
### Details
Dia is a program to draw structured diagrams.  It is open source and runs on Windows, OSX, GNU/Linux and Unix. For more details and downloads see [http://dia-installer.de](http://dia-installer.de)

### Community tips
#### Nevil Brownlee, July 2018
Dia is simple to use. Save your drawing as xxx.dia, then export it as xxx.svg.

Dia draws line-end arrowheads as filled polygons, and it doesn't use markers.

## Adobe Illustrator
## {.tabset}
### Details
Adobe Illustrator is not open source but is included as some may have already have access to it.  

### Community tips
#### Nevil Brownlee, July 2018
If you're familiar with Adobe Illustrator, it can also be used. It can save files as SVG-t (i.e. SVG Tiny), which - I assume - means that drawings saved in SVG-t don't use arrowheads.