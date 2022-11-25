---
title: RFCXML vocabulary reference
description: 
published: true
date: 2021-12-16T02:50:37.055Z
tags: 
editor: markdown
dateCreated: 2021-11-02T22:58:38.001Z
---

The current version of the RFCXML vocabulary is v3 and this page is currently the authoritative documentation for v3, superseding RFC 7991 as multiple changes have been made since the publication of RFC 7991.  

All documents written in RFCXML  begin with the root element [**\<rfc\>**](/rfcxml-vocabulary#rfc) and follow the schema rules for the contents of each element.  The available elements are listed below along with their attributes and a snippet of the [RNC schema](/templates-and-schemas) that defines that element.

> NOTE:  The schema snippets below include reference to elements and attributes that have been deprecated and should not be used.  Details of this deprecated syntax can be found in [Upgrading from v2](/upgrading-from-v2).
{.is-info}


# Elements

## abstract
## Tabs {.tabset}
### Usage
Contains the Abstract of the document. See RFC7322 for more information on restrictions for the Abstract.

Used in: [**\<front\>**](/rfcxml-vocabulary#front)
Allowed content: ([**\<dl\>**](/rfcxml-vocabulary#dl), [**\<ol\>**](/rfcxml-vocabulary#ol), [**\<t\>**](/rfcxml-vocabulary#t), [**\<ul\>**](/rfcxml-vocabulary#ul))+

### Attributes
#### anchor
Document-wide unique identifier for this element.
### Schema
```
   abstract =
     element abstract {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute anchor { xsd:ID }?,
       attribute pn { xsd:ID }?,
       (dl | ol | t | ul)+
     }
```


## address
## Tabs {.tabset}
### Usage
Provides address information for the author.

Used in: [**\<author\>**](/rfcxml-vocabulary#author), [**\<contact\>**](/rfcxml-vocabulary#contact)
Allowed content: [**\<postal\>**](/rfcxml-vocabulary#postal)?, [**\<phone\>**](/rfcxml-vocabulary#phone)?, [**\<email\>**](/rfcxml-vocabulary#email)\*, [**\<uri\>**](/rfcxml-vocabulary#uri)?
### Schema
```
   address =
     element address {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       postal?,
       phone?,
       facsimile?,
       email*,
       uri?
     }
```


## annotation
## Tabs {.tabset}
### Usage
Provides additional prose augmenting a bibliographic reference. This text is intended to be shown after the rest of the generated reference text.

Used in: [**\<reference\>**](/rfcxml-vocabulary#reference)
Allowed content: ( text | [**\<bcp14\>**](/rfcxml-vocabulary#bcp14) | [**\<cref\>**](/rfcxml-vocabulary#cref) | [**\<em\>**](/rfcxml-vocabulary#em) | [**\<eref\>**](/rfcxml-vocabulary#eref) | [**\<iref\>**](/rfcxml-vocabulary#iref) | [**\<strong\>**](/rfcxml-vocabulary#strong) | [**\<sub\>**](/rfcxml-vocabulary#sub) | [**\<sup\>**](/rfcxml-vocabulary#sup) | [**\<tt\>**](/rfcxml-vocabulary#tt) | [**\<u\>**](/rfcxml-vocabulary#u) | [**\<xref\>**](/rfcxml-vocabulary#xref) )*
### Schema
```
   annotation =
     element annotation {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       (text
        | bcp14
        | cref
        | em
        | eref
        | iref
        | relref
        | spanx
        | strong
        | sub
        | sup
        | tt
        | u
        | xref)*
     }
```

## area
## Tabs {.tabset}
### Usage
Provides information about the IETF area to which this document relates (currently not used when generating documents).

The value ought to be either the full name or the abbreviation of one of the listed [IETF areas](https://www.ietf.org/iesg/area.html).

Used in: [**\<front\>**](/rfcxml-vocabulary#front)
Allowed content: text
### Schema
```
   area =
     element area {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       text
     }
```

## artset
## Tabs {.tabset}
### Usage
This element allows for the support of multiple artwork formats, in order to provide suitable artwork for different output formats.  See [diagrams](/diagrams) for more details on diagrams and SVG.

When multiple [**\<artwork\>**](/rfcxml-vocabulary#artwork) instances are provided within one [**\<artset\>**](/rfcxml-vocabulary#artset) element, the renderer will try to pick the [**\<artwork\>**](/rfcxml-vocabulary#artwork) instance which is most appropriate for its current output format from the given alternatives.

If more than one [**\<artwork\>**](/rfcxml-vocabulary#artwork) element with the same **type** is found within an [**\<artset\>**](/rfcxml-vocabulary#artset) element, the renderer could select the first one, or possibly choose between the alternative instances based on the output format and some quality of the alternatives that make one more suitable than the others for that particular format, such as size, aspect ratio, etc.

Used in: [**\<aside\>**](/rfcxml-vocabulary#aside), [**\<blockquote\>**](/rfcxml-vocabulary#blockquote), [**\<dd\>**](/rfcxml-vocabulary#dd), [**\<figure\>**](/rfcxml-vocabulary#figure), [**\<li\>**](/rfcxml-vocabulary#li), [**\<section\>**](/rfcxml-vocabulary#section), [**\<td\>**](/rfcxml-vocabulary#td), [**\<th\>**](/rfcxml-vocabulary#th)
Allowed content: [**\<artwork\>**](/rfcxml-vocabulary#artwork)+

### Attributes
#### anchor
Document-wide unique identifier for this element.
### Schema
```
   artset =
     element artset {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute anchor { xsd:ID }?,
       attribute pn { xsd:ID }?,
       artwork+
     }
```

## artwork
## Tabs {.tabset}
### Usage
This element allows the inclusion of artwork in the document. [**\<artwork\>**](/rfcxml-vocabulary#artwork) provides full control of horizontal whitespace and line breaks; thus, it is used for a variety of things, such as diagrams ("line art") and protocol unit diagrams. See [diagrams](/diagrams) for more details on diagrams and SVG.

Tab characters (U+0009) inside of this element are prohibited.

Alternatively, the **src** attribute allows referencing an external graphics file, such as a vector drawing in SVG or a bitmap graphic file, using a URI. In this case, the textual content acts as a fallback for output representations that do not support graphics; thus, it ought to contain either (1) a "line art" variant of the graphics or (2) prose that describes the included image in sufficient detail.

In order to include alternative artwork expressions for different output formats, you should provide multiple [**\<artwork\>**](/rfcxml-vocabulary#artwork) elements enclosed within an [**\<artset\>**](/rfcxml-vocabulary#artset). The text renderer will prefer instances with **type** of "ascii-art", while the HTML and PDF renderers will prefer instances with **type** of "svg".

The [**\<artwork\>**](/rfcxml-vocabulary#artwork) element should not be used for source code and formal languages, the [**\<sourcecode\>**](/rfcxml-vocabulary#sourcecode) element should be used instead.

There are at least five ways to include SVG in artwork in Internet- Drafts:

* Inline, by including all of the SVG in the content of the element, such as:
```xml
<artwork type="svg"><svg xmlns="http://www.w3.org/2000/ svg...">
```
* Inline, but using XInclude, such as:
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

The above methods for inclusion of SVG art can also be used for including text artwork, but using a data: URI is probably confusing for text artwork.

Formatters that do pagination should attempt to keep artwork on a single page. This is to prevent artwork that is split across pages from looking like two separate pieces of artwork.

Used in: [**\<artset\>**](/rfcxml-vocabulary#artset), [**\<aside\>**](/rfcxml-vocabulary#aside), [**\<blockquote\>**](/rfcxml-vocabulary#blockquote), [**\<dd\>**](/rfcxml-vocabulary#dd), [**\<figure\>**](/rfcxml-vocabulary#figure), [**\<li\>**](/rfcxml-vocabulary#li), [**\<section\>**](/rfcxml-vocabulary#section), [**\<td\>**](/rfcxml-vocabulary#td), [**\<th\>**](/rfcxml-vocabulary#th)
Allowed content: ( [**\<text\>**](/rfcxml-vocabulary#text)\* | [**\<svg\>**](/rfcxml-vocabulary#svg) )

### Attributes
#### align
Controls whether the artwork appears left justified, centered, or right justified.

Possible values: "left", "center", "right"
Default value: "left"

#### alt
Alternative text description of the artwork (which is more than just a summary or caption). When the art comes from the **src** attribute and the format of that artwork supports alternate text, the alternative text comes from the text of the artwork itself, not from this attribute. The contents of this attribute are important to readers who are visually impaired, as well as those reading on devices that cannot show the artwork well, or at all.

#### anchor
Document-wide unique identifier for this element.

#### height
TBD

#### name
A filename suitable for the contents (such as for extraction to a local file). This attribute can be helpful for other kinds of tools (such as automated syntax checkers, which work by extracting the artwork). Note that the **name** attribute does not need to be unique for [**\<artwork\>**](/rfcxml-vocabulary#artwork) elements in a document. If multiple [**\<artwork\>**](/rfcxml-vocabulary#artwork) elements have the same **name** attribute, a processing tool might assume that the elements are all fragments of a single file, and the tool can collect those fragments for later processing.

#### src
The URI reference of a graphics file (RFC3986), or the name of a file on the local disk. This can be a "data" URI RFC2397 that contains the contents of the graphics file. Note that the inclusion of art with the **src** attribute depends on the capabilities of the processing tool reading the XML document. Tools need to be able to handle the file: URI, and they should be able to handle http: and https: URIs as well. The prep tool will be able to handle reading the **src** attribute.

If no URI scheme is given in the attribute, the attribute is considered to be a local filename relative to the current directory. Processing tools must be careful to not accept dangerous values for the filename, particularly those that contain absolute references outside the current directory. Document creators should think hard before using relative URIs due to possible later problems if files move around on the disk. Also, documents should most likely use explicit URI schemes wherever possible.

In some cases, the prep tool may remove the **src** attribute after processing its value. See RFC7998 for a description of this.

#### type
Specifies the format of the artwork. The value of this attribute is free text with certain values designated as preferred.

The preferred values for **type** are: "ascii-art", "binary-art", "svg"

Values that don't describe the format, such as "call-flow" or "hex-dump" were mentioned in RFC7991, but are not supported; they are instead candidates for use with another future attribute to describe the artwork content.

See [Diagrams](/diagrams) for more information on how these types are rendered into different output formats.

#### width
TBD
### Schema
```
   artwork =
     element artwork {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute anchor { xsd:ID }?,
       attribute pn { xsd:ID }?,
       attribute xml:space { text }?,
       [ a:defaultValue = "" ] attribute name { text }?,
       [ a:defaultValue = "" ] attribute type { text }?,
       attribute src { text }?,
       [ a:defaultValue = "left" ]
       attribute align { "left" | "center" | "right" }?,
       [ a:defaultValue = "" ] attribute alt { text }?,
       [ a:defaultValue = "" ] attribute width { text }?,
       [ a:defaultValue = "" ] attribute height { text }?,
       attribute originalSrc { text }?,
       (text* | svg)
     }
```

## aside
## Tabs {.tabset}
### Usage
This element is a container for content that is semantically less important or tangential to the content that surrounds it.
 
Used in: [**\<dd\>**](/rfcxml-vocabulary#dd), [**\<section\>**](/rfcxml-vocabulary#section)
Allowed content: ( [**\<artset\>**](/rfcxml-vocabulary#artset) | [**\<artwork\>**](/rfcxml-vocabulary#artwork) | [**\<blockquote\>**](/rfcxml-vocabulary#blockquote) | [**\<dl\>**](/rfcxml-vocabulary#dl) | [**\<figure\>**](/rfcxml-vocabulary#figure) | [**\<iref\>**](/rfcxml-vocabulary#iref) | [**\<ol\>**](/rfcxml-vocabulary#ol) | [**\<t\>**](/rfcxml-vocabulary#t) | [**\<table\>**](/rfcxml-vocabulary#table) | [**\<ul\>**](/rfcxml-vocabulary#ul) )*

### Attributes
#### anchor
Document-wide unique identifier for this element.
### Schema
```
   aside =
     element aside {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute anchor { xsd:ID }?,
       attribute pn { xsd:ID }?,
       (artset
        | artwork
        | blockquote
        | dl
        | figure
        | iref
        | ol
        | t
        | table
        | ul)*
     }
```

## author
## Tabs {.tabset}
### Usage
Provides information about a document's author. This is used both for the document itself (at the beginning of the document) and for referenced documents.

The [**\<author\>**](/rfcxml-vocabulary#author) elements contained within the document's [**\<front\>**](/rfcxml-vocabulary#front) element are used to fill the boilerplate and also to generate the "Author's Address" section (see RFC7322).

Note that an author can also be solely an organization by adding the [**\<organization\>**](/rfcxml-vocabulary#organization) child element and not specifying any of the **name** attributes.

Furthermore, the **role** attribute can be used to mark an author as "editor". This is reflected both on the front page and in the "Author's Address" section, as well as in bibliographic references.

Used in: [**\<front\>**](/rfcxml-vocabulary#front), [**\<section\>**](/rfcxml-vocabulary#section)
Allowed content: [**\<organization\>**](/rfcxml-vocabulary#organization)?, [**\<address\>**](/rfcxml-vocabulary#address)?

### Attributes
#### anchor
Document-wide unique identifier for this element.

#### asciiFullname
The Latin script equivalent of the author's full name.

#### asciiInitials
The Latin script equivalent of the author's initials, to be used in conjunction with the separately specified **asciiSurname**.

#### asciiSurname
The Latin script equivalent of the author's surname, to be used in conjunction with the separately specified **asciiInitials**.

#### fullname
The full name (used in the automatically generated "Author's Address" section). Although this attribute is optional, if one or more of the **asciiFullname**, **asciiInitials**, or **asciiSurname** attributes does not have values, the **fullname** attribute is required.

#### initials
An abbreviated variant of the given name(s), to be used in conjunction with the separately specified **surname**. It usually appears on the front page, in footers, and in references.

Some processors will post-process the value, for instance when it only contains a single letter (in which case they might add a trailing dot). Relying on this kind of post-processing can lead to results varying across formatters and thus ought to be avoided.

#### role
Specifies the role the author had in creating the document.

#### surname
The author's surname, to be used in conjunction with the separately specified **initials**. It usually appears on the front page, in footers, and in references.
### Schema
```
   author =
     element author {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute anchor { xsd:ID }?,
       attribute initials { text }?,
       attribute asciiInitials { text }?,
       attribute surname { text }?,
       attribute asciiSurname { text }?,
       attribute fullname { text }?,
       attribute role { "editor" }?,
       attribute asciiFullname { text }?,
       organization?,
       address?
     }
```

## back
## Tabs {.tabset}
### Usage
Contains the Back part of the document: the references and appendices. In [**\<back\>**](/rfcxml-vocabulary#back), [**\<section\>**](/rfcxml-vocabulary#section) elements indicate appendices.

Used in: [**\<rfc\>**](/rfcxml-vocabulary#rfc)
Allowed content: [**\<displayreference\>**](/rfcxml-vocabulary#displayreference)\*, [**\<references\>**](/rfcxml-vocabulary#references)\*, [**\<section\>**](/rfcxml-vocabulary#section)\*
### Schema
```
   back =
     element back {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       displayreference*,
       references*,
       section*
     }
```

## bcp14
## Tabs {.tabset}
### Usage
Marks text that are phrases defined in [BCP14](https://www.rfc-editor.org/rfc/rfc2119.html) such as "MUST", "SHOULD NOT", and so on. When shown in some of the output representations, the text in this element might be highlighted. The use of this element is optional but it makes the usage much clearer.

This element is only to be used around the actual phrase from BCP 14, not the full definition of a requirement. For example, it is correct to say `The packet <bcp14>MUST</bcp14> be dropped.`, but it is not correct to say `<bcp14>The packet MUST be dropped.</bcp14>`.

Used in: [**\<annotation\>**](/rfcxml-vocabulary#annotation), [**\<blockquote\>**](/rfcxml-vocabulary#blockquote), [**\<dd\>**](/rfcxml-vocabulary#dd), [**\<dt\>**](/rfcxml-vocabulary#dt), [**\<em\>**](/rfcxml-vocabulary#em), [**\<li\>**](/rfcxml-vocabulary#li), [**\<name\>**](/rfcxml-vocabulary#name), [**\<refcontent\>**](/rfcxml-vocabulary#refcontent), [**\<strong\>**](/rfcxml-vocabulary#strong), [**\<sub\>**](/rfcxml-vocabulary#sub), [**\<sup\>**](/rfcxml-vocabulary#sup), [**\<t\>**](/rfcxml-vocabulary#t), [**\<td\>**](/rfcxml-vocabulary#td), [**\<th\>**](/rfcxml-vocabulary#th), [**\<tt\>**](/rfcxml-vocabulary#tt).
Allowed content: text
### Schema
```
   bcp14 =
     element bcp14 {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       text
     }
```

## blockquote
## Tabs {.tabset}
### Usage
Specifies that a block of text is a quotation.

Used in: [**\<aside\>**](/rfcxml-vocabulary#aside), [**\<li\>**](/rfcxml-vocabulary#li), [**\<section\>**](/rfcxml-vocabulary#section)
Allowed content: ( ( [**\<artset\>**](/rfcxml-vocabulary#artset) | [**\<artwork\>**](/rfcxml-vocabulary#artwork) | [**\<dl\>**](/rfcxml-vocabulary#dl) | [**\<figure\>**](/rfcxml-vocabulary#figure) | [**\<ol\>**](/rfcxml-vocabulary#ol) | [**\<sourcecode\>**](/rfcxml-vocabulary#sourcecode) | [**\<t\>**](/rfcxml-vocabulary#t) | [**\<ul\>**](/rfcxml-vocabulary#ul) )+ | ( text | [**\<bcp14\>**](/rfcxml-vocabulary#bcp14) | [**\<br\>**](/rfcxml-vocabulary#br) | [**\<cref\>**](/rfcxml-vocabulary#cref) | [**\<em\>**](/rfcxml-vocabulary#em) | [**\<eref\>**](/rfcxml-vocabulary#eref) | [**\<iref\>**](/rfcxml-vocabulary#iref) | [**\<strong\>**](/rfcxml-vocabulary#strong) | [**\<sub\>**](/rfcxml-vocabulary#sub) | [**\<sup\>**](/rfcxml-vocabulary#sup) | [**\<tt\>**](/rfcxml-vocabulary#tt) | [**\<u\>**](/rfcxml-vocabulary#u) | [**\<xref\>**](/rfcxml-vocabulary#xref) )+ )

### Attributes
#### anchor
Document-wide unique identifier for this element.

#### cite
The source of the citation. This must be a URI. If the **quotedFrom** attribute is given, this URI will be used by processing tools as the link for the text of that attribute.

#### quotedFrom
Name of person or document the text in this element is quoted from. A formatter should render this as visible text at the end of the quotation.
### Schema
```
   blockquote =
     element blockquote {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute anchor { xsd:ID }?,
       attribute pn { xsd:ID }?,
       attribute cite { text }?,
       attribute quotedFrom { text }?,
       ((artset | artwork | dl | figure | ol | sourcecode | t | ul)+
        | (text
           | bcp14
           | br
           | cref
           | em
           | eref
           | iref
           | relref
           | strong
           | sub
           | sup
           | tt
           | u
           | xref)+)
     }
```

## boilerplate
## Tabs {.tabset}
### Usage
Holds the boilerplate text for the document. This element is filled in by the prep tool.

This element contains [**\<section\>**](/rfcxml-vocabulary#section) elements. Every [**\<section\>**](/rfcxml-vocabulary#section) element inside this element must have the **numbered** attribute set to "false".

Used in: [**\<front\>**](/rfcxml-vocabulary#front)
Allowed content: [**\<section\>**](/rfcxml-vocabulary#section)+
### Schema
```
   boilerplate =
     element boilerplate {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       section+
     }
```

## br
## Tabs {.tabset}
### Usage
Inserts a forced break. Use sparingly. In most situations, it's better to insert U+200B, ZERO WIDTH SPACE, in order to encourage line breaking at a point where it would otherwise not occur.

Used in: [**\<blockquote\>**](/rfcxml-vocabulary#blockquote), [**\<cref\>**](/rfcxml-vocabulary#cref), [**\<dd\>**](/rfcxml-vocabulary#dd), [**\<dt\>**](/rfcxml-vocabulary#dt), [**\<em\>**](/rfcxml-vocabulary#em), [**\<li\>**](/rfcxml-vocabulary#li), [**\<name\>**](/rfcxml-vocabulary#name), [**\<strong\>**](/rfcxml-vocabulary#strong), [**\<t\>**](/rfcxml-vocabulary#t), [**\<td\>**](/rfcxml-vocabulary#td), [**\<th\>**](/rfcxml-vocabulary#th), [**\<title\>**](/rfcxml-vocabulary#title), [**\<tt\>**](/rfcxml-vocabulary#tt)
Allowed content: empty
### Schema
```
   br =
     element br {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       empty
     }
```

## city
## Tabs {.tabset}
### Usage
Gives the city name in a postal address.

Used in: [**\<postal\>**](/rfcxml-vocabulary#postal)
Allowed content: text

### Attributes
#### "ascii"

The ASCII equivalent of the [**\<city\>**](/rfcxml-vocabulary#city) content. This element may have non-ASCII Latin script content without specifying an ASCII equivalent, but for other non-ASCII content an ASCII equivalent is required.
### Schema
```
   city =
     element city {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute ascii { text }?,
       text
     }
```

## cityarea
## Tabs {.tabset}
### Usage
Where postal addresses use city subdivisions, these are mapped to the [**\<cityarea\>**](/rfcxml-vocabulary#cityarea) element. Korean addresses would use this for a city district, for instance. Countries known to use this element are Ascension Island, China, Iran, South Korea, and Thailand.

Used in: [**\<postal\>**](/rfcxml-vocabulary#postal)
Allowed content: text

### Attributes
#### ascii 
The ASCII equivalent of the [**\<cityarea\>**](/rfcxml-vocabulary#cityarea) content. This element may have non-ASCII Latin script content without specifying an ASCII equivalent, but for other non-ASCII content an ASCII equivalent is required.
### Schema
```
   cityarea =
     element cityarea {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute ascii { text }?,
       text
     }
```

## code
## Tabs {.tabset}
### Usage
Gives the postal region code.

Used in: [**\<postal\>**](/rfcxml-vocabulary#postal).
Allowed content: text

### Attributes
#### "ascii" 
The ASCII equivalent of the [**\<code\>**](/rfcxml-vocabulary#code) content. This element may have non-ASCII Latin script content without specifying an ASCII equivalent, but for other non-ASCII content an ASCII equivalent is required.
### Schema
```
   code =
     element code {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute ascii { text }?,
       text
     }
```

## contact
## Tabs {.tabset}
### Usage
Provides information about contributors. This element can be used inline within a [**\<t\>**](/rfcxml-vocabulary#t), and will be rendered with name only, similarly to how [**\<author\>**](/rfcxml-vocabulary#author) is rendered in a [**\<reference\>**](/rfcxml-vocabulary#reference), or it can be used as a direct child of [**\<section\>**](/rfcxml-vocabulary#section), where it will be rendered the same way as an author address block within the Authors' Addresses section.

Note that a  [**\<contact\>**](/rfcxml-vocabulary#contact) can also be just an organization by adding the  [**\<organization\>**](/rfcxml-vocabulary#organization) child element and not providing any of the attributes that specify an individual's name.

Used in: [**\<section\>**](/rfcxml-vocabulary#section), [**\<t\>**](/rfcxml-vocabulary#t)
Allowed content: [**\<organization\>**](/rfcxml-vocabulary#organization)?, [**\<address\>**](/rfcxml-vocabulary#address)?

### Attributes
#### anchor
Document-wide unique identifier for this element.

#### asciiFullname
The Latin script equivalent of the contact's full name.

#### asciiInitials
The Latin script equivalent of the contact's initials, to be used in conjunction with the separately specified **asciiSurname**.

#### asciiSurname
The Latin script equivalent of the contact's surname, to be used in conjunction with the separately specified **asciiInitials**.

#### fullname
The full name. Although this attribute is optional, if one or more of the **asciiFullname**, **asciiInitials**, or **asciiSurname** attributes does not have values, the **fullname** attribute is required.

#### initials
An abbreviated variant of the given name(s), to be used in conjunction with the separately specified **surname**.

#### surname
The contact's surname, to be used in conjunction with the separately specified **initials**.
### Schema
```
   contact =
     element contact {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute anchor { xsd:ID }?,
       attribute initials { text }?,
       attribute asciiInitials { text }?,
       attribute surname { text }?,
       attribute asciiSurname { text }?,
       attribute fullname { text }?,
       attribute asciiFullname { text }?,
       organization?,
       address?
     }
```

## country
## Tabs {.tabset}
### Usage
Specifies the country name in a postal address. All common and official country names should be recognized; in addition two- and three-letter country codes according to ISO 3166 are recognized.

xml2rfc has a help option which will list all names and country codes it recognizes as valid country names: xml2rfc --country-help .

Used in: [**\<postal\>**](/rfcxml-vocabulary#postal).
Allowed content: text

### Attributes
#### ascii
The ASCII equivalent of the [**\<country\>**](/rfcxml-vocabulary#country) content. This element may have non-ASCII Latin script content without specifying an ASCII equivalent, but for other non-ASCII content an ASCII equivalent is required.
### Schema
```
   country =
     element country {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute ascii { text }?,
       text
     }
```

## cref
## Tabs {.tabset}
### Usage
Represents a comment.

Comments can be used in a document while it is work in progress. They might appear either inline and visually highlighted, at the end of the document, or not at all, depending on the formatting tool.

Used in: [**\<annotation\>**](/rfcxml-vocabulary#annotation), [**\<blockquote\>**](/rfcxml-vocabulary#blockquote), [**\<dd\>**](/rfcxml-vocabulary#dd), [**\<dt\>**](/rfcxml-vocabulary#dt), [**\<em\>**](/rfcxml-vocabulary#em), [**\<li\>**](/rfcxml-vocabulary#li), [**\<name\>**](/rfcxml-vocabulary#name), [**\<strong\>**](/rfcxml-vocabulary#strong), [**\<sub\>**](/rfcxml-vocabulary#sub), [**\<sup\>**](/rfcxml-vocabulary#sup), [**\<t\>**](/rfcxml-vocabulary#t), [**\<td\>**](/rfcxml-vocabulary#td), [**\<th\>**](/rfcxml-vocabulary#th), [**\<tt\>**](/rfcxml-vocabulary#tt)
Allowed content: ( text | [**\<br\>**](/rfcxml-vocabulary#br) | [**\<em\>**](/rfcxml-vocabulary#em) | [**\<eref\>**](/rfcxml-vocabulary#eref) | [**\<strong\>**](/rfcxml-vocabulary#strong) | [**\<sub\>**](/rfcxml-vocabulary#sub) | [**\<sup\>**](/rfcxml-vocabulary#sup) | [**\<tt\>**](/rfcxml-vocabulary#tt) | [**\<xref\>**](/rfcxml-vocabulary#xref) )*

### Attributes
#### anchor
Document-wide unique identifier for this element.

#### display
Suggests whether or not the comment should be displayed by formatting tools. This might be set to "false" if you want to keep a comment in a document after the contents of the comment have already been dealt with.
  
Possible values: "true", "false"
Default value: "true"

#### source 
Holds the source of a comment, such as the name or the initials of the person who made the comment.
### Schema
```
   cref =
     element cref {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute anchor { xsd:ID }?,
       attribute source { text }?,
       [ a:defaultValue = "true" ]
       attribute display { "true" | "false" }?,
       (text
        | br
        | em
        | eref
        | relref 
        | strong
        | sub
        | sup
        | tt
        | xref)*
     }
```

## date
## Tabs {.tabset}
### Usage
Provides information about the publication date. This element is used for two cases: the boilerplate of the document being produced, and inside bibliographic references that use the [**\<front\>**](/rfcxml-vocabulary#front) element.

Bibliographic references:
* In order to be able to specify fuzzy dates, such as "2002-2003", "Second quarter 2010", etc., the date element is now permitted to have text content in addition to the **year**, **month**, and **day** attributes. If there is only text content, it will be rendered as is. If there is both text content and date components, both will be rendered, with the expanded date components in parentheses.

Boilerplate for Internet-Drafts and RFCs:
* This element defines the date of publication for the current document (Internet-Draft or RFC). When producing Internet-Drafts, the prep tool uses this date to compute the expiration date (see the [Guidelines for I-D Authors](https://www.ietf.org/standards/ids/guidelines/) for details). When one or more of **year**, **month**, or **day** attributes are left out, the prep tool will attempt to use the current system date if the attributes that are present are consistent with that date.

In dates in [**\<rfc\>**](/rfcxml-vocabulary#rfc) elements, the month must be a number or a month in English. The prep tool will silently change text month names to numbers. Similarly, the year must be a four-digit number.

When the prep tool is used to create Internet-Drafts, it will warn if the draft has a [**\<date\>**](/rfcxml-vocabulary#date) element in the boilerplate for itself that is more than 3 days away from today. To avoid this problem, authors might simply not include a [**\<date\>**](/rfcxml-vocabulary#date) element in the boilerplate.

Used in: [**\<front\>**](/rfcxml-vocabulary#front)
Allowed content: text

### Attributes
#### day 
The day of publication.

#### month
The month of publication.

#### year 
The year of publication.
### Schema
```
   date =
     element date {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute day { text }?,
       attribute month { text }?,
       attribute year { text }?,
       text
     }
```

## dd
## Tabs {.tabset}
### Usage
The definition part of an entry in a definition list.

Used in: [**\<dl\>**](/rfcxml-vocabulary#dl).
Allowed content: ( ( [**\<artset\>**](/rfcxml-vocabulary#artset) | [**\<artwork\>**](/rfcxml-vocabulary#artwork) | [**\<aside\>**](/rfcxml-vocabulary#aside) | [**\<dl\>**](/rfcxml-vocabulary#dl) | [**\<figure\>**](/rfcxml-vocabulary#figure) | [**\<ol\>**](/rfcxml-vocabulary#ol) | [**\<sourcecode\>**](/rfcxml-vocabulary#sourcecode) | [**\<t\>**](/rfcxml-vocabulary#t) | [**\<table\>**](/rfcxml-vocabulary#table) | [**\<ul\>**](/rfcxml-vocabulary#ul) )+ | ( text | [**\<bcp14\>**](/rfcxml-vocabulary#bcp14) | [**\<br\>**](/rfcxml-vocabulary#br) | [**\<cref\>**](/rfcxml-vocabulary#cref) | [**\<em\>**](/rfcxml-vocabulary#em) | [**\<eref\>**](/rfcxml-vocabulary#eref) | [**\<iref\>**](/rfcxml-vocabulary#iref) | [**\<strong\>**](/rfcxml-vocabulary#strong) | [**\<sub\>**](/rfcxml-vocabulary#sub) | [**\<sup\>**](/rfcxml-vocabulary#sup) | [**\<tt\>**](/rfcxml-vocabulary#tt) | [**\<u\>**](/rfcxml-vocabulary#u) | [**\<xref\>**](/rfcxml-vocabulary#xref) )+ )

### Attributes
#### anchor
Document-wide unique identifier for this element.
### Schema
```
   dd =
     element dd {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute anchor { xsd:ID }?,
       attribute pn { xsd:ID }?,
       (( artset
          | artwork
          | aside
          | dl
          | figure
          | ol
          | sourcecode
          | t
          | table
          | ul)+
        | (text
           | bcp14
           | br
           | cref
           | em
           | eref
           | iref
           | relref
           | strong
           | sub
           | sup
           | tt
           | u
           | xref)+)
     }
```

## displayreference
## Tabs {.tabset}
### Usage
This element gives a mapping between the anchor of a reference and a name that will be displayed instead. This allows authors to display more mnemonic anchor names for automatically included references. The mapping in this element only applies to [**\<xref\>**](/rfcxml-vocabulary#xref) elements whose **format** is "default". For example, if the reference uses the anchor "RFC6949", the following would cause that anchor in the body of displayed documents to be "RFC-dev":
```xml
<displayreference target="RFC6949" to="RFC-dev"/>
```
If a reference section is sorted, this element changes the sort order.

Used in: [**\<back\>**](/rfcxml-vocabulary#back).

### Attributes
#### target
Required.

The name of an anchor in a [**\<reference\>**](/rfcxml-vocabulary#reference) or [**\<referencegroup\>**](/rfcxml-vocabulary#referencegroup) element.

#### to
Required. 

The name that will be displayed as the anchor instead of the anchor that is given in the [**\<reference\>**](/rfcxml-vocabulary#reference) element. The string given must start with one of the following characters: 0-9, a-z, or A-Z. The other characters in the string must be 0-9, a-z, A-Z, "-", ".", or "_".
### Schema
```
   displayreference =
     element displayreference {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute target { xsd:IDREF },
       attribute to { text }
     }
```

## dl
## Tabs {.tabset}
### Usage
A definition list. Each entry has a pair of elements: a term ([**\<dt\>**](/rfcxml-vocabulary#dt)) and a definition ([**\<dd\>**](/rfcxml-vocabulary#dd)). (This is slightly different and simpler than the model used in HTML, which allows for multiple terms for a single definition.)

Used in: [**\<abstract\>**](/rfcxml-vocabulary#abstract), [**\<aside\>**](/rfcxml-vocabulary#aside), [**\<blockquote\>**](/rfcxml-vocabulary#blockquote), [**\<dd\>**](/rfcxml-vocabulary#dd), [**\<li\>**](/rfcxml-vocabulary#li), [**\<note\>**](/rfcxml-vocabulary#note), [**\<section\>**](/rfcxml-vocabulary#section), [**\<td\>**](/rfcxml-vocabulary#td), [**\<th\>**](/rfcxml-vocabulary#th).
Allowed content: ( [**\<dt\>**](/rfcxml-vocabulary#dt), [**\<dd\>**](/rfcxml-vocabulary#dd) )+

### Attributes
#### anchor
Document-wide unique identifier for this element.

#### indent
Indicates the indentation to be used for the rendering of the second and following lines of the item (the first line starts with the term, and is not indented). The indentation amount is interpreted as characters when rendering plain-text documents, and en-space units when rendering in formats that have richer typographic support such as HTML or PDF. One en-space is assumed to be the length of 0.5 em-space in CSS units.

Default value: "3"

#### newline
The **newline** attribute defines whether or not the term appears on the same line as the definition. Setting **newline** to "false" indicates that the term is to the left of the definition, while setting **newline** to "true" indicates that the term will be on a separate line.

Possible values: "true", "false"
Default value: "false"

#### spacing
Defines whether or not there is a blank line between entries. Setting **spacing** to "normal" indicates a single blank line, while setting **spacing** to "compact" indicates no blank line between entries.

Possible values: "normal", "compact"
Default value: "normal"
### Schema
```
   dl =
     element dl {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute anchor { xsd:ID }?,
       [ a:defaultValue = "normal" ]
       attribute spacing { "normal" | "compact" }?,
       [ a:defaultValue = "false" ]
       attribute newline { "true" | "false" }?,
       [ a:defaultValue = "3" ]
       attribute indent { text }?,
       attribute pn { xsd:ID }?,
       (dt, dd)+
     }
```

## dt
## Tabs {.tabset}
### Usage
The term being defined in a definition list.

Used in: [**\<dl\>**](/rfcxml-vocabulary#dl).
Allowed content: ( text | [**\<bcp14\>**](/rfcxml-vocabulary#bcp14) | [**\<br\>**](/rfcxml-vocabulary#br) | [**\<cref\>**](/rfcxml-vocabulary#cref) | [**\<em\>**](/rfcxml-vocabulary#em) | [**\<eref\>**](/rfcxml-vocabulary#eref) | [**\<iref\>**](/rfcxml-vocabulary#iref) | [**\<strong\>**](/rfcxml-vocabulary#strong) | [**\<sub\>**](/rfcxml-vocabulary#sub) | [**\<sup\>**](/rfcxml-vocabulary#sup) | [**\<tt\>**](/rfcxml-vocabulary#tt) | [**\<xref\>**](/rfcxml-vocabulary#xref) )*
### Attributes
#### anchor 
Document-wide unique identifier for this element.
### Schema
```
   dt =
     element dt {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute anchor { xsd:ID }?,
       attribute pn { xsd:ID }?,
       (text
        | bcp14
        | br
        | cref
        | em
        | eref
        | iref
        | relref
        | strong
        | sub
        | sup
        | tt
        | xref)*
     }
```

## em
## Tabs {.tabset}
### Usage
Indicates text that is semantically emphasized. In HTML and PDF rendering, text enclosed within this element will be displayed as italic after processing; in text rendering it will be preceded and followed by an underline character. This element can be combined with other character formatting elements, and the formatting will be additive.

Used in: [**\<annotation\>**](/rfcxml-vocabulary#annotation), [**\<blockquote\>**](/rfcxml-vocabulary#blockquote), [**\<cref\>**](/rfcxml-vocabulary#cref), [**\<dd\>**](/rfcxml-vocabulary#dd), [**\<dt\>**](/rfcxml-vocabulary#dt), [**\<li\>**](/rfcxml-vocabulary#li), [**\<name\>**](/rfcxml-vocabulary#name), [**\<refcontent\>**](/rfcxml-vocabulary#refcontent), [**\<strong\>**](/rfcxml-vocabulary#strong), [**\<sub\>**](/rfcxml-vocabulary#sub), [**\<sup\>**](/rfcxml-vocabulary#sup), [**\<t\>**](/rfcxml-vocabulary#t), [**\<td\>**](/rfcxml-vocabulary#td), [**\<th\>**](/rfcxml-vocabulary#th), [**\<tt\>**](/rfcxml-vocabulary#tt),[**\<xref\>**](/rfcxml-vocabulary#xref).
Allowed content: ( text | [bcp14](/rfcxml-vocabulary#bcp14) | [br](/rfcxml-vocabulary#br) | [cref](/rfcxml-vocabulary#cref) | [eref](/rfcxml-vocabulary#eref) | [iref](/rfcxml-vocabulary#iref) | [strong](/rfcxml-vocabulary#strong) | [sub](/rfcxml-vocabulary#sub) | [sup](/rfcxml-vocabulary#sup) | [tt](/rfcxml-vocabulary#tt) | [xref](/rfcxml-vocabulary#xref) )*
### Schema
```
   em =
     element em {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       (text
        | bcp14
        | br
        | cref
        | eref
        | iref
        | relref
        | strong
        | sub
        | sup
        | tt
        | xref)*
     }
```

## email
## Tabs {.tabset}
### Usage
Provides an email address.

The value is expected to be the addr-spec defined in Section 2 of RFC6068.

Multiple email addresses are permitted.

Used in: [**\<address\>**](/rfcxml-vocabulary#address).

Allowed content: text
### Attributes
#### ascii
The ASCII equivalent of the author's email address. This is only used if the email address has any internationalized components.
### Schema
```
   email =
     element email {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute ascii { text }?,
       text
     }
```

## eref
## Tabs {.tabset}
### Usage
Represents an external link as specified in the **target** attribute. This is useful for embedding URIs in the body of a document.

If the [**\<eref\>**](/rfcxml-vocabulary#eref) element has non-empty text content, the content is used as the displayed text that is linked. Otherwise, the value of the **target** attribute is used as the displayed text.

Used in: [**\<annotation\>**](/rfcxml-vocabulary#annotation), [**\<blockquote\>**](/rfcxml-vocabulary#blockquote), [**\<cref\>**](/rfcxml-vocabulary#cref), [**\<dd\>**](/rfcxml-vocabulary#dd), [**\<dt\>**](/rfcxml-vocabulary#dt), [**\<em\>**](/rfcxml-vocabulary#em), [**\<li\>**](/rfcxml-vocabulary#li), [**\<name\>**](/rfcxml-vocabulary#name), [**\<strong\>**](/rfcxml-vocabulary#strong), [**\<sub\>**](/rfcxml-vocabulary#sub), [**\<sup\>**](/rfcxml-vocabulary#sup), [**\<t\>**](/rfcxml-vocabulary#t), [**\<td\>**](/rfcxml-vocabulary#td), [**\<th\>**](/rfcxml-vocabulary#th), [**\<tt\>**](/rfcxml-vocabulary#tt), .
Allowed content: text

### Attributes
#### brackets

Determines the type of brackets that an [**\<eref\>**](/rfcxml-vocabulary#eref) will be rendered with. "angle" will render with angle brackets, and "none" will render with no brackets in HTML and PDF, and with parentheses by the text renderer.

Possible values: "none", "angle"
Default value: "none"

#### target

This attribute must be specified and must be the URI of the link target (RFC3986). This must begin with a scheme name (such as "https://") and thus not be relative to the URL of the current document.
### Schema
```
   eref =
     element eref {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       [ a:defaultValue = "none" ]
       attribute brackets { "none" | "angle" }?,
       attribute target { text },
       text
     }
```

## extaddr
## Tabs {.tabset}
### Usage
Extra address information. This element can be used for address parts more specific than a street, for instance apartment numbers, suite numbers, building parts, etc.

Used in: [**\<postal\>**](/rfcxml-vocabulary#postal).

Allowed content: text
### Attributes
#### ascii

The ASCII equivalent of the [**\<extaddr\>**](/rfcxml-vocabulary#extaddr) content. This element may have non-ASCII Latin script content without specifying an ASCII equivalent, but for other non-ASCII content an ASCII equivalent is required.
### Schema
```
   extaddr =
     element extaddr {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute ascii { text }?,
       text
     }
```

## figure
## Tabs {.tabset}
### Usage
Contains a figure with a caption with the figure number. If the element contains a [**\<name\>**](/rfcxml-vocabulary#name) element, the caption will also show that name.

Used in: [**\<aside\>**](/rfcxml-vocabulary#aside), [**\<blockquote\>**](/rfcxml-vocabulary#blockquote), [**\<dd\>**](/rfcxml-vocabulary#dd), [**\<li\>**](/rfcxml-vocabulary#li), [**\<section\>**](/rfcxml-vocabulary#section), [**\<td\>**](/rfcxml-vocabulary#td), and [**\<th\>**](/rfcxml-vocabulary#th).

Allowed content: [**\<name\>**](/rfcxml-vocabulary#name)?, [**\<iref\>**](/rfcxml-vocabulary#iref)\*, ( [**\<artset\>**](/rfcxml-vocabulary#artset) | [**\<artwork\>**](/rfcxml-vocabulary#artwork) | [**\<sourcecode\>**](/rfcxml-vocabulary#sourcecode) )+
### Attributes
#### align

Possible values: "left", "center", "right" 
Default value: "left"
#### alt
TBD

#### anchor
Document-wide unique identifier for this element.

#### height
TBD

#### src
TBD

#### suppress-title
Possible values: "true", "false"
Default value: "false"

#### title
Deprecated. Use the [**\<name\>**](/rfcxml-vocabulary#name) element instead.

#### width
TBD
### Schema
```
   figure =
     element figure {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute anchor { xsd:ID }?,
       attribute pn { xsd:ID }?,
       [ a:defaultValue = "" ] attribute title { text }?,
       [ a:defaultValue = "false" ]
       attribute suppress-title { "true" | "false" }?,
       attribute src { text }?,
       attribute originalSrc { text }?,
       [ a:defaultValue = "left" ]
       attribute align { "left" | "center" | "right" }?,
       [ a:defaultValue = "" ] attribute alt { text }?,
       [ a:defaultValue = "" ] attribute width { text }?,
       [ a:defaultValue = "" ] attribute height { text }?,
       name?,
       iref*,
       preamble?,
       (artset | artwork | sourcecode)+,
       postamble?
     }
```

## front
## Tabs {.tabset}
### Usage
Represents the Front part of the document including the Author Information, the Abstract, and additional notes.

A [**\<front\>**](/rfcxml-vocabulary#front) element may have more than one [**\<seriesInfo\>**](/rfcxml-vocabulary#seriesInfo) element. Each should contain a **name** attribute with the series name and a **value** attribute with the series number; other uses of [**\<front\>**](/rfcxml-vocabulary#front)[**\<seriesInfo\>**](/rfcxml-vocabulary#seriesInfo) described in RFC7991 are deprecated.

Used in: [**\<reference\>**](/rfcxml-vocabulary#reference) and [**\<rfc\>**](/rfcxml-vocabulary#rfc).
Allowed content: [**\<title\>**](/rfcxml-vocabulary#title), [**\<seriesInfo\>**](/rfcxml-vocabulary#seriesInfo)\*, [**\<author\>**](/rfcxml-vocabulary#author)+, [**\<date\>**](/rfcxml-vocabulary#date)?, [**\<area\>**](/rfcxml-vocabulary#area)\*, [**\<workgroup\>**](/rfcxml-vocabulary#workgroup)\*, [**\<keyword\>**](/rfcxml-vocabulary#keyword)\*, [**\<abstract\>**](/rfcxml-vocabulary#abstract)?, [**\<note\>**](/rfcxml-vocabulary#note)\*, [**\<boilerplate\>**](/rfcxml-vocabulary#boilerplate)?, [**\<toc\>**](/rfcxml-vocabulary#toc)?

### Schema
```
   front =
     element front {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       title,
       seriesInfo*,
       author+,
       date?,
       area*,
       workgroup*,
       keyword*,
       abstract?,
       note*,
       boilerplate?,
       toc?
     }
```

## iref
## Tabs {.tabset}
### Usage
Provides terms for the document's index.

Index entries can be either regular entries (when just the **item** attribute is given) or nested entries (by specifying **subitem** as well), grouped under a regular entry.

Index entries generally refer to the exact place where the [**\<iref\>**](/rfcxml-vocabulary#iref) element occurred. An exception is the occurrence as a child element of [**\<section\>**](/rfcxml-vocabulary#section), in which case the whole section is considered to be relevant for that index entry. In some formats, index entries of this type might be displayed as ranges.

When the prep tool is creating index content, it collects the items in a case-sensitive fashion for both the item and subitem level.

Used in: [**\<annotation\>**](/rfcxml-vocabulary#annotation), [**\<aside\>**](/rfcxml-vocabulary#aside), [**\<blockquote\>**](/rfcxml-vocabulary#blockquote), [**\<dd\>**](/rfcxml-vocabulary#dd), [**\<dt\>**](/rfcxml-vocabulary#dt), [**\<em\>**](/rfcxml-vocabulary#em), [**\<figure\>**](/rfcxml-vocabulary#figure), [**\<li\>**](/rfcxml-vocabulary#li), [**\<name\>**](/rfcxml-vocabulary#name), [**\<section\>**](/rfcxml-vocabulary#section), [**\<strong\>**](/rfcxml-vocabulary#strong), [**\<sub\>**](/rfcxml-vocabulary#sub), [**\<sup\>**](/rfcxml-vocabulary#sup), [**\<t\>**](/rfcxml-vocabulary#t), [**\<table\>**](/rfcxml-vocabulary#table), [**\<td\>**](/rfcxml-vocabulary#td), [**\<th\>**](/rfcxml-vocabulary#th), [**\<tt\>**](/rfcxml-vocabulary#tt), .
Allowed content: empty

### Attributes
#### item
This attribute must be specified and must be the item to include.

#### primary
Setting this to "true" declares the occurrence as primary, which might cause it to be highlighted in the index. There is no restriction on the number of occurrences that can be primary.

Possible values: "true", "false"
Default value: "false"

#### subitem
The subitem to include.
### Schema
```
   iref =
     element iref {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute item { text },
       [ a:defaultValue = "" ] attribute subitem { text }?,
       [ a:defaultValue = "false" ]
       attribute primary { "true" | "false" }?,
       attribute pn { xsd:ID }?,
       empty
```

## keyword
## Tabs {.tabset}
### Usage
Specifies a keyword applicable to the document.

Note that each element should only contain a single keyword; for multiple keywords, the element can simply be repeated.

Keywords are used both in the RFC Index and in the metadata of generated document representations. They are not reflected in the HTML, PDF, or text rendering of the document.

Used in: [**\<front\>**](/rfcxml-vocabulary#front).
Allowed content: text

### Schema
```
   keyword =
     element keyword {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       text
     }
```

## li
## Tabs {.tabset}
### Usage
A list item, used in [**\<ol\>**](/rfcxml-vocabulary#ol) and [**\<ul\>**](/rfcxml-vocabulary#ul).

Used in: [**\<ol\>**](/rfcxml-vocabulary#ol) and [**\<ul\>**](/rfcxml-vocabulary#ul).
Allowed content: ( ( [**\<artset\>**](/rfcxml-vocabulary#artset) | [**\<artwork\>**](/rfcxml-vocabulary#artwork) | [**\<blockquote\>**](/rfcxml-vocabulary#blockquote) | [**\<dl\>**](/rfcxml-vocabulary#dl) | [**\<figure\>**](/rfcxml-vocabulary#figure) | [**\<ol\>**](/rfcxml-vocabulary#ol) | [**\<sourcecode\>**](/rfcxml-vocabulary#sourcecode) | [**\<t\>**](/rfcxml-vocabulary#t) | [**\<table\>**](/rfcxml-vocabulary#table) | [**\<ul\>**](/rfcxml-vocabulary#ul) )+ | ( text | [**\<bcp14\>**](/rfcxml-vocabulary#bcp14) | [**\<br\>**](/rfcxml-vocabulary#br) | [**\<cref\>**](/rfcxml-vocabulary#cref) | [**\<em\>**](/rfcxml-vocabulary#em) | [**\<eref\>**](/rfcxml-vocabulary#eref) | [**\<iref\>**](/rfcxml-vocabulary#iref) | [**\<strong\>**](/rfcxml-vocabulary#strong) | [**\<sub\>**](/rfcxml-vocabulary#sub) | [**\<sup\>**](/rfcxml-vocabulary#sup) | [**\<tt\>**](/rfcxml-vocabulary#tt) | [**\<u\>**](/rfcxml-vocabulary#u) | [**\<xref\>**](/rfcxml-vocabulary#xref) )+ )

### Attributes
#### anchor
Document-wide unique identifier for this element.
### Schema
```
   li =
     element li {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute anchor { xsd:ID }?,
       attribute derivedCounter { text }?,
       attribute pn { xsd:ID }?,
       (( artset
          | artwork
          | blockquote
          | dl
          | figure
          | ol
          | sourcecode
          | t
          | table
          | ul)+
        | (text
           | bcp14
           | br
           | cref
           | em
           | eref
           | iref
           | relref
           | strong
           | sub
           | sup
           | tt
           | u
           | xref)+)
     }
```

## link
## Tabs {.tabset}
### Usage
A link to an external document that is related to the RFC.

The following are the supported types of external documents that can be pointed to in a [**\<link\>**](/rfcxml-vocabulary#link) element:

* The current International Standard Serial Number (ISSN) for the RFC Series. The value for the **rel** attribute is "item". The link should use the form "urn:issn:".
* The Digital Object Identifier (DOI) for this document. The value for the **rel** attribute is "describedBy". The link should use the form specified in RFC7669; this is expected to change in the future.
* The Internet-Draft that was submitted to the RFC Editor to become the published RFC. The value for the **rel** attribute is "prev". (RFC7998 specified "convertedFrom", but that value is not one of the recognised values for the identicaly named rel attribute of the identically named link element in HTML. The "prev" value has the desired semantics.) The link should be to an IETF-controlled web site that retains copies of Internet-Drafts.
* A representation of the document offered by the document author. The value for the **rel** attribute is "alternate". The link can be to a personally run web site.

In RFC production mode, the prep tool needs to check the values for [**\<link\>**](/rfcxml-vocabulary#link) before an RFC is published. In draft production mode, the prep tool might remove some [**\<link\>**](/rfcxml-vocabulary#link) elements during the draft submission process.

Used in: [**\<rfc\>**](/rfcxml-vocabulary#rfc).

### Attributes
#### href (Required)
The URI of the external document.

#### rel
The relationship of the external document to this one. The relationships are taken from the IANA-maintained [Link relations registry](https://www.iana.org/assignments/link-relations/link-relations.xhtml).
### Schema
```
   link =
     element link {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute href { text },
       attribute rel { text }?
     }
```

## middle
## Tabs {.tabset}
### Usage
Represents the main content of the document.

Used in: [**\<rfc\>**](/rfcxml-vocabulary#rfc).
Allowed content: [**\<section\>**](/rfcxml-vocabulary#section)+

### Schema
```
   middle =
     element middle {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       section+
     }
```

## name
## Tabs {.tabset}
### Usage
The name of the containing (parent) element, for instance the section name. This name can include inline markup (for example, including references or making some characters use a fixed-width font).

Used in: [**\<figure\>**](/rfcxml-vocabulary#figure), [**\<note\>**](/rfcxml-vocabulary#note), [**\<references\>**](/rfcxml-vocabulary#references), [**\<section\>**](/rfcxml-vocabulary#section), [**\<table\>**](/rfcxml-vocabulary#table), .
Allowed content: ( text | [**\<bcp14\>**](/rfcxml-vocabulary#bcp14) | [**\<br\>**](/rfcxml-vocabulary#br) | [**\<cref\>**](/rfcxml-vocabulary#cref) | [**\<em\>**](/rfcxml-vocabulary#em) | [**\<eref\>**](/rfcxml-vocabulary#eref) | [**\<iref\>**](/rfcxml-vocabulary#iref) | [**\<strong\>**](/rfcxml-vocabulary#strong) | [**\<sub\>**](/rfcxml-vocabulary#sub) | [**\<sup\>**](/rfcxml-vocabulary#sup) | [**\<tt\>**](/rfcxml-vocabulary#tt) | [**\<xref\>**](/rfcxml-vocabulary#xref) )\*

### Schema
```
   name =
     element name {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute slugifiedName { xsd:ID }?,
       (text
        | bcp14
        | br
        | cref
        | em
        | eref
        | iref
        | relref
        | strong
        | sub
        | sup
        | tt
        | xref)*
     }
```

## note
## Tabs {.tabset}
### Usage
Creates an unnumbered, titled block of text that appears after the Abstract.

It is usually used for additional information to reviewers (Working Group information, mailing list, ...) or for additional publication information such as "IESG Notes".

Used in: [**\<front\>**](/rfcxml-vocabulary#front).
Allowed content: [**\<name\>**](/rfcxml-vocabulary#name)?, ( [**\<dl\>**](/rfcxml-vocabulary#dl) | [**\<ol\>**](/rfcxml-vocabulary#ol) | [**\<t\>**](/rfcxml-vocabulary#t) | [**\<ul\>**](/rfcxml-vocabulary#ul) )+

### Attributes
#### removeInRFC
If **removeInRFC** is set to "true", this note is marked in the prep tool with text indicating that it should be removed before the document is published as an RFC. That text will be "This note is to be removed before publishing as an RFC."

Possible values: "true", "false"
Default value: "false"

#### title
Deprecated. Use the [**\<name\>**](/rfcxml-vocabulary#name) element instead.
### Schema
```
   note =
     element note {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute title { text }?,
       attribute pn { xsd:ID }?,
       [ a:defaultValue = "false" ]
       attribute removeInRFC { "true" | "false" }?,
       name?,
       (dl | ol | t | ul)+
     }
```

## ol
## Tabs {.tabset}
### Usage
An ordered list. The labels on the items will be either a number or a letter, depending on the value of the **style** attribute.

Used in: [**\<abstract\>**](/rfcxml-vocabulary#abstract), [**\<aside\>**](/rfcxml-vocabulary#aside), [**\<blockquote\>**](/rfcxml-vocabulary#blockquote), [**\<dd\>**](/rfcxml-vocabulary#dd), [**\<li\>**](/rfcxml-vocabulary#li), [**\<note\>**](/rfcxml-vocabulary#note), [**\<section\>**](/rfcxml-vocabulary#section), [**\<td\>**](/rfcxml-vocabulary#td), and [**\<th\>**](/rfcxml-vocabulary#th).
Allowed content: [**\<li\>**](/rfcxml-vocabulary#li)+

### Attributes
#### anchor
Document-wide unique identifier for this element.

#### group
When the prep tool sees an [**\<ol\>**](/rfcxml-vocabulary#ol) element with a **group** attribute that has already been seen, it continues the numbering of the list from where the previous list with the same group name left off. If an [**\<ol\>**](/rfcxml-vocabulary#ol) element has both a **group** attribute and a **start** attribute, the group's numbering is reset to the given start value.

#### indent
The indentation of the list elements relative to the start of the list item number. With **indent** set to "adaptive", the width of the widest list item number will determine the indentation. With a numeric value, that value will be used to determine the amount of indentation. The indentation amount is interpreted as characters when rendering plain-text documents, and en-space units when rendering in formats that have richer typographic support such as HTML or PDF. One en-space is assumed to be the length of 0.5 em-space in CSS units. Only non-negative integer amounts of indentation are supported.

Possible values: text, "adaptive"
Default value: "adaptive"

#### spacing
Defines whether or not there is a blank line between entries. Setting **spacing** to "normal" indicates a single blank line, while setting **spacing** to "compact" indicates no blank line between entries.

Possible values: "normal", "compact"
Default value: "normal"

#### start
The ordinal value at which to start the list. This defaults to "1" and must be an integer of value 0 or greater.

Default value: "1"

#### type
Required.

The type of the labels on list items. If the length of the **type** value is 1, the meaning is the same as it is for HTML:
* "a" - Lowercase letters (a, b, c, ...)
* "A" - Uppercase letters (A, B, C, ...)
* "1" - Decimal numbers (1, 2, 3, ...)
* "i" - Lowercase Roman numerals (i, ii, iii, ...)
* "I" - Uppercase Roman numerals (I, II, III, ...)

Default value: "1"

For **type**s "a" and "A", after the 26th entry, the numbering starts at "aa"/"AA", then "ab"/"AB", and so on.

If the length of the **type** value is greater than 1, the value must contain a percent-encoded indicator and other text. The value is a free-form text that allows counter values to be inserted using a "percent-letter" format. For instance, "\[REQ%d\]" generates labels of the form "\[REQ1\]", where "%d" inserts the item number as a decimal number.

The following formats are supported:

* "%c" - Lowercase letters (a, b, c, ...)
* "%C" - Uppercase letters (A, B, C, ...)
* "%d" - Decimal numbers (1, 2, 3, ...)
* "%i" - Lowercase Roman numerals (i, ii, iii, ...)
* "%I" - Uppercase Roman numerals (I, II, III, ...)
* "%p" - The list counter of a list item in a parent list (see more below)
* "%%" - Represents a percent sign

Other formats are reserved for future use. Only one percent encoding other than "%%" and "%p" is allowed in a **type** value.

It is an error for the **type** attribute to be empty. For bulleted lists, use the [**\<ul\>**](/rfcxml-vocabulary#ul) element. For lists that have neither bullets nor numbers, use the [**\<ul\>**](/rfcxml-vocabulary#ul) element with **empty** set to "true".

'%p' may be used in nested ordered lists, where it represents the item number of the parent list item. This lets you say for instance:
```xml
<ol>
  <li>List item one</li>
  <li>
    <t>Nested list:</t>
    <ol type='%p%d'>
      <li>Sublist item 2.1</li>
      <li>Sublist item 2.2</li>
    </ol>
  </li>
</ol>
```
which is rendered as:

```
  1. List item one
  2. Nested list
     2.1 Sublist item 2.1
     2.2 Sublist item 2.2
```
Without the '%p' format specifier, you would have to explicitly insert the counter number of the parent item, which could easily result in mismatched numbering if parent list intems were inserted or removed during document editing.
### Schema
```
   ol =
     element ol {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute anchor { xsd:ID }?,
       [ a:defaultValue = "1" ] attribute type { text }?,
       [ a:defaultValue = "1" ] attribute start { text }?,
       attribute group { text }?,
       [ a:defaultValue = "normal" ]
       attribute spacing { "normal" | "compact" }?,
       [ a:defaultValue = "adaptive" ]
       attribute indent { text | "adaptive" }?,
       attribute pn { xsd:ID }?,
       li+
     }
```

## organization
## Tabs {.tabset}
### Usage
Specifies the affiliation (RFC7322) of an author.

This information appears both in the Author's Address section and on the front page (see RFC7322 for more information). If the value is long, an abbreviated variant can be specified in the **abbrev** attribute.

Used in: [**\<author\>**](/rfcxml-vocabulary#author), [**\<contact\>**](/rfcxml-vocabulary#contact)
Allowed content: text

### Attributes
#### abbrev
Abbreviated variant of the organization name.

#### ascii
The ASCII equivalent of the [**\<organization\>**](/rfcxml-vocabulary#organization) content. This element may have non-ASCII Latin script content without specifying an ASCII equivalent, but for other non-ASCII content an ASCII equivalent is required.

#### asciiAbbrev
The ASCII equivalent of the abbreviated variant of the organization's name.

#### showOnFrontPage
Turns off listing of organization with author name on the first document page.

Possible values: "true", "false"
Default value: "true"
### Schema
```
   organization =
     element organization {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute abbrev { text }?,
       attribute ascii { text }?,
       attribute asciiAbbrev { text }?,
       [ a:defaultValue = "true" ]
       attribute showOnFrontPage { "true" | "false" }?,
       text
     }
```

## phone
## Tabs {.tabset}
### Usage
Represents a phone number.

The value is expected to be the scheme-specific part of a "tel" URI (and so does not include the prefix "tel:"), using the "global-number-digits" syntax. See Section 3 of RFC3966 for details.

Used in: [**\<address\>**](/rfcxml-vocabulary#address).
Allowed content: text

### Schema
```
   phone =
     element phone {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       text
     }
```

## pobox
## Tabs {.tabset}
### Usage
Represents a post office box number.

Used in: [**\<postal\>**](/rfcxml-vocabulary#postal).
Allowed content: text

### Attributes
#### ascii

The ASCII equivalent of the [**\<pobox\>**](/rfcxml-vocabulary#pobox) content. This element may have non-ASCII Latin script content without specifying an ASCII equivalent, but for other non-ASCII content an ASCII equivalent is required.
### Schema
```
   pobox =
     element pobox {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute ascii { text }?,
       text
     }
```

## postal
## Tabs {.tabset}
### Usage
Contains optional child elements providing postal information. These elements will be displayed in an order that is specific to formatters. A postal address can contain only a set of [**\<street\>**](/rfcxml-vocabulary#street), [**\<city\>**](/rfcxml-vocabulary#city), [**\<region\>**](/rfcxml-vocabulary#region), [**\<code\>**](/rfcxml-vocabulary#code), and [**\<country\>**](/rfcxml-vocabulary#country) elements, or only an ordered set of [**\<postalLine\>**](/rfcxml-vocabulary#postalLine) elements, but not both.

Used in: [**\<address\>**](/rfcxml-vocabulary#address).
Allowed content: ( ( [**\<city\>**](/rfcxml-vocabulary#city) | [**\<cityarea\>**](/rfcxml-vocabulary#cityarea) | [**\<code\>**](/rfcxml-vocabulary#code) | [**\<country\>**](/rfcxml-vocabulary#country) | [**\<extaddr\>**](/rfcxml-vocabulary#extaddr) | [**\<pobox\>**](/rfcxml-vocabulary#pobox) | [**\<region\>**](/rfcxml-vocabulary#region) | [**\<sortingcode\>**](/rfcxml-vocabulary#sortingcode) | [**\<street\>**](/rfcxml-vocabulary#street) )* | [**\<postalLine\>**](/rfcxml-vocabulary#postalLine)+ )

### Schema
```
   postal =
     element postal {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       (( city | cityarea | code | country | extaddr | pobox | region
          | sortingcode | street)* 
        | postalLine+)
     }
```


## postalLine
## Tabs {.tabset}
### Usage
Represents one line of a postal address. When more than one [**\<postalLine\>**](/rfcxml-vocabulary#postalLine) is provided, they are rendered in the order given.

Used in: [**\<postal\>**](/rfcxml-vocabulary#postal).
Allowed content: text

### Attributes
#### ascii
The ASCII equivalent of the [**\<postalLine\>**](/rfcxml-vocabulary#postalLine) content. This element may have non-ASCII Latin script content without specifying an ASCII equivalent, but for other non-ASCII content an ASCII equivalent is required.
### Schema
```
   postalLine =
     element postalLine {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute ascii { text }?,
       text
     }
```

## refcontent
## Tabs {.tabset}
### Usage
Text that should appear between the title and the date of a [**\<reference\>**](/rfcxml-vocabulary#reference). [**\<refcontent\>**](/rfcxml-vocabulary#refcontent) should be used in preference to incorrectly using [**\<seriesInfo\>**](/rfcxml-vocabulary#seriesInfo) where the publication is not part of a recognised series.


Used in: [**\<reference\>**](/rfcxml-vocabulary#reference).
Allowed content: ( text | [**\<bcp14\>**](/rfcxml-vocabulary#bcp14) | [**\<em\>**](/rfcxml-vocabulary#em) | [**\<strong\>**](/rfcxml-vocabulary#strong) | [**\<sub\>**](/rfcxml-vocabulary#sub) | [**\<sup\>**](/rfcxml-vocabulary#sup) | [**\<tt\>**](/rfcxml-vocabulary#tt) )*

### Examples
The following [**\<reference\>**](/rfcxml-vocabulary#reference) uses [**\<refcontent\>**](/rfcxml-vocabulary#refcontent):
```xml
<reference anchor="April1"> 
  <front> 
    <title>On Being A Fool</title> 
    <author initials="K." surname="Phunny" fullname="Knot Phunny"/> 
    <date year="2000" month="April"/> 
  </front> 
  <refcontent>Self-published pamphlet</refcontent> 
</reference>
```
and renders as:
```
    [April1] Phunny, K., "On Being A Fool", Self-published pamphlet, April 2000.
```

### Schema
```
   refcontent =
     element refcontent {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       (text | bcp14 | em | strong | sub | sup | tt)*
     }
```

## reference
## Tabs {.tabset}
### Usage
Represents a bibliographic reference. [**\<reference\>**](/rfcxml-vocabulary#reference) should only be used for references where a BibXML file does not exist.  

See [References in RFCXML](/references-in-rfcxml) for more information.

Used in: [**\<referencegroup\>**](/rfcxml-vocabulary#referencegroup) and [**\<references\>**](/rfcxml-vocabulary#references).
Allowed content: [**\<stream\>**](/rfcxml-vocabulary#stream)?, [**\<front\>**](/rfcxml-vocabulary#front), ( [**\<annotation\>**](/rfcxml-vocabulary#annotation) | [**\<refcontent\>**](/rfcxml-vocabulary#refcontent) | [**\<seriesInfo\>**](/rfcxml-vocabulary#seriesInfo) )*

### Attributes
#### anchor (Required)
Document-wide unique identifier for this element. Usually, this will be used both to label the reference in the References section and as an identifier in links to this reference entry; but see [**\<displayreference\>**](/rfcxml-vocabulary#displayreference) for how to change this.

#### quote-title
Specifies whether or not the title in the reference should be quoted. This can be used to prevent quoting, such as on errata.

Possible values: "true", "false"

#### target
Holds the URI for the reference.
### Schema
```
   reference =
     element reference {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute anchor { xsd:ID },
       attribute derivedAnchor { text }?,
       attribute target { text }?,
       [ a:defaultValue = "true" ]
       attribute quoteTitle { "true" | "false" }?,
       attribute quote-title { "true" | "false" }?,
       stream?,
       front,
       (annotation | format | refcontent | seriesInfo)*
     }
```

## referencegroup
## Tabs {.tabset}
### Usage
Represents a list of bibliographic references that will be represented as a single reference. This is most often used to reference STDs and BCPs, where a single reference (such as "BCP 9") may encompass more than one RFC.  

See [References in RFCXML](/references-in-rfcxml) for more information.

Used in: [**\<references\>**](/rfcxml-vocabulary#references).
Allowed content: [**\<reference\>**](/rfcxml-vocabulary#reference)+

### Attributes
#### anchor (Required)
Document-wide unique identifier for this element. Usually, this will be used both to label the reference group in the References section and as an identifier in links to this reference entry; but see [**\<displayreference\>**](/rfcxml-vocabulary#displayreference) for how to change this.

#### target
Holds an URI for the reference group, analogous to the **target** attribute of [**\<reference\>**](/rfcxml-vocabulary#reference). Useful for a STD which consists of multiple RFCs with their own URLs, but also has its own unique URL.
### Schema
```
   referencegroup =
     element referencegroup {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute anchor { xsd:ID },
       attribute derivedAnchor { text }?,
       attribute target { text }?,
       reference+
     }
```

## references
## Tabs {.tabset}
### Usage
Contains a set of bibliographic references.  In general, the [**\<name\>**](/rfcxml-vocabulary#name) child element should be either "Normative References" or "Informative References".

See [References in RFCXML](/references-in-rfcxml) for more information.

Used in: [**\<back\>**](/rfcxml-vocabulary#back) and [**\<references\>**](/rfcxml-vocabulary#references).
Allowed content: [**\<name\>**](/rfcxml-vocabulary#name)?, ( [**\<references\>**](/rfcxml-vocabulary#references)+ | ( [**\<reference\>**](/rfcxml-vocabulary#reference) | [**\<referencegroup\>**](/rfcxml-vocabulary#referencegroup) )* )

### Attributes
#### anchor
An optional user-supplied identifier for this set of references.

#### title
Deprecated. Use the [**\<name\>**](/rfcxml-vocabulary#name) element instead.
### Schema
```
   references =
     element references {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute pn { xsd:ID }?,
       attribute anchor { xsd:ID }?,
       attribute title { text }?,
       name?,
       (references+ | (reference | referencegroup)*)
     }
```

## region
## Tabs {.tabset}
### Usage
Provides the region name in a postal address.

Used in: [**\<postal\>**](/rfcxml-vocabulary#postal).
Allowed content: text

### Attributes
#### ascii
The ASCII equivalent of the [**\<region\>**](/rfcxml-vocabulary#region) content. This element may have non-ASCII Latin script content without specifying an ASCII equivalent, but for other non-ASCII content an ASCII equivalent is required.
### Schema
```
   region =
     element region {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute ascii { text }?,
       text
     }
```

## rfc
## Tabs {.tabset}
### Usage
This is the root element of RFCXML.

Allowed content: [**\<link\>**](/rfcxml-vocabulary#link)\*, [**\<front\>**](/rfcxml-vocabulary#front), [**\<middle\>**](/rfcxml-vocabulary#middle), [**\<back\>**](/rfcxml-vocabulary#back)?

### Attributes
#### category
Document category

For RFCs, the **category** attribute determines the maturity level (see Section 4 of RFC2026). The allowed values are "std" for "Standards Track", "bcp" for "BCP", "info" for "Informational", "exp" for "Experimental", and "historic" for "Historic".

For Internet-Drafts, the **category** attribute is not needed; when supplied, it will appear as "Intended Status". Supplying this information can be useful to reviewers.

Possible values: "std", "bcp", "exp", "info", "historic"

#### consensus
Affects the generated boilerplate. Note that the values of "no" and "yes" are deprecated and are replaced by "false" and "true".

See RFC7841 for more information.

Possible values: "false" | "true"
Default value: "false"

#### docName
Indicates the draft name (including revision number) for a draft, or the draft from which an RFC derived, for an RFC. Used to insert the `<link rel="prev" href="...">` element that points to the precursor of the RFC, in accordance with the intentions of Section 5.6.3 of RFC7998.

#### indexInclude
Specifies whether or not a formatter is requested to include an index in generated files. If the source file has no [**\<iref\>**](/rfcxml-vocabulary#iref) elements, an index is never generated. This option is useful for generating documents where the source document has [**\<iref\>**](/rfcxml-vocabulary#iref) elements but the author no longer wants an index.

Possible values: "true", "false"
Default value: "true"

#### ipr
Represents the Intellectual Property status of the document.

The possible values are specified in Appendix A.1 of RFC 7991 and explained in [Copyright Notice](/required-content#copyright-notice). 

If the attribute is set to the empty string, it is assumed that this is not a regular IETF/IRTF/IAB/ISE document, and the document header content is reduced. This is considered a feature by a few other standards organisations that use IETF tools to format their standards documents.

#### iprExtract
Identifies a single section within the document for which extraction "as is" is explicitly allowed (only relevant for historic values of **ipr**).

#### number
Used to determine whether to produce an RFC or an Internet-Draft.

#### obsoletes
A comma-separated list of RFC numbers or Internet-Draft names.

The prep tool will parse the attribute value so that incorrect references can be detected.

#### prepTime
The date that the XML was processed by a prep tool. This is included in the XML file just before it is saved to disk. The value is formatted using the "date-time" format defined in Section 5.6 of RFC3339. The "time-offset" should be "Z".

#### seriesNo
Deprecated; instead, use the **value** attribute in [**\<seriesInfo\>**](/rfcxml-vocabulary#seriesInfo).

#### sortRefs
Specifies whether or not the prep tool will sort the references in each reference section.

Possible values: "true", "false"
Default value: "false"

#### submissionType
The document stream, as described in RFC7841.

Possible values: "IETF", "IAB", "IRTF", "independent"
Default value: "IETF"

#### symRefs
Specifies whether or not a formatter is requested to use symbolic references (such as "RFC2119"). If the value for this is "false", the references come out as numbers (such as `[3]`).

Possible values: "true", "false"
Default value: "true"

#### tocDepth
Specifies the number of levels of headings that a formatter is requested to include in the table of contents.

Default value: "3"

#### tocInclude
Specifies whether or not a formatter is requested to include a table of contents in generated files.

Possible values: "true", "false"
Default value: "true"

#### updates
A comma-separated list of RFC numbers or Internet-Draft names.

The prep tool will parse the attribute value so that incorrect references can be detected.

#### version
Specifies the version of RFCXML syntax used in this document. The only expected value is "3".
### Schema
```
   rfc =
     element rfc {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute number { text }?,
       [ a:defaultValue = "" ] attribute obsoletes { text }?,
       [ a:defaultValue = "" ] attribute updates { text }?,
       attribute category { 
         "std" | "bcp" | "exp" | "info" | "historic" 
       }?,
       attribute mode { text }?,
       [ a:defaultValue = "false" ]
       attribute consensus { "no" | "yes" | "false" | "true" }?,
       attribute seriesNo { text }?,
       attribute ipr { text }?,
       attribute iprExtract { xsd:IDREF }?,
       [ a:defaultValue = "IETF" ]
       attribute submissionType {
         "IETF" | "IAB" | "IRTF" | "independent"
       }?,
       attribute docName { text }?,
       [ a:defaultValue = "false" ]
       attribute sortRefs { "true" | "false" }?,
       [ a:defaultValue = "true" ]
       attribute symRefs { "true" | "false" }?,
       [ a:defaultValue = "true" ]
       attribute tocInclude { "true" | "false" }?,
       [ a:defaultValue = "3" ] attribute tocDepth { text }?,
       attribute prepTime { text }?,
       [ a:defaultValue = "true" ]
       attribute indexInclude { "true" | "false" }?,
       attribute version { text }?,
       [ a:defaultValue = "Common,Latin" ] attribute scripts { text }?,
       attribute expiresDate { text }?,
       link*,
       front,
       middle,
       back?
     }
```

## section
## Tabs {.tabset}
### Usage
Represents a section (when inside a [**\<middle\>**](/rfcxml-vocabulary#middle) element) or an appendix (when inside a [**\<back\>**](/rfcxml-vocabulary#back) element).

Subsections are created by nesting [**\<section\>**](/rfcxml-vocabulary#section) elements inside [**\<section\>**](/rfcxml-vocabulary#section) elements. Sections are allowed to be empty.

Used in: [**\<back\>**](/rfcxml-vocabulary#back), [**\<boilerplate\>**](/rfcxml-vocabulary#boilerplate), [**\<middle\>**](/rfcxml-vocabulary#middle), [**\<section\>**](/rfcxml-vocabulary#section), and [**\<toc\>**](/rfcxml-vocabulary#toc).
Allowed content: [**\<name\>**](/rfcxml-vocabulary#name)?, ( [**\<artset\>**](/rfcxml-vocabulary#artset) | [**\<artwork\>**](/rfcxml-vocabulary#artwork) | [**\<aside\>**](/rfcxml-vocabulary#aside) | [**\<author\>**](/rfcxml-vocabulary#author) | [**\<blockquote\>**](/rfcxml-vocabulary#blockquote) | [**\<contact\>**](/rfcxml-vocabulary#contact) | [**\<dl\>**](/rfcxml-vocabulary#dl) | [**\<figure\>**](/rfcxml-vocabulary#figure) | [**\<iref\>**](/rfcxml-vocabulary#iref) | [**\<ol\>**](/rfcxml-vocabulary#ol) | [**\<sourcecode\>**](/rfcxml-vocabulary#sourcecode) | [**\<t\>**](/rfcxml-vocabulary#t) | [**\<table\>**](/rfcxml-vocabulary#table) | [**\<ul\>**](/rfcxml-vocabulary#ul) )*, section\*

### Attributes
#### anchor
Document-wide unique identifier for this [**\<section\>**](/rfcxml-vocabulary#section) element.

#### numbered
If set to "false", the formatter is requested to not display a section number. The prep tool will verify that such a section is not followed by a numbered section in this part of the document. Descendant sections of unnumbered sections are unnumbered by definition. Both top-level [**\<section\>**](/rfcxml-vocabulary#section)s and other [**\<section\>**](/rfcxml-vocabulary#section)s may have **numbered** set to "false".

Possible values: "true", "false"
Default value: "true"

#### removeInRFC
If set to "true", this section is marked in the prep tool with text indicating that it should be removed before the document is published as an RFC. That text will be "This section is to be removed before publishing as an RFC."

Possible values: "true", "false"
Default value: "false"

#### title
Deprecated. Use the [**\<name\>**](/rfcxml-vocabulary#name) element instead.

#### toc
Indicates to a formatter whether or not the section is to be included in a table of contents, if such a table of contents is produced. This only takes effect if the level of the section would have appeared in the table of contents based on the **tocDepth** attribute of the [**\<rfc\>**](/rfcxml-vocabulary#rfc) element, and of course only if the table of contents is being created based on the **tocInclude** attribute of the [**\<rfc\>**](/rfcxml-vocabulary#rfc) element. If this is set to "exclude", any section below this one will be excluded as well. The "default" value indicates inclusion of the section if it would be included by the **tocDepth** attribute of the [**\<rfc\>**](/rfcxml-vocabulary#rfc) element.

Possible values: "include", "exclude", "default"
Default value: "default"
### Schema
```
   section =
     element section {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute anchor { xsd:ID }?,
       attribute pn { xsd:ID }?,
       attribute title { text }?,
       [ a:defaultValue = "true" ]
       attribute numbered { "true" | "false" }?,
       [ a:defaultValue = "default" ]
       attribute toc { "include" | "exclude" | "default" }?,
       [ a:defaultValue = "false" ]
       attribute removeInRFC { "true" | "false" }?,
       name?,
       (artset
        | artwork
        | aside
        | author
        | blockquote
        | contact
        | dl
        | figure
        | iref
        | ol
        | sourcecode
        | t
        | table
        | texttable
        | ul)*,
       section*
     }
```

## seriesInfo
## Tabs {.tabset}
### Usage
Specifies the document series in which this document appears, and also specifies an identifier within that series.

A processing tool determines whether it is working on an RFC or an Internet-Draft by inspecting the **name** attribute of a [**\<seriesInfo\>**](/rfcxml-vocabulary#seriesInfo) element inside the [**\<front\>**](/rfcxml-vocabulary#front) element inside the [**\<rfc\>**](/rfcxml-vocabulary#rfc) element, looking for "RFC" or "Internet-Draft". (Specifying neither value in any of the [**\<seriesInfo\>**](/rfcxml-vocabulary#seriesInfo) elements can be useful for producing other types of documents but is out of scope for this specification.)

It is invalid to have multiple [**\<seriesInfo\>**](/rfcxml-vocabulary#seriesInfo) elements inside the same [**\<front\>**](/rfcxml-vocabulary#front) element containing the same **name** value. Some combinations of [**\<seriesInfo\>**](/rfcxml-vocabulary#seriesInfo) **name** attribute values make no sense, such as having both `<seriesInfo name="rfc"/>` and `<seriesInfo name="Internet-Draft"/>` in the same [**\<front\>**](/rfcxml-vocabulary#front) element.

Used in: [**\<front\>**](/rfcxml-vocabulary#front) and [**\<reference\>**](/rfcxml-vocabulary#reference).
Allowed content: empty

### Attributes
#### asciiName
The ASCII equivalent of the **name** attribute.

#### asciiValue
The ASCII equivalent of the **value** attribute.

#### name
Required.

The name of the series. Some values in use by the IETF community are "RFC", "Internet-Draft", and "DOI", but other names such as "ISO", "W3C" for exist for other standardisation organisations.

#### status
TBD

#### stream
Deprecated. Use the [**\<stream\>**](/rfcxml-vocabulary#stream) element instead.

Possible values: "IETF", "IAB", "IRTF", "independent"

#### value
Required.

The identifier within the series specified by the **name** attribute. 

* For BCPs, FYIs, RFCs, and STDs, this is the number within the series.
* For Internet-Drafts, it is the full draft name (ending with the two-digit version number).
* For DOIs, the value is given, such as "10.17487/rfc1149", as described in RFC7669.

The name in the value should be the document name without any file extension.
### Schema
```
   seriesInfo =
     element seriesInfo {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute name { text },
       attribute value { text },
       attribute asciiName { text }?,
       attribute asciiValue { text }?,
       attribute status { text }?,
       attribute stream { "IETF" | "IAB" | "IRTF" | "independent" }?,
       empty
     }
```

## sortingcode
## Tabs {.tabset}
### Usage
A sorting code is related to postal codes in that it is used in addresses to allow sorting, for example to route mail to a certain postal centre or to distinguish streets with the same name in two different areas of the same settlement.

Used in: [**\<postal\>**](/rfcxml-vocabulary#postal).
Allowed content: text

### Attributes
#### ascii

The ASCII equivalent of the [**\<sortingcode\>**](/rfcxml-vocabulary#sortingcode) content. This element may have non-ASCII Latin script content without specifying an ASCII equivalent, but for other non-ASCII content an ASCII equivalent is required.
### Schema
```
   sortingcode =
     element sortingcode {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute ascii { text }?,
       text
     }
```

## sourcecode
## Tabs {.tabset}
### Usage
This element allows the inclusion of source code into the document.

When rendered, source code is always shown in a monospace font. When [**\<sourcecode\>**](/rfcxml-vocabulary#sourcecode) is a child of [**\<figure\>**](/rfcxml-vocabulary#figure) or [**\<section\>**](/rfcxml-vocabulary#section), it provides full control of horizontal whitespace and line breaks. When formatted, it is indented relative to the left margin of the enclosing element. It is thus useful for source code and formal languages, such as ABNF (RFC5234) or the RNC notation used in this document. (When [**\<sourcecode\>**](/rfcxml-vocabulary#sourcecode) is a child of other elements, it flows with the text that surrounds it.) Tab characters (U+0009) inside of this element are prohibited.

The use of `<![CDATA[ ... ]]>` wrappers is recommended to avoid unxpected processing or issues with angle brackets. 

For artwork such as character-based art, diagrams of message layouts, and so on, use the [**\<artwork\>**](/rfcxml-vocabulary#artwork) element instead.

Output formatters that do pagination will attempt to keep source code on a single page. This is to prevent source code that is split across pages from looking like two separate pieces of code.

Used in: [**\<blockquote\>**](/rfcxml-vocabulary#blockquote), [**\<dd\>**](/rfcxml-vocabulary#dd), [**\<figure\>**](/rfcxml-vocabulary#figure), [**\<li\>**](/rfcxml-vocabulary#li), [**\<section\>**](/rfcxml-vocabulary#section), [**\<td\>**](/rfcxml-vocabulary#td), and [**\<th\>**](/rfcxml-vocabulary#th).
Allowed content: text

### Attributes
#### anchor
Document-wide unique identifier for this element.

#### markers
Indicates whether `<CODE BEGINS>` and `<CODE ENDS>` markers, as introduced by RFC6087, should be generated when rendering the [**\<sourcecode\>**](/rfcxml-vocabulary#sourcecode) element. The alternative is to include these explicitly inside the element, but that would necessitate extra code to strip these, when extracting code from the XML source.

Possible values: "true", "false"
Default value: "false"

#### name
A filename suitable for the contents (such as for extraction to a local file). This attribute can be helpful for other kinds of tools (such as automated syntax checkers, which work by extracting the source code). Note that the **name** attribute does not need to be unique for [**\<artwork\>**](/rfcxml-vocabulary#artwork) elements in a document. If multiple [**\<sourcecode\>**](/rfcxml-vocabulary#sourcecode) elements have the same **name** attribute, a formatter might assume that the elements are all fragments of a single file, and such a formatter can collect those fragments for later processing.

#### src
The URI reference of a source file (RFC3986).

It is an error to have both a **src** attribute and content in the [**\<sourcecode\>**](/rfcxml-vocabulary#sourcecode) element.

#### type
Specifies the type of the source code. The value of this attribute is free text with certain values designated as preferred.

Most of the preferred values for [**\<sourcecode\>**](/rfcxml-vocabulary#sourcecode) types are language names, in a wide sense, such as "abnf", "asn.1", "bash", "c++", etc.

A list of the preferred values is maintained on the RFC Editor web site at [https://www.rfc-editor.org/materials/sourcecode-types.txt](https://www.rfc-editor.org/materials/sourcecode-types.txt), and that list is updated over time. Thus, a consumer of RFCXML should not cause a failure when it encounters an unexpected type or no type is specified.
### Examples
The following is a basic example of a c program as set by the **type** attribute, using a CDATA block because the source code contains angle brackets, and a **name** attribute that suggests a file name for the extracted code:
```xml
<sourcecode name="helloworld.c" type="c" markers="true">
  <![CDATA[
  #include <stdio.h>
        
  int main() {
    printf("Hello World");
    return 0;
  }
  ]]>
</sourcecode>
```

Another example can be found at [https://www.rfc-editor.org/rfc/rfc8689.html#section-2-2.8.1](https://www.rfc-editor.org/rfc/rfc8689.html#section-2-2.8.1) where the  [**\<sourcecode\>**](/rfcxml-vocabulary#sourcecode) element is within an [**\<li\>**](/rfcxml-vocabulary#li) and therefore indented to start at the same level of ident.

### Schema
```
   sourcecode =
     element sourcecode {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute anchor { xsd:ID }?,
       attribute pn { xsd:ID }?,
       [ a:defaultValue = "" ] attribute name { text }?,
       [ a:defaultValue = "" ] attribute type { text }?,
       [ a:defaultValue = "false" ] 
       attribute markers { "true" | "false" }?,
       attribute src { text }?,
       attribute originalSrc { text }?,
       text
     }
```

## stream
## Tabs {.tabset}
### Usage
Indicates which stream an RFC belongs to.

Used in: [**\<reference\>**](/rfcxml-vocabulary#reference).
Allowed content: ( "IETF" | "IAB" | "IRTF" | "independent" )?

### Schema
```
   stream = 
     element stream {
       ( "IETF" | "IAB" | "IRTF" | "independent" )?
   }
```

## street
## Tabs {.tabset}
### Usage
Provides a street address.

Used in: [**\<postal\>**](/rfcxml-vocabulary#postal).
Allowed content: text

### Attributes
#### ascii
The ASCII equivalent of the [**\<street\>**](/rfcxml-vocabulary#street) content. This element may have non-ASCII Latin script content without specifying an ASCII equivalent, but for other non-ASCII content an ASCII equivalent is required.
### Schema
```
   street =
     element street {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute ascii { text }?,
       text
     }
```

## strong
## Tabs {.tabset}
### Usage
Indicates text that is semantically strong. In HTML and PDF rendering, text enclosed within this element will be displayed as bold after processing; in text rendering it will be preceeded and followed by an asterisk. This element can be combined with other character formatting elements, and the formatting will be additive.

Used in: [**\<annotation\>**](/rfcxml-vocabulary#annotation), [**\<blockquote\>**](/rfcxml-vocabulary#blockquote), [**\<cref\>**](/rfcxml-vocabulary#cref), [**\<dd\>**](/rfcxml-vocabulary#dd), [**\<dt\>**](/rfcxml-vocabulary#dt), [**\<em\>**](/rfcxml-vocabulary#em), [**\<li\>**](/rfcxml-vocabulary#li), [**\<name\>**](/rfcxml-vocabulary#name), [**\<refcontent\>**](/rfcxml-vocabulary#refcontent), [**\<sub\>**](/rfcxml-vocabulary#sub), [**\<sup\>**](/rfcxml-vocabulary#sup), [**\<t\>**](/rfcxml-vocabulary#t), [**\<td\>**](/rfcxml-vocabulary#td), [**\<th\>**](/rfcxml-vocabulary#th), [**\<tt\>**](/rfcxml-vocabulary#tt), and [**\<xref\>**](/rfcxml-vocabulary#xref).
Allowed content: ( text | [**\<bcp14\>**](/rfcxml-vocabulary#bcp14) | [**\<br\>**](/rfcxml-vocabulary#br) | [**\<cref\>**](/rfcxml-vocabulary#cref) | [**\<em\>**](/rfcxml-vocabulary#em) | [**\<eref\>**](/rfcxml-vocabulary#eref) | [**\<iref\>**](/rfcxml-vocabulary#iref) | [**\<sub\>**](/rfcxml-vocabulary#sub) | [**\<sup\>**](/rfcxml-vocabulary#sup) | [**\<tt\>**](/rfcxml-vocabulary#tt) | [**\<xref\>**](/rfcxml-vocabulary#xref) )*

### Schema
```
   strong =
     element strong {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       (text
        | bcp14
        | br
        | cref
        | em
        | eref
        | iref
        | relref
        | sub
        | sup
        | tt
        | xref)*
     }
```

## sub
## Tabs {.tabset}
### Usage
Causes the text to be displayed as subscript, approximately half a letter-height lower than normal text, in HTML and PDF rendering. This element can be combined with other character formatting elements, and the formatting will be additive.

Used in: [**\<annotation\>**](/rfcxml-vocabulary#annotation), [**\<blockquote\>**](/rfcxml-vocabulary#blockquote), [**\<cref\>**](/rfcxml-vocabulary#cref), [**\<dd\>**](/rfcxml-vocabulary#dd), [**\<dt\>**](/rfcxml-vocabulary#dt), [**\<em\>**](/rfcxml-vocabulary#em), [**\<li\>**](/rfcxml-vocabulary#li), [**\<name\>**](/rfcxml-vocabulary#name), [**\<refcontent\>**](/rfcxml-vocabulary#refcontent), [**\<strong\>**](/rfcxml-vocabulary#strong), [**\<sub\>**](/rfcxml-vocabulary#sub), [**\<sup\>**](/rfcxml-vocabulary#sup), [**\<t\>**](/rfcxml-vocabulary#t), [**\<td\>**](/rfcxml-vocabulary#td), [**\<th\>**](/rfcxml-vocabulary#th), [**\<tt\>**](/rfcxml-vocabulary#tt), and [**\<xref\>**](/rfcxml-vocabulary#xref).
Allowed content: ( text | [**\<bcp14\>**](/rfcxml-vocabulary#bcp14) | [**\<cref\>**](/rfcxml-vocabulary#cref) | [**\<em\>**](/rfcxml-vocabulary#em) | [**\<eref\>**](/rfcxml-vocabulary#eref) | [**\<iref\>**](/rfcxml-vocabulary#iref) | [**\<strong\>**](/rfcxml-vocabulary#strong) | [**\<sub\>**](/rfcxml-vocabulary#sub) | [**\<sup\>**](/rfcxml-vocabulary#sup) | [**\<tt\>**](/rfcxml-vocabulary#tt) | [**\<xref\>**](/rfcxml-vocabulary#xref) )*
### Examples
* [RFC 8759, Section 6](https://www.rfc-editor.org/rfc/rfc8759.html#section-6)
### Schema
```
   sub =
     element sub {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       (text
        | bcp14
        | cref
        | em
        | eref
        | iref
        | relref
        | strong
        | sub
        | sup
        | tt
        | xref)*
     }
```

## sup
## Tabs {.tabset}
### Usage
Causes the text to be displayed as superscript, approximately half a letter-height higher than normal text, in HTML and PDF rendering. This element can be combined with other character formatting elements, and the formatting will be additive.

Used in: [**\<annotation\>**](/rfcxml-vocabulary#annotation), [**\<blockquote\>**](/rfcxml-vocabulary#blockquote), [**\<cref\>**](/rfcxml-vocabulary#cref), [**\<dd\>**](/rfcxml-vocabulary#dd), [**\<dt\>**](/rfcxml-vocabulary#dt), [**\<em\>**](/rfcxml-vocabulary#em), [**\<li\>**](/rfcxml-vocabulary#li), [**\<name\>**](/rfcxml-vocabulary#name), [**\<refcontent\>**](/rfcxml-vocabulary#refcontent), [**\<strong\>**](rfcxml-elements[**\<strong\>**](/rfcxml-vocabulary#strong), [**\<sub\>**](/rfcxml-vocabulary#sub), [**\<sup\>**](/rfcxml-vocabulary#sup), [**\<t\>**](/rfcxml-vocabulary#t), [**\<td\>**](/rfcxml-vocabulary#td), [**\<th\>**](/rfcxml-vocabulary#th), [**\<tt\>**](/rfcxml-vocabulary#tt), and [**\<xref\>**](/rfcxml-vocabulary#xref).
Allowed content: ( text | [**\<bcp14\>**](/rfcxml-vocabulary#bcp14) | [**\<cref\>**](/rfcxml-vocabulary#cref) | [**\<em\>**](/rfcxml-vocabulary#em) | [**\<eref\>**](/rfcxml-vocabulary#eref) | [**\<iref\>**](/rfcxml-vocabulary#iref) | [**\<strong\>**](/rfcxml-vocabulary#strong) | [**\<sub\>**](/rfcxml-vocabulary#sub) | [**\<sup\>**](/rfcxml-vocabulary#sup) | [**\<tt\>**](/rfcxml-vocabulary#tt) | [**\<xref\>**](/rfcxml-vocabulary#xref) )*
### Examples
* [RFC 8681, Section 1.2](https://www.rfc-editor.org/rfc/rfc8681.html#section-1.2)
### Schema
```
   sup =
     element sup {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       (text
        | bcp14
        | cref
        | em
        | eref
        | iref
        | relref
        | strong
        | sub
        | sup
        | tt
        | xref)*
     }
```

## t
## Tabs {.tabset}
### Usage
Contains a paragraph of text.

Used in: [**\<abstract\>**](/rfcxml-vocabulary#abstract), [**\<aside\>**](/rfcxml-vocabulary#aside), [**\<blockquote\>**](/rfcxml-vocabulary#blockquote), [**\<dd\>**](/rfcxml-vocabulary#dd), [**\<li\>**](/rfcxml-vocabulary#li), [**\<note\>**](/rfcxml-vocabulary#note), [**\<section\>**](/rfcxml-vocabulary#section), [**\<td\>**](/rfcxml-vocabulary#td), and [**\<th\>**](/rfcxml-vocabulary#th).
Allowed content: ( text | [**\<bcp14\>**](/rfcxml-vocabulary#bcp14) | [**\<br\>**](/rfcxml-vocabulary#br) | [**\<contact\>**](/rfcxml-vocabulary#contact) | [**\<cref\>**](/rfcxml-vocabulary#cref) | [**\<em\>**](/rfcxml-vocabulary#em) | [**\<eref\>**](/rfcxml-vocabulary#eref) | [**\<iref\>**](/rfcxml-vocabulary#iref) | [**\<strong\>**](/rfcxml-vocabulary#strong) | [**\<sub\>**](/rfcxml-vocabulary#sub) | [**\<sup\>**](/rfcxml-vocabulary#sup) | [**\<tt\>**](/rfcxml-vocabulary#tt) | [**\<u\>**](/rfcxml-vocabulary#u) | [**\<xref\>**](/rfcxml-vocabulary#xref) )*

### Attributes
#### anchor
Document-wide unique identifier for this paragraph.

#### hangText
Deprecated. Instead, use [**\<dd\>**](/rfcxml-vocabulary#dd) inside of a definition list ([**\<dl\>**](/rfcxml-vocabulary#dl)).

#### indent
Indicates any extra amount of indentation to be used when rendering the paragraph of text. The indentation amount is interpreted as characters when rendering plain-text documents, and en-space units when rendering in formats that have richer typographic support such as HTML or PDF. One en-space is assumed to be the length of 0.5 em-space in CSS units. Only non-negative integer amounts of indentation are supported.

Default value: "0"

#### keepWithNext
Acts as a hint to the output formatters that do pagination to do a best-effort attempt to keep the paragraph with the next element, whatever that happens to be. For example, for HTML output @media print CSS might translate this to `page-break-after: avoid`. For PDF, the paginator could attempt to keep the paragraph with the next element. Note: this attribute is strictly a hint and not always actionable.

Possible values: "true", "false"
Default value: "false"

#### keepWithPrevious
Acts as a hint to the output formatters that do pagination to do a best-effort attempt to keep the paragraph with the previous element, whatever that happens to be. For example, for HTML output @media print CSS might translate this to `page-break-before: avoid`. For PDF, the paginator could attempt to keep the paragraph with the previous element. Note: this attribute is strictly a hint and not always actionable.

Possible values: "true", "false"
Default value: "false"
### Schema
```
   t =
     element t {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute anchor { xsd:ID }?,
       attribute pn { xsd:ID }?,
       attribute hangText { text }?,
       [ a:defaultValue = "0" ]
       attribute indent { text }?,
       [ a:defaultValue = "false" ]
       attribute keepWithNext { "true" | "false" }?,
       [ a:defaultValue = "false" ]
       attribute keepWithPrevious { "true" | "false" }?,
       (text
        | bcp14
        | br
        | contact
        | cref
        | em
        | eref
        | iref
        | \list
        | relref
        | spanx
        | strong
        | sub
        | sup
        | tt
        | u
        | vspace
        | xref)*
     }
```

## table
## Tabs {.tabset}
### Usage
Contains a table with a caption with the table number. If the element contains a [**\<name\>**](/rfcxml-vocabulary#name) element, the caption will also show that name.

Inside the [**\<table\>**](/rfcxml-vocabulary#table) element there is, optionally, a [**\<thead\>**](/rfcxml-vocabulary#thead) element to contain the rows that will be the table's heading and, optionally, a [**\<tfoot\>**](/rfcxml-vocabulary#tfoot) element to contain the rows of the table's footer. If the XML is converted to a representation that has page breaks (such as PDFs or printed HTML), the header and footer are meant to appear on each page.

Used in: [**\<aside\>**](/rfcxml-vocabulary#aside), [**\<dd\>**](/rfcxml-vocabulary#dd), [**\<li\>**](/rfcxml-vocabulary#li), and [**\<section\>**](/rfcxml-vocabulary#section).
Allowed content: [**\<name\>**](/rfcxml-vocabulary#name)?, [**\<iref\>**](/rfcxml-vocabulary#iref)\*, [**\<thead\>**](/rfcxml-vocabulary#thead)?, [**\<tbody\>**](/rfcxml-vocabulary#tbody)+, [**\<tfoot\>**](/rfcxml-vocabulary#tfoot)?

### Attributes
#### align
Controls whether the table appears left justified, centered, or right justified. The caption will be centered under the table, and the combined table and caption will be aligned according to the **align** attribute.

Possible values: "left", "center", "right"
Default value: "center"

#### anchor
Document-wide unique identifier for this element.
### Schema
```
   table =
     element table {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       [ a:defaultValue = "center" ]
       attribute align { "left" | "center" | "right" }?,
       attribute anchor { xsd:ID }?,
       attribute pn { xsd:ID }?,
       name?,
       iref*,
       thead?,
       tbody+,
       tfoot?
     }
```

## tbody
## Tabs {.tabset}
### Usage
A container for a set of body rows for a table.

Used in: [**\<table\>**](/rfcxml-vocabulary#table).
Allowed content: [**\<tr\>**](/rfcxml-vocabulary#tr)+

### Attributes
#### anchor
Document-wide unique identifier for this element.
### Schema
```
   tbody =
     element tbody {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute anchor { xsd:ID }?,
       tr+
     }
```

## td
## Tabs {.tabset}
### Usage
A cell in a table row.

Used in: [**\<tr\>**](/rfcxml-vocabulary#tr).
Allowed content: ( ( [**\<artset\>**](/rfcxml-vocabulary#artset) | [**\<artwork\>**](/rfcxml-vocabulary#artwork) | [**\<dl\>**](/rfcxml-vocabulary#dl) | [**\<figure\>**](/rfcxml-vocabulary#figure) | [**\<ol\>**](/rfcxml-vocabulary#ol) | [**\<sourcecode\>**](/rfcxml-vocabulary#sourcecode) | [**\<t\>**](/rfcxml-vocabulary#t) | [**\<ul\>**](/rfcxml-vocabulary#ul) )+ | ( text | [**\<bcp14\>**](/rfcxml-vocabulary#bcp14) | [**\<br\>**](/rfcxml-vocabulary#br) | [**\<cref\>**](/rfcxml-vocabulary#cref) | [**\<em\>**](/rfcxml-vocabulary#em) | [**\<eref\>**](/rfcxml-vocabulary#eref) | [**\<iref\>**](/rfcxml-vocabulary#iref) | [**\<strong\>**](/rfcxml-vocabulary#strong) | [**\<sub\>**](/rfcxml-vocabulary#sub) | [**\<sup\>**](/rfcxml-vocabulary#sup) | [**\<tt\>**](/rfcxml-vocabulary#tt) | [**\<u\>**](/rfcxml-vocabulary#u) | [**\<xref\>**](/rfcxml-vocabulary#xref) )* )

### Attributes
#### align
Controls whether the content of the cell appears left justified, centered, or right justified. Note that "center" or "right" will probably only work well in cells with plain text; any other elements might make the contents render badly.

Possible values: "left", "center", "right"
Default value: "left"

#### anchor
Document-wide unique identifier for this element.

#### colspan
The number of columns that the cell is to span. For example, setting **colspan** to "3" indicates that the cell occupies the same horizontal space as three cells of a row without the **colspan** attributes.

Default value: "1"

#### rowspan
The number of rows that the cell is to span. For example, setting **rowspan** to "3" indicates that the cell occupies the same vertical space as three rows.

Default value: "1"
### Examples
Fully featured table elements using rowspan or colspan)
* [Table 5 in RFC 8761](https://www.rfc-editor.org/rfc/rfc8761.html#table-5)
* [Table 6 in RFC 8697](https://www.rfc-editor.org/rfc/rfc8697.html#table-6)
### Schema
```
   td =
     element td {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute anchor { xsd:ID }?,
       [ a:defaultValue = "1" ] attribute colspan { text }?,
       [ a:defaultValue = "1" ] attribute rowspan { text }?,
       [ a:defaultValue = "left" ]
       attribute align { "left" | "center" | "right" }?,
       ((artset | artwork | dl | figure | ol | sourcecode | t | ul)+
        | (text
           | bcp14
           | br
           | cref
           | em
           | eref
           | iref
           | relref
           | strong
           | sub
           | sup
           | tt
           | u
           | xref)*)
     }
```

## tfoot
## Tabs {.tabset}
### Usage
A container for a set of footer rows for a table.

Used in: [**\<table\>**](/rfcxml-vocabulary#table).
Allowed content: [**\<tr\>**](/rfcxml-vocabulary#tr)+

### Attributes
#### anchor
Document-wide unique identifier for this element.
### Schema
```
   tfoot =
     element tfoot {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute anchor { xsd:ID }?,
       tr+
     }
```

## th
## Tabs {.tabset}
### Usage
A cell in a table row. When rendered, this will normally come out in boldface; other than that, there is no difference between this and the [**\<td\>**](/rfcxml-vocabulary#td) element.

Used in: [**\<tr\>**](/rfcxml-vocabulary#tr).
Allowed content: ( ( [**\<artset\>**](/rfcxml-vocabulary#artset) | [**\<artwork\>**](/rfcxml-vocabulary#artwork) | [**\<dl\>**](/rfcxml-vocabulary#dl) | [**\<figure\>**](/rfcxml-vocabulary#figure) | [**\<ol\>**](/rfcxml-vocabulary#ol) | [**\<sourcecode\>**](/rfcxml-vocabulary#sourcecode) | [**\<t\>**](/rfcxml-vocabulary#t) | [**\<ul\>**](/rfcxml-vocabulary#ul) )+ | ( text | [**\<bcp14\>**](/rfcxml-vocabulary#bcp14) | [**\<br\>**](/rfcxml-vocabulary#br) | [**\<cref\>**](/rfcxml-vocabulary#cref) | [**\<em\>**](/rfcxml-vocabulary#em) | [**\<eref\>**](/rfcxml-vocabulary#eref) | [**\<iref\>**](/rfcxml-vocabulary#iref) | [**\<strong\>**](/rfcxml-vocabulary#strong) | [**\<sub\>**](/rfcxml-vocabulary#sub) | [**\<sup\>**](/rfcxml-vocabulary#sup) | [**\<tt\>**](/rfcxml-vocabulary#tt) | [**\<u\>**](/rfcxml-vocabulary#u) | [**\<xref\>**](/rfcxml-vocabulary#xref) )* )

### Attributes
#### align
Controls whether the content of the cell appears left justified, centered, or right justified. Note that "center" or "right" will probably only work well in cells with plain text; any other elements might make the contents render badly.

Possible values: "left", "center", "right"
Default value: "left"

#### anchor
Document-wide unique identifier for this element.

#### colspan
The number of columns that the cell is to span. For example, setting **colspan** to "3" indicates that the cell occupies the same horizontal space as three cells of a row without the **colspan** attributes.

Default value: "1"

#### rowspan
The number of rows that the cell is to span. For example, setting **rowspan** to "3" indicates that the cell occupies the same vertical space as three rows.

Default value: "1"
### Schema
```
   th =
     element th {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute anchor { xsd:ID }?,
       [ a:defaultValue = "1" ] attribute colspan { text }?,
       [ a:defaultValue = "1" ] attribute rowspan { text }?,
       [ a:defaultValue = "left" ]
       attribute align { "left" | "center" | "right" }?,
       ((artset | artwork | dl | figure | ol | sourcecode | t | ul)+
        | (text
           | bcp14
           | br
           | cref
           | em
           | eref
           | iref
           | relref
           | strong
           | sub
           | sup
           | tt
           | u
           | xref)*)
     }
```

## thead
## Tabs {.tabset}
### Usage
A container for a set of header rows for a table.

Used in: [**\<table\>**](/rfcxml-vocabulary#table).
Allowed content: [**\<tr\>**](/rfcxml-vocabulary#tr)+

### Attributes
#### anchor
Document-wide unique identifier for this element.
### Schema
```
   thead =
     element thead {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute anchor { xsd:ID }?,
       tr+
     }
```

## title
## Tabs {.tabset}
### Usage
Represents the document title.

When this element appears in the [**\<front\>**](/rfcxml-vocabulary#front) element of the current document, the title might also appear in page headers or footers. If it is long (\~40 characters), the **abbrev** attribute can be used to specify an abbreviated variant.

Used in: [**\<front\>**](/rfcxml-vocabulary#front).
Allowed content: ( text | [**\<br\>**](/rfcxml-vocabulary#br) )*

### Attributes
#### abbrev
Specifies an abbreviated variant of the document title.

#### ascii
The ASCII equivalent of the [**\<title\>**](/rfcxml-vocabulary#title) content. This element may have non-ASCII Latin script content without specifying an ASCII equivalent, but for other non-ASCII content an ASCII equivalent is required.
### Schema
```
   title =
     element title {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute abbrev { text }?,
       attribute ascii { text }?,
       (text | br)*
     }
```

## toc
## Tabs {.tabset}
### Usage
This element contains the Table of Content. The content of the [**\<toc\>**](/rfcxml-vocabulary#toc) element is generated by the preptool based on the **tocInclude** and **tocDepth** attributes of the [**\<rfc\>**](/rfcxml-vocabulary#rfc) element. As a document author, you should not use [**\<toc\>**](/rfcxml-vocabulary#toc) directly.

Used in: [**\<front\>**](/rfcxml-vocabulary#front).
Allowed content: [**\<section\>**](/rfcxml-vocabulary#section)*
### Schema
```
   toc =
     element toc {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       section*
     }
```

## tr
## Tabs {.tabset}
### Usage
A row of a table.

Used in: [**\<tbody\>**](/rfcxml-vocabulary#tbody), [**\<tfoot\>**](/rfcxml-vocabulary#tfoot), and [**\<thead\>**](/rfcxml-vocabulary#thead).
Allowed content: ( [**\<td\>**](/rfcxml-vocabulary#td) | [**\<th\>**](/rfcxml-vocabulary#th) )+

### Attributes
#### anchor
Document-wide unique identifier for this element.
### Schema
```
   tr =
     element tr {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute anchor { xsd:ID }?,
       (td | th)+
     }
```

## tt
## Tabs {.tabset}
### Usage
Causes the text to be displayed in a constant-width font. This element can be combined with other character formatting elements, and the formatting will be additive.

Used in: [**\<annotation\>**](/rfcxml-vocabulary#annotation), [**\<blockquote\>**](/rfcxml-vocabulary#blockquote), [**\<cref\>**](/rfcxml-vocabulary#cref), [**\<dd\>**](/rfcxml-vocabulary#dd), [**\<dt\>**](/rfcxml-vocabulary#dt), [**\<em\>**](/rfcxml-vocabulary#em), [**\<li\>**](/rfcxml-vocabulary#li), [**\<name\>**](/rfcxml-vocabulary#name), [**\<refcontent\>**](/rfcxml-vocabulary#refcontent), [**\<strong\>**](/rfcxml-vocabulary#strong), [**\<sub\>**](/rfcxml-vocabulary#sub), [**\<sup\>**](/rfcxml-vocabulary#sup), [**\<t\>**](/rfcxml-vocabulary#t), [**\<td\>**](/rfcxml-vocabulary#td), [**\<th\>**](/rfcxml-vocabulary#th), and [**\<xref\>**](/rfcxml-vocabulary#xref).
Allowed content: ( text | [**\<bcp14\>**](/rfcxml-vocabulary#bcp14) | [**\<br\>**](/rfcxml-vocabulary#br) | [**\<cref\>**](/rfcxml-vocabulary#cref) | [**\<em\>**](/rfcxml-vocabulary#em) | [**\<eref\>**](/rfcxml-vocabulary#eref) | [**\<iref\>**](/rfcxml-vocabulary#iref) | [**\<strong\>**](/rfcxml-vocabulary#strong) | [**\<sub\>**](/rfcxml-vocabulary#sub) | [**\<sup\>**](/rfcxml-vocabulary#sup) | [**\<xref\>**](/rfcxml-vocabulary#xref) )\*

### Schema
```
   tt =
     element tt {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       (text
        | bcp14
        | br
        | cref
        | em
        | eref
        | iref
        | relref
        | strong
        | sub
        | sup
        | xref)*
     }
```

## u
## Tabs {.tabset}
### Usage
The elements [**\<author\>**](/rfcxml-vocabulary#author), [**\<organisation\>**](/rfcxml-vocabulary#organisation), [**\<street\>**](/rfcxml-vocabulary#street), [**\<city\>**](/rfcxml-vocabulary#city), [**\<region\>**](/rfcxml-vocabulary#region), [**\<code\>**](/rfcxml-vocabulary#code), [**\<country\>**](/rfcxml-vocabulary#country), [**\<postalLine\>**](/rfcxml-vocabulary#postalLine), [**\<email\>**](/rfcxml-vocabulary#email), [**\<seriesInfo\>**](/rfcxml-vocabulary#seriesInfo), and [**\<title\>**](/rfcxml-vocabulary#title) may contain non- ascii characters for the purpose of rendering author names, addresses, and reference titles correctly. They also have an additional **ascii** attribute for the purpose of proper rendering in ascii-only media.

In order to insert Unicode characters in any other context, RFCXML requires that the Unicode string be enclosed within an [**\<u\>**](/rfcxml-vocabulary#u) element. For more details see [non-ASCII characters in RFCXML](/non-ascii-characters-in-rfcxml).

Used in: [**\<annotation\>**](/rfcxml-vocabulary#annotation), [**\<blockquote\>**](/rfcxml-vocabulary#blockquote), [**\<dd\>**](/rfcxml-vocabulary#dd), [**\<li\>**](/rfcxml-vocabulary#li), [**\<t\>**](/rfcxml-vocabulary#t), [**\<td\>**](/rfcxml-vocabulary#td), and [**\<th\>**](/rfcxml-vocabulary#th).
Allowed content: text

### Attributes
#### anchor
Document-wide unique identifier for this element.

#### ascii
The ASCII equivalent of the content, to be used if the "ascii" keyword is used in the **format** specification.

#### format
The **format** attribute accepts either a simplified format specification, or a full format string with placeholders for the various possible Unicode expansions.

For more details see [non-ASCII characters in RFCXML](/non-ascii-characters-in-rfcxml).

Default value: "lit-name-num"

### Examples
Non-ASCII characters in an author's name:
* in the Latin blocks: RFC 8655, RFC 8753, RFC 8831.
* outside the Latin blocks: RFC 8694, RFC 9005, RFC 9093, RFC 9094
Non-ASCII characters in a contact's name:
* in the Latin blocks: RFC 8725
* outside the Latin blocks: RFC 9000, RFC 9001, RFC 9002

### Schema
```
   u = 
     element u {
       attribute anchor { xsd:ID }?,
       attribute ascii { text }?,
       [ a:defaultValue = "lit-name-num" ]
       attribute format { text }?,
       attribute pn { xsd:ID }?,
       text
     }
```

## ul
## Tabs {.tabset}
### Usage
An unordered list. The labels on the items will be symbols picked by the formatter.

Used in: [**\<abstract\>**](/rfcxml-vocabulary#abstract), [**\<aside\>**](/rfcxml-vocabulary#aside), [**\<blockquote\>**](/rfcxml-vocabulary#blockquote), [**\<dd\>**](/rfcxml-vocabulary#dd), [**\<li\>**](/rfcxml-vocabulary#li), [**\<note\>**](/rfcxml-vocabulary#note), [**\<section\>**](/rfcxml-vocabulary#section), [**\<td\>**](/rfcxml-vocabulary#td), and [**\<th\>**](/rfcxml-vocabulary#th).

Allowed content: [**\<li\>**](/rfcxml-vocabulary#li)+

### Attributes
#### anchor
Document-wide unique identifier for this element.

#### bare
Can only be used with **empty** set to "true" (see below). Determines if the blank bullet has an horizontal extension or not. With **bare** set to "false", the empty list bullet will still occupy the same space as for **empty** set to "false". With **empty** set to "true", there will be no bullet at all, i.e., the list items will have no indentation.

Possible values: "true", "false"
Default value: "false"

#### empty
Defines whether or not the list item bullets are empty. Setting **empty** to "true" indicates that a blank (empty) bullet will be shown.

Possible values: "true" "false"
Default value: "false"


#### indent
The indentation of the list elements relative to the start of the bullet or bullet text.

Default value: "3"

#### spacing
Defines whether or not there is a blank line between entries. Setting **spacing** to "normal" indicates a single blank line, while setting **spacing** to "compact" indicates no blank line between entries.

Possible values: "normal", "compact"
Default value: "normal"
### Examples
Example: an unordered list with **bare** as "true" and **empty** as "true":
```
List:
One
Two
```
Example: an unordered list with **bare** as "false" and **empty** as "false":
```
List:
 * One
 * Two
```
Example: an unordered list with **bare** as "false" and **empty** as "true":
```
List:
   One  
   Two
```
### Schema
```
   ul =
     element ul {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute anchor { xsd:ID }?,
       [ a:defaultValue = "normal" ]
       attribute spacing { "normal" | "compact" }?,
       ([ a:defaultValue = "false" ]
        attribute empty { "true" | "false" },
        [ a:defaultValue = "false" ]
        attribute bare { "true" | "false" }?)?,
       [ a:defaultValue = "3" ]
        attribute indent { text }?,
        attribute pn { xsd:ID }?,
       li+
     }
```

## uri
## Tabs {.tabset}
### Usage
Contains a web address associated with the author.

The contents should be a valid URI; this most likely will be an "http:" or "https:" URI.

Used in: [**\<address\>**](/rfcxml-vocabulary#address)
Allowed content: text

### Schema
```
   uri =
     element uri {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       text
     }
```

## workgroup
## Tabs {.tabset}
### Usage
This element is used to specify the Working Group (IETF) or Research Group (IRTF) from which the document originates, if any. The recommended format is the official name of the Working Group (with some capitalization).

In Internet-Drafts, this is used in the upper left corner of the boilerplate, replacing the "Network Working Group" string. Formatting software can append the words "Working Group" or "Research Group", depending on the **submissionType** attribute of the [**\<rfc\>**](/rfcxml-vocabulary#rfc) element.

Used in: [**\<front\>**](/rfcxml-vocabulary#front).
Allowed content: text

### Schema
```
   workgroup =
     element workgroup {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       text
     }
```

## xref
## Tabs {.tabset}
### Usage
A reference to an anchor in this document. Formatters that have links (such as HTML and PDF) are likely to render [**\<xref\>**](/rfcxml-vocabulary#xref) elements as internal hyperlinks. This element is useful for referring to references in the References section, to specific sections of the document, to specific figures, and so on.

If the **section** attribute is present, this represents a link to a specific part of a document that appears in a [**\<reference\>**](/rfcxml-vocabulary#reference) element. Formatters that have links (such as HTML and PDF) render [**\<xref\>**](/rfcxml-vocabulary#xref) elements with **section** attributes as external hyperlinks to the specified part of the reference, creating the link target by combining the base URI from the [**\<reference\>**](/rfcxml-vocabulary#reference) element with the **relative** attribute from this element. The **target** attribute is required, and it must be the anchor of a [**\<reference\>**](/rfcxml-vocabulary#reference) element.

If the reference is not an RFC or Internet-Draft that is in the v3 format, the element needs to have a **relative** attribute; in this case, the value of the **section** attribute is used to render the text of the external link.

If the **section** attribute is present, the rendering will, for most cominations of the **format** and **sectionFormat**, have two links; one external link to the specific part of the referenced document, and one internal link to the [**\<reference\>**](/rfcxml-vocabulary#reference) entry.

The  **format** attribute affect the internal link rendering only, and the **sectionFormat** attribute affects the rendering of the external link and its textual relationship to the internal link only.

See [References in RFCXML](/references-in-rfcxml) for more information.

Used in: [**\<annotation\>**](/rfcxml-vocabulary#annotation), [**\<blockquote\>**](/rfcxml-vocabulary#blockquote), [**\<cref\>**](/rfcxml-vocabulary#cref), [**\<dd\>**](/rfcxml-vocabulary#dd), [**\<dt\>**](/rfcxml-vocabulary#dt), [**\<em\>**](/rfcxml-vocabulary#em), [**\<li\>**](/rfcxml-vocabulary#li), [**\<name\>**](/rfcxml-vocabulary#name), [**\<strong\>**](/rfcxml-vocabulary#strong), [**\<sub\>**](/rfcxml-vocabulary#sub), [**\<sup\>**](/rfcxml-vocabulary#sup), [**\<t\>**](/rfcxml-vocabulary#t), [**\<td\>**](/rfcxml-vocabulary#td), [**\<th\>**](/rfcxml-vocabulary#th), [**\<tt\>**](/rfcxml-vocabulary#tt).
Allowed content: ( text | [**\<em\>**](/rfcxml-vocabulary#em) | [**\<strong\>**](/rfcxml-vocabulary#strong) | [**\<sub\>**](/rfcxml-vocabulary#sub) | [**\<sup\>**](/rfcxml-vocabulary#sup) | [**\<tt\>**](/rfcxml-vocabulary#tt) )*

### Attributes
#### format
Possible values: "default", "title", "counter", "none"
Default value: "default"

This attribute signals to formatters what the desired format of the internal link to the relevant [**\<reference\>**](/rfcxml-vocabulary#reference) should be.

* "default" - If the element has no content, the **derivedContent** attribute will contain a text fragment that describes the referenced part completely, such as "XML" for a target that is a [**\<reference\>**](/rfcxml-vocabulary#reference), or "Section 2" or "Table 4" for a target to a non-reference.

* "title" - If the target is a [**\<reference\>**](/rfcxml-vocabulary#reference) element, the **derivedContent** attribute will contain the name of the reference, extracted from the [**\<title\>**](/rfcxml-vocabulary#title) child of the [**\<front\>**](/rfcxml-vocabulary#front) child of the reference. Or, if the target element has a [**\<name\>**](/rfcxml-vocabulary#name) child element, the **derivedContent** attribute will contain the text content of that [**\<name\>**](/rfcxml-vocabulary#name) element concatenated with the text content of each descendant node of [**\<name\>**](/rfcxml-vocabulary#name) (that is, stripping out all of the XML markup, leaving only the text). Or, if the target element does not contain a [**\<name\>**](/rfcxml-vocabulary#name) child element, the **derivedContent** attribute will contain the name of the **anchor** attribute of that element with no other adornment.

* "counter" - The **derivedContent** attribute will contain just a counter. This is used for targets that are [**\<section\>**](/rfcxml-vocabulary#section), [**\<figure\>**](/rfcxml-vocabulary#figure), [**\<table\>**](/rfcxml-vocabulary#table), or items in an ordered list. Setting **format** to "counter" where the target is any other type of element is an error.

* "none" - There will be no autogenerated text for the xref. When this value is used, it expected that the [**\<xref\>**](/rfcxml-vocabulary#xref) element will have explicit text content.

#### relative
Specifies a relative reference from the URI in the target reference. This value must include whatever leading character is needed to create the relative reference; typically, this is "#" for HTML documents.

#### section
Specifies a section of the target reference. If the reference is not an RFC or Internet-Draft in the v3 format, and no **relative** attribute has been provided, it is an error.

#### sectionFormat
Possible values: "of", "comma", "parens", "bare"
Default value: "of"

This attribute is used to signal formatters what the desired format of the external reference should be. Formatters for document types that have linking capability should wrap each part of the displayed text in hyperlinks. If there is content in the [**\<xref\>**](/rfcxml-vocabulary#xref) element, that content will be used when rendering the internal link part of the [**\<xref\>**](/rfcxml-vocabulary#xref) rendering, but will not affect the external link.

* "of" - The [**\<xref\>**](/rfcxml-vocabulary#xref) element will be displayed as an external link followed by an internal link, separated by the word 'of'. The external link will have as its display text the word "Section" followed by a space and the contents of the **section** attribute. This will be followed by a space, the word "of", another space, and an internal link to the relevant [**\<reference\>**](/rfcxml-vocabulary#reference) entry, formatted based on the **format** attribute.

* "comma" - The [**\<xref\>**](/rfcxml-vocabulary#xref) element will be displayed as an internal link followed by an external link, separated by a comma. The external link will have as its display text the word "Section" followed by a space and the contents of the **section** attribute. The internal link will point to the relevant [**\<reference\>**](/rfcxml-vocabulary#reference) entry, and will be rendered according to the **format** attribute.

* "parens" - The [**\<xref\>**](/rfcxml-vocabulary#xref) element will be displayed as an internal link followed by an external link within parentheses. The external link will have as its display text the word "Section" followed by a space and the contents of the **section** attribute. The internal link will point to the relevant [**\<reference\>**](/rfcxml-vocabulary#reference) entry, and will be rendered according to the **format** attribute.

* "bare" - The [**\<xref\>**](/rfcxml-vocabulary#xref) element will be displayed as an external link, possibly followed by the same link within parentheses. The first external link will have as its display text only contents of the **section** attribute; the second link will be present within parentheses only if the [**\<xref\>**](/rfcxml-vocabulary#xref) element has any text content, and will then have the text content as its display text.

This value for the **sectionFormat** attribute is useful when it is desired to express for instance 
```
Sections 3.2 and 3.3 of [RFC7997]
```

#### target
Required.

Identifies the document component being referenced.  The value needs to match the value of the **anchor** attribute of an element in the document; otherwise, it is an error.
### Schema
```
   xref =
     element xref {
       attribute xml:base { text }?,
       attribute xml:lang { text }?,
       attribute target { xsd:IDREF },
       [ a:defaultValue = "false" ]
       attribute pageno { "true" | "false" }?,
       [ a:defaultValue = "default" ]
       attribute format { "default" | "title" | "counter" | "none" }?,
       attribute derivedContent { text }?,
       [ a:defaultValue = "of" ]
       attribute sectionFormat { "of" | "comma" | "parens" | "bare" }?,
       attribute section { text }?,
       attribute relative { text }?,
       attribute derivedLink { text }?,
       (text | em | strong | sub | sup | tt)*
     }
```
