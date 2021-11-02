---
title: RFCXML Elements
description: 
published: true
date: 2021-11-02T23:30:45.448Z
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

