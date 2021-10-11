---
title: Document validation
description: 
published: true
date: 2021-09-01T04:12:04.357Z
tags: 
editor: markdown
dateCreated: 2021-08-20T02:57:26.157Z
---

As your I-D evolves you will inevitably want to check the contents and validate the format at regular stages.

## Checking spelling, grammar and terminology

### 1. idspell
[idspell](https://tools.ietf.org/tools/idspell/webservice) is a shell script that checks the spelling of plain text I-Ds. It requires GNU Aspell and supplements that with a [custom wordlist](tools.ietf.org/tools/idspell/ietf-words.wl) of common IETF terminology built from two years' of published RFCs, the surnames of I-D authors in the reference bibliography and a short list of manually added words.

## Validating your Internet-Draft
Document validation is an important step for an Internet-Draft to ensure that it is correctly formatted.  This is different from the syntax validation that some of the tools perform as you use them.

### 1. Validating XML I-Ds with xml2rfc
XML I-Ds are validated through one of three methods:

1. Using the xml2rfc [web service]()
1. Running [xml2rfc] locally or as part of your build process
1. By submitting the I-D to datatracker. This will automatically use [xml2rfc] to validate the I-D and report any errors.

### 2. Validating plain text I-Ds with idnits
Plain text I-Ds are validated through one of three methods:

1. Using the idnits [web service](https://tools.ietf.org/tools/idnits/webservice).
1. Running [idnits](https://tools.ietf.org/tools/idnits/index) locally or as part of your build service.
1. By submitting the I-D to datatracker. This will automatically use [idnits] to validate the I-D and report any errors.

### 3. Validating I-Ds in other formats
Document validation is only possible for I-Ds written in XML or plain text.  An I-D authored in a different format needs to be converted to either XML or plain text and then validated using one of the methods above.

## Validating formal languages
There are a number of formal languages used in I-Ds and several tools have been written to help process them.

### 1. rfcstrip
[rfcstrip](https://github.com/mbj4668/rfcstrip) extracts code components, YANG modules and SMIv2 modules from RFCs and I-Ds, and extracts and unfolds artwork from RFCs and I-Ds in XML format.

### 2. Extract and validate ABNF with bap
[bap](https://github.com/fenner/bap) can extract and validate ABNF.  The extraction feature is available as a separate [web service](https://tools.ietf.org/abnf/) and the validation as a separate [web form](https://tools.ietf.org/tools/bap/abnf.cgi).

### 3. MIB templates from the MIB doctors
The MIB Doctors have produced three templates specifically aimed at drafts containing MIB modules: 
* The first is an [XML template](https://tools.ietf.org/tools/templates/mib-doc-template-xml.txt). Some advice echoing guidelines from RFC4181 is embedded in comments. 
* A second template is a plain text [template for MIB documents with advice embedded](https://tools.ietf.org/tools/templates/mib-doc-template-advice.txt) in the document. 
* A third template is a plain text [template with no advice included](https://tools.ietf.org/tools/templates/mib-doc-template-plain.txt).

### 4. Extract and validate YANG with YANG Catalog
[YANG Catalog](https://www.yangvalidator.com/) is a website operated and maintained by the IETF that provides a central resource for the use of YANG, including the [YANG Validator](https://www.yangvalidator.com/yangvalidator).

### 5. Validate SVG with svgcheck
[svgcheck](https://github.com/ietf-tools/RfcEditor/tree/master/svgcheck) takes an XML file containing an SVG or an RFC document. It then compares all of the SVG elements with the schema defined in the document with RFC 7996 bis. The program has the option of modifying and writing out a version of the input that passes the defined schema.