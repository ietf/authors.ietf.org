---
title: Document validation
description: 
published: true
date: 2021-12-11T22:33:58.282Z
tags: 
editor: markdown
dateCreated: 2021-08-20T02:57:26.157Z
---

As your I-D evolves you will inevitably want to check the contents and validate the format at regular stages.

# Validating your Internet-Draft
Document validation is an important step for an Internet-Draft to ensure that it is correctly formatted.  This is different from the syntax validation that some of the tools perform as you use them.  There are three approaches to validation:

## Validating with the Author Tools web service
[Author Tools](/https://author-tools.ietf.org) is a fully featured web service for validation, rendering and more. It allows you to validate documents written in a range of common formats by chaining together multiple tools.  For more details see [Author Tools web service](/author-tools-web-service).
  
## Validating with command line tools
There are two key command line tools provided for validation.  Both can be installed locally for command line access, or as part of an automated build system, or in a web service.

The command line validation tools below only support I-Ds written in RFCXML or plaintext.  It is common for authors who draft in other formats to to create their own local build process, chaining together multiple tools.

### xml2rfc
[xml2rfc](https://github.com/ietf-tools/xml2rfc) is the core tool for validating and transforming RFCXML files with a wide range of features. xml2rfc is the main tool used behind the scenes in the Author Tools web service.

### idnits
[idnits](https://github.com/ietf-tools/idnits-mirror) validates plaintext I-Ds. idnits is also used behind the scenes by the Author Tools web service.

## Validating by submitting your I-D to Datatracker
When an I-D is submitted to Datatracker it automatically validates the I-D and reports any errors.  For more details, see [Submitting your Internet-Draft](/submitting-your-internet-draft).


# Validating SVG
## 1. Validating use the Author Tools web service
The [Author Tools](/https://author-tools.ietf.org) web service can validate your SVG and output a corrected SVG file if required.

## 2. Validating locally with svgcheck
[svgcheck](https://github.com/ietf-tools/RfcEditor/tree/master/svgcheck) takes an XML file containing an SVG or an RFC document. It then compares all of the SVG elements with the schema defined in the document with RFC 7996 bis. The program has the option of modifying and writing out a version of the input that passes the defined schema. The [Author Tools](/https://author-tools.ietf.org) web service uses [svgcheck](https://github.com/ietf-tools/RfcEditor/tree/master/svgcheck) in the background.

# Validating formal languages
There are a number of formal languages used in I-Ds and several tools have been written to help process them. 

> Make sure that any use of formal languages conforms with the [IESG statement on the use of formal languages](https://www.ietf.org/about/groups/iesg/statements/formal-languages-use/).
{.is-success}

## 1. rfcstrip
[rfcstrip](https://github.com/mbj4668/rfcstrip) extracts code components, YANG modules and SMIv2 modules from RFCs and I-Ds, and extracts and unfolds artwork from RFCs and I-Ds in XML format.

## 2. Extract and validate ABNF with bap
[bap](https://github.com/ietf-tools/bap) can extract and validate ABNF.  The extraction feature is available as a separate [web service](https://tools.ietf.org/abnf/) and the validation as a separate [web form](https://tools.ietf.org/tools/bap/abnf.cgi).

If ABNF is used, your I-D should contain a normative reference to RFC 5234, the specification for ABNF.

## 3. Extract and validate YANG with YANG Catalog
[YANG Catalog](https://www.yangvalidator.com/) is a website operated and maintained by the IETF that provides a central resource for the use of YANG, including the [YANG Validator](https://www.yangvalidator.com/yangvalidator).

## 4. Validate and convert YANG with pyang
[pyang](https://github.com/mbj4668/pyang) validates YANG modules and converts them into other formal languages.

## 5. Validate MIBs with smilint
smilint is a command line tool that is part of the [libsmi](https://www.ibr.cs.tu-bs.de/projects/libsmi/download.html?lang=de) suite of tools and is available as a [package](https://command-not-found.com/smilint) for most operating systems.

All MIB modules should have correct syntax, so they should compile cleanly using smilint, e.g.:
```bash
smilint -m -s -l 6 -i namelength-32
```
An [online service](https://www.ibr.cs.tu-bs.de/projects/libsmi/tools/) is available for MIB syntax checking. This allows you to extract the MIB module from a document for your own local use, but you can also directly run a syntax check.

Please evaluate all diagnostic messages and if in doubt, feel free to check on the [ietfmibs mailing list](https://www.ietf.org/mailman/listinfo/IETFMIBS) or with the OPS ADs.

> You should also ensure that you follow the Guidelines for Authors and Reviewers of MIB documents (RFC 4181)
{.is-success}