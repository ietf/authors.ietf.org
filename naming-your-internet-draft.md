---
title: Naming your Internet-Draft
description: 
published: true
date: 2021-12-16T04:43:36.904Z
tags: 
editor: markdown
dateCreated: 2021-12-14T23:17:10.215Z
---

Internet-Drafts have structured names that should accurately reflect the status and subject of the draft.  Please ensure that the following guidelines are followed when naming your draft.

If your I-D is submitted as XML (which is highly recommended), the name and version of the document will be declared in the **value** attribute of a [**\<seriesInfo\>**](https://authors.ietf.org/en/rfcxml-vocabulary#seriesinfo) element. The filename submitted must have a .xml extension.

If your I-D is submitted as plain text (which is not recommended), the name and version will appear on the document's first page, and the filename submitted must must have a .txt extension.

# Formats
Internet-Draft names have one of the following formats each made up of a number of components:

1. **Individual submissions**
   This format is used if the I-D has not been adopted into any stream (i.e. an individual submission) or if it is being considered for publication in the Independent Submission Stream
  
> draft-***(author)***-***(subject)***-***(version)***
> draft-***(author)***-***(group)***-***(subject)***-***(version)***
{.is-info}

2. **Adopted submissions and submissions from related organizations**
   This format is used if an I-D has been adopted into any stream other than the Independent Submission Stream, or if the I-D has been authored by one of the related organizations as listed under ***(source)*** below.

> draft-***(source)***-***(group)***-***(subject)***-***(version)***
> draft-***(source)***-***(subject)***-***(version)***
{.is-info}

All components are required, and are separate by a hyphen.

The characters that may appear in an I-D name are restricted to:
* lowercase letters a-z,
* digits 0-9,
* hyphens (-).

## draft-
All I-D names begin with "draft-" in order to identify the document as an I-D and not another document type, such as a charter or a review.

## (author)
This component should consist of a string related to the names(s) of the author(s). The string is typically the last name of the lead author or editor. There are no mechanical rules for this string beyond consisting only of the allowed characters.

Where possible, this component should not contain a hyphen. Hyphenated last names are allowed but having a hyphen in the second component makes it hard to extract programmatically and forces many tools to use heuristics when tying to separate the second component from the components that follow.

This component must not be easily confused with a group acronym or a reserved string as listed for ***(source)*** below.

Ojectionable or misleading strings are subject to change or removal.

## (source)
For I-Ds that have been adopted by a stream, this component identifies the stream as follows:

* "ietf" for the IETF stream
* "irtf" for the IRTF stream
* "iab" for the IAB stream

For I-Ds authored by a related organization, this component identifies the related organization as follows (some of which are historic):

* "iana"
* "iaoc"
* "iesg"
* "ietf-trust"
* "rfc-editor"

Note that any I-D submitted with one of these stream/organization strings in the second component that has not been adopted/authored by the indicated stream/organization will either be rejected or replaced.

In particular for IETF stream documents, the first version of an I-D with a name that begins with "draft-ietf-wgname-" for any working group name must be approved by the working group's chairs before it will be posted.

## (group)
If the I-D is targeted at or has been adopted by a group, the group's acronym should be added to the name just after the ***(source)*** component, separated by a hyphen. See the [list of active IETF working groups](https://datatracker.ietf.org/wg/) for reference.

A popular convention is that an individual submission seeking adoption by a working group will include the working group's acronym as the second component. For example, a person or group identified as "authors" seeking to get a document about "specific-subject" adopted by the "wgname" working group might choose the name draft-authors-wgname-specific-subject, and submit the file draft-authors-wgname-specific-subject-00.xml. If the document is later adopted by the working group, the authors will usually create a new I-D named draft-ietf-wgname-specific-subject and submit it as draft-ietf-wgname-specific-subject-00.xml. Note that the version number of this new I-D will always be 00, no matter how many versions of the individual draft were posted before adoption.

## (subject)
This describes the subject of the I-D, usually in just a few words. Each word is separated by a hyphen.

The name of an I-D should not imply a status. Avoid the use of the terms "Standard", "Proposed", "Draft", "Experimental", "Historic", "Required", "Recommended", "Elective", or "Restricted".

Internet-Drafts that revise existing RFCs often have names with "bis" in them, meaning 'again' or 'twice'. For example, an I-D that is proposed as a replacement to RFC 2345 might be called "draft-someone-rfc2345bis-00".

## (version)
Internet-Drafts are versioned with two digits, separated from the name with a hyphen. The initial version of an I-D must be "00", and subsequent updates must increment the version number by one.
