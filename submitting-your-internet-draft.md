---
title: Submitting your Internet-Draft
description: 
published: true
date: 2021-12-09T04:10:17.084Z
tags: 
editor: markdown
dateCreated: 2021-12-09T03:59:06.890Z
---

# Submission tool
Internet-Draft submissions are made using the [IETF Datatracker's submission tool](https://datatracker.ietf.org/submit). Datatracker accounts are free and automatically created by a number of IETF processes. 

An I-D submission should be an [RFCXML](https://authors.ietf.org/en/rfcxml-overview) v3 source file, but a v2 source will be accepted. If an RFCXML file is submitted, this is taken as the authoritative version of the document.

If RFCXML source is submitted, the Datatracker will generate both plaintext and HTML versions of the I-D and place them in the Archive.

If an RFCXML submission is not possible, the draft can be submitted as plaintext and will be taken as the authoritive version. A plaintext version can also be submitted as an "alternate form" of the I-D when and RFCXML version is submitted.

It is currently possible to submit a PDF version of the document, which is kept with the authoritative document source in the repository and archive. It is expected that supoprt for PDF will be removed at some point.

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
If authors are unable to submit an I-D through the Datatracker, they may make a manual-post request by sending the I-D via email to support@ietf.org. The message may contain the I-D as an attachment, or a URL that will resolve to the I-D. The I-D must be a standalone document in either RFCXML or plaintext format. Multiple files presented in containers such as zip or tar will not be accepted. All other formats will be discarded without opening.

# After submission
Active versions of Internet-Drafts are also placed in the [Internet-Draft Repository](https://www.ietf.org/id). Versions of Internet-Drafts are superseded in the Repository when any of the following occur:

* The I-D is updated with a new version.
* The I-D is replaced by another Internet-Draft.
* The I-D is published as an RFC.
* The I-D expires.

An I-D expires 185 days after it was placed in the Repository, unless it is in a state that prevents it from expiring. Examples of such states include being processed by the IESG for publication in the IETF stream, or being under review by the Independent Series Editor (ISE) for publication in the [Independent Submission Stream](https://www.rfc-editor.org/about/independent/).

All versions of Internet-Drafts are kept in the [Internet-Draft Archive](https://www.ietf.org/archive/id). Internet-Drafts are not removed from the Archive when they are superseded in the Repository. Removing an I-D from the Archive occurs only in exceptional circumstances, described in this [IESG Statement](https://www.ietf.org/about/groups/iesg/statements/internet-draft-removal/).

Even though Internet-Drafts are kept in the Archive, they are not an archival series and should not be cited or quoted as anything other than "work in progress".