---
title: I-D author guidelines
description: 
published: true
date: 2021-08-24T04:14:15.156Z
tags: 
editor: markdown
dateCreated: 2021-08-24T04:14:11.973Z
---

# Guidelines to Authors of Internet-Drafts

## Table of Contents

* [Introduction](#introduction)
* [Background](#background)
* [Internet-Draft Names](#internet-draft-names)
* [The Submission Process](#the-submission-process)
* [Content](#content)
  * [Required Content](#required-content)
  * [Content Considerations](#content-considerations)
* [Format](#format)
* [Acknowledgement](#acknowledgement)

## Introduction

Internet-Drafts (I-Ds) are the basic work items of the IETF. They are the
primary inputs into what may eventually be published as a Request for Comment
(RFC).

Internet-Drafts are used by all of the [RFC
Streams](https://rfc-editor.org/info/rfc8729). The guidance in this document
applies to all streams unless it is identified as specific to a particular
stream.

Internet-Drafts are prepared by people acting in possibly several roles, such
as an author or an editor. This guidance uses the term "author", but the
guidance applies to people acting in any role.

This document collects and summarizes requirements and guidance from
many sources. The following resources should be consulted
for definitive details:

* The IETF Standards Process is described in [RFC
  2026](https://rfc-editor.org/info/rfc2026).
* The IETF rules concerning copyright are described in [BCP
  78](https://www.rfc-editor.org/info/bcp78).
* The IETF rules on IPR are described in [BCP
  79](https://www.rfc-editor.org/info/bcp79).
* The IETF [Trust Legal Provisions Relating to IETF
  Documents](https://trustee.ietf.org/documents/trust-legal-provisions/), called
  "the TLP" for short, provides many details about copyright policy and
  practice.

Much of the guidance in this document is in the form of something that can be
inspected, or checked, to see whether changes should be made before submitting
an I-D. These items are marked with checkboxes ([ ]). However, authors are
expected to be familiar with and to apply the full guidance in this document.

There are tools to help with the creation of Internet-Drafts. Rather than
attempting to construct a plaintext Internet-Draft manually, it is highly
recommended using a structured language for authoring, and a toolchain like
[xml2rfc](https://pypi.org/project/xml2rfc/) or
[kramdown-rfc2629](https://github.com/cabo/kramdown-rfc2629) to build a
submission.

An [online converter](https://xml2rfc.tools.ietf.org/experimental.html) for
documents in the [xml2rfc](https://pypi.org/project/xml2rfc/) or
[kramdown-rfc2629](https://github.com/cabo/kramdown-rfc2629) input formats is
available. Authors working with the xml2rfc XML source format should be familiar
with [the XML grammar](https://rfc-editor.org/info/rfc7991) [that the xml2rfc
tool currently accepts](https://xml2rfc.tools.ietf.org/xml2rfc-doc.html), and
the [RFC Editor's FAQ on using the v3 XML
format](https://www.rfc-editor.org/materials/FAQ-xml2rfcv3.html).

As Internet-Drafts may be eventually published as RFCs, it is recommended to
consult the [RFC Editor's publication
process](https://www.rfc-editor.org/pubprocess/).

## Background

All versions of Internet-Drafts are kept in the [Internet-Draft
Archive](https://www.ietf.org/archive/id). Active versions of Internet-Drafts
are also placed in the [Internet-Draft Repository](https://www.ietf.org/id).

Versions of Internet-Drafts are removed from the Repository when any of the
following occur:

* The I-D is updated with a new version.
* The I-D is replaced by another Internet-Draft.
* The I-D is published as an RFC.
* The I-D expires.

An I-D expires 185 days after it was placed in the Repository, unless it
is in a state that prevents it from expiring. Examples of such states include
being processed by the IESG for publication in the IETF stream, or being under
review by the Independent Series Editor (ISE) for publication in the
[Independent Submission Stream](https://www.rfc-editor.org/about/independent/).

Internet-Drafts are not removed from the Archive when they are removed from the
Repository. Removing an I-D from the Archive occurs only in exceptional
circumstances, described in [this IESG
Statement](https://www.ietf.org/about/groups/iesg/statements/internet-draft-removal/).

Even though Internet-Drafts are kept in the Archive, they are not an archival
series and should not be cited or quoted as anything other than "work in
progress".

## Internet-Draft Names

Internet-Draft names appear inside the I-D, and are used as components of
filenames for the various formats the I-D may appear in. The characters
that may appear in an I-D name are restricted:

* [ ] Ensure that the I-D name consists only of
  * the lowercase letters `a-z`,
  * the digits `0-9`,
  * or hyphens (`-`).

The name of an I-D consists of several components, separated by a hyphen.
No empty components are allowed. That is, consecutive hyphens may not appear
in an I-D name.

The first component identifies the I-D as a draft (as opposed to other
document types, such as a charter or a review).

* [ ] Verify that the I-D name begins with `draft-`.

The second component identifies the source of an I-D. If an I-D has
been adopted into any stream other than the Independent Submission Stream,
this component will identify the stream.

If the I-D has not been adopted into any stream or if it is being considered for
publication in the Independent Submission Stream, the second component should
consist of a string related to the names(s) of the author(s). There are no
mechanical rules for this string beyond consisting only of the allowed
characters. However, objectionable or misleading strings are subject to change
or removal. The string is typically the last name of the lead author or editor.

The second component must not be easily confused with a group acronym. The
following strings for the second component are reserved for their respective
organizations (some of which are historic):

* `iana`
* `iaoc`
* `iesg`
* `ietf-trust`
* `rfc-editor`

The second component should not contain a hyphen. Legacy uses and edge cases
such as hyphenated last names are allowed. Having a hyphen in the second
component makes it hard to extract programmatically. This forces many tools
to use heuristics when tying to locate the second component.

* [ ] Ensure the second component reasonably identifies the source of the I-D.

* [ ] If the I-D has been adopted by a stream, ensure the second component is:
  * `ietf` for the IETF stream
  * `irtf` for the IRTF stream
  * `iab` for the IAB stream

Otherwise, ensure that the second component is not a group acronym or a
reserved string, is not objectionable, and does not introduce confusion.

Note that any I-D submitted with one of these stream identifiers in the second
component that has not been adopted by the indicated stream will either be
rejected or replaced.

If the I-D is targeted at or has been adopted by a group, the group's acronym
should be added to the name just after the second component, separated by a
hyphen.

* [ ] Ensure an adopted or group-targeted I-D identifies the group just after
  the second component by including the group's acronym.

Note again that if the I-D has not been adopted into a stream, and it identifies
a stream in the second component, it will be rejected or replaced. In particular
for IETF stream documents, the first version of an I-D with a name that begins
with `draft-ietf-acronym-` for any working group acronym must be approved by the
working group's chairs before it will be posted.

The remainder of the name describes the purpose of the I-D, usually in just a
few words. Each word is separated by a hyphen.

* [ ] Ensure the name reasonably reflects the purpose of the I-D.

Internet-Drafts are versioned with two digits, separated from the name with a
hyphen. The initial version of an I-D must be `00`, and subsequent updates must
increment the version number by one.

If the I-D is submitted as XML (which is highly recommended), the name and
version of the document will be declared in the appropriate ["name" and
"version" attributes](https://rfc-editor.org/info/rfc7991), and the filename
submitted must be of the form `name-version.xml`.

If the I-D is submitted as plain text (which is not recommended), the name and
version will appear on the document's first page, and the filename submitted
must be of the form `name-version.txt`.

Convention dictates that an individual submission seeking adoption by a
working group will include the working group's acronym just after the
second component. For example, a person or group identified as "foo"
seeking to get a document about "specific-subject" adopted by the "bar"
working group might choose the name `draft-foo-bar-specific-subject`, and
submit the file `draft-foo-bar-specific-subject-00.xml`. If the document is
later adopted by the working group, the authors will usually create a new
I-D named `draft-ietf-bar-specific-subject` and submit it as
`draft-ietf-bar-specific-subject-00.xml`. Note that the version number of
this new I-D will always be `00`.

## The Submission Process

Internet-Draft submissions are made using the [IETF Datatracker's submission
tool](https://datatracker.ietf.org/submit). An I-D submission should preferably
be an [xml2rfc version 3](https://rfc-editor.org/info/rfc7991) XML source file,
but a [version 2 source](https://rfc-editor.org/info/rfc7749) will be accepted.
If an XML source is not available, a plaintext submission will be accepted.

Currently, the submission tool will accept both an XML and plaintext
submission, as well as PDF and PostScript versions of the document. In such
submissions, the XML is authoritative, if present, otherwise the plain text is
authoritative. It is expected that the tool will change to allow only the
submission of XML or plain text, but not both, and to not accept other formats.

**In short: submit XML if at all possible, with v3 preferred over v2.**

If XML source is submitted, the Datatracker will generate a plain text version
of the I-D and place it in the Archive. If v3 source is submitted, the
Datatracker will also generate an HTML version and place it in the Archive.

When a submission is made through the submission tool, the authors will
receive email with a request to verify the submission. The submission will
not be accepted and posted until the action requested in that email is
performed. If the submitter is logged into the Datatracker and listed as
an author this step is bypassed.

If the I-D being submitted replaces another I-D (such as in the earlier
example discussing creating a new I-D when a working group adopts a
document), the submitter will be able to identify the replacement using
the submission tool. A group chair or the IETF Secretariat will verify
the replacement before the relationship is added to the Datatracker.

The submission tool will double-check many, but not all, of the guidance points
called out in this document. Authors are expected to have manually applied the
guidance before submission.

While many of the requirements highlighted by this document are for RFCs,
Internet-Drafts are expected to adhere to them to the extent possible. In
particular, IETF stream I-Ds submitted to the IESG must follow all of the
guidance. Working groups are encouraged to require the guidance be followed for
I-Ds entering Working Group Last Call. I-Ds will progress through the review
and publication process more efficiently the earlier the guidance is followed
in the I-D.

### Manual Submissions

If authors are unable to submit an I-D through the Datatracker, they may make a
manual-post request by sending the I-D via email to support@ietf.org. The
message may contain the I-D as an attachment, or a URL that will resolve to the
I-D. The I-D must be a standalone document in either XML or plaintext format.
Multiple files presented in containers such as zip or tar will not be accepted.
All other formats will be discarded without opening.

Be aware of the deadlines for submitting I-Ds before each IETF Meeting. The
[important dates page](https://datatracker.ietf.org/meeting/important-dates)
will show the deadline for submitting I-Ds. Some meetings may have an earlier
deadline for initial versions of I-Ds than for updates to existing I-Ds. After
the deadlines, submissions will not be accepted until the meeting begins. The
leadership responsible for each stream can override this submission blackout
period when appropriate. Care should be taken when submitting an I-D near the
deadline, especially if a manual post is requested. The steps to confirm and
post the submission take time.

## Content

Internet-Drafts and RFCs have certain required content. I-Ds should take the
accrued knowledge on frequent and particularly important topics into
consideration as early in their life cycle as possible.

### Required Content

If an Internet-Draft is prepared in XML, the tooling will ensure that
required content is present, automatically provide selected boilerplate
text, and handle the majority of formatting concerns. An Internet-Draft
prepared as plain text requires more effort to ensure that the required
content is present and in the right form.

As Internet-Drafts are inputs into what might eventually be published as RFCs,
their content requirements are based on what is required in an RFC.
Specifically, many of the documents defining these requirements are written in
terms of RFCs and do not mention Internet-Drafts, but these requirements, with
very few exceptions, apply to Internet-Drafts. See [RFC
7841](https://rfc-editor.org/info/rfc7841) for specific details.

* [ ] Ensure that the I-D correctly provides the following:
  * The date the document was generated.
  * A list of authors/editors and their affiliations.
  * The group that originated the I-D (if any).
  * The intended status of the document.
  * The set of RFCs this I-D intends to update or replace, if any.

These required elements are represented explicitly in XML source. The tools
will automatically format the information when building a presentation format.
The format required for these items in plaintext submissions is discussed
in the [Format section](#format) below.

* [ ] Ensure that the I-D contains each of the following sections:
  * IPR-Related Notices
  * Abstract
  * Introduction
  * Security Considerations
  * IANA Considerations
  * References
  * Authors' Addresses

* [ ] If the document uses [BCP 14](https://www.rfc-editor.org/info/bcp14)
  normative language, ensure the unchanged boilerplate text from [BCP
  14](https://www.rfc-editor.org/info/bcp14) is present in the I-D, and that
  [BCP 14](https://www.rfc-editor.org/info/bcp14) is normatively referenced.

Note that [BCP 14](https://www.rfc-editor.org/info/bcp14) is made up of both
[RFC 2119](https://rfc-editor.org/info/rfc2119) and [RFC
8174](https://rfc-editor.org/info/rfc8174), and they must be cited as described
in the latter document. Please use the boilerplate text *exactly* as specified
in [RFC 8174](https://rfc-editor.org/info/rfc8174).

* [ ] If the I-D intends to obsolete or update existing RFCs, ensure there
      is a "Summary of Changes" section.

#### IPR-Related Notices 

[BCP 78](https://www.rfc-editor.org/info/bcp78) and [BCP
79](https://www.rfc-editor.org/info/bcp79) specify the IETF's Intellectual
Property policies. Among them is a requirement to include certain standardized
text in each Internet-Draft. This text is managed by the IAB, see the [current
acceptable boilerplate
texts](https://www.iab.org/documents/headers-boilerplate/) and the [fully
expanded forms of the boilerplate
texts](https://www.rfc-editor.org/materials/status-memos.txt).

Authors preparing XML submissions indicate which boilerplate text to use by
providing one of a set of enumerated values to the `ipr` attribute of the `rfc`
element in the XML source. The tooling generates the actual required text. See
Appendix A.1  in [RFC 7991](https://rfc-editor.org/info/rfc7991) for the
available `ipr` attribute values. The majority of IETF stream I-Ds indicate
`trust200902` or `pre5378Trust200902`, as needed.

Authors preparing plaintext submissions must carefully reproduce the
text most appropriate for their Internet-Draft.

Authors of IETF stream documents must not select boilerplate that prohibits
publication as an RFC.

A standard Copyright Notice and Disclaimer must be included. This will be
generated automatically for authors preparing XML submissions. Authors of
plaintext submissions should refer to the [TLP Section
6](https://trustee.ietf.org/documents/trust-legal-provisions/) for the exact
text to reproduce.

* [ ] Verify that one of the approved IPR boilerplate selections are
      indicated in XML submissions or exactly reproduced in plaintext
      submissions.

* [ ] Verify that the most appropriate IPR boilerplate for the I-D is
      indicated.

Any Internet-Draft submitted that does not select one of the required IPR
boilerplate statements will be rejected. The IETF Secretariat cannot add
a selection for the author.

##### Limiting Modifications and Derivative Works

If the submitter of a non-IETF stream I-D desires to eliminate the IETF's
right to make modifications and derivative works of the I-D, one of two
notices must be included after the IPR statement.

The first choice is used if the contributor intends for the I-D to be
published as an RFC:

> This document may not be modified, and derivative works of it may
not be created, except to format it for publication as an RFC or
to translate it into languages other than English.

This will be automatically generated by the tools from XML source if the
`ipr` attribute value `noModificationTrust200902` is selected.

The second choice is used when the contributor does not intend for the I-D
to be published as an RFC:

> This document may not be modified, and derivative works of it may
not be created, and it may not be published except as an
Internet-Draft.

This will be automatically generated by the tools from XML source if the
`ipr` attribute value `noDerivativesTrust200902` is selected.

These notices may not be used with any IETF Standards Track document or with
most working group documents, except as discussed in [BCP
78](https://www.rfc-editor.org/info/bcp78), since the IETF must retain change
control over its documents and the ability to augment, clarify, and enhance the
original contribution in accordance with the IETF Standards Process.

The first choice may be appropriate when republishing standards produced by a
standards body other than the IETF, industry consortia, or companies. These are
typically published as Informational RFCs and do not require that change
control be ceded to the IETF. Documents of this type convey information for the
Internet community.

The second choice may be used on I-Ds that are intended to provide background
information to educate and to facilitate discussions within IETF working groups
but are not intended to be published as RFCs.

If you think that you, your company, or anyone else owns a patent or other
Intellectual Property Rights (IPR) on the work described in the I-D, you should
carefully read [BCP 79](https://www.rfc-editor.org/info/bcp79). The first notice
required in an I-D, described earlier in this section, obligates you to send an
IPR disclosure statement under certain circumstances. In particular, when
preparing a document intended to be included in the IETF Stream, before
submitting the I-D, discussing it with the working group chairs or Area
Directors is advised.

#### Abstract

Every Internet-Draft must have an abstract. The abstract should provide a
concise and comprehensive overview of the purpose and contents of the entire
document. Its purpose is to give a technically knowledgeable reader a general
overview of the function of the document, to decide whether reading it will be
useful. In addition to its function in the document, the abstract is used as a
summary in publication announcements and in the [online index of
I-Ds](https://www.ietf.org/id/1id-abstracts.txt).

Composing a useful abstract is a nontrivial writing task. Often, a
satisfactory abstract can be constructed in part from material from the
introduction section, but a good abstract will be shorter, less detailed, and
broader in scope than the introduction. Simply copying and pasting the first
few paragraphs of the introduction is tempting, but it generally results in an
abstract that is both incomplete and redundant. An abstract will typically be
five to ten lines. An abstract of more than 20 lines or fewer than three lines
is generally not acceptable.

* [ ] Ensure the Internet-Draft contains an appropriate abstract.

An abstract should be complete in itself, so it should not contain citations
unless they are completely defined within the abstract. Abbreviations appearing
in the abstract should generally be expanded in parentheses. There is a set of
reasonable exceptions to this rule; for example, readers don't need to be
reminded of what "IP" or "TCP" or "MIB" means. The RFC Editor maintains a [list
of approved
abbreviations](https://www.rfc-editor.org/materials/abbrev.expansion.txt) that
do not need to be expanded. In the end, this is a judgment call, but
please err on the side of explicitness.

* [ ] Verify that the abstract stands alone.
* [ ] Ensure abbreviations in the abstract are expanded as appropriate.
* [ ] If the I-D intends to obsolete or update a previous RFC, ensure the
      abstract says so explicitly.

The RFC Editor's [Style Guide](https://www.rfc-editor.org/styleguide/) includes
further guidance about writing an abstract.

#### Introduction

* [ ] If the I-D intends to obsolete or update a previous RFC, ensure the
      Introduction briefly explains what is being updated and why.

#### Security Considerations

[RFC 3552](https://rfc-editor.org/info/rfc3552) describes current best practices
about writing a Security Considerations section. This section is mandatory in
all documents.

The text of this section must have a meaningful exploration of security issues
raised by the proposal, which should include both risks and a description of
solutions or workarounds. It is rare that technical work can legitimately make
a claim like "This protocol introduces no security considerations," so it needs
to be fairly obvious for that to be believable, or the document will be
returned for further development. Procedural documents, however, more commonly
can claim no added security risk.

Some other references that may be useful when crafting this section are:

* [Internet Security Glossary, Version 2](https://rfc-editor.org/info/rfc4949)
* [Guidelines for Specifying the Use of IPsec Version
  2](https://rfc-editor.org/info/rfc5406)
* [Guidelines for Authors and Reviewers of MIB
  Documents](https://rfc-editor.org/info/rfc4181)
* [Security Guidelines for IETF MIB
  Modules](https://trac.ietf.org/trac/ops/wiki/mib-security)
* [YANG Security
  Considerations](https://trac.ietf.org/trac/ops/wiki/yang-security-guidelines)

* [ ] Verify that a meaningful Security Consideration section is present.

#### IANA Considerations

This section must be present to enumerate any actions IANA must take upon
publication of the document as an RFC.

* [ ] Verify this section contains clear instructions if IANA is expected
      to create a new registry or modify rules for an existing registry.

* [ ] Verify this section contains clear instructions if the document
      requires IANA to assign or update values in an IANA registry before
      RFC publication.

* [ ] Check the existing IANA registry for registration policy rules
      and any requirements for specific requests for registration of
      protocol parameters. Individual RFCs have specific criteria and
      instructions that should be followed.

* [ ] If the registration policy is "Expert Review" or "Specification
      Required" and/or requires mailing list review, as soon as the
      requested parameter information is properly formed, consider
      initiating reviews with IANA or sending to the appropriate mailing
      list (where applicable; see the RFC for that the registry for
      instructions). If there are any questions about what type of approval
      is needed from the Designated Expert (for example, if the registration
      should be made immediately or only pre-reviewed before publication),
      please contact IANA.

* [ ] If registrations are needed early for registries with "Specification
      Required", "RFC Required", "IETF Review", or "Standards Action" policies,
      consider using the early allocation process defined in [RFC 7120](https://rfc-editor.org/info/rfc7120).

* [ ] Verify this section explicitly and clearly identifies any references
      to this document that should be added for any registrations and any
      that should replace existing references.

* [ ] If the document has considerable instructions for IANA actions, request
      an early review of the document by IANA.

* [ ] If there is no action for IANA, verify that this section explicitly says
      “This document has no IANA actions.” It is often helpful for the IANA
      Considerations section to remain in place upon publication as an RFC
      even if there are no actions.

For more specific guidelines regarding structure and content for writing IANA
Considerations sections, please see [RFC
8126](https://rfc-editor.org/info/rfc8126) and the IANA [Protocol Registration
Procedures](https://www.iana.org/help/protocol-registration).

#### Summary of Changes

As noted in the abstract and introduction sections above, the abstract
and introduction must call out any RFCs an I-D intends to obsolete
or update. There should also be a section providing greater detail about
the motivation and changes.

* [ ] Ensure the I-D clearly summarizes any changes made from the RFCs
      being updated or obsoleted.

* [ ] Ensure any errata against RFCs that are being obsoleted or updated
      have been considered, and that the I-D clearly identifies those that
      have been addressed.

#### References

A references section must be present and split into normative and informative
sections. For guidance, see the RFC Editor's [Style
Guide](https://www.rfc-editor.org/styleguide/) and the [IESG Statement on
Normative and Informative
References](https://www.ietf.org/about/groups/iesg/statements/normative-informative-references/).

Normative and informative references to non-IETF documents are permitted.
However, it is best to minimize such normative references, because assessing
their status when the IETF document advances on the standards track is very
difficult. It is important to use the exact title, author name(s), organization
and publication date. External specifications referenced by
Internet-Standard-level Technical Specifications or Applicability Statements
must be to open external standards, per [RFC 2026](https://rfc-editor.org/info/rfc2026).

* [ ] Ensure all needed references are present and correctly identified
      as normative or informative.

* [ ] Verify that references are stable and resolvable.

A bare URI is not generally considered a stable reference. For web-only
documents, adding a reference number, title , and/or an author will help make
the reference more stable. See the RFC Editor's [Style
Guide](https://www.rfc-editor.org/styleguide/) for specific guidance about URIs
in Internet-Drafts. Judgment can be used here; the stability of normative
references is even more important than the stability of informative references.

Also note that normative references to I-Ds will cause the referencing document
to wait in the RFC Editor queue for the referenced I-Ds to be published as RFCs.
They may in some cases become a [cluster of
documents](https://www.rfc-editor.org/about/clusters/) that will be published as
RFCs simultaneously.

#### Authors' Addresses

* [ ] Verify that the I-D contains a section giving the name and contact
      information (postal mail, phone, and/or email) for the authors.

Note that if the I-D is eventually published as an RFC, this
information will not be changeable. When possible, provide
contact information that is expected to be stable over time.

* [ ] Verify that there are no more than five authors or editors. If there
      is a need to list more, discuss the need with the relevant stream
      leadership as early in the process as possible. For the IETF stream,
      consult an Area Director.

Per [RFC 7322](https://rfc-editor.org/info/rfc7322):

> The total number of authors or editors on the first page is generally
limited to five individuals and their affiliations.  If there is a
request for more than five authors, the stream-approving body needs
to consider if one or two editors should have primary responsibility
for this document, with the other individuals listed in the
Contributors or Acknowledgements section.  There must be a direct
correlation of authors and editors in the document header and the
Authors' Addresses section.  These are the individuals that must sign
off on the document during the AUTH48 process and respond to
inquiries, such as errata.

### Content Considerations

#### Internet-Drafts Are Not RFCs

* [ ] Verify that the I-D does not refer to itself as an RFC or a draft RFC.

* [ ] Verify that the I-D neither states nor implies that it has any
      standards-like status.

To do so conflicts with the roles of the RFC Editor and the IESG. The title of
the document should not imply a status. Avoid the use of the terms Standard,
Proposed, Draft, Experimental, Historic, Required, Recommended, Elective, or
Restricted in the I-D title. An I-D may indicate its intended status, if it were
to be published as an RFC, by setting the `status` attribute of the `seriesInfo`
XML element (see [RFC 7322](https://rfc-editor.org/info/rfc7322)) or by placing the
words "Intended status: \<status\>" on the left side of the headers in the first
page if preparing a plaintext submission.

#### Use of BCP 14 Terms

If [BCP 14](https://www.rfc-editor.org/info/bcp14) language (MUST, SHOULD, etc.)
is used, the guidelines in [RFC 2119](https://rfc-editor.org/info/rfc2119),
especially those in Sections 6 and 7, should be followed. SHOULD is especially
problematic: it needs to be clear why SHOULD is used rather than MUST, and what
the implications are of varying from the recommendation.

#### Programing Languages

When programming languages are used in Internet-Drafts, it is necessary to
include as a reference the formal definition of that coding language (e.g., C87,
C99, etc.).

#### Formal Languages

* [ ] Verify that any use of formal languages conforms with the [IESG statement
      on the use of formal languages](https://www.ietf.org/about/groups/iesg/statements/formal-languages-use/).

Some particular points to observe are enumerated below.

##### MIB modules

All MIB modules should have correct syntax, so they should compile cleanly
using the `smilint` tool, e.g.:

          smilint -m -s -l 6 -i namelength-32

An [online service is available for MIB syntax
checking](https://www.ibr.cs.tu-bs.de/projects/libsmi/tools/). This allows you
to extract the MIB module from a document for your own local use, but you can
also directly run a syntax check.

You can also download the
[`libsmi`](https://www.ibr.cs.tu-bs.de/projects/libsmi/tools/) tools for local
use. In most cases, there should be no errors or warnings present in the report.
Please evaluate all diagnostic messages before assuming that they are OK. If in
doubt, feel free to check on the [ietfmibs mailing
list](https://www.ietf.org/mailman/listinfo/IETFMIBS) or with the [OPS
ADs](mailto:ops-ads@ietf.org).

* [ ] Ensure that MIB modules compile cleanly

* [ ] Verify that the I-D follows the guidelines in [RFC
  4181](https://rfc-editor.org/info/rfc4181) as updated by [RFC
  4841](https://www.rfc-editor.org/info/rfc4841).

##### Augmented Backus-Naur Form (ABNF)

* [ ] Ensure all Augmented Backus-Naur Form (ABNF) in the I-D compiles cleanly;
  [a tool is available](https://tools.ietf.org/tools/bap/). See [RFC
  5234](https://rfc-editor.org/info/rfc5234) for information about IETF ABNF.

* [ ] If ABNF is used, ensure the I-D contains a normative reference to [RFC
  5234](https://rfc-editor.org/info/rfc5234).

##### XML

Protocol specifications that use XML should always use well-formed XML at a
minimum. Sample XML instances included in a specification have to be
well-formed, and if the XML is supposed to be valid (according to the current
W3C definition of validity), the samples must reference and be validated using
an appropriate XML Schema, DTD, or another standard validation mechanism that
is structurally and syntactically correct.

Other guidelines for the use of XML in IETF protocols can be found in [RFC
3470](https://rfc-editor.org/info/rfc3470).  Internet-Drafts that include an XML
Schema should include a normative reference to either the W3C XML Schema
Definition Language 1.1 [Part1](https://www.w3.org/TR/xmlschema11-1/) or [Part
2](https://www.w3.org/TR/xmlschema11-2/) .

* [ ] Verify that any XML in the I-D is well-formed, and if it is intended to
      be valid, confirm that it validates against the appropriate definition.

XML provides structures, such as the "`<any>`" element information item in XML
Schema, to allow element extensions.

* [ ] Ensure the I-D contains clear guidance on how, when, and where any
      extension structures, such as versioning, can be used.

* [ ] Check that any new or updated XML Schemas, Namespaces, and Resource
  Description Framework (RDF) Schemas are being registered with IANA using the
  procedures described in [RFC 3688](https://rfc-editor.org/info/rfc3688).

##### YANG

YANG (Yet Another Next Generation) is a data modeling language for data sent
over network management protocols such as NETCONF and RESTCONF. Specifications
that present a YANG module should test, review, and format them using [these tools
and guidance](https://trac.ietf.org/trac/ops/wiki/yang-review-tools).

Other useful references when considering inclusion of a YANG module include [RFC
8340](https://rfc-editor.org/info/rfc8340), [RFC
8407](https://rfc-editor.org/info/rfc8407), and the [YANG module security
considerations](https://trac.ietf.org/trac/ops/wiki/yang-security-guidelines).

#### Example Addresses

* [ ] Verify that examples use example FQDNs whenever possible.

Addresses used in examples should use fully qualified domain names instead of
literal IP addresses, and should use example FQDNs such as "foo.example.com"
instead of real-world FQDNs. See [RFC 2606](https://rfc-editor.org/info/rfc2606)
for example domain names that can be used. Note that the entire “.example” TLD
is reserved, allowing for arbitrary subdomains (in particular, ones that are not
considered same-origin on the Web.

* [ ] Verify that literal IP addresses are from the example ranges.

There are also ranges of IP addresses set aside for this purpose. For IPv4,
these are defined in [RFC 6890](https://rfc-editor.org/info/rfc6890); for IPv6,
see [RFC 3849](https://rfc-editor.org/info/rfc3849). Per the [IAB Statement on
IPv6](https://www.iab.org/2016/11/07/iab-statement-on-ipv6), IPv6 examples
should be used.

* [ ] Verify that private addresses that would be used in the real world
      are not used in examples.

* [ ] Verify that real telephone numbers are not used in examples.

Use those numbers that were reserved for examples or fictitious use.
Available numbers for use in examples are:

          UK: +44-<geographic-area-code>-496-<0000-0999>
          USA: +1-<area code>-555-<0100-0199> 

For USA examples, also see
[ATIS-0300115](https://www.nationalnanpa.com/pdf/NRUF/ATIS-0300115.pdf).

#### Stale Text

Avoid text that will become outdated after the I-D is published. Examples
include non-permanent URLs, mentions of specific mailing lists as places to send
comments on a document, or referring to specific WGs as a place to perform
specific future actions (e.g., reviewing follow-up documents). In some cases
(like the `ORGANIZATION` clause in MIB modules), references to working groups
are impossible to avoid; however, generally, Internet-Drafts should not assign
powers or responsibilities to WGs unless the WG in question is certain to exist
as long as the practice documented in the published RFC remains valid. In cases
where a specific WG is expected to be a focal point for future action, it is
acceptable to give the task to the IESG, giving instructions on how the action
is expected to be delegated, e.g., by forwarding to an appropriate WG or another
set of experts.

* [ ] Check the I-D for text that could become stale. To the extent
      possible, make it future-proof.

#### Protocol Issues

This section provides some general guidance that will help to avoid extended
discussion during the document review and approval process. The IESG has
compiled a [list of useful topics to
consider](https://trac.ietf.org/trac/iesg/wiki/ExpertTopics).

* [ ] Ensure the I-D avoids IPv4 specificity. Both IPv4 and IPv6 must be
      supportable, unless the protocol is naturally IPv4 specific or IPv6
      specific. Expect an IPv4-only protocol to be met with friction.

* [ ] Ensure the I-D does not introduce congestion issues. No application can be
  permitted to cause catastrophic congestion. See [RFC
  2914](https://rfc-editor.org/info/rfc2914) for details. Applications using TCP
  or SCTP will normally fulfill this requirement automatically. Applications
  using UDP should adhere to the guidance in [RFC
  8085](https://rfc-editor.org/info/rfc8085).

* [ ] Verify that any sort of end-to-end checksum or integrity check being used
      (especially, but not limited to, cryptographic checksums or MACs)
      precisely specifies the contents of the fields to be checksummed, and in
      exactly what order the operations are done. Pay special attention to any
      area reserved for the checksum itself.

* [ ] Verify that all user-visible text fields are internationalizable; see [RFC
  2277](https://rfc-editor.org/info/rfc2277). For most cases, this means
  [UTF-8](https://rfc-editor.org/info/rfc3629). But note that it is often not
  sufficient to simply say that strings are encoded with UTF-8 (see below about
  comparisons), especially when talking about case-(in)sensitivity, case
  folding, and the like.

* [ ] If text fields are included in some calculations, like matching, sorting,
  etc., verify that how those operations are applied to the Unicode/ISO 10646
  character set are described in detail. See
  ["stringprep"](https://rfc-editor.org/info/rfc8264) for more information on
  the recommended way of handling comparisons.

#### Inclusive Language

The IESG has made a
[statement](https://www.ietf.org/about/groups/iesg/statements/on-inclusive-language/)
recommending authors review [NISTIR 8366](https://doi.org/10.6028/NIST.IR.8366)
for guidelines on using inclusive terminology.

## Format

Formatting is automatically handled when Internet-Drafts are submitted in
XML form. Authors of such I-Ds have very few formatting issues to consider.
The primary consideration is ensuring the tools are able to render the various
formats. In particular, the content of the XML must be amenable to rendering
with the 72 character per line restriction in the text format.

Authors preparing Internet-Drafts in plain text must ensure the document
conforms to many formatting rules.

The format constraints for a plaintext I-D are primarily the same as those for
the text format of an RFC as specified in [RFC
7994](https://rfc-editor.org/info/rfc7994). One notable difference is that
Internet-Drafts are paginated, and include running headers and footers. A few
formatting requirements are highlighted here, but authors preparing plaintext
documents should fully understand the requirements in [RFC
7994](https://rfc-editor.org/info/rfc7994), [RFC
7841](https://rfc-editor.org/info/rfc7841), [RFC
7332](https://rfc-editor.org/info/rfc7332), [RFC
7322](https://rfc-editor.org/info/rfc7322), the RFC Editor's [Style
Guide](https://www.rfc-editor.org/styleguide/), and the [current acceptable
boilerplate texts](https://www.iab.org/documents/headers-boilerplate/).

The submission tool will block submission for many formatting errors and flag
many others. The [`idnits` tool](https://tools.ietf.org/tools/idnits/) can be
used to identify those so they can be corrected before submission.
Well-formatted I-Ds tend to progress through the review process more quickly.
When an I-D is approved for publication as an RFC, the RFC Editor can take care
of a few small formatting errors. However, if many formatting errors exist, the
document will be returned to the stream requesting publication for fixes. Please
be aware that not conforming to the formatting rules will most probably delay
publication and consume time that can be spent on other work.

These are formatting requirements for plaintext I-Ds that often are
overlooked:

* [ ] Verify that the document name and version appears on the first page.

* [ ] Verify that the I-D contains a "Table of Contents" section between
      the "Copyright Notice" and the introduction. This section must not
      be numbered.

* [ ] Verify that no text extends beyond the 72nd column of a line. This
      limit is especially important for diagrams, which the RFC
      Editor may not be able to trivially reformat to fall within the
      margins.

* [ ] Verify that source code does not extend beyond the 69th column.

* [ ] Verify that the text is ragged-right.

* [ ] Verify that hyphenation is not used for line breaks. However,
      hyphenated words (e.g., "Internet-Draft") may be split at the
      hyphen across successive lines.

* [ ] Verify that the I-D contains no footnotes.

* [ ] Verify the characters in the I-D meet the requirements of [RFC
  7994](https://rfc-editor.org/info/rfc7994). In brief, the document must be
  UTF-8 encoded, but code points not corresponding to ASCII are allowed only in
  certain contexts (see [RFC 7997](https://rfc-editor.org/info/rfc7997)).
  Control characters other than `CR`, `NL`, and `FF` are not allowed. The use of
  non-ASCII characters is limited to when there is a specific need, most notably
  for names. Many uses of non-ASCII characters will require listing the Unicode
  codepoint by number in addition to the character itself.

* [ ] Verify that the "Status of This Memo" and "Abstract" sections are not
      numbered.

* [ ] Verify that the appropriate boilerplate text in the IPR-related sections
  is reproduced exactly (see the [IPR-Related Notices
  section](#ipr-related-notices)). In particular, ensure that the names of RFCs
  contained in that content are not reformatted as references.

* [ ] Verify that the I-D is well formatted for readability and clarity.

* [ ] If the I-D has "Contributors" and/or "Acknowlegments" sections, verify
  that the sections are unnumbered and placed after the "References" section and
  any appendices. See Section 4 of [RFC
  7322](https://rfc-editor.org/info/rfc7322).

* [ ] Verify that references to Internet-Drafts and RFCs are formatted as shown
  in the "web portion" of the RFC Editor's Style Guide (see
  [here](https://www.rfc-editor.org/styleguide/part2/#ref_ids) for guidance on
  I-Ds and [here](https://www.rfc-editor.org/part2/#ref_rfcs) for guidance on
  RFCs). Note that these formats can change over time, so review these links
  carefully with each document submission.

## Acknowledgement

This document is based heavily on the work of Russ Housley, Ben Kaduk,
Murray Kucherawy, Alvaro Retana, and the members of many IESGs.