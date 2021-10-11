---
title: Content Considerations
description: 
published: true
date: 2021-09-01T20:52:28.743Z
tags: 
editor: markdown
dateCreated: 2021-08-16T23:46:37.851Z
---

#### Internet-Drafts Are Not RFCs

* [ ] Verify that the I-D does not refer to itself as an RFC or a draft RFC.

* [ ] Verify that the I-D neither states nor implies that it has any standards-like status.

To do so conflicts with the roles of the RFC Editor and the IESG. The title of the document should not imply a status. Avoid the use of the terms Standard, Proposed, Draft, Experimental, Historic, Required, Recommended, Elective, or Restricted in the I-D title. An I-D may indicate its intended status, if it were to be published as an RFC, by setting the `status` attribute of the `seriesInfo` XML element (see [RFC 7322](https://rfc-editor.org/info/rfc7322)) or by placing the words "Intended status: \<status\>" on the left side of the headers in the first page if preparing a plaintext submission.

#### Use of BCP 14 Terms

If [BCP 14](https://www.rfc-editor.org/info/bcp14) language (MUST, SHOULD, etc.) is used, the guidelines in [RFC 2119](https://rfc-editor.org/info/rfc2119), especially those in Sections 6 and 7, should be followed. SHOULD is especially problematic: it needs to be clear why SHOULD is used rather than MUST, and what the implications are of varying from the recommendation.

#### Programing Languages

When programming languages are used in Internet-Drafts, it is necessary to include as a reference the formal definition of that coding language (e.g., C87, C99, etc.).

#### Formal Languages

* [ ] Verify that any use of formal languages conforms with the [IESG statement on the use of formal languages](https://www.ietf.org/about/groups/iesg/statements/formal-languages-use/).

Some particular points to observe are enumerated below.

##### MIB modules

All MIB modules should have correct syntax, so they should compile cleanly using the `smilint` tool, e.g.:

          smilint -m -s -l 6 -i namelength-32

An [online service is available for MIB syntax checking](https://www.ibr.cs.tu-bs.de/projects/libsmi/tools/). This allows you to extract the MIB module from a document for your own local use, but you can also directly run a syntax check.

You can also download the [`libsmi`](https://www.ibr.cs.tu-bs.de/projects/libsmi/tools/) tools for local use. In most cases, there should be no errors or warnings present in the report. Please evaluate all diagnostic messages before assuming that they are OK. If in doubt, feel free to check on the [ietfmibs mailing list](https://www.ietf.org/mailman/listinfo/IETFMIBS) or with the [OPS ADs](mailto:ops-ads@ietf.org).

* [ ] Ensure that MIB modules compile cleanly

* [ ] Verify that the I-D follows the guidelines in [RFC 4181](https://rfc-editor.org/info/rfc4181) as updated by [RFC 4841](https://www.rfc-editor.org/info/rfc4841).

##### Augmented Backus-Naur Form (ABNF)

* [ ] Ensure all Augmented Backus-Naur Form (ABNF) in the I-D compiles cleanly; [a tool is available](https://tools.ietf.org/tools/bap/). See [RFC 5234](https://rfc-editor.org/info/rfc5234) for information about IETF ABNF.

* [ ] If ABNF is used, ensure the I-D contains a normative reference to RFC5234.


##### XML

Protocol specifications that use XML should always use well-formed XML at a minimum. Sample XML instances included in a specification have to be well-formed, and if the XML is supposed to be valid (according to the current W3C definition of validity), the samples must reference and be validated using an appropriate XML Schema, DTD, or another standard validation mechanism that is structurally and syntactically correct.

Other guidelines for the use of XML in IETF protocols can be found in [RFC 3470](https://rfc-editor.org/info/rfc3470).  Internet-Drafts that include an XML Schema should include a normative reference to either the W3C XML Schema Definition Language 1.1 [Part1](https://www.w3.org/TR/xmlschema11-1/) or [Part 2](https://www.w3.org/TR/xmlschema11-2/) .

* [ ] Verify that any XML in the I-D is well-formed, and if it is intended to be valid, confirm that it validates against the appropriate definition.

XML provides structures, such as the "`<any>`" element information item in XML Schema, to allow element extensions.

* [ ] Ensure the I-D contains clear guidance on how, when, and where any extension structures, such as versioning, can be used.

* [ ] Check that any new or updated XML Schemas, Namespaces, and Resource Description Framework (RDF) Schemas are being registered with IANA using the procedures described in [RFC 3688](https://rfc-editor.org/info/rfc3688).

##### YANG

YANG (Yet Another Next Generation) is a data modeling language for data sent over network management protocols such as NETCONF and RESTCONF. Specifications that present a YANG module should test, review, and format them using [these tools and guidance](https://trac.ietf.org/trac/ops/wiki/yang-review-tools).

Other useful references when considering inclusion of a YANG module include [RFC 8340](https://rfc-editor.org/info/rfc8340), [RFC 8407](https://rfc-editor.org/info/rfc8407), and the [YANG module security considerations](https://trac.ietf.org/trac/ops/wiki/yang-security-guidelines).

#### Example Addresses

* [ ] Verify that examples use example FQDNs whenever possible.

Addresses used in examples should use fully qualified domain names instead of literal IP addresses, and should use example FQDNs such as "foo.example.com" instead of real-world FQDNs. See [RFC 2606](https://rfc-editor.org/info/rfc2606) for example domain names that can be used. Note that the entire “.example” TLD is reserved, allowing for arbitrary subdomains (in particular, ones that are not considered same-origin on the Web.

* [ ] Verify that literal IP addresses are from the example ranges.

There are also ranges of IP addresses set aside for this purpose. For IPv4, these are defined in [RFC 6890](https://rfc-editor.org/info/rfc6890); for IPv6, see [RFC 3849](https://rfc-editor.org/info/rfc3849). Per the [IAB Statement on IPv6](https://www.iab.org/2016/11/07/iab-statement-on-ipv6), IPv6 examples should be used.

* [ ] Verify that private addresses that would be used in the real world are not used in examples.

* [ ] Verify that real telephone numbers are not used in examples.

Use those numbers that were reserved for examples or fictitious use. Available numbers for use in examples are:

          UK: +44-<geographic-area-code>-496-<0000-0999>
          USA: +1-<area code>-555-<0100-0199> 

For USA examples, also see [ATIS-0300115](https://www.nationalnanpa.com/pdf/NRUF/ATIS-0300115.pdf).

#### Stale Text

Avoid text that will become outdated after the I-D is published. Examples include non-permanent URLs, mentions of specific mailing lists as places to send comments on a document, or referring to specific WGs as a place to perform specific future actions (e.g., reviewing follow-up documents). In some cases (like the `ORGANIZATION` clause in MIB modules), references to working groups are impossible to avoid; however, generally, Internet-Drafts should not assign powers or responsibilities to WGs unless the WG in question is certain to exist as long as the practice documented in the published RFC remains valid. In cases where a specific WG is expected to be a focal point for future action, it is acceptable to give the task to the IESG, giving instructions on how the action is expected to be delegated, e.g., by forwarding to an appropriate WG or another set of experts.

* [ ] Check the I-D for text that could become stale. To the extent possible, make it future-proof.

#### Protocol Issues

This section provides some general guidance that will help to avoid extended discussion during the document review and approval process. The IESG has compiled a [list of useful topics to consider](https://trac.ietf.org/trac/iesg/wiki/ExpertTopics).

* [ ] Ensure the I-D avoids IPv4 specificity. Both IPv4 and IPv6 must be supportable, unless the protocol is naturally IPv4 specific or IPv6 specific. Expect an IPv4-only protocol to be met with friction.

* [ ] Ensure the I-D does not introduce congestion issues. No application can be permitted to cause catastrophic congestion. See [RFC 2914](https://rfc-editor.org/info/rfc2914) for details. Applications using TCP or SCTP will normally fulfill this requirement automatically. Applications using UDP should adhere to the guidance in [RFC 8085](https://rfc-editor.org/info/rfc8085).

* [ ] Verify that any sort of end-to-end checksum or integrity check being used (especially, but not limited to, cryptographic checksums or MACs) precisely specifies the contents of the fields to be checksummed, and in exactly what order the operations are done. Pay special attention to any area reserved for the checksum itself.

* [ ] Verify that all user-visible text fields are internationalizable; see [RFC 2277](https://rfc-editor.org/info/rfc2277). For most cases, this means [UTF-8](https://rfc-editor.org/info/rfc3629). But note that it is often not sufficient to simply say that strings are encoded with UTF-8 (see below about comparisons), especially when talking about case-(in)sensitivity, case folding, and the like.

* [ ] If text fields are included in some calculations, like matching, sorting, etc., verify that how those operations are applied to the Unicode/ISO 10646 character set are described in detail. See ["stringprep"](https://rfc-editor.org/info/rfc8264) for more information on the recommended way of handling comparisons.

#### Inclusive Language

The IESG has made a [statement](https://www.ietf.org/about/groups/iesg/statements/on-inclusive-language/) recommending authors review [NISTIR 8366](https://doi.org/10.6028/NIST.IR.8366) for guidelines on using inclusive terminology.