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
RFCXML is an XML language, used as the preferred format for Internet-Drafts and the canonical format for published RFCs since RFC 8650 in November 2019.  It is documented on this site and formally specified in a RELAX NG Compact Syntax (RNC) schema. RFCXML documents can be fully validated against the schema.

The [RFCXML vocabulary reference](/rfcxml-vocabulary) documents all of the elements and attributes and their usage and allowed values.  

We recommend that authors start an I-D using a template from [Templates and Schemas](/templates-and-schemas) as this will simplify the process.

Authors will normally want to render their RFCXML I-D into more readable output and that process is explained in [Rendering and converting](/rendering-and-converting).

RFCXML was previously known as the "xml2rfc vocabulary".

# Background
v1 of RFCXML was documented in RFC2629, published in 1999, when the preferred format for I-Ds was plain text and the canonical format for RFCs was nroff.  This used a DTD for the formal specification.

v2 was documented in RFC 7749, published in February 2016, and switched to a RELAX NG Compact Syntax (RNC) schema.  v2, is still actively used as some of the tools that process RFC XML do not fully support v3 or still default to v2. 

v3 was documented in RFC 7991, published in December 2016 but following publication a number of changes were made to the schema and so RFC 7991 cannot be considered a normative reference for RFCXML. The authoritative source of documentation for the schema as it currently exists, is this site in [RFCXML vocabulary reference](/rfcxml-vocabulary).  For information only, the background to these changes is documented in the [implementation notes for RFC 7991](https://datatracker.ietf.org/doc/html/draft-levkowetz-xml2rfc-v3-implementation-notes-11) (though it does not cover everyhing and there have been some further changes since that was written) and a more recent attempt to document those changes in [The "xml2rfc" version 3 Vocabulary as Implemented](https://datatracker.ietf.org/doc/draft-irse-draft-irse-xml2rfcv3-implemented/).

# The 'prep' tool

Published RFCs go through a 'prep' process that makes multiple changes to the RFCXML in order to support the long time archival nature of RFCs.  Key aspects of the prep tool are documented in RFC 7998.  
