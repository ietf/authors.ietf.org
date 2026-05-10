---
title: RFC Publication process
description: 
published: true
date: 2026-05-10T23:45:10.052Z
tags: 
editor: markdown
dateCreated: 2024-07-23T22:38:08.063Z
---

# Stream approval
The process for publishing an RFC begins when an Internet-Draft is approved by one of the publication streams:
* **IETF Stream**. I-Ds from the IETF stream are submitted by the IESG following their processes documented in [RFC 2026](https://www.rfc-editor.org/rfc/rfc2026) and multiple subsequent RFCs.
* **IAB Stream**. The process for publication of IAB RFCs is documented in [RFC 4845](https://www.rfc-editor.org/rfc/rfc4845).
* **IRTF Stream**. The process for publication of IRTF RFCs is documented in [Section 3](https://www.rfc-editor.org/rfc/rfc5743#section-3) of [RFC 5743](https://www.rfc-editor.org/rfc/rfc5743).
* **Independent Stream**. The process for publication of Independent Submission RFCs is documented in [Section 3](https://www.rfc-editor.org/rfc/rfc4846#section-3) of [RFC 4846](https://www.rfc-editor.org/rfc/rfc4846).
* **Editorial Stream**. The process for publication of Editorial Stream RFCs is documented in [Section 3.2](https://www.rfc-editor.org/rfc/rfc9920#name-process) of [RFC 9920](https://www.rfc-editor.org/rfc/rfc9920). 

# Publication queue and states
Once a document is approved, it enters the [publication queue](https://queue.rfc-editor.org/) and is managed by the RFC Production Center (RPC). From this point on, the RPC has change control of the document. This means that the RPC now manages the document in their own repository, and that all changes the authors wish to make must go through the RPC. Any non-technical changes, such as updating the contact information, will normally be accepted directly, but any technical updates will require stream approval.

When a document enters the publication queue, it is assigned an initial state, and this state is updated as the document progresses through the queue. Any time the document's state changes, an automatic email message summarizing the state change is sent to the authors.

## Clusters
Sometimes groups of documents are managed together as a cluster. This can be for two reasons:
1. Where the documents contain normative references to each other, either directly or indirectly through intermediate documents, and therefore need to be published in a certain order and/or simultaneously.
2. Where the originating stream specifically submits a set of documents that should be published together even though they are not explicitly coupled by normative references.

Clusters can include both documents that are in the queue and those that are not yet in the queue (shown as `Not received`).

Clusters are assigned IDs and linked to each document in the cluster.  The [Clusters page](https://queue.rfc-editor.org/clusters/) shows the current clusters and the status of each document in the cluster.

## Initial reference check
A document waiting for a normative reference (or a stream-specified dependency) to enter the queue is shown as blocked and `Reference Not Received`. Specifically:
- `Reference Not Received` has a reference to a document that is not received.
- `Reference Not Received (2nd Generation)` has a reference to a document that references a document that is not received.
- `Reference Not Received (3rd Generation)` has a reference to a document that references a document that references a document that is not received.

Documents in a cluster can sometimes wait for a long time for the dependencies on the other documents to be resolved. Once the dependencies are resolved, the document is no longer blocked and is edited.

# Professional editing
Once a document is approved and submitted for publication, control is handed over to the professional editors of the RFC Publication Center (RPC). They start by sending the authors an intake form to gather information significant to the editing process. Then they put the document through an extensive editing process with multiple stages.

## RFCXML editing
If the document is not already in [RFCXML](https://authors.ietf.org/en/rfcxml-overview), it is converted into RFCXML. The RFCXML is examined and may be restructured to ensure consistency and readability. The editors perform the following updates:
* Look for UTF-8 characters and mark them appropriately.
* Update the DOCTYPE to the following:
```   <!DOCTYPE rfc [
    <!ENTITY nbsp    "&#160;">
    <!ENTITY zwsp   "&#8203;">
    <!ENTITY nbhy   "&#8209;">
    <!ENTITY wj     "&#8288;">
   ]> 
```   
* Check the following elements for accuracy and update them if needed:
   * [\<rfc\>](/rfcxml-vocabulary#rfc)
   * [\<workgroup\>](/rfcxml-vocabulary#workgroup)
   * [\<area\>](/rfcxml-vocabulary#workgroup)
* Add the [\<seriesInfo\>](/rfcxml-vocabulary#seriesinfo) element to capture the RFC number.
* If the document has key words from BCP 14 (e.g., “MUST”, “RECOMMENDED”), tag those key words with the [\<bcp14\>](/rfcxml-vocabulary#bcp14) element, which provides text formatting.
* Check the contents of anything tagged with [\<artwork\>](/rfcxml-vocabulary#artwork) to assess whether it should be converted to a table, a list, or tagged with [\<sourcecode\>](/rfcxml-vocabulary#sourcecode) instead.
* Clean up any blank spaces or lines around [\<artwork\>](/rfcxml-vocabulary#artwork) or [\<sourcecode\>](/rfcxml-vocabulary#sourcecode) and may make edits to get the the contents to fit within the width limit.
* Check lists for correct semantics and update if necessary (e.g., changing a bulleted list to a definition list).
* If **\<ul empty=”true”\>** is used for indentation, this will be replaced with a more appropriate tag such as [\<blockquote\>](/rfcxml-vocabulary#blockquote), [\<aside\>](/rfcxml-vocabulary#aside), or **\<t indent=”6″\>**.
* Adjust [\<table\>](/rfcxml-vocabulary#table) formatting if needed.
* Subscripts and superscripts are tagged with [\<sub\>](/rfcxml-vocabulary#sub) and [\<sup\>](/rfcxml-vocabulary#sup) respectively.
* Add [\<contact\>](/rfcxml-vocabulary#contact) elements around each person’s name.
* Remove any markdown source and any empty paragraphs.
* Any long-format references to RFCs and Internet-Drafts are updated to use the [\<xi:xinclude\>](/references-in-rfcxml#inserting-references-from-a-library) mechanism so that information from the citation library can be pulled into the document.
* Any citation tags are updated to use [\<displayreference\>](/rfcxml-vocabulary#displayreference). For example, this RFCXML:
```    <xref target="URI"/>
    <reference anchor="URI" target="https://www.rfc-editor.org/info/rfc3986"> 
      ... 
    </reference>
```
  is changed to the following:
```    <xref target="RFC3986"/>
    <displayreference target="RFC3986" to="URI"/>
    <xi:include href="https://bib.ietf.org/public/rfc/bibxml/reference.RFC.3986.xml"/>
```

## Copy editing
During `First Edit`, the document is copy edited to find and correct errors and to ensure that the document conforms to the [style guide](https://www.rfc-editor.org/authors/rfc-style-guide/). See [Language and Style](/language-and-style) for details.

## Reference checking and editing
The references in the document are checked for accuracy and stability and, where needed, edited for correctness. See [reference style guidance](/reference-style-guidance) for details.

## IANA processing
If the document contains IANA actions, such as creating or updating an IANA registry, then IANA will start their processing when the document is approved for publication. IANA processing usually takes place in parallel with editing.

Occasionally IANA processing can take longer than editing, for example, if IANA is waiting for a designated expert to respond. In which case, the document will be shown as blocked and "IANA Hold", until the IANA processing is complete. Once IANA has completed their actions, the document will 

# Second Edit

During `Second Edit`, a senior editor reviews the formatting, copy edits, and the team's proposed questions to authors.

If there is an IANA Considerations section, the senior editor reviews the messages regarding IANA actions, compares the information within the document to the information within the registry, and updates the section. If there are any issues with the IANA registry itself, these are noted for discussion with IANA during Final Review. 

If there are code components such as YANG modules, XML, or ABNF, the senior editor validates them with automated tools and notes any issues to discuss with authors during final approval.

Once `Second Edit` is complete, the senior editor launches `Final Review` (formerly known as AUTH48).

# Authors' Final Review
After editing, the document then enters `Final Review`, when the changes made by the RPC are shared with the authors for their approval. 

`Final Review` begins with an email sent to the authors asking them to complete the following actions:
1. Review and resolve any questions raised by the RPC editors. These are included in an attached RFCXML file as XML comments and they are also sent in a subsequent email.
2. Review any changes submitted by coauthors. The RPC assume that if authors do not speak up that they agree to changes submitted by coauthors.
3. Review the full content of the document, as this cannot change once the RFC is published. 
4. Review the copyright notice and legends as defined in RFC 5378 and the Trust Legal Provisions (TLP – https://trustee.ietf.org/license-info/).
5. Review the markup in the RFCXML file to ensure that elements of content are correctly tagged. 
6. Review the PDF, HTML, and TXT files to ensure that the formatted output, as generated from the RFCXML file, is reasonable. 

Instructions are provided on how an author can submit changes and how to give final approval for the document to be published. Sometimes this process involves multiple discussions about the edits, alternative edits proposed by the authors, and negotiation. 

If the authors make any changes that seem beyond editorial in nature, e.g., addition of new text, deletion of text, and technical changes, then the RPC will seek approval for those changes from the originating stream.

`Final Review` finishes when **all** authors of the document give their final approval.

If it was determined that an IANA registry needed updates, the RPC editor will request that IANA make those updates. 

## Unavailable authors
There may be an occasion when one of the authors is no longer available, in which case the remaining authors can opt for one of the following paths:

1. The unavailable author can be removed as an author and moved to the Acknowledgements section.
2. The unavailable author can be removed as an author and moved to the Contributors section.
3. A stream manager can approve the document (during `Final Review`) in place of the unavailable author. (See the [IESG Statement on Final Review State](https://www.ietf.org/iesg/statement/auth48.html).)

Option 3 is typically used in instances where the unavailable author made significant contributions to the document, so the other authors are not comfortable removing the individual from the author list.

# Exceptional cases
There are a number of reaons that a document can be blocked from further processing.

## Author Input Required
Sometimes the editors have questions for the authors that need to be resolved before they can move forward with copy editing the document. When this is the case, the document is shown as `Author Input Required` until the answers are received.

## Tools Issue
Occasionally, at the end of `Final Review` publication of the document is on hold pending the resolution of an issue with the software tools used to create the pubished versions.  For example, if there is an error in the PDF generation. In these circumstances, the document is labeled as `Tools Issue` until the issue is resolved.

## Stream Hold
Sometimes a stream asks for a document to be held or the editing process raises issues that lead to technical discussions (e.g., involving the working group and an Area Director). In this case, the document is labeled as `Stream Hold` until the issue is resolved.

## Withdrawn 
A document may occasionally be withdrawn from the queue, e.g., because a stream requests that it be withdrawn.

# Publication
When an RFC is published, an announcement is sent to the ietf-announce and rfc-dist mailing lists. The URL for the info page of an RFC is of the form: https://www.rfc-editor.org/info/rfcXXXX. The RFC Editor maintains a list of [the most recently published RFCs (RSS Feed)](https://www.rfc-editor.org/rfcrss.xml).
