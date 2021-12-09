---
title: Submitting your Internet-Draft
description: 
published: true
date: 2021-12-09T19:31:26.698Z
tags: 
editor: markdown
dateCreated: 2021-12-09T03:59:06.890Z
---

# Submission tool
Internet-Draft submissions are made using the [IETF Datatracker's submission tool](https://datatracker.ietf.org/submit). You do not need to be logged in to Datatracker to submit an I-D but it is recommended and it will simplify the submission process.

Your submission should be an [RFCXML](https://authors.ietf.org/en/rfcxml-overview) I-D, which the Datatracker will use as the authoritative source to generate plaintext and HTML renderings. A plaintext rendering can be submitted alongside the RFCXML version, instead of being generated.

If an RFCXML submission is not possible, the draft can be submitted as plaintext and this will be used as the authoritative version but no renderings will be generated. 

It is currently possible to submit a legacy v2 RFCXML I-D instead of the current v3.  This will be run through the v2 to v3 processor, the renderings generated from the v3 file and the v3 file then discarded.

It is also currently possible to submit a PDF rendering of the document alongside both an RFCXML and plaintext submission. It is expected that support for PDF will be removed at some point.

> In short: submit RFCXML if at all possible, with v3 preferred over v2.
{.is-success}

# Submission process
When a submission is made through the submission tool, the authors will receive email with a request to verify the submission. The submission will not be accepted and posted until the action requested in that email is performed. If the submitter is logged into the Datatracker and listed as an author this step is bypassed.

If the I-D being submitted replaces another I-D, the submitter will be able to identify the replacement using the submission tool. A group chair or the IETF Secretariat will verify the replacement before the relationship is added to the Datatracker.

The submission tool will validate the document using [xml2rfc](https://github.com/ietf-tools/xml2rfc), [id2xml](https://github.com/ietf-tools/id2xml) and [idnits](https://github.com/ietf-tools/idnits-mirror) as appropriate, but authors are expected to have manually applied all relevant guidance before submission.

While some of the requirements highlighted on this site are for RFCs, Internet-Drafts are expected to adhere to them to the extent possible. In particular, IETF stream I-Ds submitted to the IESG must follow all of the guidance.  Working groups are encouraged to require the guidance be followed for I-Ds entering Working Group Last Call. I-Ds will progress through the review and publication process more efficiently the earlier the guidance is followed in the I-D.

# Submission deadlines
Be aware of the deadlines for submitting I-Ds before each IETF meeting. The [important dates page](https://datatracker.ietf.org/meeting/important-dates) will show the deadline for submitting I-Ds. Some meetings may have an earlier deadline for initial versions of I-Ds than for updates to existing I-Ds.

After the deadlines, submissions will not be accepted until the meeting begins. The leadership responsible for each stream can override this submission blackout period when appropriate.

Care should be taken when submitting an I-D near the deadline, especially if a manual post is requested. The steps to confirm and post the submission take time.

# Manual submissions
If you are unable to submit an I-D through the Datatracker, you may make a manual-post request by sending the I-D via email to support@ietf.org. The message may contain the I-D as an attachment, or a URL that will resolve to the I-D. The I-D must be a standalone document in either RFCXML or plaintext format. Multiple files presented in containers such as zip or tar will not be accepted. All other formats will be discarded without opening.

# Repository and archive
When an Internet-Draft is submitted it is placed in both the [Internet-Draft Repository](https://www.ietf.org/id)  and the [Internet-Draft Archive](https://www.ietf.org/archive/id) along with any additional renderings.

The [Internet-Draft Repository](https://www.ietf.org/id) contains only active versions of Internet-Drafts.  When an Internet-Draft is submitted, that version becomes active and ceases to be active, and so removed from the Repository, when any of the following occur:

* The I-D is updated with a new version.
* The I-D is replaced by another Internet-Draft.
* The I-D is published as an RFC.
* The I-D expires.

An I-D expires 185 days after it was placed in the Repository, unless it is in a state that prevents it from expiring. Examples of such states include being processed by the IESG for publication in the IETF stream, or being under review by the Independent Series Editor (ISE) for publication in the [Independent Submission Stream](https://www.rfc-editor.org/about/independent/).

Additionally, all versions of Internet-Drafts are kept in the [Internet-Draft Archive](https://www.ietf.org/archive/id) along with any additional renderings.  Removing an I-D from the Archive occurs only in exceptional circumstances, described in this [IESG Statement](https://www.ietf.org/about/groups/iesg/statements/internet-draft-removal/).

Even though Internet-Drafts are kept in an Archive, they are not an archival series and should not be cited or quoted as anything other than "work in progress".
