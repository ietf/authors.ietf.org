---
title: RFCXML Elements
description: 
published: true
date: 2021-11-02T23:49:19.000Z
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

### Schema
Parents: `artset`, `aside`, `blockquote`, `dd`, `figure`, `li`, `section`, `td`, `th`

Contents: `( text* | svg )`

### "align"
Controls whether the artwork appears left justified, centered, or right justified.

Possible values: `( "left" | "center" | "right" )`
Default value: `"left"`

### "alt"
Alternative text description of the artwork (which is more than just a summary or caption). When the art comes from the "src" attribute and the format of that artwork supports alternate text, the alternative text comes from the text of the artwork itself, not from this attribute. The contents of this attribute are important to readers who are visually impaired, as well as those reading on devices that cannot show the artwork well, or at all.

### "anchor"
Document-wide unique identifier for this `artwork` element.

### "height"
TBD

### "name"
A filename suitable for the contents (such as for extraction to a local file). This attribute can be helpful for other kinds of tools (such as automated syntax checkers, which work by extracting the artwork). Note that the "name" attribute does not need to be unique for `artwork` elements in a document. If multiple `artwork` elements have the same "name" attribute, a processing tool might assume that the elements are all fragments of a single file, and the tool can collect those fragments for later processing.

### "src"
The URI reference of a graphics file RFC3986, or the name of a file on the local disk. This can be a "data" URI RFC2397 that contains the contents of the graphics file. Note that the inclusion of art with the "src" attribute depends on the capabilities of the processing tool reading the XML document. Tools need to be able to handle the file: URI, and they should be able to handle http: and https: URIs as well. The prep tool will be able to handle reading the "src" attribute.

If no URI scheme is given in the attribute, the attribute is considered to be a local filename relative to the current directory. Processing tools must be careful to not accept dangerous values for the filename, particularly those that contain absolute references outside the current directory. Document creators should think hard before using relative URIs due to possible later problems if files move around on the disk. Also, documents should most likely use explicit URI schemes wherever possible.

In some cases, the prep tool may remove the "src" attribute after processing its value. See RFC7998 for a description of this.

### "type"
Specifies the format of the artwork. The value of this attribute is free text with certain values designated as preferred.

The preferred values for `artwork` types are:

* ascii-art
* binary-art
* svg

Values that don't describe the format, such as "call-flow" or "hex-dump" were mentioned in RFC7991, but are not supported here; they are instead candidates for use with another future attribute to describe the artwork content.

A complete list of the preferred values is maintained on the RFC Editor web site, and that list is expected to be updated over time. Thus, a consumer of this attribute should not cause a failure when it encounters an unexpected type or no type is specified. The table will also indicate which type of art can appear in plain-text output (for example, type="svg" cannot).

### "width"
TBD

## aside
## Tabs {.tabset}
### Usage
This element is a container for content that is semantically less important or tangential to the content that surrounds it.
 
### Schema
Parents: `dd`, `section`

Contents: `( artset | artwork | blockquote | dl | figure | iref | ol | t | table | ul )*`

### "anchor"
Document-wide unique identifier for this `aside` element.

## author
## Tabs {.tabset}
### Usage
Provides information about a document's author. This is used both for the document itself (at the beginning of the document) and for referenced documents.

The `author` elements contained within the document's `front` element are used to fill the boilerplate and also to generate the "Author's Address" section (see RFC7322).

Note that an "author" can also be just an organization (by not specifying any of the "name" attributes, but adding the `organization` child element).

Furthermore, the "role" attribute can be used to mark an author as "editor". This is reflected both on the front page and in the "Author's Address" section, as well as in bibliographic references. Note that this specification does not define a precise meaning for the term "editor".

### Schema
Parents: `front`, `section`

Contents: `organization?, address?`

### "anchor"
Document-wide unique identifier for this `author` element.

### "asciiFullname" 

The Latin script equivalent of the author's full name.

### "asciiInitials" 

The Latin script equivalent of the author's initials, to be used in conjunction with the separately specified asciiSurname.

### "asciiSurname" 

The Latin script equivalent of the author's surname, to be used in conjunction with the separately specified asciiInitials.

### "fullname" 

The full name (used in the automatically generated "Author's Address" section). Although this attribute is optional, if one or more of the "asciiFullname", "asciiInitials", or "asciiSurname" attributes does not have values, the "fullname" attribute is required.

### "initials" 

An abbreviated variant of the given name(s), to be used in conjunction with the separately specified surname. It usually appears on the front page, in footers, and in references.

Some processors will post-process the value -- for instance, when it only contains a single letter (in which case they might add a trailing dot). Relying on this kind of post-processing can lead to results varying across formatters and thus ought to be avoided.

### "role" 

Specifies the role the author had in creating the document.

### "surname" 

The author's surname, to be used in conjunction with the separately specified initials. It usually appears on the front page, in footers, and in references.


