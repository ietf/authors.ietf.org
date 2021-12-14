---
title: Drafting in plaintext
description: 
published: true
date: 2021-12-14T23:32:41.442Z
tags: 
editor: markdown
dateCreated: 2021-12-10T00:25:37.371Z
---

Drafting in plaintext can be achieved with any text editor or word processor and so no toolchains are listed here.  It should be noted that drafting in plaintext, in comparison to a markup language, requires authors to manually handle multiple sections of content and ensure that the document conforms to many formatting rules.

Some of the tools listed in [Drafting in other markup languages](/drafting-in-other-markup-languages) output plaintext only and that plaintext may also need further work.

Plaintext I-Ds can be validated prior to submission as explained in [Document validation](/document-validation).

# General guidelines
The format constraints for a plaintext I-D are primarily the same as those for the text format of an RFC as specified in RFC 7994. One notable difference is that Internet-Drafts are paginated, and include running headers and footers. A few formatting requirements are highlighted here, but authors drafting plaintext documents should fully understand the requirements in RFC 7994, RFC 7841, RFC 7332, RFC 7322, the RFC Editor's [Style Guide](https://www.rfc-editor.org/styleguide/), and the current [acceptable boilerplate texts](https://www.iab.org/documents/headers-boilerplate/).

# Checklist

The following formatting requirements for plaintext I-Ds are often overlooked:

- [ ] Verify the required content:
  - [ ] Verify that the document name and version appears on the first page.
  - [ ] Verify that the I-D contains a "Table of Contents" section between the "Copyright Notice" and the introduction. This section must not be numbered.
  - [ ] Verify that the "Status of This Memo" and "Abstract" sections:
    - [ ] Contain the appropriate boilerplate text, reproduced exactly
    - [ ] Are not numbered.
    - [ ] The names of RFCs contained in these sections are not reformatted as references.
  - [ ] If the I-D has "Contributors" and/or "Acknowlegments" sections, verify that the sections are unnumbered and placed after the "References" section and any appendices.
  - [ ] Verify that references to Internet-Drafts and RFCs are formatted as shown in the "web portion" of the RFC Editor's Style Guide. Note that these formats can change over time, so review these links carefully with each document submission.
  - [ ] Verify that the I-D contains no footnotes.
- [ ] Verify the formatting:
  - [ ] Verify that no text extends beyond the 72nd column of a line. This limit is especially important for diagrams, which the RFC Editor may not be able to trivially reformat to fall within the margins.
  - [ ] Verify that source code does not extend beyond the 69th column.
  - [ ] Verify that the text is ragged-right.
  - [ ] Verify that hyphenation is not used for line breaks. However, hyphenated words (e.g., "Internet-Draft") may be split at the hyphen across successive lines.
  - [ ] Verify the characters in the I-D meet the requirements of RFC 7994. In brief:
    - [ ] The document must be UTF-8 encoded, but code points not corresponding to ASCII are allowed only in certain contexts (see RFC 7997). 
    - [ ] Control characters other than CR, NL, and FF are not allowed. 
    - [ ] The use of non-ASCII characters is limited to when there is a specific need, most notably for names. Many uses of non-ASCII characters will require listing the Unicode codepoint by number in addition to the character itself.
- [ ] Verify that the I-D is well formatted for readability and clarity.
