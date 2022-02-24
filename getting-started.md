---
title: Getting started
description: 
published: true
date: 2022-02-24T00:42:27.958Z
tags: 
editor: markdown
dateCreated: 2021-08-17T23:57:12.813Z
---

# Quick start guide
If you want to get authoring straight away then these quick start guides should be enough.  For a more thorough guide to getting started please read the overview and the guide to choosing tools below.

Quick start for RFCXML:
1. Clone or download the [RFCXML template repository](https://github.com/ietf-authors/rfcxml-templates-and-schemas).
1. Edit the Standard (or Annotated) template with your choice of [XML toolchain](/drafting-in-xml).

Quick start for Markdown:
1. Start with an existing Markdown I-D or [template](/templates-and-schemas#templates-1). **Note**, your choice of template will determine which flavour of Markdown you will be authoring in.
1. Edit the template with your choice of text editor.

Next steps for both:
1. If you require automated builds then consider the [Github workflow](https://github.com/martinthomson/i-d-template/blob/main/doc/TEMPLATE.md).
1. Process your edited I-D using the [IETF Author Tools web service](https://author-tools.ietf.org).
1. When it is ready for publishing, [submit it](https://authors.ietf.org/en/submitting-your-internet-draft) to the IETF I-D repository and then share the IETF Datatracker link to your I-D and gather feedback.


# Overview of the authoring process
The diagram below deconstructs the authoring process into stages and shows the different formats supported at each stage:

```mermaid
graph TD  
  A("Initial drafting<br/>(Any format)") --> B("Collaborative editing<br/>(Any format)")
  A -.-> D
  B -.-> D
  B -- Optional --> C("Document validation<br/>(RFCXML or plaintext only)")
  C -.-> D([Rendered output])
  C --> E("Datatracker submission with document validation<br/>(RFCXML or plaintext only)")
  E -.-> D
  B -- Required --> E
  E --> F("RFC Pre-publication review<br/>(RFCXML only)")
  F --> G([RFC Publication])
```

- **Initial drafting** 
At this stage, before you adopt a format/tool we recommend reading through all the stages below before you make a decision. New authors often report that they used a format and tool recommended by a fellow author and then later had to put in significant effort to convert it into something they could use more productively. 

- **Collaborative editing**
It is common for a group of authors to work on an I-D and so it is important to consider if all of your co-authors can work with your chosen format and have access to and familiarity with the same tools. Additionally, you need to consider if your I-Ds will be worked on using an integrated issue tracker and source control system such as GitHub.  For more details see [Collaborative editing](/collaborative-editing).

- **Document validation** 
Validation is an important step for a document to ensure that it is correctly formatted and for it to successfully pass the next steps of submission as an Internet-Draft or output rendering.  For more details, see [Document validation](/document-validation).

- **Rendered output**
It is common for authors to render their documents into a easily read format such as PDF, HTML or plaintext.  For more details see [Rendering and converting](/rendering-and-converting).

- **Datatracker submission with document validation**
When you are ready to share your I-D you need to submit it to the Datatracker at which point it will be automatically validated.  Datatracker only accepts I-Ds in RFCXML or plaintext format.  For more details see [Submitting your Internet-Draft](/submitting-your-internet-draft).

- **RFC Pre-publication review**
If your document is chosen to become an RFC (each [RFC Stream](https://rfc-editor.org/info/rfc8729) has a different process for this) then it will need to go through the [AUTH48 pre-publication review process](https://www.rfc-editor.org/pubprocess/auth48/). At this stage you will need to work with RFCXML to address any issues raised by the editors in order for the RFC to be published.

- **RFC Publication**
The canonical format for published RFCs is RFCXML and the other published formats, PDF, HTML and plain text, are derived from this RFCXML. The published RFCXML looks quite different from Internet-Draft RFCXML as it has been passed through the 'prep' tool which makes it work better as a standalone document. 

# Choosing your format and tools

Writing Internet-Drafts is complex and time consuming and careful choice of authoring format and authoring tools can make this task much easier. Your choice of format and tools is likely to depend on what markup languages and document editing tools you are familiar with, and how you intend to work.  Your options are:
1. **RFCXML**.  This is the most popular choice as RFCXML is the markup language used for published RFCs and can be used end-to-end throughout the authoring process. However, RFCXML is also the most complex and best suits an author or group of co-authors who are very familiar with XML and who all have access to XML editing tools.  See [Drafting in XML](/drafting-in-xml) for more details.
1. **Markdown**.  This is the next most popular choice as Markdown is a simplified text markup language, used with one of the tools that converts Markdown to RFCXML.  See [Drafting in Markdown](/drafting-in-markdown) for more details.
1. **Other markup languages**.  If you are very familiar with one of the less well known text markup languages and their normal editors, for example LaTeX, nroff or Org Mode in Emacs, then this may be a good choice for you.  A number of these markup languages are supported by tools that can convert your text to either RFCXML or plaintext I-D format, though they may not be as well maintained or fully featured as the Markdown tools.  See [Drafting in other markup languages](/drafting-in-other-markup-languages) for more details.
1. **Plain text**.  Plaintext documents are still accepted for I-Ds submission some people either directly create plaintext documents in a text editor, or author in a markup language and generating the plaintext from that.  Drafting in plaintext requires the author to manually provide lots of content that is automatically generated when using a markup language.
  1.  **Word processors**.  Finally, there are a couple of tools that support word processors such as Microsoft Word, converting their output to RFCXML. See [Drafting in word processors](/drafting-in-word-processors) for more details.


