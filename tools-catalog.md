---
title: Tools catalog
description: 
published: true
date: 2021-11-12T11:44:35.800Z
tags: 
editor: markdown
dateCreated: 2021-08-17T00:37:22.495Z
---

# Classification of tools
## Modes
The tools generally support one or more of the following modes of operation:

- Interactive **Editor** 
- Command Line Interface (**CLI**).  Where the author installs the tools locally and then runs them on local files from the command line, one operation at a time.
- Automated **Build** process. Where the author(s) installs the tools into a build manager that then runs a sequence of tools on a source target.  This allows for a continuous integrated build process much as software developers use when building code. 
- **Web** service. This can be broken down into two sub-modes:
    - Where the author uses an interactive web page that in turns calls a remote web service, on individual local files generally one operation at the time.
    - Where the author(s) configures their build service to use a remote web service via an API instead of installing the tools. 

## Operations
The tools generally provide one of more of the following broad operations:

-  **Convert** the document from one format to another such as from XML to PDF.
-  **Validate** that the format/structure of the document source conforms to the format/structure rules for an I-D/RFC.
-  **Extract** part of the document. For example, extracting a code module such as YANG, MIB or ABNF and passing it to a separate validator. 
-  **Insert** new text into an I-D. This may be boilerplate, references, new sections or other custom text.
-  **Compare** two different I-Ds or two versions of an I-D.
-  Supports an interactive **Editor** with features such as auto-completion.

## Formats
The formats that we are aware of tools supporting include: AsciiDoc, DOCX, EPUB, LaTeX, Markdown, nroff, Org Mode, PDF, Plain Text, RFC XML v2, RFC XML v3

# Feature matrix
# Tables {.tabset}
## Basic

| Tool | Description |
| :--- | :---------- |
| bibtext2rfc |
| **bibxml2md** | Converts bibxml references into markdown | 
| Bill's ABNF parser |
| id2xml |
| idnits |
| idspell |
| kramdown-rfc2629 |
| lyx2rfc |
| metanorma-ietf |
| **nroff2xml** | Converts nroff I-D sources into xml2rfc format (xml) | 
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

## Features

| Tool | Modes | Operations | Input formats | Output formats |
| :--- | :---- | :------------ | :------------ | :------------- |
| bibtext2rfc |
| **bibxml2md** | Build, CLI | Convert | BibXML | XML |
| Bill's ABNF parser |
| id2xml |
| idnits |
| idspell |
| kramdown-rfc2629 |
| lyx2rfc |
| metanorma-ietf |
| **nroff2xml** | Build, CLI | Convert | nroff | XML |
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

| Tool | Author | Ownership | License | Repository | Maintained | Maintainer |
| :--- | :----- | :-------- | :------ | :--------- | :--------- | :--------- |
| bibtext2rfc |
| **bibxml2md** | Yaron Sheffer | None | None | [GitHub](https://github.com/yaronf/bibxml2md) | Yes | Yaron Sheffer |
| Bill's ABNF parser |
| id2xml |
| idnits |
| idspell |
| kramdown-rfc2629 |
| lyx2rfc |
| metanorma-ietf |
| **nroff2xml** | Tomek Mrugalski | IETF Trust | Simplified BSD | [GitHub](https://github.com/tomaszmrugalski/nroff2xml) | No | None |
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

