---
title: Required content
description: 
published: true
date: 2021-12-16T23:02:52.918Z
tags: 
editor: markdown
dateCreated: 2021-12-15T09:33:48.572Z
---

All Internet-Drafts must contain the following sections:
* [Abstract](#abstract)
* [Status of This Memo](#status-of-this-memo)
* [Copyright Notice](#copyright-notice)
* [Introduction](#introduction)
* [Security Considerations](#security-considerations)
* [IANA Considerations](#iana-considerations)
* [References](#references)
* [Authors' Addresses](#authors-addresses)

For each of these sections, please consult the [RFC Editor's Style Guide](https://www.rfc-editor.org/styleguide/) for further guidance.

# Abstract
Every Internet-Draft must have an abstract. The abstract should provide a concise and comprehensive overview of the purpose and contents of the entire document. Its purpose is to give a technically knowledgeable reader a general overview of the function of the document, to decide whether reading it will be useful. In addition to its function in the document, the abstract is used as a summary in publication announcements and in the online [index of I-Ds](https://www.ietf.org/id/1id-abstracts.txt).

Composing a useful abstract is a nontrivial writing task. Often, a satisfactory abstract can be constructed in part from material from the introduction section, but a good abstract will be shorter, less detailed, and broader in scope than the introduction. Simply copying and pasting the first few paragraphs of the introduction is tempting, but it generally results in an abstract that is both incomplete and redundant. An abstract will typically be around 50-150 words in length. An abstract that is much shorter or longer is generally not acceptable.

An abstract should be complete in itself, so it should not contain citations unless they are completely defined within the abstract. Abbreviations appearing in the abstract should follow the [Abbreviations](/language-and-style#abbreviations) guidelines.

Checklist:
- [x] Verify that the abstract stands alone.
- [x] Ensure abbreviations in the abstract are expanded as appropriate.
- [x] If the I-D intends to obsolete or update a previous RFC, ensure the abstract says so explicitly.

# Status of This Memo
The text of this section consists of two parts:

1. "Submission Compliance for Internet-Drafts" boilerplate as specified in section 6.a of the [Trust Legal Provisions (TLP) 5.0](https://trustee.ietf.org/documents/trust-legal-provisions/tlp-5/).
```
   This Internet-Draft is submitted in full conformance with the 
   provisions of BCP 78 and BCP 79.
```
2. Boilerplate explaining the status and usage of Internet-Drafts:
```
   Internet-Drafts are working documents of the Internet Engineering
   Task Force (IETF).  Note that other groups may also distribute
   working documents as Internet-Drafts.  The list of current Internet-
   Drafts is at https://datatracker.ietf.org/drafts/current/.

   Internet-Drafts are draft documents valid for a maximum of six months
   and may be updated, replaced, or obsoleted by other documents at any
   time.  It is inappropriate to use Internet-Drafts as reference
   material or to cite them other than as "work in progress."
```
3. A statement specifying the expiry date of the Internet-Draft.
```
This Internet-Draft will expire on DD MMMM YYYY.
```
This section is automatically generated for authors who submit their I-D in RFCXML.  Authors of plaintext I-Ds must reproduce the text exactly.

# Copyright Notice
Authors who submit their I-D in RFCXML must indicate which IPR text to use by providing one of a set of enumerated values to the **ipr** attribute of the [**\<rfc\>**](https://authors.ietf.org/en/rfcxml-vocabulary#rfc) element, and the tooling generates the actual required text. Authors preparing plaintext submissions must carefully reproduce the text from TLP Section 6 that is most appropriate for their Internet-Draft.

The majority of IETF stream I-Ds specify one of the following values for the **ipr** attribute:

* "trust200902" generates a notice from the text of section 6.b of the [TLP](https://trustee.ietf.org/documents/trust-legal-provisions/tlp-5/).

* "pre5378Trust200902" generates a notice from the text of sections 6.b and 6.c.iii of the [TLP](https://trustee.ietf.org/documents/trust-legal-provisions/tlp-5/).  See the [TLP Modification of February 15, 2009](https://trustee.ietf.org/about/faq/#tlp-mod) section of the Trust FAQ for more information on when to use this value.

Additional values of the **ipr** attribute are available that generate notices that limit modifications and derivative rights. These notices may not be used with any IETF Standards Track document or with most working group documents, except as discussed in BCP 78, since the IETF must retain change control over its documents and the ability to augment, clarify, and enhance the original contribution in accordance with the IETF Standards Process.

* "noModificationTrust200902" generates a notice from the text of sections 6.b and 6.c.i of the [TLP](https://trustee.ietf.org/documents/trust-legal-provisions/tlp-5/).  This choice may be appropriate when republishing standards produced by a standards body other than the IETF, industry consortia, or companies. These are typically published as Informational RFCs and do not require that change control be ceded to the IETF. Documents of this type convey information for the Internet community.

* "noDerivativesTrust200902" generates a notice from the text of sections 6.b and 6.c.ii of the [TLP](https://trustee.ietf.org/documents/trust-legal-provisions/tlp-5/).  This choice may be used on I-Ds that are intended to provide background information to educate and to facilitate discussions within IETF working groups but are not intended to be published as RFCs.

Any Internet-Draft submitted that does not include one of the required IPR boilerplate notices will be rejected. The IETF Secretariat cannot add this for the author.

Checklist:
- [x] Verify that one of the approved IPR boilerplate selections are indicated in RFCXML submissions or exactly reproduced in plaintext submissions.
- [x] Verify that the most appropriate IPR boilerplate for the I-D is indicated.

> If you think that you, your company, or anyone else owns a patent or other Intellectual Property Rights (IPR) on the work described in the I-D, you should carefully read BCP 79. The first notice required in an I-D, described earlier in this section, obligates you to send an IPR disclosure statement under certain circumstances. In particular, when preparing a document intended to be included in the IETF Stream, before submitting the I-D, discussing it with the working group chairs or Area Directors is advised.
{.is-info}

# Introduction
Your I-D must include an Introduction section that (among other things) explains the motivation for the I-D and (if appropriate) describes the applicability of the document, e.g., whether it specifies a protocol, provides a discussion of some problem, is simply of interest to the Internet community, or provides a status report on some activity.  The Introduction must call out any RFCs an I-D intends to obsolete or update  This may result in some duplication of text between the Abstract and the Introduction; this is acceptable.

Checklist:
- [ ] If the I-D intends to obsolete or update a previous RFC, ensure the Introduction briefly explains what is being updated and why.

# Summary of Changes
As noted in the [Abstract](#abstract) and [Introduction](#introduction) sections above, the Abstract and Introduction must call out any RFCs an I-D intends to obsolete or update. There should also be a section providing greater detail about the motivation and changes.

Checklist:
- [ ] Ensure the I-D clearly summarizes any changes made from the RFCs being updated or obsoleted.
- [ ] Ensure any errata against RFCs that are being obsoleted or updated have been considered, and that the I-D clearly identifies those that have been addressed.

# Security Considerations
RFC 3552 describes current best practices about writing a Security Considerations section. This section is mandatory in all documents.

The text of this section must have a meaningful exploration of security issues raised by the proposal, which should include both risks and a description of solutions or workarounds. It is rare that technical work can legitimately make a claim like "This protocol introduces no security considerations," so it needs to be fairly obvious for that to be believable, or the document will be returned for further development. Procedural documents, however, more commonly can claim no added security risk.

Some other references that may be useful when crafting this section are:

* [Pervasive Monitoring Is an Attack](https://rfc-editor.org/info/rfc7258)
* [Internet Security Glossary, Version 2](https://rfc-editor.org/info/rfc4949)
* [Guidelines for Specifying the Use of IPsec Version 2](https://rfc-editor.org/info/rfc5406)
* [Guidelines for Authors and Reviewers of MIB Documents](https://rfc-editor.org/info/rfc4181)
* [Security Guidelines for IETF MIB Modules](https://trac.ietf.org/trac/ops/wiki/mib-security)
* [YANG Security Considerations](https://trac.ietf.org/trac/ops/wiki/yang-security-guidelines)

Checklist:
- [x] Verify that a meaningful Security Consideration section is present.

# IANA Considerations

The [Internet Assigned Numbers Authority](https://www.iana.org/) (IANA) provides global coordination of the DNS root, IP addressing, and many other Internet protocol resources for the IETF. The "IANA Considerations" section must be present in a document and enumerate any actions IANA must take upon publication of the document as an RFC.

For more specific guidelines regarding structure and content for writing IANA Considerations sections, please see RFC 8126 and the IANA [Protocol Registration Procedures](https://www.iana.org/help/protocol-registration).

Checklist:
- [x] Verify this section contains clear instructions if IANA is expected to create a new registry or modify rules for an existing registry.
- [x] Verify this section contains clear instructions if the document requires IANA to assign or update values in an IANA registry before RFC publication.
- [x] Check the existing IANA registry for registration policy rules and any requirements for specific requests for registration of protocol parameters. Individual RFCs have specific criteria and instructions that should be followed.
- [x] If the registration policy is "Expert Review" or "Specification Required" and/or requires mailing list review, as soon as the requested parameter information is properly formed, consider initiating reviews with IANA or sending to the appropriate mailing list (where applicable; see the RFC for that the registry for instructions). If there are any questions about what type of approval is needed from the Designated Expert (for example, if the registration should be made immediately or only pre-reviewed before publication), please contact IANA.
- [x] If registrations are needed early for registries with "Specification Required", "RFC Required", "IETF Review", or "Standards Action" policies, consider using the early allocation process defined in RFC 7120.
- [x] Verify this section explicitly and clearly identifies any references to this document that should be added for any registrations and any that should replace existing references.
- [x] If the document has considerable instructions for IANA actions, request an early review of the document by IANA.
- [x] If there is no action for IANA, verify that this section explicitly says “This document has no IANA actions.” It is often helpful for the IANA Considerations section to remain in place upon publication as an RFC even if there are no actions.

# References
A references section must be present and split into normative and informative sections. The IESG has a [Statement on Normative and Informative References](https://www.ietf.org/about/groups/iesg/statements/normative-informative-references/).

Normative and informative references to non-IETF documents are permitted. However, it is best to minimize such normative references, because assessing their status when the IETF document advances on the standards track is very difficult. It is important to use the exact title, author name(s), organization and publication date. External specifications referenced by Internet-Standard-level Technical Specifications or Applicability Statements must be to open external standards, per RFC 2026.

A bare URI is not generally considered a stable reference. For web-only documents, adding a reference number, title , and/or an author will help make the reference more stable. See the RFC Editor's [Style Guide](https://www.rfc-editor.org/styleguide/) for specific guidance about URIs in Internet-Drafts. Judgment can be used here; the stability of normative references is even more important than the stability of informative references.

Also note that normative references to I-Ds will cause the referencing document to wait in the RFC Editor queue for the referenced I-Ds to be published as RFCs. They may in some cases become a [cluster of documents](https://www.rfc-editor.org/about/clusters/) that will be published as RFCs simultaneously.

Checklist:
- [x] Ensure all needed references are present and correctly identified as normative or informative.
- [x] Verify that references are stable and resolvable.

# Authors' Addresses
Note that if the I-D is eventually published as an RFC, this information will not be changeable. When possible, provide contact information that is expected to be stable over time.

Per RFC 7322:

> The total number of authors or editors on the first page is generally limited to five individuals and their affiliations. If there is a request for more than five authors, the stream-approving body needs to consider if one or two editors should have primary responsibility for this document, with the other individuals listed in the Contributors or Acknowledgements section. There must be a direct correlation of authors and editors in the document header and the Authors' Addresses section. These are the individuals that must sign off on the document during the AUTH48 process and respond to inquiries, such as errata.

Checklist:
- [x] Verify that the I-D contains a section giving the name and contact information (postal mail, phone, and/or email) for the authors.
- [x] Verify that there are no more than five authors or editors. If there is a need to list more, discuss the need with the relevant stream leadership as early in the process as possible. For the IETF stream, consult an Area Director.
