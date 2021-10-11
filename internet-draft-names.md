---
title: Internet-Draft names
description: 
published: true
date: 2021-08-25T22:20:39.034Z
tags: 
editor: markdown
dateCreated: 2021-08-16T22:51:45.856Z
---

Internet-Draft names appear inside the I-D, and are used as components of filenames for the various formats the I-D may appear in. The characters that may appear in an I-D name are restricted:

* [ ] Ensure that the I-D name consists only of
  * the lowercase letters `a-z`,
  * the digits `0-9`,
  * or hyphens (`-`).

The name of an I-D consists of several components, separated by a hyphen. No empty components are allowed. That is, consecutive hyphens may not appear in an I-D name.

The first component identifies the I-D as a draft (as opposed to other document types, such as a charter or a review).

* [ ] Verify that the I-D name begins with `draft-`.

The second component identifies the source of an I-D. If an I-D has been adopted into any stream other than the Independent Submission Stream, this component will identify the stream.

If the I-D has not been adopted into any stream or if it is being considered for publication in the Independent Submission Stream, the second component should consist of a string related to the names(s) of the author(s). There are no mechanical rules for this string beyond consisting only of the allowed characters. However, objectionable or misleading strings are subject to change or removal. The string is typically the last name of the lead author or editor.

The second component must not be easily confused with a group acronym. The following strings for the second component are reserved for their respective organizations (some of which are historic):

* `iana`
* `iaoc`
* `iesg`
* `ietf-trust`
* `rfc-editor`

The second component should not contain a hyphen. Legacy uses and edge cases such as hyphenated last names are allowed. Having a hyphen in the second component makes it hard to extract programmatically. This forces many tools to use heuristics when tying to locate the second component.

* [ ] Ensure the second component reasonably identifies the source of the I-D.

* [ ] If the I-D has been adopted by a stream, ensure the second component is:
  * `ietf` for the IETF stream
  * `irtf` for the IRTF stream
  * `iab` for the IAB stream

Otherwise, ensure that the second component is not a group acronym or a reserved string, is not objectionable, and does not introduce confusion.

Note that any I-D submitted with one of these stream identifiers in the second component that has not been adopted by the indicated stream will either be rejected or replaced.

If the I-D is targeted at or has been adopted by a group, the group's acronym should be added to the name just after the second component, separated by a hyphen.

* [ ] Ensure an adopted or group-targeted I-D identifies the group just after the second component by including the group's acronym.

Note again that if the I-D has not been adopted into a stream, and it identifies a stream in the second component, it will be rejected or replaced. In particular for IETF stream documents, the first version of an I-D with a name that begins with `draft-ietf-acronym-` for any working group acronym must be approved by the working group's chairs before it will be posted.

The remainder of the name describes the purpose of the I-D, usually in just a few words. Each word is separated by a hyphen.

* [ ] Ensure the name reasonably reflects the purpose of the I-D.

Internet-Drafts are versioned with two digits, separated from the name with a hyphen. The initial version of an I-D must be `00`, and subsequent updates must increment the version number by one.

If the I-D is submitted as XML (which is highly recommended), the name and version of the document will be declared in the appropriate ["name" and "version" attributes](https://rfc-editor.org/info/rfc7991), and the filename submitted must be of the form `name-version.xml`.

If the I-D is submitted as plain text (which is not recommended), the name and version will appear on the document's first page, and the filename submitted must be of the form `name-version.txt`.

Convention dictates that an individual submission seeking adoption by a working group will include the working group's acronym just after the second component. For example, a person or group identified as "foo" seeking to get a document about "specific-subject" adopted by the "bar" working group might choose the name `draft-foo-bar-specific-subject`, and submit the file `draft-foo-bar-specific-subject-00.xml`. If the document is later adopted by the working group, the authors will usually create a new I-D named `draft-ietf-bar-specific-subject` and submit it as `draft-ietf-bar-specific-subject-00.xml`. Note that the version number of this new I-D will always be `00`.