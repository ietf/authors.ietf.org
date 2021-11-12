---
title: Tools catalog
description: 
published: true
date: 2021-11-12T14:20:02.268Z
tags: 
editor: markdown
dateCreated: 2021-08-17T00:37:22.495Z
---

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
| idnits |
| idspell |
| kramdown-rfc2629 |
| lyx2rfc |
| metanorma-ietf |
| [**nroff2xml**](https://github.com/tomaszmrugalski/nroff2xml) | Converts nroff I-D sources into xml2rfc format (xml) |
| pyang | |
| rfcdiff | |
| SMICng | |
| smilint | |
| svgcheck | |
| xml2rfc | |
| xml2rfc-xxe | |
| xym | |
| YANG validator |
| yanglint | |

## Feature classification

| Tool | Modes | Operations | Input formats | Output formats | Supports v3 |
| :--- | :---- | :--------- | :------------ | :------------- | :---------: |
| [**bibtext2rfc**](https://github.com/yaronf/bibtex2rfc) | Build, CLI | Convert | BibTex | BibXML | Yes |
| [**bibxml2md**](https://github.com/yaronf/bibxml2md) | Build, CLI | Convert | BibXML | RFCXML(old) | No |
| [**bap**](https://github.com/ietf-tools/bap) | Build, CLI | Validate | ABNF | n/a | n/a |
| [**id2xml**]() | Build, CLI | Convert | Plain text | RFCXML | Yes |
| idnits |
| idspell |
| kramdown-rfc2629 |
| lyx2rfc |
| metanorma-ietf |
| [**nroff2xml**](https://github.com/tomaszmrugalski/nroff2xml) | Build, CLI | Convert | nroff | RFCXML(old) | No |
| pyang |
| rfcdiff |
| SMICng |
| smilint |
| svgcheck |
| xml2rfc |
| xml2rfc-xxe |
| xym |
| YANG validator |
| yanglint |

## Status

| Tool | Author | Ownership | License | Maintained | Maintainer |
| :--- | :----- | :-------- | :------ | :--------- | :--------- |
| [**bibtext2rfc**](https://github.com/yaronf/bibtex2rfc) | Yaron Sheffer | Yaron Sheffer | Public domain | Yes | Yaron Sheffer |
| [**bibxml2md**](https://github.com/yaronf/bibxml2md) | Yaron Sheffer | Yaron Sheffer | Unknown | Unsure | Yaron Sheffer |
| [**bap**](https://github.com/ietf-tools/bap) | Bill Fenner | Bill Fenner | Unknown | No | None | 
| [**id2xml**]() | Henrik Levkowetz | IETF Trust | Simplified BSD | Unknown | Unknown |
| idnits |
| idspell |
| kramdown-rfc2629 |
| lyx2rfc |
| metanorma-ietf |
| [**nroff2xml**](https://github.com/tomaszmrugalski/nroff2xml) | Tomek Mrugalski | IETF Trust | Simplified BSD | No | None |
| pyang |
| rfcdiff |
| SMICng |
| smilint |
| svgcheck |
| xml2rfc |
| xml2rfc-xxe | | | | 
| xym |
| YANG validator |
| yanglint |

