---
title: Upgrading from v2
description: 
published: true
date: 2021-11-09T15:44:38.811Z
tags: 
editor: markdown
dateCreated: 2021-11-04T19:26:45.619Z
---

# Converting an XML file from v2 to v3
## Initial conversion
There are two ways:
* Use the [Author Tools](hhtps://author-tools.ietf.org) web service
* Use xml2rfc locally.  On the command line: `xml2rfc --v2v3 inputfile.xml`. You can use the `--add-xinclude` option to replace RFC and I-D reference elements with the appropriate `xi:include` element.

## Futher updates after converting an XML file from v2 to v3
You may want to do the following (for the sake of generating good output and having a semantically accurate XML file):

* Review each list.
  * Is it really a list? Or should indentation be added in another manner, e.g., [**\<blockquote\>**](/rfcxml-vocabulary#blockquote).
  * If so, should it be [**\<dl\>**](/rfcxml-vocabulary#dl), [**\<ul\>**](/rfcxml-vocabulary#ul), or [**\<ol\>**](/rfcxml-vocabulary#ol)?
* Review each [**\<artwork\>**](/rfcxml-vocabulary#artwork).
  * Should it be [**\<sourcecode\>**](/rfcxml-vocabulary#sourcecode)? If so, what type?
  * Should it be a table?
* Check for misuse of lists where [**\<aside\>**] or [**\<blockquote\>**] might be more appropriate.
* Search for URLs; should these be [**\<eref\>**](/rfcxml-vocabulary#eref) or should a full reference be created and linked using [**\<xref\>**]?
* Look for equations or other text where new features may improve clarity.
* Search for hardcoded citation tags (e.g., `[RFC5234]`) and update to [**\<xref\>**](/rfcxml-vocabulary#xref)s.
* Search for "section" and make a link for any section number in RFCs and I-Ds (using [**\<xref\>**](/rfcxml-vocabulary#xref) with **section** and **sectionFormat** attributes).
* Review postal addresses of authors; has each address been tagged correctly?

## Fixing common errors after the upgrade from v2 to v3

1. xml2rfc warns *"Setting consensus="true" for IETF STD document"*.
This is being discussed on the xml2rfc-dev list. You should disregard this warning for now.
2. xml2rfc fails with *"Reserved anchor name: section-.... Don't use anchor names beginning with one of u-, section-, iref-, figure-, table-"*.
Rename your section.

Other errors can appear if you're using a helper tool to write your XML:

### kramdown-rfc2629

1. If you don't specify a date for a reference, xml2rfc fails with *"Expected \<date\> attribute "year" to be an integer, but found "n.d.""*
This issue is tracked in https://github.com/cabo/kramdown-rfc2629/issues/64. Add `date: false` to your reference to avoid the error.

### i-d-template
1. xml2rfc warns that *"The 'docName' attribute of the \<rfc/\> element should have a revision number as the last component: docName="draft-foo-bar-02"."*
This issue is tracked in https://trac.ietf.org/tools/xml2rfc/trac/ticket/439. You can't modify your source to avoid it.

# New features with v3
Some highlights are including Unicode characters, text formatting, and SVG diagrams. For complete details, see Section 1.3 of RFC7991.

# Deprecated syntax
## Elements
The following elements still appear in the schema but have been deprecated and should not be used. 

* **\<texttable\>** **\<ttcol\>** **\<c\>**
These three were previously used to create tables and have now been replaced with [**\<table\>**](/rfcxml-vocabulary#table), [**\<thead\>**](/rfcxml-vocabulary#thead), [**\<tbody\>**](/rfcxml-vocabulary#tbody), [**\<tfoot\>**](/rfcxml-vocabulary#tfoot), [**\<tr\>**](/rfcxml-vocabulary#tr) , [**\<th\>**](/rfcxml-vocabulary#th) and [**\<td\>**](/rfcxml-vocabulary#td) elements as found in HTML.
* **\<facsimile\>**
This is is no longer used as facsmilies are no longer used and email is a more useful method of contact.
* **\<format\>**
This was used in [**\<reference\>**](/rfcxml-vocabulary#reference) and is replaced with the use of the **target** attribute in [**\<reference\>**](/rfcxml-vocabulary#reference).
* **\<list\>**
This was used for a list and has been replaced with [**\<ul\>**](/rfcxml-vocabulary#ul), [**\<ol\>**](/rfcxml-vocabulary#ol), [**\<dl\>**](/rfcxml-vocabulary#dl) and [**\<li\>**](/rfcxml-vocabulary#li) as found in HTML.
* **\<postamble\>** **\<preamble\>**
These were special elements associated with text before or after figures and tables. The recommended replacement is to add [**\<t\>**](/rfcxml-vocabulary#t) paragraphs before and/or after the figure or table.
* **\<relref\>**
The functionality of the [**\<xref\>**](/rfcxml-vocabulary#xref) element has extended to replicate the functionality of this element
* **\<spanx\>**
This was a generic text formatting element, now replaced with specific text attribute elements:
  * [**\<em\>**](/rfcxml-vocabulary#em) for emphasised text (typically rendered as slanted or italic text )
  * [**\<strong\>**](/rfcxml-vocabulary#strong) for boldly rendered text
  * [**\<sub\>**](/rfcxml-vocabulary#sub) for subscript text
  * [**\<sup\>**](/rfcxml-vocabulary#sup) for superscript text
  * [**\<tt\>**](/rfcxml-vocabulary#tt) for teletype text (typically a generic mono-spaced text).
* **\<vspace\>**
This was used for vertical spacing and has been replaced by an attribute `newline="true"` when used with definition lists, in order to make the definition start on a new line. For other use cases, there is no replacement.

## Attributes
The following attributes still appear in the schema for non-deprecated elements but have been deprecated and should not be used.

* [**\<artwork\>**](/rfcxml-vocabulary#artwork)
  * **height**
  * **width**
* [**\<figure\>**](/rfcxml-vocabulary#figure)
  * **align**
  * **alt**
  * **height**
  * **src**
  * **suppress-title**
  * **title**
  * **width**
* [**\<note\>**](/rfcxml-vocabulary#note)
  * **title**
* [**\<reference\>**](/rfcxml-vocabulary#reference)
  * **title**
* [**\<section\>**](/rfcxml-vocabulary#section)
  * **title**
* [**\<seriesInfo\>**](/rfcxml-vocabulary#seriesInfo)
  * **status**
  * **stream**
* [**\<t\>**](/rfcxml-vocabulary#t)
  * **hangText**
  Use a definition list ([**\<dl\>**](/rfcxml-vocabulary#dl)) instead.

