---
title: Formal languages
description: 
published: true
date: 2021-12-16T04:44:58.833Z
tags: 
editor: markdown
dateCreated: 2021-12-11T22:42:14.471Z
---

There are a number of formal languages used in I-Ds and several tools have been written to help process them. 

> Make sure that any use of formal languages conforms with the [IESG statement on the use of formal languages](https://www.ietf.org/about/groups/iesg/statements/formal-languages-use/).
{.is-success}

# ABNF
ABNF is a general purpose formal grammar notation specified in STD 68 (RFC 5234).

[bap](https://github.com/ietf-tools/bap) can extract and validate ABNF. It can be run locally on the command-line, or using [the online services at author-tools.ietf.org](https://author-tools.ietf.org/abnf). The utility provides the ability to validate ABNF and to extract ABNF from an I-D or RFC.

When ABNF is used, your I-D must contain a normative reference to RFC 5234, the specification for ABNF.

# MIB modules
MIB modules are collections of related objects of SMIv2 management information specified in STD 58 (RFC 2578, RFC 2579, RFC2580).

All MIB modules must follow the "Guidelines for Authors and Reviewers of MIB documents" (RFC 4181).  When using the tools below, please evaluate all diagnostic messages and if in doubt, feel free to check on the [ietfmibs mailing list](https://www.ietf.org/mailman/listinfo/IETFMIBS) or with the OPS ADs.

## libsmi
[libsmi](https://www.ibr.cs.tu-bs.de/projects/libsmi/download.html?lang=de) suite of tools and is available as a [package](https://command-not-found.com/smilint) for most operating systems and as an [online service](https://www.ibr.cs.tu-bs.de/projects/libsmi/tools/). libsmi contains three command line tools:

* smilint for checking a MIB file
* smistrip for extracting a MIB from a document
* smidump for converting a MIB into another format (including YANG) 

MIB modules with the correct syntax will compile cleanly using smilint, e.g.:
```bash
smilint -m -s -l 6 -i namelength-32
```

## rfcstrip
[rfcstrip](https://github.com/mbj4668/rfcstrip) extracts code components, YANG modules and SMIv2 (MIB) modules from RFCs and I-Ds, and extracts and unfolds artwork from RFCs and I-Ds in XML format.

# YANG
YANG (Yet Another Next Generation) is a data modeling language for data sent over network management protocols such as NETCONF and RESTCONF specified in RFC 7950, RFC 8340 and many others  

All YANG modules must follow the "Guidelines for Authors and Reviewers of YANG Data Model Documents" (RFC 8407) and the [YANG module security considerations](https://trac.ietf.org/trac/ops/wiki/yang-security-guidelines).

When YANG is used, your I-D must contain normative references to RFC 8446, RFC 6241, RFC 6242, RFC 8341, and RFC8040.

## YANG Catalog
[YANG Catalog](https://www.yangvalidator.com/) is a website operated and maintained by the IETF that provides a central resource for the use of YANG, including the [YANG Validator](https://www.yangvalidator.com/yangvalidator).  YANG Catalog is [open source](https://github.com/YangCatalog).

## pyang
[pyang](https://github.com/mbj4668/pyang) is an open source tool that validates YANG modules and converts them into other formal languages. pyang has a flag `--ietf` that checks RFC 8407 rules.

The RFC editor ensures that all published YANG modules are formatted consistently using pyang as follows:

```bash
# ensure that the module fits into the line limits of an I-D
pyang --ietf --max-line-length 69 FILE

# format the module
pyang -f yang --keep-comments --yang-line-length 69 FILE
```

## libyang
[libyang](https://github.com/CESNET/libyang) is an open source YANG data modelling language parser and toolkit that includes the [yanglint](https://github.com/CESNET/libyang/blob/master/tools/lint/examples/README.md) command line tool for validation and conversion of the schemas and YANG modeled data.

## xym
[xym](https://github.com/xym-tool/xym) is an open source tool for extracting YANG modules from files.  See also [rfcstrip](#rfcstrip).

# XML
Protocol specifications that use XML should always use well-formed XML at a minimum. Sample XML instances included in a specification have to be well-formed, and if the XML is supposed to be valid (according to the current W3C definition of validity), the samples must reference and be validated using an appropriate XML Schema, DTD, or another standard validation mechanism that is structurally and syntactically correct.

Other guidelines for the use of XML in IETF protocols can be found in RFC 3470. Internet-Drafts that include an XML Schema should include a normative reference to either the W3C XML Schema Definition Language 1.1 [Part1](https://www.w3.org/TR/xmlschema11-1/) or [Part 2](https://www.w3.org/TR/xmlschema11-2/).

XML allows syntax extensions using structures, such as the `<any>` element information item in XML Schema.  If your XML defines and extension mechanism then:

- [x] Ensure the I-D contains clear guidance on how, when, and where any extension structures, such as versioning, can be used.
- [x] Check that any new or updated XML Schemas, Namespaces, and Resource Description Framework (RDF) Schemas are being registered with IANA using the procedures described in RFC 3688.

# Programming languages
When programming languages are used in Internet-Drafts, you must include as a reference the formal definition of that coding language (e.g., [C99](https://www.iso.org/standard/29237.html)).
