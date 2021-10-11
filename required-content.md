---
title: Required Content
description: 
published: true
date: 2021-08-19T10:35:51.639Z
tags: 
editor: markdown
dateCreated: 2021-08-16T23:20:42.916Z
---

Internet-Drafts and RFCs have certain required content. I-Ds should take the accrued knowledge on frequent and particularly important topics into consideration as early in their life cycle as possible.

If an Internet-Draft is prepared in XML, the tooling will ensure that required content is present, automatically provide selected boilerplate text, and handle the majority of formatting concerns. An Internet-Draft prepared as plain text requires more effort to ensure that the required content is present and in the right form.

As Internet-Drafts are inputs into what might eventually be published as RFCs, their content requirements are based on what is required in an RFC. Specifically, many of the documents defining these requirements are written in terms of RFCs and do not mention Internet-Drafts, but these requirements, with very few exceptions, apply to Internet-Drafts. See [RFC 7841](https://rfc-editor.org/info/rfc7841) for specific details.

* [ ] Ensure that the I-D correctly provides the following:
  * The date the document was generated.
  * A list of authors/editors and their affiliations.
  * The group that originated the I-D (if any).
  * The intended status of the document.
  * The set of RFCs this I-D intends to update or replace, if any.

These required elements are represented explicitly in XML source. The tools will automatically format the information when building a presentation format. The format required for these items in plaintext submissions is discussed in the [Format section](#format) below.

* [ ] Ensure that the I-D contains each of the following sections:
  * IPR-Related Notices
  * Abstract
  * Introduction
  * Security Considerations
  * IANA Considerations
  * References
  * Authors' Addresses

* [ ] If the document uses [BCP 14](https://www.rfc-editor.org/info/bcp14) normative language, ensure the unchanged boilerplate text from [BCP 14](https://www.rfc-editor.org/info/bcp14) is present in the I-D, and that [BCP 14](https://www.rfc-editor.org/info/bcp14) is normatively referenced.

Note that [BCP 14](https://www.rfc-editor.org/info/bcp14) is made up of both [RFC 2119](https://rfc-editor.org/info/rfc2119) and [RFC 8174](https://rfc-editor.org/info/rfc8174), and they must be cited as described in the latter document. Please use the boilerplate text *exactly* as specified in [RFC 8174](https://rfc-editor.org/info/rfc8174).

* [ ] If the I-D intends to obsolete or update existing RFCs, ensure there is a "Summary of Changes" section.

#### IPR-Related Notices 

[BCP 78](https://www.rfc-editor.org/info/bcp78) and [BCP 79](https://www.rfc-editor.org/info/bcp79) specify the IETF's Intellectual Property policies. Among them is a requirement to include certain standardized text in each Internet-Draft. This text is managed by the IAB, see the [current acceptable boilerplate texts](https://www.iab.org/documents/headers-boilerplate/) and the [fully expanded forms of the boilerplate texts](https://www.rfc-editor.org/materials/status-memos.txt).

Authors preparing XML submissions indicate which boilerplate text to use by providing one of a set of enumerated values to the `ipr` attribute of the `rfc` element in the XML source. The tooling generates the actual required text. See Appendix A.1  in [RFC 7991](https://rfc-editor.org/info/rfc7991) for the available `ipr` attribute values. The majority of IETF stream I-Ds indicate `trust200902` or `pre5378Trust200902`, as needed.

Authors preparing plaintext submissions must carefully reproduce the text most appropriate for their Internet-Draft.

Authors of IETF stream documents must not select boilerplate that prohibits publication as an RFC.

A standard Copyright Notice and Disclaimer must be included. This will be generated automatically for authors preparing XML submissions. Authors of plaintext submissions should refer to the [TLP Section 6](https://trustee.ietf.org/documents/trust-legal-provisions/) for the exact text to reproduce.

* [ ] Verify that one of the approved IPR boilerplate selections are indicated in XML submissions or exactly reproduced in plaintext submissions.

* [ ] Verify that the most appropriate IPR boilerplate for the I-D is indicated.

Any Internet-Draft submitted that does not select one of the required IPR boilerplate statements will be rejected. The IETF Secretariat cannot add a selection for the author.

##### Limiting Modifications and Derivative Works

If the submitter of a non-IETF stream I-D desires to eliminate the IETF's right to make modifications and derivative works of the I-D, one of two notices must be included after the IPR statement.

The first choice is used if the contributor intends for the I-D to be published as an RFC:

> This document may not be modified, and derivative works of it may not be created, except to format it for publication as an RFC or to translate it into languages other than English.

This will be automatically generated by the tools from XML source if the `ipr` attribute value `noModificationTrust200902` is selected.

The second choice is used when the contributor does not intend for the I-D to be published as an RFC:

> This document may not be modified, and derivative works of it may not be created, and it may not be published except as an Internet-Draft.

This will be automatically generated by the tools from XML source if the `ipr` attribute value `noDerivativesTrust200902` is selected.

These notices may not be used with any IETF Standards Track document or with most working group documents, except as discussed in [BCP 78](https://www.rfc-editor.org/info/bcp78), since the IETF must retain change control over its documents and the ability to augment, clarify, and enhance the original contribution in accordance with the IETF Standards Process.

The first choice may be appropriate when republishing standards produced by a standards body other than the IETF, industry consortia, or companies. These are typically published as Informational RFCs and do not require that change control be ceded to the IETF. Documents of this type convey information for the Internet community.

The second choice may be used on I-Ds that are intended to provide background information to educate and to facilitate discussions within IETF working groups but are not intended to be published as RFCs.

If you think that you, your company, or anyone else owns a patent or other Intellectual Property Rights (IPR) on the work described in the I-D, you should carefully read [BCP 79](https://www.rfc-editor.org/info/bcp79). The first notice required in an I-D, described earlier in this section, obligates you to send an IPR disclosure statement under certain circumstances. In particular, when preparing a document intended to be included in the IETF Stream, before submitting the I-D, discussing it with the working group chairs or Area Directors is advised.

#### Abstract

Every Internet-Draft must have an abstract. The abstract should provide a concise and comprehensive overview of the purpose and contents of the entire document. Its purpose is to give a technically knowledgeable reader a general overview of the function of the document, to decide whether reading it will be useful. In addition to its function in the document, the abstract is used as a summary in publication announcements and in the [online index of I-Ds](https://www.ietf.org/id/1id-abstracts.txt).

Composing a useful abstract is a nontrivial writing task. Often, a satisfactory abstract can be constructed in part from material from the introduction section, but a good abstract will be shorter, less detailed, and broader in scope than the introduction. Simply copying and pasting the first few paragraphs of the introduction is tempting, but it generally results in an abstract that is both incomplete and redundant. An abstract will typically be five to ten lines. An abstract of more than 20 lines or fewer than three lines is generally not acceptable.

* [ ] Ensure the Internet-Draft contains an appropriate abstract.

An abstract should be complete in itself, so it should not contain citations unless they are completely defined within the abstract. Abbreviations appearing in the abstract should generally be expanded in parentheses. There is a set of reasonable exceptions to this rule; for example, readers don't need to be reminded of what "IP" or "TCP" or "MIB" means. The RFC Editor maintains a [list of approved abbreviations](https://www.rfc-editor.org/materials/abbrev.expansion.txt) that do not need to be expanded. In the end, this is a judgment call, but please err on the side of explicitness.

* [ ] Verify that the abstract stands alone.
* [ ] Ensure abbreviations in the abstract are expanded as appropriate.
* [ ] If the I-D intends to obsolete or update a previous RFC, ensure the abstract says so explicitly.

The RFC Editor's [Style Guide](https://www.rfc-editor.org/styleguide/) includes further guidance about writing an abstract.

#### Introduction

* [ ] If the I-D intends to obsolete or update a previous RFC, ensure the Introduction briefly explains what is being updated and why.

#### Security Considerations

[RFC 3552](https://rfc-editor.org/info/rfc3552) describes current best practices about writing a Security Considerations section. This section is mandatory in all documents.

The text of this section must have a meaningful exploration of security issues raised by the proposal, which should include both risks and a description of solutions or workarounds. It is rare that technical work can legitimately make a claim like "This protocol introduces no security considerations," so it needs to be fairly obvious for that to be believable, or the document will be returned for further development. Procedural documents, however, more commonly can claim no added security risk.

Some other references that may be useful when crafting this section are:

* [Internet Security Glossary, Version 2](https://rfc-editor.org/info/rfc4949)
* [Guidelines for Specifying the Use of IPsec Version 2](https://rfc-editor.org/info/rfc5406)
* [Guidelines for Authors and Reviewers of MIB Documents](https://rfc-editor.org/info/rfc4181)
* [Security Guidelines for IETF MIB Modules](https://trac.ietf.org/trac/ops/wiki/mib-security)
* [YANG Security Considerations](https://trac.ietf.org/trac/ops/wiki/yang-security-guidelines)

* [ ] Verify that a meaningful Security Consideration section is present.

#### IANA Considerations

This section must be present to enumerate any actions IANA must take upon publication of the document as an RFC.

* [ ] Verify this section contains clear instructions if IANA is expected to create a new registry or modify rules for an existing registry.

* [ ] Verify this section contains clear instructions if the document requires IANA to assign or update values in an IANA registry before RFC publication.

* [ ] Check the existing IANA registry for registration policy rules and any requirements for specific requests for registration of protocol parameters. Individual RFCs have specific criteria and instructions that should be followed.

* [ ] If the registration policy is "Expert Review" or "Specification Required" and/or requires mailing list review, as soon as the requested parameter information is properly formed, consider initiating reviews with IANA or sending to the appropriate mailing list (where applicable; see the RFC for that the registry for instructions). If there are any questions about what type of approval is needed from the Designated Expert (for example, if the registration should be made immediately or only pre-reviewed before publication), please contact IANA.

* [ ] If registrations are needed early for registries with "Specification Required", "RFC Required", "IETF Review", or "Standards Action" policies, consider using the early allocation process defined in [RFC 7120](https://rfc-editor.org/info/rfc7120).

* [ ] Verify this section explicitly and clearly identifies any references to this document that should be added for any registrations and any that should replace existing references.

* [ ] If the document has considerable instructions for IANA actions, request an early review of the document by IANA.

* [ ] If there is no action for IANA, verify that this section explicitly says “This document has no IANA actions.” It is often helpful for the IANA Considerations section to remain in place upon publication as an RFC even if there are no actions.

For more specific guidelines regarding structure and content for writing IANA Considerations sections, please see [RFC 8126](https://rfc-editor.org/info/rfc8126) and the IANA [Protocol Registration Procedures](https://www.iana.org/help/protocol-registration).

#### Summary of Changes

As noted in the abstract and introduction sections above, the abstract and introduction must call out any RFCs an I-D intends to obsolete or update. There should also be a section providing greater detail about the motivation and changes.

* [ ] Ensure the I-D clearly summarizes any changes made from the RFCs being updated or obsoleted.

* [ ] Ensure any errata against RFCs that are being obsoleted or updated have been considered, and that the I-D clearly identifies those that have been addressed.

#### References

A references section must be present and split into normative and informative sections. For guidance, see the RFC Editor's [Style Guide](https://www.rfc-editor.org/styleguide/) and the [IESG Statement on Normative and Informative References](https://www.ietf.org/about/groups/iesg/statements/normative-informative-references/).

Normative and informative references to non-IETF documents are permitted. However, it is best to minimize such normative references, because assessing their status when the IETF document advances on the standards track is very difficult. It is important to use the exact title, author name(s), organization and publication date. External specifications referenced by Internet-Standard-level Technical Specifications or Applicability Statements must be to open external standards, per [RFC 2026](https://rfc-editor.org/info/rfc2026).

* [ ] Ensure all needed references are present and correctly identified as normative or informative.

* [ ] Verify that references are stable and resolvable.

A bare URI is not generally considered a stable reference. For web-only documents, adding a reference number, title , and/or an author will help make the reference more stable. See the RFC Editor's [Style Guide](https://www.rfc-editor.org/styleguide/) for specific guidance about URIs in Internet-Drafts. Judgment can be used here; the stability of normative references is even more important than the stability of informative references.

Also note that normative references to I-Ds will cause the referencing document to wait in the RFC Editor queue for the referenced I-Ds to be published as RFCs. They may in some cases become a [cluster of documents](https://www.rfc-editor.org/about/clusters/) that will be published as RFCs simultaneously.

#### Authors' Addresses

* [ ] Verify that the I-D contains a section giving the name and contact information (postal mail, phone, and/or email) for the authors.

Note that if the I-D is eventually published as an RFC, this information will not be changeable. When possible, provide contact information that is expected to be stable over time.

* [ ] Verify that there are no more than five authors or editors. If there is a need to list more, discuss the need with the relevant stream leadership as early in the process as possible. For the IETF stream, consult an Area Director.

Per [RFC 7322](https://rfc-editor.org/info/rfc7322):

> The total number of authors or editors on the first page is generally limited to five individuals and their affiliations.  If there is a request for more than five authors, the stream-approving body needs to consider if one or two editors should have primary responsibility for this document, with the other individuals listed in the Contributors or Acknowledgements section.  There must be a direct correlation of authors and editors in the document header and the Authors' Addresses section.  These are the individuals that must sign off on the document during the AUTH48 process and respond to inquiries, such as errata.