---
title: Templates and schemas
description: 
published: true
date: 2021-11-18T09:20:03.556Z
tags: 
editor: markdown
dateCreated: 2021-11-15T10:07:09.043Z
---

# RFCXML
## Templates
To use one of these templates you will also need to download both of the schemas and the character entity file below and keep them all in the same directory.

### draft-rfcxml-general-template-standard.xml
[draft-rfcxml-general-template-standard.xml]() is an RFCXML template that includes examples of the most commonly used features of RFCXML with comments explaining how to customise them.  This template can be quickly turned into an I-D by editing the examples provided. 

### draft-rfcxml-general-template-annotated.xml
[draft-rfcxml-general-template-annotated.xml]() is an RFCXML template that includes examples for almost all of the features of RFCXML and many examples of how to achieve specific formatting, along with ample comments to explain the examples.

### draft-rfcxml-general-template-bare.xml
[draft-rfcxml-general-template-bare.xml]() is an RFCXML template for experienced authors who want to start from the barest template possible. This template validates correctly but is not a valid I-D as many key sections are missing.

## Schema

### rfc7991bis.rnc
[rfc7991bis.rnc]() is the RelaxNG Compact Schema for the current version of RFCXML.  XML editors that validate against a schema and which support schema-aware editing, require a local copy of this schema and the following processing instruction in the RFCXML file:
```
<?xml-model href="rfc7991bis.rnc"?>
```
All of the templates above aleady have this processing instruction included and so will support schema validation and schema-aware editing out of the box.

### rfc7996.rnc
[rfc7996.rnc]() is the RelaxNG Compact schema for the subset of SVG allowed in RFCXML documents.  This schema is referenced in rfc7991bis.rnc and so no specific processing instruction is required to include it but a local copy must be present. 

## Character entities
In XML a character entity is a way of using a name in the XML, such as `&nbhy;` in place of the character itself (in this example the 'non-breaking hyphen' character).

RFCXML documents can reference a set of character entities to assist authors
### rfcxml.ent
This set of character entities includes:
* All of ISO Latin 1
* Some of ISO Latin 9 and 10
* Other useful Unicode characters (including some from the windows-1252 repertoire)
* Typographic help characters

To use this set of character entities, the following line must appear in your XML source:

```xml
<!DOCTYPE rfc SYSTEM "rfcxml.ent">
```

## Legacy files
The following legacy files are for those working with old I-Ds or RFCs and should not be used for any new I-Ds.

* [rfc7991.rnc]() is the RelaxNG Compact Schema for the version of RFCXML described in RFC7991.
* [rfc7749.rnc]() is the RelaxNG Compact Schema for the version of RFCXML described in RFC7749.
* [rfc2629-other.ent]() is small set of character entities.


# Markdown
## Templates

## Schemas
Markdown doesn't yet have the concept of a schema.
