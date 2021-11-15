---
title: Tools catalog
description: 
published: true
date: 2021-11-15T02:03:29.636Z
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
The formats that we are aware of tools supporting include: AsciiDoc, DOCX, EPUB, LaTeX, Markdown, nroff, Org Mode, PDF, Plain Text, RFCXML, as well as the formal languages of ABNF, MIB, YANG and SVG.

Some tools only support the previous version of RFCXML (v2) and the format is written as RFCXML(old) in the table where that occurs, as well as "No" in the "Supports v3" column.

# Catalog
# Tables {.tabset}
## Basic

| Tool | Description |
| :--- | :---------- |
| [**bibtext2rfc**](https://github.com/yaronf/bibtex2rfc) | Converts BibTeX citations into bibxml references |
| [**bibxml2md**](https://github.com/yaronf/bibxml2md) | Converts bibxml references into markdown |
| [**bap**](https://github.com/ietf-tools/bap) | Extract and validates ABNF |
| [**id2xml**]() | Convert plain text I-D into RFCXML |
| [**idnits**]() | Check plain text I-D for submission nits |
| [**idspell**]() | Checks the spelling in I-Ds |
| [**kramdown-rfc2629**](https://github.com/cabo/kramdown-rfc2629) | Generates RFCXML from Markdown documents |
| [**lyx2rfc**](https://github.com/nicowilliams/lyx2rfc) | Generates RFCXML from Lyx (LaTeX) documents and then transforms using xml2rfc |
| [**metanorma-ietf**](https://github.com/metanorma/metanorma-ietf) | Generates RFCXML from AsciiRFC (AsciiDoc) documents |
| [**mmark**](https://mmark.miek.nl) | Generates RFCXML from Markdown documents |
| [**nroff2xml**](https://github.com/tomaszmrugalski/nroff2xml) | Generates RFCXML from nroff documents |
| [**pyang**](https://github.com/mbj4668/pyang) | Validates and converts YANG modules |
| [**rfcdiff**](https://tools.ietf.org/rfcdiff) | Side-by-side comparison of an I-D and another version or an RFC |
| [**svgcheck**](https://github.com/ietf-tools/RfcEditor/tree/master/svgcheck) | Validates RFC-specific SVG and generates conformant SVG |
| [**xml2rfc**]() | Validates RFCXML and plain text I-Ds and converts to multiple output formats |
| [**xml2rfc-xxe**](https://github.com/wkumari/xml2rfc-xxe) | A configuration to assist editing xml2rfc-format documents using XMLMind XML Editor |
| [**xym**](https://github.com/xym-tool/xym) | Extracts YANG modules from I-Ds and RFCs |
| YANG validator |
| yanglint | |

## Feature classification

| Tool | Modes | Operations | Input formats | Output formats | Supports v3 |
| :--- | :---- | :--------- | :------------ | :------------- | :---------: |
| [**bibtext2rfc**](https://github.com/yaronf/bibtex2rfc) | Build, CLI | Convert | BibTex | BibXML | Yes |
| [**bibxml2md**](https://github.com/yaronf/bibxml2md) | Build, CLI | Convert | BibXML | RFCXML(old) | No |
| [**bap**](https://github.com/ietf-tools/bap) | Build, CLI | Extract, Validate | ABNF | - | Unknown |
| [**id2xml**]() | Build, CLI | Convert | Plain text | RFCXML | Yes |
| [**idnits**]() | Build, CLI, Web | Validate | Plain text | - | N/A |
| [**idspell**]() | Build, CLI, Web | Validate | Plain text | - | N/A |
| [**kramdown-rfc2629**](https://github.com/cabo/kramdown-rfc2629) | Build, CLI, Web | Convert, Validate | Markdown | RFCXML | Yes |
| [**lyx2rfc**](https://github.com/nicowilliams/lyx2rfc) | ? | Validate, Convert | LaTeX(Lyx) | ? | No |
| [**metanorma-ietf**](https://github.com/metanorma/metanorma-ietf) | Build, CLI | Validate, Convert | AsciiDoc(AsciiRFC) | RFCXML | Yes |
| [**mmark**](https://mmark.miek.nl) | Validate, Convert | Build, CLI | Markdown | RFCXML | Yes |
| [**nroff2xml**](https://github.com/tomaszmrugalski/nroff2xml) | Build, CLI | Convert | nroff | RFCXML(old) | No |
| [**pyang**](https://github.com/mbj4668/pyang) | Build, CLI | Validate, Convert | YANG | ? | N/A |
| [**rfcdiff**](https://tools.ietf.org/rfcdiff) | Web | Compare | Plain text | - | N/A |
| [**svgcheck**](https://github.com/ietf-tools/RfcEditor/tree/master/svgcheck) | Build, CLI, Web | Validate, Convert | SVG | SVG | Yes |
| [**xml2rfc**]() | Build, CLI, Web | Validate, Convert | RFCXML, RFCXML(old), Plain text | RFCXML Plain text, PDF, HTML, HTMLised, EPUB, nroff | Yes |
| [**xml2rfc-xxe**](https://github.com/wkumari/xml2rfc-xxe) | Editor | Validate, Insert | RFCXML(old) | RFCXML(old) | No |
| [**xym**](https://github.com/xym-tool/xym) | Build, CLI | Extract | RFCXML | YANG | Yes |
| YANG validator |
| yanglint |

## Status

| Tool | Author | Ownership | License | Maintained | Maintainer |
| :--- | :----- | :-------- | :------ | :--------- | :--------- |
| [**bibtext2rfc**](https://github.com/yaronf/bibtex2rfc) | Yaron Sheffer | Yaron Sheffer | Public domain | Yes | Yaron Sheffer |
| [**bibxml2md**](https://github.com/yaronf/bibxml2md) | Yaron Sheffer | Yaron Sheffer | Unknown | Unknown | Yaron Sheffer |
| [**bap**](https://github.com/ietf-tools/bap) | Bill Fenner | Bill Fenner | Unknown | No | None | 
| [**id2xml**]() | Henrik Levkowetz | IETF Trust | Simplified BSD | Unknown | Unknown |
| [**idnits**]() | Henrik Levkowetz | Henrik Levkowetz | GPL | Yes | Tools Team |
| [**idspell**]() | Henrik Levkowetz | Henrik Levkowetz | GPL | No | None |
| [**kramdown-rfc2629**](https://github.com/cabo/kramdown-rfc2629) | Carsten Bormann | Carsten Bormann | MIT | Yes | Carsten Bormann |
| [**lyx2rfc**](https://github.com/nicowilliams/lyx2rfc) | Nico Williams | Nico Williams | Unknown | No | None |
| [**metanorma-ietf**](https://github.com/metanorma/metanorma-ietf) | Ribose | Ribose | Simplified BSD | Yes | Ribose |
| [**mmark**](https://mmark.miek.nl) | Miek Gieben | Miek Gieben | Simplified BSD | Yes | Miek Gieben |
| [**nroff2xml**](https://github.com/tomaszmrugalski/nroff2xml) | Tomek Mrugalski | IETF Trust | Simplified BSD | No | None |
| [**pyang**](https://github.com/mbj4668/pyang) | Martin Bjorklund | Martin Bjorklund | ISC | Yes | Martin Bjorklund |
| [**rfcdiff**](https://tools.ietf.org/rfcdiff) | Henrik Levkowetz | Henrik Levkowetz | Unknown | Unknown | Unknown |
| [**svgcheck**](https://github.com/ietf-tools/RfcEditor/tree/master/svgcheck) | Jim Schaad | IETF Trust | Simplied BSD | Yes | Tools Team |
| [**xml2rfc**]() | Henrik Levkowetz | IETF Trust | Simplified BSD | Yes | Tools Team |
| [**xml2rfc-xxe**](https://github.com/wkumari/xml2rfc-xxe) | Warren Kumari | Warren Kumari | Unknown | No | None | 
| [**xym**](https://github.com/xym-tool/xym) | Multiple | Cisco Systems | Revised BSD | Yes | Einar Nilsen-Nygaard |
| YANG validator |
| yanglint |

