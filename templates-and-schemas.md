---
title: Templates and schemas
description: 
published: true
date: 2022-03-03T00:18:11.692Z
tags: 
editor: markdown
dateCreated: 2021-11-15T10:07:09.043Z
---

# RFCXML
## Templates
To use one of these templates you will also need to download both of the schemas below and keep them all in the same directory.  For those that use Git, you can clone the [repository](https://github.com/ietf-tools/rfcxml-templates-and-schemas) and go from there.

> NOTE: While RFCs validate with the same schema as Internet-Drafts, using an XML RFC as a template for an Internet-Draft is not recommended as the prep tool hard codes multiple data into the RFC, making it unsuitable for further manual editing.
{.is-warning}

### draft-rfcxml-general-template-standard-00.xml
[draft-rfcxml-general-template-standard-00.xml](https://github.com/ietf-tools/rfcxml-templates-and-schemas/raw/main/draft-rfcxml-general-template-standard-00.xml) is an RFCXML template that includes examples of the most commonly used features of RFCXML with comments explaining how to customise them.  This template can be quickly turned into an I-D by editing the examples provided. 

### draft-rfcxml-general-template-bare-00.xml
[draft-rfcxml-general-template-bare-00.xml](https://github.com/ietf-tools/rfcxml-templates-and-schemas/raw/main/draft-rfcxml-general-template-bare-00.xml) is an RFCXML template for experienced authors who want to start from the barest template possible. This template validates correctly but is not a valid I-D as many key sections are missing.

### draft-rfcxml-general-template-annotated-00.xml
[draft-rfcxml-general-template-annotated-00.xml](https://github.com/ietf-tools/rfcxml-templates-and-schemas/raw/main/draft-rfcxml-general-template-annotated-00.xml) is an RFCXML template that includes examples for almost all of the features of RFCXML and many examples of how to achieve specific formatting, along with ample comments to explain the examples.

## Schemas

### rfc7991bis.rnc
[rfc7991bis.rnc](https://github.com/ietf-tools/rfcxml-templates-and-schemas/raw/main/rfc7991bis.rnc) is the RelaxNG Compact Schema for the current version of RFCXML.  XML editors that validate against a schema and which support schema-aware editing, require a local copy of this schema and the following processing instruction in the RFCXML file:
```xml
<?xml-model href="rfc7991bis.rnc"?>
```
All of the templates above aleady have this processing instruction included and so will support schema validation and schema-aware editing out of the box.

### SVG-1.2-RFC.rnc
[SVG-1.2-RFC.rnc](https://github.com/ietf-tools/rfcxml-templates-and-schemas/raw/main/SVG-1.2-RFC.rnc) is the RelaxNG Compact schema for the subset of SVG allowed in RFCXML documents (SVG 1.2 RFC).  This schema is referenced in rfc7991bis.rnc and so no specific processing instruction is required to include it but a local copy must be present. 

## Character entities
In XML a character entity is a way of using a name in the XML, such as `&nbhy;` in place of the character itself (in this example the 'non-breaking hyphen' character).

The templates above include a small set of character entities defined in a DOCTYPE statement.  These are for typographic characters that if entered directly into the source can cause problems, either because they are invisible to the reader, or indistinguishable from other typographic characters.

They are typically used for controlling the placement of line breaks in rendering:
* `&nbsp;` - to prevent a line break between words (e.g. `BCP&nbsp;14` to prevent a line break within "BCP 14")
* `&nbhy;` - to prevent a line break after a hyphen (e.g. `EUI&nbhy;64` to prevent a line break within "EUI-64")
* `&wj;` - to prevent a line break in a specific location (e.g. `S/&wj;MIME` to prevent a line break after the "/" in "S/MIME")
* `&zwsp;` - to mark a good location to insert a line break (e.g. forcing the content of a table cell to have a line break in the desired location. `<td>request-inactive-&zwsp;other-active</td>` as in Table 10 of RFC 9132)

For info, this DOCTYPE statement is:

```xml
<!DOCTYPE rfc [
  <!ENTITY nbsp    "&#160;">
  <!ENTITY zwsp   "&#8203;">
  <!ENTITY nbhy   "&#8209;">
  <!ENTITY wj     "&#8288;">
]>
```
If you wish to use additional character entities then the recommended method is to add further inline definitions to this DOCTYPE declaration.  Replacing the DOCTYPE with a reference to an external entity file is possible but not recommended as that will prevent you from using the [Author Tools web service](/author-tools-web-service).

## Legacy files
The following legacy files are for those working with old I-Ds or RFCs and should not be used for any new I-Ds.

### rfc7991.rnc
[rfc7991.rnc](https://github.com/ietf-tools/legacy-templates-and-schemas/raw/main/rfc7991.rnc) is the RelaxNG Compact Schema for the first release of v3 of RFCXML as documented in RFC7991.  Use [rfc7991bis.rnc](#rfc7991bisrnc) instead.
### rfc7749.rnc
[rfc7749.rnc](https://github.com/ietf-tools/legacy-templates-and-schemas/raw/main/rfc7749.rnc) is the RelaxNG Compact Schema for v2 of RFCXML as documented in RFC7749.  When originally published, this file was called v2.rnc.
### rfc2629-other.ent
[rfc2629-other.ent](https://github.com/ietf-tools/legacy-templates-and-schemas/raw/main/rfc2629-other.ent) is a small set of character entities.  This file is no longer needed as the [special processing of non-ASCII character](/upgrading-from-v2#special-processing-of-non-ascii-characters) has been superseded by direct support for [non-ASCII characters in RFCXML](/non-ascii-characters-in-rfcxml).
### rfc2629-xhtml.ent
[rfc2629-xhtml.ent](https://github.com/ietf-tools/legacy-templates-and-schemas/raw/main/rfc2629-xhtml.ent) is a larger set of character entities. This file is no longer needed as the [special processing of non-ASCII character](/upgrading-from-v2#special-processing-of-non-ascii-characters) has been superseded by direct support for[non-ASCII characters in RFCXML](/non-ascii-characters-in-rfcxml).
### rfc2629.dtd
[rfc2629.dtd](https://github.com/ietf-tools/legacy-templates-and-schemas/raw/main/rfc2629.dtd) is the DTD for v1 of RFCXML as documented in RFC2629.


# Markdown
## Templates
The following are community developed Markdown templates specific to [kramdown-rfc](https://github.com/cabo/kramdown-rfc):
* [Martin Thomson's Markdown Template](https://github.com/martinthomson/internet-draft-template/raw/main/draft-todo-yourname-protocol.md)
* [kramdown-rfc standard template](https://raw.githubusercontent.com/cabo/kramdown-rfc/master/examples/draft-rfcxml-general-template-standard-00.xml-edited.md)

## Schemas
Markdown doesn't yet have the concept of a schema. It may never have.
