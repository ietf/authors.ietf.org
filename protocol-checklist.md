---
title: Protocol checklist
description: 
published: true
date: 2022-05-02T08:57:16.921Z
tags: 
editor: markdown
dateCreated: 2021-12-15T04:40:23.005Z
---

This is a general checklist that will help to avoid extended discussion during the document review and approval process. The IESG has compiled a more detailed list of [useful topics to consider](https://trac.ietf.org/trac/iesg/wiki/ExpertTopics).

- [x] Ensure the I-D avoids IPv4 specificity. Both IPv4 and IPv6 must be supportable, unless the protocol is naturally IPv4 specific or IPv6 specific. Expect an IPv4-only protocol to be met with friction.
- [x] Ensure the I-D does not introduce congestion issues. No application can be permitted to cause catastrophic congestion. See RFC 2914 for details. Applications using TCP, SCTP, DCCP, or QUIC will normally fulfill this requirement automatically. Other applications using UDP should adhere to the guidance in RFC 8085.
- [x] Verify that any sort of end-to-end checksum or integrity check being used (especially, but not limited to, cryptographic checksums or MACs) precisely specifies the contents of the fields to be checksummed, and in exactly what order the operations are done. Pay special attention to any area reserved for the checksum itself.
- [x] Verify that all user-visible text fields are internationalizable; see RFC 2277. For most cases, this means [UTF-8](https://rfc-editor.org/info/rfc3629). But note that it is often not sufficient to simply say that strings are encoded with UTF-8 (see below about comparisons), especially when talking about case-(in)sensitivity, case folding, and the like.
- [x] If text fields are included in some calculations, like matching, sorting, etc., verify that how those operations are applied to the Unicode/ISO 10646 character set are described in detail. See [stringprep](https://rfc-editor.org/info/rfc8264) for more information on the recommended way of handling comparisons.