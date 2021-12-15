---
title: Language and style
description: 
published: true
date: 2021-12-15T01:38:30.164Z
tags: 
editor: markdown
dateCreated: 2021-12-14T23:52:28.098Z
---

# Style guide
The recommended style for Internet-Drafts is documented in a collection of documents that are together known as the [RFC Style Guide](https://www.rfc-editor.org/styleguide/).

# Abbreviations
Abbreviations should generally be expanded in parentheses.  The RFC Editor maintains a list of [approved abbreviations](https://www.rfc-editor.org/materials/abbrev.expansion.txt) that do not need to be expanded.

# Internet-Drafts Are Not RFCs
There are some key rules for I-D authors:
* Your I-D must not refer to itself as an RFC or a draft RFC.
* Your I-D must neither state nor imply that it has any standards-like status.
* Avoid the use of the terms "Standard", "Proposed", "Draft", "Experimental", "Historic", "Required", "Recommended", "Elective", or "Restricted" in the I-D title. 

An I-D may indicate its intended status, if it were to be published as an RFC, by setting the **status** attribute of the [**\<seriesInfo\>**](https://authors.ietf.org/en/rfcxml-vocabulary#seriesinfo) RFCXML element (see RFC 7322) or by placing the words `Intended status: <status>` on the left side of the headers in the first page if preparing a plaintext submission.

# Use of BCP 14 terms
If [BCP 14](https://www.rfc-editor.org/info/bcp14) language (MUST, SHOULD, etc.) is used, the guidelines in RFC 2119, especially those in Sections 6 and 7, should be followed. SHOULD is especially problematic: it needs to be clear why SHOULD is used rather than MUST, and what the implications are of varying from the recommendation.

# Inclusive Language
The IESG has made a [statement](https://www.ietf.org/about/groups/iesg/statements/on-inclusive-language/) recommending authors review [NISTIR 8366](https://doi.org/10.6028/NIST.IR.8366) for guidelines on using inclusive terminology. Similar guidance pointing to NISTIR 8366 exists for other RFC Streams. Authors are encouraged to familiarize themselves with and apply the guidance.

# Stale text
Avoid text that will become outdated after the I-D is published. Examples include non-permanent URLs, mentions of specific mailing lists as places to send comments on a document, or referring to specific WGs as a place to perform specific future actions (e.g., reviewing follow-up documents). In some cases (like the ORGANIZATION clause in MIB modules), references to working groups are impossible to avoid; however, generally, Internet-Drafts should not assign powers or responsibilities to WGs unless the WG in question is certain to exist as long as the practice documented in the published RFC remains valid. In cases where a specific WG is expected to be a focal point for future action, it is acceptable to give the task to the IESG, giving instructions on how the action is expected to be delegated, e.g., by forwarding to an appropriate WG or another set of experts.

# Example addresses
## Domain names
Addresses used in examples should use fully qualified domain names instead of literal IP addresses, and should use example FQDNs such as "foo.example.com" instead of real-world FQDNs. See RFC 2606 for example domain names that can be used. Note that the entire “.example” TLD is reserved, allowing for arbitrary subdomains (in particular, ones that are not considered same-origin on the Web.

## IP addresses
Literal IP addresses used in examples should be from the example ranges set aside for this purpose. For IPv4, these are defined in RFC 6890; for IPv6, see RFC 3849. Per the IAB Statement on IPv6, IPv6 examples should be used.

> Verify that private IP addresses that would be used in the real world are not used in examples.
{.is-danger}

## Telephone number
Telephone numbers used in examples should be those numbers that were reserved for examples or fictitious use. Available numbers for use in examples are:

UK: +44-\<geographic-area-code\>-496-\<0000-0999\>
USA: +1-\<area code\>-555-\<0100-0199\>

For USA examples, also see ATIS-0300115.
  
> Verify that real telephone numbers are not used in examples.
{.is-danger}