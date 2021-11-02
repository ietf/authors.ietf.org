---
title: RFCXML Elements
description: 
published: true
date: 2021-11-02T23:36:37.335Z
tags: 
editor: markdown
dateCreated: 2021-11-02T22:58:38.001Z
---


## abstract
## Tabs {.tabset}
### Usage
Contains the Abstract of the document. See RFC7322 for more information on restrictions for the Abstract.
### Schema
Parents: `front`

Contents: `(dl, ol, t, ul)+`

### "anchor"

Document-wide unique identifier for this `<abstract>` element.

## address
## Tabs {.tabset}
### Usage
Provides address information for the author.
### Schema
Parents: `author`, `contact`

Contents: `postal?, phone?, email*, uri?`

## annotation
## Tabs {.tabset}
### Usage
Provides additional prose augmenting a bibliographic reference. This text is intended to be shown after the rest of the generated reference text.
### Schema
Parents: `reference`

Contents: `( text | bcp14 | cref | em | eref | iref | strong | sub | sup | tt | u | xref )*`

## area
## Tabs {.tabset}
### Usage
Provides information about the IETF area to which this document relates (currently not used when generating documents).

The value ought to be either the full name or the abbreviation of one of the IETF areas as listed on http://www.ietf.org/iesg/area.html. A list of full names and abbreviations will be kept by the RFC Series Editor.
### Schema
Parents: `front`

Contents: `text`

## artset
## Tabs {.tabset}
### Usage
This element allows for the support of multiple artwork formats, in order to provide suitable artwork for different output formats.

When multiple `artwork` instances are provided within one `artset` element, the renderer will try to pick the `artwork` instance which is most appropriate for its current output format from the given alternatives.

If more than one `artwork` element with the same "type" is found within an `artset` element, the renderer could select the first one, or possibly choose between the alternative instances based on the output format and some quality of the alternatives that make one more suitable than the others for that particular format, such as size, aspect ratio, etc.
### Schema
Parents: `aside`, `blockquote`, `dd`, `figure`, `li`, `section`, `td`, `th`

Contents: `artwork+`
### "anchor"
Document-wide unique identifier for this `artset` element.

## artwork
## Tabs {.tabset}
### Usage
This element allows the inclusion of "artwork" in the document. `artwork` provides full control of horizontal whitespace and line breaks; thus, it is used for a variety of things, such as diagrams ("line art") and protocol unit diagrams. Tab characters (U+0009) inside of this element are prohibited.

Alternatively, the "src" attribute allows referencing an external graphics file, such as a vector drawing in SVG or a bitmap graphic file, using a URI. In this case, the textual content acts as a fallback for output representations that do not support graphics; thus, it ought to contain either (1) a "line art" variant of the graphics or (2) prose that describes the included image in sufficient detail.

In order to include alternative artwork expressions for different output formats, you should provide multiple `artwork` elements enclosed within an `artset`. The text renderer will prefer instances with type="ascii-art", while the HTML and PDF renderers will prefer instances with type="svg".

In previous versions of the schema, the `artwork` element was also used for source code and formal languages; this is now done with `sourcecode`.

There are at least five ways to include SVG in artwork in Internet- Drafts:

* Inline, by including all of the SVG in the content of the element, such as:
```<artwork type="svg"><svg xmlns="http://www.w3.org/2000/ svg...">```
* Inline, but using XInclude (see Appendix B.1), such as:
```<artwork type="svg"><xi:include href=...>```
* As a data: URI, such as:
```<artwork type="svg" src="data:image/svg+xml,%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww...">```
* As a URI to an external entity, such as:
```<artwork type="svg" src="http://www.example.com/...">```
* As a local file, such as:
```<artwork type="svg" src="diagram12.svg">```

The use of SVG in Internet-Drafts and RFCs is covered in much more detail in [RFC7996].

The above methods for inclusion of SVG art can also be used for including text artwork, but using a data: URI is probably confusing for text artwork.

Formatters that do pagination should attempt to keep artwork on a single page. This is to prevent artwork that is split across pages from looking like two separate pieces of artwork.

See Section 5 for a description of how to deal with issues of using "&" and "<" characters in artwork.

Parents: `artset`, `aside`, `blockquote`, `dd`, `figure`, `li`, `section`, `td`, `th`

Contents: `( text* | svg )`
