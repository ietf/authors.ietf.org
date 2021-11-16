---
title: Templates and schemas
description: 
published: true
date: 2021-11-16T10:25:39.542Z
tags: 
editor: markdown
dateCreated: 2021-11-15T10:07:09.043Z
---

# RFCXML
## Templates
### draft-tools-rfcxml-template-annotated
[draft-tools-rfcxml-template-annotated.xml]() is an RFCXML template that includes examples for almost all of the features of RFCXML and many examples of how to achieve specific formatting, along with ample comments to explain the examples.

### draft-tools-rfcxml-template-standard
[draft-tools-rfcxml-template-annotated.xml]() is an RFCXML template that includes examples of the most commonly used features of RFCXML with comments explaining how to customise them.  This template can be quickly turned into an I-D by editing the examples provided. 

### draft-tools-rfcxml-template-bare
[draft-tools-rfcxml-template-bare.xml]() is an RFCXML template for experienced authors who want to start from the barest template possible. This template validates correctly but is not a valid I-D as many key sections are missing.

## Schema

### rfc7991bis.rnc
[rfc7991bis.rnc]() is the RelaxNG Compact Schema for the current version of RFCXML.  XML editors that validate against a schema and which support schema-aware editing,  require a local copy of this schema and the following processing instruction in the RFCXML file:
```
<?xml-model href="rfc7991bis.rnc"?>
```
All of the **draft-tools-\*** templates above aleady have this processing instruction included and so will support schema validation and schema-aware editing out of the box.

### SVG-1.2-RFC.rnc
[SVG-1.2-RFC.rnc]() is the RelaxNG Compact schema for the current subset of SVG allowed in RFCXML documents.  This schema is referenced in rfc7991bis.rnc and so no specific processing instruction is required to include it but a local copy must be present. 

### rfc7991.rnc
[rfc7991.rnc]() is the RelaxNG Compact Schema for the version of RFCXML described in RFC7991.  It is provided as a legacy schema for those working with old I-Ds or RFCs.

### rfc7749.rnc
[rfc7749.rnc]() is the RelaxNG Compact Schema for the version of RFCXML described in RFC7749.  It is provided as a legacy schema for those working with old I-Ds or RFCs.

## Character entities
In XML a character entity is a way of using a name in the XML, such as `&nbhy;` that can be used in place of the character itself (in this example the 'non-breaking hyphen' character).

RFCXML documents can reference a set of character entities to assist authors
### rfcxml-standard.ent
This set of character entities includes:
* All of ISO Latin 1
* Some of ISO Latin 9 and 10
* Other useful Unicode characters (including some from the windows-1252 repertoire)
* Typographic help characters

To use this set of character entities, the following line must appear in your XML source:

```xml
<!DOCTYPE rfc SYSTEM "rfcxml-standard.ent">
```

# Markdown
## Templates

## Schemas
Markdown doesn't yet have the concept of a schema.
