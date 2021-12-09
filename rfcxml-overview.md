---
title: RFCXML overview and background
description: 
published: true
date: 2021-12-09T03:43:42.456Z
tags: 
editor: markdown
dateCreated: 2021-11-03T13:17:49.168Z
---

# Overview
RFCXML is an XML language, used as the preferred format for Internet-Drafts and the canonical format for published RFCs since RFC 8650 in November 2019.  It is documented in RFCs and formally specified in a RELAX NG Compact Syntax (RNC) schema. The RNC schema only allows specified XML elements and attributes to be used, which means that RFCXML documents can be fully validated against the schema.

The [RFCXML vocabulary reference](/rfcxml-vocabulary) documents all of the elements and attributes and their usage and allowed values.  

We recommend that authors start an I-D using a template from [Templates and Schemas](/templates-and-schemas) as this will simplify the process.

Authors will normally want to render their RFCXML I-D into more readable output and that process is explained in [Rendering and converting](/rendering-and-converting).

RFCXML was previously known as the "xml2rfc vocabulary".

# Background
v1 of RFCXML was documented in RFC2629, published in 1999, when the preferred format for I-Ds was plain text and the canonical format for RFCs was nroff.  This used a DTD for the formal specification.

v2 was documented in RFC 7749, published in February 2016, and switched to a RELAX NG Compact Syntax (RNC) schema.  v2, is still actively used as some of the tools that process RFC XML do not fully support v3 or still default to v2. 

v3 was documented in RFC 7991, published in December 2016. Since the publication of RFC 7991, a number of changes have been made to the schema but these have not yet made it into an RFC though they are documented in the [RFCXML vocabulary reference](/rfcxml-vocabulary).  The background to these changes is documented in the [implementation notes for RFC 7991](https://datatracker.ietf.org/doc/html/draft-levkowetz-xml2rfc-v3-implementation-notes-11).

# The 'prep' tool

Published RFCs go through a 'prep' process that makes multiple changes to the RFCXML in order to support the long time archival nature of RFCs.  Key aspects of the prep tool are documented in RFC 7998.  
