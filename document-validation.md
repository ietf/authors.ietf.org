---
title: Document validation
description: 
published: true
date: 2022-01-31T22:26:01.925Z
tags: 
editor: markdown
dateCreated: 2021-08-20T02:57:26.157Z
---

Document validation is an important step for an Internet-Draft to ensure that it is correctly formatted.  This is different from the syntax validation that some of the tools perform as you use them.  

> For information on validating SVG see [Diagrams](/diagrams) and for information on validating formal languages see [Formal languages](/formal-languages).
{.is-info}


There are three approaches to validation:

# Validating with the Author Tools web service
[Author Tools](https://author-tools.ietf.org) is a fully featured web service for validation, rendering and more. It allows you to validate documents written in a range of common formats by chaining together multiple tools.  For more details see [Author Tools web service](/author-tools-web-service).
  
# Validating with command line tools
There are two key command line tools provided for validation.  Both can be installed locally for command line access, or as part of an automated build system, or in a web service.

The command line validation tools below only support I-Ds written in RFCXML or plaintext.  It is common for authors who draft in other formats to to create their own local build process, chaining together multiple tools.

## xml2rfc
[xml2rfc](https://github.com/ietf-tools/xml2rfc) is the core tool for validating and transforming RFCXML files with a wide range of features. xml2rfc is the main tool used behind the scenes in the Author Tools web service.

## rfclint
[rfclint](https://github.com/ietf-tools/RfcEditor/tree/master/rfclint) is used by the RFC Production Center as a validation tool for RFCXML files.  rfclint performs the following checks:
* Validate the file is well formed XML and that it conforms to the XML2RFC Version 3 schema as defined in RFC 7991.
* Verify that embedded XML stanzas are well formed.
* Verify that embedded ABNF is complete and well formed.
* Identify misspelled words.
* Detect duplicate words.

## idnits
[idnits](https://github.com/ietf-tools/idnits-mirror) validates plaintext I-Ds. idnits is also used behind the scenes by the Author Tools web service.

# Validating by submitting your I-D to Datatracker
When an I-D is submitted to Datatracker it automatically validates the I-D and reports any errors.  For more details, see [Submitting your Internet-Draft](/submitting-your-internet-draft).

