---
title: Document validation
description: 
published: true
date: 2021-12-08T20:53:11.304Z
tags: 
editor: markdown
dateCreated: 2021-08-20T02:57:26.157Z
---

As your I-D evolves you will inevitably want to check the contents and validate the format at regular stages.

# Validating your Internet-Draft
Document validation is an important step for an Internet-Draft to ensure that it is correctly formatted.  This is different from the syntax validation that some of the tools perform as you use them.

## 1. Validating use the Author Tools web service
The [Author Tools](/https://author-tools.ietf.org) web service supports a wide range of formats for validation. 

## 2. Validating RFCXML I-Ds with xml2rfc
RFCXML I-Ds can be validated by running [xml2rfc](https://github.com/ietf-tools/xml2rfc) locally or as part of your build process

## 3. Validating plain text I-Ds with idnits
Plain text I-Ds can be validated by running [idnits](https://github.com/ietf-tools/idnits-mirror) locally or as part of your build service.

## 4. Validating by submitting your I-D to Datatracker
When an I-D is submitted to Datatracker it automatically validates the I-D and reports any errors.

## 5. Validating I-Ds in other formats
Document validation is only possible for I-Ds written in RFCXML or plain text.  An I-D authored in a different format needs to be converted to either RFCXML or plain text and then validated using one of the methods above.

# Validating SVG
## 1. Validating use the Author Tools web service
The [Author Tools](/https://author-tools.ietf.org) web service can validate your SVG and output a corrected SVG file if required.

## 2. Validating locally with svgcheck
[svgcheck](https://github.com/ietf-tools/RfcEditor/tree/master/svgcheck) takes an XML file containing an SVG or an RFC document. It then compares all of the SVG elements with the schema defined in the document with RFC 7996 bis. The program has the option of modifying and writing out a version of the input that passes the defined schema. The [Author Tools](/https://author-tools.ietf.org) web service uses [svgcheck](https://github.com/ietf-tools/RfcEditor/tree/master/svgcheck) in the background.

# Validating formal languages
There are a number of formal languages used in I-Ds and several tools have been written to help process them.

## 1. rfcstrip
[rfcstrip](https://github.com/mbj4668/rfcstrip) extracts code components, YANG modules and SMIv2 modules from RFCs and I-Ds, and extracts and unfolds artwork from RFCs and I-Ds in XML format.

## 2. Extract and validate ABNF with bap
[bap](https://github.com/ietf-tools/bap) can extract and validate ABNF.  The extraction feature is available as a separate [web service](https://tools.ietf.org/abnf/) and the validation as a separate [web form](https://tools.ietf.org/tools/bap/abnf.cgi).

## 3. Extract and validate YANG with YANG Catalog
[YANG Catalog](https://www.yangvalidator.com/) is a website operated and maintained by the IETF that provides a central resource for the use of YANG, including the [YANG Validator](https://www.yangvalidator.com/yangvalidator).

## 4. Validate and convert YANG with pyang
[pyang](https://github.com/mbj4668/pyang) validates YANG modules and converts them into other formal languages.