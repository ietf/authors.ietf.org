---
title: References in RFCXML
description: 
published: true
date: 2021-11-17T10:02:08.318Z
tags: 
editor: markdown
dateCreated: 2021-11-04T23:45:18.949Z
---

# Introduction
RFCXML uses references that are encoded in a format called BibXML, as defined in RFC 7991. To simplify the process of inserting references, the IETF maintains a set of online citation libraries as follows:
* For RFCs the official site is [rfc-editor.org](https://rfc-editor.org/). The information page for each RFC has a link to the BibXML file.
* For RFCs, Internet-Drafts, and documents produced by the W3C, 3GPP, IANA and NIST, the new site is [bib.ietf.org](https://bib.ietf.org) (at the time of writing, this site has only just gone live and some usability issues are still to be resolved). Many of these sets of references can be downloaded as a set for offline access.

# Inserting references from a library
Use an `xi:include` in the [**\<references\>**](/rfcxml-vocabulary#references) section that points to a citation in the library as follows.
```xml
<xi:include href="https://www.rfc-editor.org/refs/bibxml/reference.RFC.2119.xml"/>
```
For an Internet-Draft, the citation filename uses the draft string. For example:
```xml
<xi:include href="https://bib.ietf.org/public/rfc/bibxml3/reference.I-D.ietf-wgname-topic.xml"/>
```
All are cited textually in the same manner, by using [**\<xref\>**](/rfcxml-vocabulary#xref) elements where the target corresponds to the anchor of the reference element, e.g., `<xref target="RFC2119" />`. 
* The anchors for RFCs are "RFCNNNN" (4 digits, using leading zeros)
* The anchors for Internet-Drafts are "I-D.<name without "draft-" or the version number>".

# Inserting references manually
The following complete example is for an RFC (verbatim contents of [https://www.rfc-editor.org/refs/bibxml/reference.RFC.2119.xml](https://www.rfc-editor.org/refs/bibxml/reference.RFC.2119.xml)). Full references should only be used where an `xi:include` cannot be used, or where the authors wish to specify different BibXML from that supplied in the citation libraries:
```xml
<reference anchor="RFC2119" target="https://www.rfc-editor.org/info/rfc2119">
  <front>
    <title>Key words for use in RFCs to Indicate Requirement Levels</title>
    <author initials="S." surname="Bradner" fullname="S. Bradner">
      <organization/>
    </author>
    <date year="1997" month="March"/>
    <abstract>
      <t>In many standards track documents several words are used to signify the requirements in the specification. These words are often capitalized. This document defines these words as they should be interpreted in IETF documents. This document specifies an Internet Best Current Practices for the Internet Community, and requests discussion and suggestions for improvements.
      </t>
    </abstract>
  </front>
  <seriesInfo name="BCP" value="14"/>
  <seriesInfo name="RFC" value="2119"/>
  <seriesInfo name="DOI" value="10.17487/RFC2119"/>
</reference>
```
A bare minimum example is:
```xml
<reference anchor="min_ref">
  <front>
    <title>Minimal Reference</title>
    <author initials="authInitials" surname="authSurName">
      <organization/>
    </author>
    <date year="2006"/>
  </front>
</reference>
```
An example of a reference written by an organisation is:
```xml
<reference anchor="org_ref" target="http://www.example.com/">
  <front>
    <title>Organisational Reference</title>
    <author>
      <organization>Example Inc.</organization>
    </author>
    <date year="2001"/>
  </front>
</reference>
```

# Changing all reference tags from symbolic to numeric
For example, `[1]` instead of `[RFC2119]`

In the [**\<rfc\>**](/rfcxml-vocabulary#rfc) element, set the attribute **symRefs** to "false" for symbolic references. This makes reference tags be numeric, e.g., `[1]`, instead of symbolic, e.g., `[RFC2119]`.

# Changing a reference tag to use a nickname
For example, `[IKEv2]` instead of `[RFC4306]`

Use the [**\<displayreference\>**](/rfcxml-vocabulary#displayreference) element and set the **to** attribute to the nickname. Tip: place it before the first references element. For example:
```xml
<displayreference target="RFC7296" to="IKEv2"/>
<references>
[...]
<xi:include href="https://www.rfc-editor.org/refs/bibxml/reference.RFC.7296.xml"/>
```
yields:
```
  [IKEv2]    Kaufman, C., Hoffman, P., Nir, Y., Eronen, P., and T. 
             Kivinen, "Internet Key Exchange Protocol Version 2 
             (IKEv2)", STD 79, RFC 7296, DOI 10.17487/RFC7296, 
             October 2014, <https://www.rfc-editor.org/info/rfc7296>.
```
# Listing references in alphabetical order

In the [**\<rfc\>**](/rfcxml-vocabulary#rfc) element, set the attribute **sortRefs** to "true". Note that **sortRefs** only has an effect if **symRefs** is "true".

# Referencing a URL

The [**\<eref\>**](/rfcxml-vocabulary#eref) element for an external reference creates a link in the HTML output. For example:
```xml
<eref target="https://www.w3.org" />
```
yields 
```html
<a href ="https://www.w3.org"/>
```
and
```xml
<eref target="https://www.w3.org">W3C Home Page</eref>
```
yields
```html
<a href ="https://www.w3.org">W3C Home Page</a>
```

Another option is using xref and creating a reference that uses the **target** attribute for the URL. For example:
```xml
<reference anchor="W3C" target="https://www.w3.org/">
  <front>
    <title>World Wide Web Consortium (W3C)</title>
    <author/>
  </front>
</reference>
```
yields
```
  [W3C]     "World Wide Web Consortium (W3C)", <https://www.w3.org/>.
```
# Two sections: Normative and Informative References

Use the [**\<name\>**](/rfcxml-vocabulary#name) element (child of the [**\<references\>**](/rfcxml-vocabulary#references) element) as follows:
```xml
<back>
  <references>
    <name>References</name>
    <references>
      <name>Normative References</name>
      ...
    </references>
    <references>
      <name>Informative References</name>
      ...
    </references>
  </references>
</back>
```
# Creating a reference to a BCP (or STD) that contains multiple RFCs

Use [**\<referencegroup\>**](/rfcxml-vocabulary#referencegroup) with an `xi:include` for each RFC inside it:
```xml
<referencegroup anchor="STD78" target="https://www.rfc-editor.org/info/std78">
  <xi:include href="https://www.rfc-editor.org/refs/bibxml/reference.RFC.5343.xml"/>
  <xi:include href="https://www.rfc-editor.org/refs/bibxml/reference.RFC.5590.xml"/>
  <xi:include href="https://www.rfc-editor.org/refs/bibxml/reference.RFC.5591.xml"/>
  <xi:include href="https://www.rfc-editor.org/refs/bibxml/reference.RFC.6353.xml"/>
</referencegroup>
```
which yields
```
  [STD78]    Schoenwaelder, J., "Simple Network Management Protocol
             (SNMP) Context EngineID Discovery", STD 78, RFC 5343,
             September 2008.

             Harrington, D. and J. Schoenwaelder, "Transport Subsystem
             for the Simple Network Management Protocol (SNMP)",
             STD 78, RFC 5590, June 2009.

             Harrington, D. and W. Hardaker, "Transport Security Model
             for the Simple Network Management Protocol (SNMP)",
             STD 78, RFC 5591, June 2009.

             Hardaker, W., "Transport Layer Security (TLS) Transport
             Model for the Simple Network Management Protocol (SNMP)",
             STD 78, RFC 6353, July 2011.

             <https://www.rfc-editor.org/info/std78>
```
# Cross-referencing to another section

Make sure the section you want to reference has an **anchor** attribute. For example:
```xml
   <section anchor="s_using_lists">
```
Then, refer to it with an [**\<xref\>**](/rfcxml-vocabulary#xref) element:
```xml
  See <xref target="s_using_lists" />.
```
which yields
```html
  See <a href="#s_using_lists">Section 4.</a>
```
(where the number of that section is determined dynamically).

# Referring to a section in another document such as another RFC

Use [**\<xref\>**](/rfcxml-vocabulary#xref) and set the **sectionFormat** attribute to various options.

To construct `See Section 1.3 of [RFC7991]`, use "of" with the sectionFormat attribute:
```xml
   See <xref target="RFC7991" sectionFormat="of" section="1.3" />
```
To construct `See [RFC7991], Section 1.3`, use "comma" with the sectionFormat attribute:
```xml
   See <xref target="RFC7991" sectionFormat="comma" section="1.3" />
```
To construct `See [RFC7991] (Section 1.3)`, use "parens" with the sectionFormat attribute:
```xml
   See <xref target="RFC7991" sectionFormat="parens" section="1.3" />
```
To construct `See 1.3`, use "bare" with the sectionFormat attribute:
```xml
   See <xref target="RFC7991" sectionFormat="bare" section="1.3" />
```

When **sectionFormat** is not set at all, the output is the same as "of".

# Linking to multiple sections within a document 
For example, `See Sections 3 and 4.`

Use [**\<xref\>**](/rfcxml-vocabulary#xref) with the format attribute. For example, assuming the anchors for the relevant sections match the targets:
```xml
  See Sections <xref target="s_using_refs" format="counter" /> and
  <xref target="s_using_lists" format="counter" />.
```
yields the output:
```html
See Sections <a href="#s_using_refs">3</a> and <a href="#s_using_lists">4</a>.
```
Note: The **format** attribute can have the value "title", which displays the title of the section. For example,
```xml
  See Sections <xref target="s_using_refs" format="title" /> and
  <xref target="s_using_lists" format="title" />.
```
yields the output:
```html
  See <a href="#s_using_refs">Using References</a> and 
  <a href="#s_using_lists">Using Lists.</a>
```
# Linking to multiple sections in a different document 
For example, 'see Sections 5 and 6 in RFC 3550'.

Use [**\<xref\>**](/rfcxml-vocabulary#xref) with sectionFormat="bare". For example:
```xml
See Sections <xref target="RFC3550" section="5" sectionFormat="bare" /> and
<xref target="RFC3550" section="6" sectionFormat="bare" /> in
<xref target="RFC3550"/>.
```
yields the output:
```html
See Sections <a href="https://www.rfc-editor.org/rfc/rfc3550#section-5">5</a> 
and <a href="https://www.rfc-editor.org/rfc/rfc3550#section-6">6</a> in 
[<a href="#RFC3550">RFC3550</a>].
```

# Supporting tools

## bibtex2rfc
Authors who often cite academic publications may find the [bibtex2rfc](https://github.com/yaronf/bibtex2rfc) tool, which converts BibTeX references into valid RFCXML references, helpful since most databases include bibliographic entries in BibTex format.
