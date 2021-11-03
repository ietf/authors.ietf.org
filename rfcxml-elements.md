---
title: RFCXML Elements
description: 
published: true
date: 2021-11-03T01:27:25.721Z
tags: 
editor: markdown
dateCreated: 2021-11-02T22:58:38.001Z
---


## abstract
## Tabs {.tabset}
### Usage
Contains the Abstract of the document. See RFC7322 for more information on restrictions for the Abstract.
### Schema
Can be child of: [`front`](rfcxml-elements#front)

Contents: ([`dl`](rfcxml-elements#dl), ol, t, ul)+

### "anchor"
Document-wide unique identifier for this element.

## address
## Tabs {.tabset}
### Usage
Provides address information for the author.
### Schema
Can be child of: [`author`](rfcxml#author), `contact`

Contents: `postal?, phone?, email*, uri?`

## annotation
## Tabs {.tabset}
### Usage
Provides additional prose augmenting a bibliographic reference. This text is intended to be shown after the rest of the generated reference text.
### Schema
Can be child of: `reference`

Contents: `( text | bcp14 | cref | em | eref | iref | strong | sub | sup | tt | u | xref )*`

## area
## Tabs {.tabset}
### Usage
Provides information about the IETF area to which this document relates (currently not used when generating documents).

The value ought to be either the full name or the abbreviation of one of the IETF areas as listed on http://www.ietf.org/iesg/area.html. A list of full names and abbreviations will be kept by the RFC Series Editor.
### Schema
Can be child of: `front`

Contents: `text`

## artset
## Tabs {.tabset}
### Usage
This element allows for the support of multiple artwork formats, in order to provide suitable artwork for different output formats.

When multiple `artwork` instances are provided within one `artset` element, the renderer will try to pick the `artwork` instance which is most appropriate for its current output format from the given alternatives.

If more than one `artwork` element with the same "type" is found within an `artset` element, the renderer could select the first one, or possibly choose between the alternative instances based on the output format and some quality of the alternatives that make one more suitable than the others for that particular format, such as size, aspect ratio, etc.
### Schema
Can be child of: `aside`, `blockquote`, `dd`, `figure`, `li`, `section`, `td`, `th`

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
```xml
<artwork type="svg"><svg xmlns="http://www.w3.org/2000/ svg...">
  ```
* Inline, but using XInclude (see Appendix B.1), such as:
```xml
<artwork type="svg"><xi:include href=...>
  ```
* As a data: URI, such as:
```xml 
<artwork type="svg" src="data:image/svg+xml,%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww...">
  ```
* As a URI to an external entity, such as:
```xml
<artwork type="svg" src="http://www.example.com/...">
  ```
* As a local file, such as:
```xml
<artwork type="svg" src="diagram12.svg">
  ```

The use of SVG in Internet-Drafts and RFCs is covered in much more detail in [RFC7996].

The above methods for inclusion of SVG art can also be used for including text artwork, but using a data: URI is probably confusing for text artwork.

Formatters that do pagination should attempt to keep artwork on a single page. This is to prevent artwork that is split across pages from looking like two separate pieces of artwork.

See Section 5 for a description of how to deal with issues of using "&" and "<" characters in artwork.

### Schema
Can be child of: `artset`, `aside`, `blockquote`, `dd`, `figure`, `li`, `section`, `td`, `th`

Contents: `( text* | svg )`
### Attributes

#### "align"
Controls whether the artwork appears left justified, centered, or right justified.

Possible values: `( "left" | "center" | "right" )`
Default value: `"left"`

#### "alt"
Alternative text description of the artwork (which is more than just a summary or caption). When the art comes from the "src" attribute and the format of that artwork supports alternate text, the alternative text comes from the text of the artwork itself, not from this attribute. The contents of this attribute are important to readers who are visually impaired, as well as those reading on devices that cannot show the artwork well, or at all.

#### "anchor"
Document-wide unique identifier for this element.

#### "height"
TBD

#### "name"
A filename suitable for the contents (such as for extraction to a local file). This attribute can be helpful for other kinds of tools (such as automated syntax checkers, which work by extracting the artwork). Note that the "name" attribute does not need to be unique for `artwork` elements in a document. If multiple `artwork` elements have the same "name" attribute, a processing tool might assume that the elements are all fragments of a single file, and the tool can collect those fragments for later processing.

#### "src"
The URI reference of a graphics file RFC3986, or the name of a file on the local disk. This can be a "data" URI RFC2397 that contains the contents of the graphics file. Note that the inclusion of art with the "src" attribute depends on the capabilities of the processing tool reading the XML document. Tools need to be able to handle the file: URI, and they should be able to handle http: and https: URIs as well. The prep tool will be able to handle reading the "src" attribute.

If no URI scheme is given in the attribute, the attribute is considered to be a local filename relative to the current directory. Processing tools must be careful to not accept dangerous values for the filename, particularly those that contain absolute references outside the current directory. Document creators should think hard before using relative URIs due to possible later problems if files move around on the disk. Also, documents should most likely use explicit URI schemes wherever possible.

In some cases, the prep tool may remove the "src" attribute after processing its value. See RFC7998 for a description of this.

#### "type"
Specifies the format of the artwork. The value of this attribute is free text with certain values designated as preferred.

The preferred values for `artwork` types are:

* ascii-art
* binary-art
* svg

Values that don't describe the format, such as "call-flow" or "hex-dump" were mentioned in RFC7991, but are not supported here; they are instead candidates for use with another future attribute to describe the artwork content.

A complete list of the preferred values is maintained on the RFC Editor web site, and that list is expected to be updated over time. Thus, a consumer of this attribute should not cause a failure when it encounters an unexpected type or no type is specified. The table will also indicate which type of art can appear in plain-text output (for example, type="svg" cannot).

#### "width"
TBD

## aside
## Tabs {.tabset}
### Usage
This element is a container for content that is semantically less important or tangential to the content that surrounds it.
 
### Schema
Can be child of: `dd`, `section`

Contents: `( artset | artwork | blockquote | dl | figure | iref | ol | t | table | ul )*`
### Attributes

#### "anchor"
Document-wide unique identifier for this `aside` element.

## author
## Tabs {.tabset}
### Usage
Provides information about a document's author. This is used both for the document itself (at the beginning of the document) and for referenced documents.

The `author` elements contained within the document's `front` element are used to fill the boilerplate and also to generate the "Author's Address" section (see RFC7322).

Note that an "author" can also be just an organization (by not specifying any of the "name" attributes, but adding the `organization` child element).

Furthermore, the "role" attribute can be used to mark an author as "editor". This is reflected both on the front page and in the "Author's Address" section, as well as in bibliographic references. Note that this specification does not define a precise meaning for the term "editor".

### Schema
Can be child of: `front`, `section`

Contents: `organization?, address?`
### Attributes

#### "anchor"
Document-wide unique identifier for this `author` element.

#### "asciiFullname" 

The Latin script equivalent of the author's full name.

#### "asciiInitials" 

The Latin script equivalent of the author's initials, to be used in conjunction with the separately specified asciiSurname.

#### "asciiSurname" 

The Latin script equivalent of the author's surname, to be used in conjunction with the separately specified asciiInitials.

#### "fullname" 

The full name (used in the automatically generated "Author's Address" section). Although this attribute is optional, if one or more of the "asciiFullname", "asciiInitials", or "asciiSurname" attributes does not have values, the "fullname" attribute is required.

#### "initials" 

An abbreviated variant of the given name(s), to be used in conjunction with the separately specified surname. It usually appears on the front page, in footers, and in references.

Some processors will post-process the value -- for instance, when it only contains a single letter (in which case they might add a trailing dot). Relying on this kind of post-processing can lead to results varying across formatters and thus ought to be avoided.

#### "role" 

Specifies the role the author had in creating the document.

#### "surname" 

The author's surname, to be used in conjunction with the separately specified initials. It usually appears on the front page, in footers, and in references.

## back
## Tabs {.tabset}
### Usage
Contains the "back" part of the document: the references and appendices. In `back`, `section` elements indicate appendices.

### Schema
Can be child of: `rfc`

Contents: `displayreference*, references*, section*`

## bcp14
## Tabs {.tabset}
### Usage
Marks text that are phrases defined in BCP14 such as "MUST", "SHOULD NOT", and so on. When shown in some of the output representations, the text in this element might be highlighted. The use of this element is optional.

This element is only to be used around the actual phrase from BCP 14, not the full definition of a requirement. For example, it is correct to say "The packet \<bcp14>MUST\</bcp14> be dropped.", but it is not correct to say "\<bcp14>The packet MUST be dropped.\</bcp14>".
### Schema
Can be child of: `annotation`, `blockquote`, `dd`, `dt`, `em`, `li`, `name`, `refcontent`, `strong`, `sub`, `sup`, `t`, `td`, `th`, `tt`.

Contents: `text`

## blockquote
## Tabs {.tabset}
### Usage
Specifies that a block of text is a quotation.
### Schema
Can be child of: `aside`, `li`, `section`

Contents: `( ( artset | artwork | dl | figure | ol | sourcecode | t | ul )+ | ( text | bcp14 | br | cref | em | eref | iref | strong | sub | sup | tt | u | xref )+ )`
### Attributes

#### "cite" 
The source of the citation. This must be a URI. If the "quotedFrom" attribute is given, this URI will be used by processing tools as the link for the text of that attribute.

#### "quotedFrom" 
Name of person or document the text in this element is quoted from. A formatter should render this as visible text at the end of the quotation.

## boilerplate
## Tabs {.tabset}
### Usage
Holds the boilerplate text for the document. This element is filled in by the prep tool.

This element contains `section` elements. Every `section` element in this element must have the "numbered" attribute set to "false".
### Schema
Can be child of: `front`

Contents: `section+`

## br
## Tabs {.tabset}
### Usage
Inserts a forced break. Use sparingly. In most situations, it's better to insert U+200B, ZERO WIDTH SPACE, in order to encourage line breaking at a point where it would otherwise not occur.

### Schema
Can be child of: `blockquote`, `cref`, `dd`, `dt`, `em`, `li`, `name`, `strong`, `t`, `td`, `th`, `title`, `tt`

Contents: `empty`

## city
## Tabs {.tabset}
### Usage
Gives the city name in a postal address.

### Schema
Can be child of: `postal`

Contents: `text`
### Attributes
#### "ascii"

The ASCII equivalent of the `city` content. This element may have non-ASCII Latin script content without specifying an ASCII equivalent, but for other non-ASCII content an ASCII equivalent is required.

## cityarea
## Tabs {.tabset}
### Usage
Where postal addresses use city subdivisions, these are mapped to the `cityarea` element. Korean addresses would use this for a city district, for instance. Countries known to use this element are Ascension Island, China, Iran, South Korea, and Thailand.
### Schema
Can be child of: `postal`

Content schema: `text`
### Attributes
#### "ascii" 
The ASCII equivalent of the `cityarea` content. This element may have non-ASCII Latin script content without specifying an ASCII equivalent, but for other non-ASCII content an ASCII equivalent is required.

## code
## Tabs {.tabset}
### Usage
Gives the postal region code.
### Schema
This element can be a child element of `postal`.

Contents: `text`

### "ascii" 
The ASCII equivalent of the `code` content. This element may have non-ASCII Latin script content without specifying an ASCII equivalent, but for other non-ASCII content an ASCII equivalent is required.

## contact
## Tabs {.tabset}
### Usage
Provides information about contributors. This element can be used inline within a `t`, and will be rendered with name only, similarly to how `author` is rendered in a `reference`, or it can be used as a direct child of `section`, where it will be rendered the same way as an author address block within the "Authors' Addresses" section.

Note that a "contact" can also be just an organization (by not specifying any of the "name" attributes, but adding the `organization` child element).
### Schema
This element can be a child element of `section`, `t`

Contents: `organization?, address?`
### Attributes
#### "anchor" 
Document-wide unique identifier for this element.

#### "asciiFullname"
The Latin script equivalent of the contact's full name.

#### "asciiInitials" 
The Latin script equivalent of the contact's initials, to be used in conjunction with the separately specified asciiSurname.

#### "asciiSurname" 
The Latin script equivalent of the contact's surname, to be used in conjunction with the separately specified asciiInitials.

#### "fullname"
The full name. Although this attribute is optional, if one or more of the "asciiFullname", "asciiInitials", or "asciiSurname" attributes does not have values, the "fullname" attribute is required.

#### "initials" 
An abbreviated variant of the given name(s), to be used in conjunction with the separately specified surname.

#### "surname" 
The contact's surname, to be used in conjunction with the separately specified initials.

## country
## Tabs {.tabset}
### Usage
Specifies the country name in a postal address. All common and official country names should be recognized; in addition two- and three-letter country codes according to ISO 3166 are recognized.

xml2rfc has a help option which will list all names and country codes it recognizes as valid country names: xml2rfc --country-help .
### Schema
This element can be a child element of `postal`.

Contents: `text`
### Attributes
#### "ascii" 
The ASCII equivalent of the `country` content. This element may have non-ASCII Latin script content without specifying an ASCII equivalent, but for other non-ASCII content an ASCII equivalent is required.

## cref
## Tabs {.tabset}
### Usage
Represents a comment.

Comments can be used in a document while it is work in progress. They might appear either inline and visually highlighted, at the end of the document, or not at all, depending on the formatting tool.

### Schema
This element can be a child element of `annotation`, `blockquote`, `dd`, `dt`, `em`, `li`, `name`, `strong`, `sub`, `sup`, `t`, `td`, `th`, `tt`

Content schema: ( text | br | em | eref | strong | sub | sup | tt | xref )*
### Attributes
#### "anchor" 
Document-wide unique identifier for this element.

#### "display" 
Suggests whether or not the comment should be displayed by formatting tools. This might be set to "false" if you want to keep a comment in a document after the contents of the comment have already been dealt with.
  
Possible values: ( "true" | "false" )
Default value: "true"

#### "source" 
Holds the "source" of a comment, such as the name or the initials of the person who made the comment.

## date
## Tabs {.tabset}
### Usage
Provides information about the publication date. This element is used for two cases: the boilerplate of the document being produced, and inside bibliographic references that use the `front` element.

Bibliographic references:
* In order to be able to specify fuzzy dates, such as "2002-2003", "Second quarter 2010", etc., the date element is now permitted to have text content in addition to the "year", "month", and "day" attributes. If there is only text content, it will be rendered as is. If there is both text content and date components, both will be rendered, with the expanded date components in parentheses.

Boilerplate for Internet-Drafts and RFCs:
* This element defines the date of publication for the current document (Internet-Draft or RFC). When producing Internet-Drafts, the prep tool uses this date to compute the expiration date (see [IDGUIDE]). When one or more of "year", "month", or "day" are left out, the prep tool will attempt to use the current system date if the attributes that are present are consistent with that date.

In dates in `rfc` elements, the month must be a number or a month in English. The prep tool will silently change text month names to numbers. Similarly, the year must be a four-digit number.

When the prep tool is used to create Internet-Drafts, it will warn if the draft has a `date` element in the boilerplate for itself that is more than 3 days away from today. To avoid this problem, authors might simply not include a `date` element in the boilerplate.
### Schema
This element can be a child element of `front`

Content schema: text
### Attributes
#### "day" 
The day of publication.

#### "month" 
The month of publication.

#### "year" 
The year of publication.

## dd
## Tabs {.tabset}
### Usage
The definition part of an entry in a definition list.
### Schema
This element can be a child element of `dl`.

Content schema: ( ( artset | artwork | aside | dl | figure | ol | sourcecode | t | table | ul )+ | ( text | bcp14 | br | cref | em | eref | iref | strong | sub | sup | tt | u | xref )+ )
### Attributes
#### "anchor" 
Document-wide unique identifier for this element.

## displayreference
## Tabs {.tabset}
### Usage
This element gives a mapping between the anchor of a reference and a name that will be displayed instead. This allows authors to display more mnemonic anchor names for automatically included references. The mapping in this element only applies to `xref` elements whose format is "default". For example, if the reference uses the anchor "RFC6949", the following would cause that anchor in the body of displayed documents to be "RFC-dev":
```xml
<displayreference target="RFC6949" to="RFC-dev"/>
```
If a reference section is sorted, this element changes the sort order.
### Schema
This element can be a child element of `back`.
### Attributes
#### "target" (Required)
This attribute must be the name of an anchor in a `reference` or `referencegroup` element.

#### "to" (Required)
This attribute is a name that will be displayed as the anchor instead of the anchor that is given in the `reference` element. The string given must start with one of the following characters: 0-9, a-z, or A-Z. The other characters in the string must be 0-9, a-z, A-Z, "-", ".", or "_".

## dl
## Tabs {.tabset}
### Usage
A definition list. Each entry has a pair of elements: a term (`dt`) and a definition (`dd`). (This is slightly different and simpler than the model used in HTML, which allows for multiple terms for a single definition.)
### Schema
This element can be a child element of `abstract`, `aside`, `blockquote`, `dd`, `li`, `note`, `section`, `td`, `th`.

Content schema: ( dt, dd )+
### Attributes
#### "anchor" 
Document-wide unique identifier for this element.

#### "indent"
Indicates the indentation to be used for the rendering of the second and following lines of the item (the first line starts with the term, and is not indented). The indentation amount is interpreted as characters when rendering plain-text documents, and en-space units when rendering in formats that have richer typographic support such as HTML or PDF. One en-space is assumed to be the length of 0.5 em-space in CSS units.

Default value: "3"

#### "newline"
The "newline" attribute defines whether or not the term appears on the same line as the definition. newline="false" indicates that the term is to the left of the definition, while newline="true" indicates that the term will be on a separate line.

Possible values: ( "true" | "false" )
Default value: "false"

#### "spacing"
Defines whether or not there is a blank line between entries. spacing="normal" indicates a single blank line, while spacing="compact" indicates no blank line between entries.

Possible values: ( "normal" | "compact" )
Default value: "normal"


