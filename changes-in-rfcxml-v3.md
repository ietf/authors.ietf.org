---
title: Changes in RFCXML v3
description: 
published: true
date: 2021-11-04T19:26:45.619Z
tags: 
editor: markdown
dateCreated: 2021-11-04T19:26:45.619Z
---

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
These were special elements associated with text before or after figures and tables. The recommended replacments is to add [**\<t\>**](/rfcxml-vocabulary#t) paragraphs before and/or after the figure or table.
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

