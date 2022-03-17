---
title: Tools catalog
description: 
published: true
date: 2022-01-12T23:32:51.657Z
tags: 
editor: markdown
dateCreated: 2021-08-17T00:37:22.495Z
---

# Introduction
While there are many tools that can be used by I-D authors, there are some that have been specifically developed to support I-D authors and are commonly referred to.  This catalog is a reference catalog for these tools and is intended to supplement the task/context-specific mentions of the tools elsewhere in this documentation, not replace it.

# Feature classification of tools
The catalog below includes a feature classification which lists the following for each tool:
## Supported modes
The tools generally support one or more of the following modes of operation:

- Interactive **Editor** 
- Command Line Interface (**CLI**).  Where the author installs the tools locally and then runs them on local files from the command line, one operation at a time.
- Automated **Build** process. Where the author(s) installs the tools into a build manager that then runs a sequence of tools on a source target.  This allows for a continuous integrated build process much as software developers use when building code. 
- **Web** service. This can be broken down into two sub-modes:
    - Where the author uses an interactive web page that in turns calls a remote web service, on individual local files generally one operation at the time.
    - Where the author(s) configures their build service to use a remote web service via an API instead of installing the tools. 

## Supported operations
The tools generally provide one of more of the following broad operations:

-  **Convert** the document from one format to another such as from XML to PDF.
-  **Validate** that the format/structure of the document source conforms to the format/structure rules for an I-D/RFC.
-  **Extract** part of the document. For example, extracting a code module such as YANG, MIB or ABNF and passing it to a separate validator. 
-  **Insert** new text into an I-D. This may be boilerplate, references, new sections or other custom text.
-  **Compare** two different I-Ds or two versions of an I-D.
-  Supports an interactive **Editor** with features such as auto-completion.

## Supported formats
The formats that we are aware of tools supporting include: AsciiDoc, DOCX, EPUB, LaTeX, Markdown, nroff, Org Mode, PDF, plaintext, RFCXML, as well as the formal languages of ABNF, MIB, YANG and SVG.

Some tools only support the previous version of RFCXML (v2) and the format is written as RFCXML(old) in the table where that occurs, as well as "No" in the "Supports v3" column.

# Catalog
# Tables {.tabset}
## Basic

| Tool | Description |
| :--- | :---------- |
| [**bibtex2rfc**](https://github.com/yaronf/bibtex2rfc) | Generates BibXML references from BibTeX citations |
| [**bibxml2md**](https://github.com/yaronf/bibxml2md) | Generates Markdown references from BibXML references |
| [**bap**](https://github.com/ietf-tools/bap) | Extract and validates ABNF |
| [**id2xml**](https://github.com/ietf-tools/id2xml) | Generates RFCXML from plain text I-Ds |
| [**idnits**](https://github.com/ietf-tools/idnits-mirror) | Check plain text I-D for submission nits |
| [**kramdown-rfc**](https://github.com/cabo/kramdown-rfc) | Generates RFCXML from Markdown I-Ds |
| [**lyx2rfc**](https://github.com/nicowilliams/lyx2rfc) | Generates RFCXML from Lyx (LaTeX) I-Ds and then transforms using xml2rfc |
| [**metanorma-ietf**](https://github.com/metanorma/metanorma-ietf) | Generates RFCXML from AsciiRFC (AsciiDoc) I-Ds |
| [**mmark**](https://mmark.miek.nl) | Generates RFCXML from Markdown I-Ds |
| [**nroff2xml**](https://github.com/tomaszmrugalski/nroff2xml) | Generates RFCXML from nroff I-Ds |
| [**pyang**](https://github.com/mbj4668/pyang) | Validates and converts YANG modules |
| [**rfcdiff**](https://www.ietf.org/rfcdiff) | Side-by-side comparison of an I-D and another version or an RFC |
| [**rfcfold**](https://github.com/ietf-tools/rfcfold) | Handling of long lines in width-bounded text content, e.g., code fragments or example text, in an I-D or RFC |
| [**rfclint**](https://github.com/ietf-tools/RfcEditor/tree/master/rfclint) | Validates RFCXML documents |
| [**rfcstrip**](https://github.com/mbj4668/rfcstrip) | Extracts code components, YANG modules and SMIv2 modules from RFCs and Internet Drafts, and extracts and unfolds artwork from RFCs and Internet Drafts in XML format |
| [**svgcheck**](https://github.com/ietf-tools/RfcEditor/tree/master/svgcheck) | Validates RFC-specific SVG and generates conformant SVG |
| [**xml2rfc**](https://github.com/ietf-tools/xml2rfc) | Validates RFCXML and plain text I-Ds and converts to multiple output formats |
| [**xml2rfc-xxe**](https://github.com/wkumari/xml2rfc-xxe) | A configuration to assist editing RFCXML documents using XMLMind XML Editor |
| [**xym**](https://github.com/xym-tool/xym) | Extracts YANG modules from I-Ds and RFCs |
| [**YANG validator**](https://github.com/YangCatalog/bottle-yang-extractor-validator) | Extract and validate YANG modules |

## Feature classification

| Tool | Modes | Operations | Input formats | Output formats | Supports v3 |
| :--- | :---- | :--------- | :------------ | :------------- | :---------: |
| [**bibtex2rfc**](https://github.com/yaronf/bibtex2rfc) | Build, CLI | Convert | BibTex | BibXML | Yes |
| [**bibxml2md**](https://github.com/yaronf/bibxml2md) | Build, CLI | Convert | BibXML | RFCXML(old) | No |
| [**bap**](https://github.com/ietf-tools/bap) | Build, CLI | Extract, Validate | ABNF | - | Unknown |
| [**id2xml**](https://github.com/ietf-tools/id2xml) | Build, CLI | Convert | plaintext | RFCXML | Yes |
| [**idnits**](https://github.com/ietf-tools/idnits) | Build, CLI, Web | Validate | plaintext | - | N/A |
| [**kramdown-rfc**](https://github.com/cabo/kramdown-rfc) | Build, CLI, Web | Convert, Validate | Markdown | RFCXML | Yes |
| [**lyx2rfc**](https://github.com/nicowilliams/lyx2rfc) | ? | Validate, Convert | LaTeX(Lyx) | ? | No |
| [**metanorma-ietf**](https://github.com/metanorma/metanorma-ietf) | Build, CLI | Validate, Convert | AsciiDoc(AsciiRFC) | RFCXML | Yes |
| [**mmark**](https://mmark.miek.nl) | Validate, Convert | Build, CLI | Markdown | RFCXML | Yes |
| [**nroff2xml**](https://github.com/tomaszmrugalski/nroff2xml) | Build, CLI | Convert | nroff | RFCXML(old) | No |
| [**pyang**](https://github.com/mbj4668/pyang) | Build, CLI | Validate, Convert | YANG | ? | N/A |
| [**rfcdiff**](https://tools.ietf.org/rfcdiff) | Web | Compare | plaintext | - | N/A |
| [**rfcfold**](https://github.com/ietf-tools/rfcfold) | CLI | Convert | plaintext | plaintext | N/A |
| [**rfclint**](https://github.com/ietf-tools/RfcEditor/tree/master/rfclint) | Build, CLI | Validate | RFCXML | RFCXML | Yes |
| [**rfcstrip**](https://github.com/mbj4668/rfcstrip) | CLI | Extract | plaintext, RFCXML | YANG, SMIv2, plaintext | Yes |
| [**svgcheck**](https://github.com/ietf-tools/RfcEditor/tree/master/svgcheck) | Build, CLI, Web | Validate, Convert | SVG | SVG | Yes |
| [**xml2rfc**](https://github.com/ietf-tools/xml2rfc) | Build, CLI, Web | Validate, Convert | RFCXML, RFCXML(old), plaintext | RFCXML Plain text, PDF, HTML, HTMLised, EPUB, nroff | Yes |
| [**xml2rfc-xxe**](https://github.com/wkumari/xml2rfc-xxe) | Editor | Validate, Insert | RFCXML(old) | RFCXML(old) | No |
| [**xym**](https://github.com/xym-tool/xym) | Build, CLI | Extract | RFCXML | YANG | Yes |
| [**YANG validator**](https://github.com/YangCatalog/bottle-yang-extractor-validator) | Web | RFCXML | YANG | Yes |

## Status

| Tool | Author | Ownership | License | Maintained | Maintainer |
| :--- | :----- | :-------- | :------ | :--------- | :--------- |
| [**bibtex2rfc**](https://github.com/yaronf/bibtex2rfc) | Yaron Sheffer | Yaron Sheffer | Public domain | Yes | Yaron Sheffer |
| [**bibxml2md**](https://github.com/yaronf/bibxml2md) | Yaron Sheffer | Yaron Sheffer | Public domain | Yes | Yaron Sheffer |
| [**bap**](https://github.com/ietf-tools/bap) | Bill Fenner | Bill Fenner | Unknown | No | None | 
| [**id2xml**](https://github.com/ietf-tools/id2xml) | Henrik Levkowetz | IETF Trust | Revised BSD | Unknown | Unknown |
| [**idnits**](https://github.com/ietf-tools/idnits) | Henrik Levkowetz | Henrik Levkowetz | GPL | Yes | Tools Team |
| [**kramdown-rfc**](https://github.com/cabo/kramdown-rfc) | Carsten Bormann | Carsten Bormann | MIT | Yes | Carsten Bormann |
| [**lyx2rfc**](https://github.com/nicowilliams/lyx2rfc) | Nico Williams | Nico Williams | Unknown | No | None |
| [**metanorma-ietf**](https://github.com/metanorma/metanorma-ietf) | Ribose | Ribose | Simplified BSD | Yes | Ribose |
| [**mmark**](https://mmark.miek.nl) | Miek Gieben | Miek Gieben | Simplified BSD | Yes | Miek Gieben |
| [**nroff2xml**](https://github.com/tomaszmrugalski/nroff2xml) | Tomek Mrugalski | IETF Trust | Revised BSD | No | None |
| [**pyang**](https://github.com/mbj4668/pyang) | Martin Bjorklund | Martin Bjorklund | ISC | Yes | Martin Bjorklund |
| [**rfcdiff**](https://tools.ietf.org/rfcdiff) | Henrik Levkowetz | Henrik Levkowetz | Unknown | Unknown | Unknown |
| [**rfcfold**](https://github.com/ietf-tools/rfcfold) | Kent Watsen and Erik Auerswald | IETF Trust | Revised BSD | Yes | Kent Watsen and Erik Auerswald |
| [**rfclint**](https://github.com/ietf-tools/RfcEditor/tree/master/rfclint) | Jim Schaad | IETF Trust | Revised BSD | Yes | AMS |
| [**rfcstrip**](https://github.com/mbj4668/rfcstrip) | Multiple | Frank Strauss, Technical University of Braunschweig, and other parties | A custom license | Yes | Martin Bjorklund |
| [**svgcheck**](https://github.com/ietf-tools/RfcEditor/tree/master/svgcheck) | Jim Schaad | IETF Trust | Revised BSD | Yes | Tools Team |
| [**xml2rfc**](https://github.com/ietf-tools/xml2rfc) | Henrik Levkowetz | IETF Trust | Revised BSD | Yes | Tools Team |
| [**xml2rfc-xxe**](https://github.com/wkumari/xml2rfc-xxe) | Warren Kumari | Warren Kumari | Unknown | No | None | 
| [**xym**](https://github.com/xym-tool/xym) | Multiple | Cisco Systems | Revised BSD | Yes | Einar Nilsen-Nygaard |
| [**YANG validator**](https://github.com/YangCatalog/bottle-yang-extractor-validator) | Multiple | IETF Trust | Revised BSD | Yes | Pantheon |

# Miscellaneous tools
There are a number of miscellaneous tools, not directly related to drafting I-Ds and not included in the catalog, that authors may find useful:

- **[ietf-cli](https://trac.tools.ietf.org/tools/ietf-cli/)**
A multi-functional command line tool for manipulating I-Ds and RFCs and local repositories.

- **[print_rfc_or_draft](https://www.kumari.net/index.php/programming/programmingcat/45-printrfcordraft)**
A simple program that prints an Internet Draft (ID) or RFC. Because of the difference between the number of lines on laser printers and line / dot-matrix printers, each "page" of the draft actually takes up 2 pages and you end up with lots of pages with just a one line footer. This script tries to fix that by downloading the draft, converting it to a PDF and then printing it.

- **[Rewrite IETF ID URLs to Tools or Datatracker](https://chrome.google.com/webstore/detail/rewrite-ietf-id-urls-to-t/aiccdpabeagpjcebilebhlifplfkinao)**
Google Chrome extension that rewrites I-D URLs that point to www.ietf.org to point to datatracker.ietf.org or tools.ietf.org. 

- **[RFC-what-I-mean](https://www.strayalpha.com/tools/)**
Checks a list of RFCs to find the most recent list and their dependents. It needs to run with a copy of rfc-index.txt as input.

- **[rfc-mode](https://github.com/galdor/rfc-mode)**
A plugin Emacs major mode that provides support for reading RFCs.
