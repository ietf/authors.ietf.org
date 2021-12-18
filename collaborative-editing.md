---
title: Collaborative editing
description: 
published: true
date: 2021-12-14T20:46:04.995Z
tags: 
editor: markdown
dateCreated: 2021-08-25T04:21:06.810Z
---

Collaborative editing is generally the hardest part of authoring an I-D as you will need to keep on top of multiple changes from multiple sources.

# GitHub
GitHub is widely used by IETF WGs for tracking issues and the related changes to Internet-Drafts.  The following tools/services have been created by community members to support the use of GitHub:
## internet-draft-template and i-d-template
[internet-draft-template](https://github.com/martinthomson/internet-draft-template) and [i-d-template](https://github.com/martinthomson/i-d-template) are a pair of tools that work together to provide an automated Markdown I-D build system in GitHub.  These are described further in [Drafting in Markdown](/drafting-in-markdown).

## ietf-github-services
The [ietf-github-services](https://github.com/ietf-github-services) organisation contains a number of repositories providing supporting functionality, including:

* [activity-summary](https://github.com/ietf-github-services/activity-summary). Emails weekly summaries of GitHub repository activity to IETF mailing lists.
* [issue-summary](https://github.com/ietf-github-services/issue-summary).  Emails a weekly summary of all open issues.
* [datatracker-tweet](https://github.com/ietf-github-services/datatracker-tweet). Tweets events related to a Working Group based upon datatracker updates.


# Comparing two documents
[iddiff](https://author-tools.ietf.org/iddiff) is a web service that provides a side-by-side comparison of two documents.  It is generally used to show the differences between two version of the same I-D to see what has changed, or between a submitted I-D and a working draft.
