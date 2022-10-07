---
title: Diagrams
description: 
published: true
date: 2021-12-17T02:29:30.282Z
tags: 
editor: markdown
dateCreated: 2021-11-17T10:06:49.972Z
---

Your diagrams can be provided in ASCII-art, SVG or both:
*  If only ASCII-art is provided then it is used in all rendering (see RFC9139 for example)
*  If both are provided then SVG is used in the HTML and PDF rendering, and ASCII-art is used in the plaintext rendering
*  If only SVG is provided then it is used in the HTML and PDF rendering but no diagram is included in the plaintext rendering, replaced with a message that says "Artwork only available as SVG".  For this reason, providing only SVG is **not recommended**.

If you are [Drafting in XML](/drafting-in-xml) then all the choices are open to you.

If you are [Drafting in Markdown](/drafting-in-markdown) or [Drafting in other markup languages](/drafting-in-other-markup-languages) then your options depend on the toolchain you use:
1. Some tools allow you to specify an external SVG file
1. Some tools support embedded diagramming languages and manage the conversion of those into SVG
1. Some tools do not support SVG diagrams requiring you to use ASCII-art diagrams and/or add the SVG manually after the I-D has been converted to RFCXML.

If you are [Drafting in plaintext](/drafting-in-plaintext) then all diagrams need to be included as ASCII-art inline in the text.

# Generating ASCII-art diagrams

## asciiflow
## {.tabset}
### Details
[asciiflow](https://asciiflow.com/#/) is a web based interactive ASCII diagramming tool. It support both ASCII and extended Unicode box drawing characters.  asciiflow only exports as text.

## Textik
## {.tabset}
### Details
[Textik](https://textik.com/) is a web based interactive ASCII diagramming tool.  It only supports ASCII characters.  Textik is [open source](https://github.com/astashov/tixi).

## Monodraw
## {.tabset}
### Details
[Monodraw](https://monodraw.helftone.com) is an interactive ASCII diagramming tool that support both ASCII and extended Unicode box drawing characters.  It is paid, but very cheap, and MacOS only.  Monodraw can generate SVG but no information is available on the features used by the generated SVG.

# Generating SVG diagrams
SVG can be generated in one of a number of methods:
1. Using an interactive diagramming tool that generates SVG
1. Using a diagramming language that generates SVG
1. Converting a diagram in another format into SVG
1. Hand-coding the SVG

Your SVG diagrams must conform to the SVG profile "SVG 1.2 RFC" as documented in RFC 7996 (which is in turn a subset of SVG Tiny 1.2) that has the following restrictions compared to standard SVG:
* No animation
* No interactivity
* No scripting or other extensibility
* No colour or grayscale, only black and white
* Only 'serif', 'sans-serif', and 'monospace' generic font families from the WebFonts facility
* Only ASCII links

See [Validating your SVG](#validating-your-svg) for details of how to validate your SVG.

In addition, please provide detailed descriptions of the artwork in SVG `<desc>` elements to assist readers who are visually impaired. For more information about this element, please see the [Accessibility Features of SVG](https://www.w3.org/TR/SVG-access/#Equivalent).

The following tools are known to be used by community members to generate SVG using one or more of the methods above:

## Dia
## {.tabset}
### Details
Dia is a program to draw structured diagrams.  It is open source and runs on Windows, OSX, GNU/Linux and Unix. For more details and downloads see [http://dia-installer.de](http://dia-installer.de).  Dia outputs SVG where text strings within the diagram are searchable and selectable.

### Community tips
#### Nevil Brownlee, July 2018
Dia is simple to use. Save your drawing as xxx.dia, then export it as xxx.svg.

Dia draws line-end arrowheads as filled polygons, and it doesn't use markers.

## aasvg
## {.tabset}
### Details
[aasvg](https://github.com/martinthomson/aasvg) takes ASCII diagrams and converts them into SVG.  This has the advantage of ensuring that the text version of the RFC presents very similar diagrams to HTML and PDF formats.

This tool is inspired by [goat](https://github.com/blampe/goat) and uses a modified version of the original [markdeep](https://casual-effects.com/markdeep/) code.

aasvg can be used in [kramdown-rfc](https://github.com/cabo/kramdown-rfc/wiki) by starting a block with `~~~ aasvg`.

## Inkscape
## {.tabset}
### Details
[Inkscape](https://inkscape.org) is a professional quality, open source, vector graphics  editor that runs on Linux, Windows and MacOS.

### Community tips
#### Nevil Brownlee, July 2018
Of the Open Source packages, in my opinion Inkscape is the best of them. It's a big package, though, with many features, so there's a big learning curve to go through. Fortunately there's a lot of tutorial material on the web, for example: [Inkscape tutorial](http://tavmjong.free.fr/INKSCAPE/MANUAL/html/QuickStart.html) Note, however, that SVG 1.2 RFC only allows objects that are part of black-and-white line drawings.

Again, Inkscape uses markers for line-end symbols (even if you create your own markers using Object → Objects to Marker). That means, if you want arrowheads at the end of lines, you have to draw them in yourself. The simplest way to do that is to make an arrowhead with two lines grouped together, draw your lines, then copy your arrowhead at the end(s) of them.

Another nice feature of Inkscape is that its 'Resize page to content' lets you resize your svg drawing to trim the white space around its edges before you save it as 'Plain SVG'. See the example [SVG flowchart diagram](https://www.rfc-editor.org/rse/wiki/lib/exe/fetch.php?media=inkscape-drawn-arrows.svg) produced in this way.

## LibreOffice Draw
## {.tabset}
### Details
[LibreOffice Draw](https://www.libreoffice.org/discover/draw/) is an open source, vector graphics editor.

### Community tips
#### Nevil Brownlee, July 2018
This is good if you're used to LibreOffice, and your drawing is fairly simple.

Create your drawing using Draw, group it into a single object, then export it. (For me, that makes an SVG diagram that emacs and Inkscape display properly, but Firefox donesn't - however, check-svg.py's rewritten SVG diagram displays properly in Firefox, with Draw's arrowheads displayed properly.)

## Powerpoint
## {.tabset}
### Details
Powerpoint is a commercial presentation tools with basic digramming capabilities, part of the MS Office suite. 

### Community tips
#### Don Fedyk, April 2021
If you have black and white diagrams in PowerPoint these can be copied and pasted into Inkscape. You can resize and position on Inkscape's default page or you can create a drawing size and adjust. Then you can save as a plain svg. PowerPoint can save natively into SVG as well but that SVG is very detailed.

The plain SVG will have:
```xml
  width="210mm"
  height="279mm"
  viewBox="0 0 210 279" 
```
(or whatever your starting size was)

It is easier to make Inkscape drawing size close to the dimensions you want before saving. For a 1/2 page drawing a full page may be used and the height can be adjusted, but sometimes the conversion will complain and the height/width have to be removed. See positioning tips.)

Editing the basic svg:

You will need to remove clipPath and metadata (it will probably look something like this):
```xml
 <defs
    id="defs2">
   <clipPath
      id="clip0">
     <rect
        x="52"
        y="349"
        width="2159"
        height="889"
        id="rect10" />
   </clipPath>
 </defs>
 <metadata
    id="metadata5">
   <rdf:RDF>
     <cc:Work
        rdf:about="">
       <dc:format>image/svg+xml</dc:format>
       <dc:type
          rdf:resource="http://purl.org/dc/dcmitype/StillImage" />
       <dc:title></dc:title>
     </cc:Work>
   </rdf:RDF>
 </metadata>
```
The basic svg has some identifiers that must be removed:
```
font-weight
font-family
style="stroke-width:0.0911541"<...
```
The font-related ones can usually be deleted by deleting the whole line. The style one is part of a tspan tag and you must only remove the text. These VIM command line commands do it properly:
```
:1,$s/style="stroke.*"// 
:g/font-weight/d   
:g/font-family/d
```
At this point you can test the SVG either by including and running it in xml2rfc or using the SVG tester but xml2rfc catches more issues so I skip the tester. Rendering: `xml2rfc –pdf your_v3_xml_draft.xml`

Another issue is with `<tspan>`s. It seems text is expanded to text and tspan tags. Sometimes the physical text is between `<text>like this</text>`and sometimes it is between `<text><tspan>like</tspan><tspan>this</tspan></text>`which is fine but with hyphenated text there are two issues. It might put the text between the tspan and text tags: `<text><tspan>fouled</tspan>-</tspan>up</text>` and you need to correct it by either moving the text or deleting the tags. The `xml2rfc –pdf` will complain about this. Simply moving the text inside the tspan tags works.

Usually there are coordinates within the text and tspan tags - you want to keep those. Another issue is the coordinates of the text can cause the characters to overwrite in different tspans. `<text><tspan>fouled-up</tspan></text>` will print better than `<text><tspan>fouled</tspan>-up</tspan></text>`.

Positioning: The ViewBox has x-min y-min
```
x="0" y="0" width="100%" height="100%"/
```
For a half page drawing from the original:
```
  width="210mm"
  height="279mm"
  viewBox="0 0 210 279" 
           x y  w%   h%
```

The height controls the whitespace; if your drawing is 1/2 page you can usually reduce by 1/2 and it will only take 1/2 a page. Inch-based dimensions were harder to work with, and width and height had to be removed, but with mm dimensions the height could be reduced more before it complained. The x y controls move the origin; positive values for y move the origin down and the drawing upwards.

Adjusted for 1/2 page it might look like this:
```

  width="210mm"
  height="110mm"
  viewBox="0 15 210 110"  
```

Note that the x dimension is unchanged; also, in my experience, the scaling is far from linear. A slightly large diagram needed these values but the difference from 50 to 30 on the veiwBox height was hardly noticeable.
```

  width="210mm"
  height="135mm"
  viewBox="0 52 210 30"
```

The scaling is constant whether the drawing is at the top or following other drawings. Two pictures easily fit with captions on a page using this.

## Adobe Illustrator
## {.tabset}
### Details
Adobe Illustrator is not open source but is included as some may have already have access to it.  

### Community tips
#### Nevil Brownlee, July 2018
If you're familiar with Adobe Illustrator, it can also be used. It can save files as SVG-t (i.e. SVG Tiny), which - I assume - means that drawings saved in SVG-t don't use arrowheads.

## Other tools
For reference, the following tools are also known to generate SVG.  If you use any of these tools then please send us any tips that should be included here.

* [Graphviz](https://www.graphviz.org) (open source)
* [LucidChart](https://www.lucidchart.com/) (paid)
* [OmniGraffle](https://www.omnigroup.com/omnigraffle) (paid)
* [Boxy SVG Editor](https://boxy-svg.com) (paid)

# Validating your SVG
The [Author Tools](https://author-tools.ietf.org) web service can validate your SVG and output a corrected SVG file if required.

[svgcheck](https://github.com/ietf-tools/RfcEditor/tree/master/svgcheck) is a command line tool that takes an XML file containing an SVG or an RFC document. It then compares all of the SVG elements with the schema defined in the document with RFC 7996 bis. The program has the option of modifying and writing out a version of the input that passes the defined schema. The [Author Tools](/https://author-tools.ietf.org) web service uses [svgcheck](https://github.com/ietf-tools/RfcEditor/tree/master/svgcheck) in the background.

# Examples
## SVG in RFCs
[RFC 9115](https://www.rfc-editor.org/rfc/rfc9115.html#figure-1) (Figures 1, 11 - 14)
[RFC 9100](https://www.rfc-editor.org/rfc/rfc9100.html#figure-1) (Figure 1)
[RFC 9043](https://www.rfc-editor.org/rfc/rfc9043.html#figure-4) (Figures 4 - 17, 22, 23, 29, 30)
[RFC 8899](https://www.rfc-editor.org/rfc/rfc8899.html#figure-1) (Figures 1 - 5)
[RFC 8989](https://www.rfc-editor.org/rfc/rfc8989.html#figure-1) (Figures 1 - 4)

Some extracted SVG diagrams are also [available](https://www.rfc-editor.org/materials/format/svg/)
## ASCII-art and SVG in a single \<artset\>
The following example has one [**\<artset\>**](https://authors.ietf.org/en/rfcxml-vocabulary#artset) element that contains two [**\<artwork\>**](https://authors.ietf.org/en/rfcxml-vocabulary#artwork) elements, each of a different type. The SVG is included directly and a **name** attribute provided to recommend a filename if the diagram is extracted.
```xml
<figure>
  <name>Box diagram</name>
  <artset>
    <artwork type="svg" name="box.svg">
      <svg xmlns="http://www.w3.org/2000/svg" version="1.1" viewBox="0 0 71 40">
        <g>
          <title>Layer 1</title>
          <rect x="4.5" y="6.5" width="61.0" height="27.0" stroke="black" stroke-width="1.0" stroke-linecap="square" stroke-linejoin="miter" fill="none" />
          <text x="33.883" text-anchor="middle" y="26.559">
            <tspan fill="black" font-size="13.0">A box</tspan>
          </text>
        </g>
      </svg>
    </artwork>
    <artwork type="ascii-art" name="box.txt">
      <![CDATA[
 +--------+
 | A box  |
 +--------+          
      ]]>
    </artwork>
  </artset>
</figure>
```
