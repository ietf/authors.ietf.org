---
title: IANA Considerations
description: 
published: true
date: 2024-07-21T22:32:52.691Z
tags: 
editor: markdown
dateCreated: 2024-07-21T22:32:52.691Z
---

The [Internet Assigned Numbers Authority](https://www.iana.org/) (IANA) operates the registries that provide global coordination of the DNS root, IP addressing, and many other Internet protocol resources for the IETF. These registries are created, revised, obsoleted and closed by RFCs. For some registries, an RFC is required to register or deprecate an entry in that registry. 

All Internet-Drafts must contain an **IANA Considerations** section that enumerate any actions IANA must take upon publication of the document as an RFC. That section should only contain information for IANA and designated expert reviewers, where those are specified.

> If there is nothing to say in the **IANA Consideration** section then that section should explicitly state “This document has no IANA actions.”
{.is-info}

BCP 26 (RFC 8126) contains full guidelines on writing IANA Considerations sections, including:
* An upfront [checklist](https://www.rfc-editor.org/rfc/rfc8126.html#section-1.3) to help you navigate the document.
* How registries are [organized](https://www.rfc-editor.org/rfc/rfc8126.html#section-2.1)
* How to create, revise, obsolete and close a registry
* How to register new values in an existing registry and update existing registrations
* How to choose a registration policy (it also provides a detailed set of well-known policies to choose from)
* The role of designated experts and when they should be specified

The IANA [Protocol Registration Procedures](https://www.iana.org/help/protocol-registration) augment those guidelines with additional guidance and more specific details, including:
* Suggested text
* Examples of registry formats

RFC 7120 describes 'early allocation', a process that can be used to `alleviate the problem where code point allocation is needed to facilitate desired or required implementation and deployment experience prior to publication of an RFC`.


# Checklist
- [x] Verify this section contains clear instructions if IANA is expected to create a new registry or modify rules for an existing registry.
- [x] Verify this section contains clear instructions if the document requires IANA to assign or update values in an IANA registry before RFC publication.
- [x] Check the existing IANA registry for registration policy rules and any requirements for specific requests for registration of protocol parameters. Individual RFCs have specific criteria and instructions that should be followed.
- [x] If the registration policy is "Expert Review" or "Specification Required" and/or requires mailing list review, as soon as the requested parameter information is properly formed, consider initiating reviews with IANA or sending to the appropriate mailing list (where applicable; see the RFC for that the registry for instructions). If there are any questions about what type of approval is needed from the Designated Expert (for example, if the registration should be made immediately or only pre-reviewed before publication), please contact IANA.
- [x] If registrations are needed early for registries with "Specification Required", "RFC Required", "IETF Review", or "Standards Action" policies, consider using the early allocation process defined in RFC 7120.
- [x] Verify this section explicitly and clearly identifies any references to this document that should be added for any registrations and any that should replace existing references.
- [x] If the document has considerable instructions for IANA actions, request an early review of the document by IANA.

