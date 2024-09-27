---
title: IANA Considerations
description: 
published: true
date: 2024-09-27T13:14:14.193Z
tags: 
editor: markdown
dateCreated: 2024-07-21T22:32:52.691Z
---

> PAGE UNDER CONSTRUCTION
{.is-warning}

The [Internet Assigned Numbers Authority](https://www.iana.org/) (IANA) operates registries that provide global coordination of the DNS root, IP addressing, and other Internet protocol resources for the IETF. These registries are created, revised, obsoleted and closed by RFCs. For some registries, an RFC is required to register or deprecate an entry in that registry. 

All Internet-Drafts MUST contain an **IANA Considerations** section, which enumerates registry actions for IANA to take upon publication of the document as an RFC. Common actions include creating a new IANA registry, modifying rules for an existing registry, and assigning or updating values in an IANA registry.

This section should contain clear instructions for IANA (and designated expert reviewers where appropriate) and nothing else.

If there is nothing to say in the **IANA Consideration** section then it should say “This document has no IANA actions.”

# Writing the IANA Considerations section

BCP 26 (RFC 8126) contains full guidelines on writing IANA Considerations sections. Notable highlights include:
* An upfront [checklist](https://www.rfc-editor.org/rfc/rfc8126.html#section-1.3) to help you navigate the document.
* How registries are [organized](https://www.rfc-editor.org/rfc/rfc8126.html#section-2.1).
* How to [create](https://www.rfc-editor.org/rfc/rfc8126.html#section-2.2), [revise](https://www.rfc-editor.org/rfc/rfc8126.html#section-2.4), [obsolete and close](https://www.rfc-editor.org/rfc/rfc8126.html#section-9.6) a registry.
* How to [register new values](https://www.rfc-editor.org/rfc/rfc8126.html#section-3.1) in an existing registry and [update existing](https://www.rfc-editor.org/rfc/rfc8126.html#section-3.2) registrations.
* How to choose a [registration policy](https://www.rfc-editor.org/rfc/rfc8126.html#section-4) (it also provides a detailed set of well-known policies to choose from).
* The role of [designated experts](https://www.rfc-editor.org/rfc/rfc8126.html#section-5), when they should be specified and how they are managed.

The IANA [Protocol Registration Procedures](https://www.iana.org/help/protocol-registration) augment those guidelines with additional guidance and more specific details, including:
* What to include for [creating registries](https://www.iana.org/help/protocol-registration#registries) and [making registrations](https://www.iana.org/help/protocol-registration#registrations).
* Recommendations for [common issues](https://www.iana.org/help/protocol-registration#issues).
* [Suggested text](https://www.iana.org/help/protocol-registration#verbiage) for use in your Internet-Draft.
* [Examples](https://www.iana.org/help/protocol-registration#examples) of registry formats.

# References
This section should explicitly and clearly identify any references to this document that should be added for any registrations and any that should replace existing references.

# Early allocation
RFC 7120 describes 'early allocation', a mechanism for registering a code point in an IANA registry before the document is published as an RFC. This is used to facilitate desired or required implementation and deployment experience prior to publication of an RFC.  It is generally used for registries with "Specification Required", "RFC Required", "IETF Review", or "Standards Action" policies.

# Getting your I-D reviewed
There are a number of situations where it might be useful to ask IANA to review your I-D:
* If your Internet-Draft is adding a code point to a registry that has a registration policy of "Expert Review" or "Specification Required".
* If there are any questions about what type of approval is needed for a code point registration from the Designated Expert (e.g., if the registration should be made immediately or only pre-reviewed before publication). 
* If your Internet-Draft has considerable IANA actions.

If the registration policy requires mailing list review, consider reaching out to the appropriate mailing list.

# Replacing an RFC that has IANA actions
If your I-D aims to replace an existing RFC that contains IANA actions, then special care is needed. This is explained in [Section 8 of RFC 8126](https://www.rfc-editor.org/rfc/rfc8126.html#section-8) with additional guidance in the IANA [Protocol Registration Procedures](https://www.iana.org/help/protocol-registration#bis.)

