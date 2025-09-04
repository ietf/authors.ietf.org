---
title: References in RFCXML
description: 
published: true
date: 2025-09-04T03:41:49.869Z
tags: 
editor: markdown
dateCreated: 2021-11-04T23:45:18.949Z
---

# Introduction
RFCXML supports references through the [**\<reference\>**](/rfcxml-vocabulary#reference) and [**\<referencegroup\>**](/rfcxml-vocabulary#referencegroup) elements. 

# Inserting references
## The IETF library of pre-built references
To simplify the process of inserting references, the IETF maintains libraries of pre-built reference files for RFCs and Internet-Drafts, and for documents produced by the W3C, 3GPP, IANA and NIST, on the site [bib.ietf.org](https://bib.ietf.org). These pre-built references files are referred to as BibXML files though they are only XML excerpts, not fully XML documents.

In addition, for RFCs the information page for each RFC on [rfc-editor.org](https://rfc-editor.org/) has a link to the BibXML file.

To use a pre-built references file, use an `xi:include` in the [**\<references\>**](/rfcxml-vocabulary#references) section that points to a citation in the library.  Examples below.

### Library references to RFCs
The following creates a reference to an RFC:
```xml
<xi:include href="https://bib.ietf.org/public/rfc/bibxml/reference.RFC.2119.xml"/>
```
That creates the anchor `RFC2119`.

### Library references to Internet-Drafts
For an Internet-Draft, the citation filename uses the draft string. Note there are two ways to create the URL. The first way, where the draft string is constructed as "I-D.<name without "draft-" or the version number>", will point to the most current version of the I-D, for example:
```xml
<xi:include href="https://bib.ietf.org/public/rfc/bibxml3/reference.I-D.daley-meeting-network-requirements.xml"/>
```
If you want to point to a specific version of an I-D, the draft string should include both "draft-" and the version number. For example: 
```xml
<xi:include href="https://bib.ietf.org/public/rfc/bibxml3/reference.I-D.daley-meeting-network-requirements-00.xml"/>
```
That creates the anchor `I-D.daley-meeting-network-requirements`.

### Library references to BCPs and STDs
References to BCPs and STDs are added in a similar way to RFCs:
```xml
 <xi:include href="https://bib.ietf.org/public/rfc/bibxml-rfcsubseries/reference.BCP.14.xml"/>
```
That creates the anchor `BCP14`.

**Please note** that BCP and STD references are implemented as a [**\<referencegroup\>**](/rfcxml-vocabulary#referencegroup) element that contains within it full [**\<reference\>**](/rfcxml-vocabulary#reference) elements for each of the components RFCs that makes up that BCP or STD.  This automatically adds them as references and so they do not need to be added separately (doing so will give an XML error).  It also means that the rendered output lists all of the component RFCs.


### Library references to W3C, 3GPP, IANA and NIST documents
These are found individually by searching on the [bib.ietf.org](https://bib.ietf.org) site. (The UI is not very friendly and is due to be replaced).  For example, searching that site for "W3C XSLT" leads to a reference that is then included as:
```xml
 <xi:include href="https://bib.ietf.org/public/rfc/bibxml4/reference.W3C.xslt.xml"/>
```
That creates the anchor `W3C.xslt`.


## Inserting references manually
Full references should only be used where an `xi:include` cannot be used, or where the authors wish to specify different BibXML from that supplied in the citation libraries.  The following complete example is for an RFC (verbatim contents of [https://bib.ietf.org/public/rfc/bibxml/reference.RFC.2119.xml](https://bib.ietf.org/public/rfc/bibxml/reference.RFC.2119.xml)):
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
<reference anchor="org_ref" target="https://www.example.com/">
  <front>
    <title>Organisational Reference</title>
    <author>
      <organization>Example Inc.</organization>
    </author>
    <date year="2001"/>
  </front>
</reference>
```

## Referencing a URL
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

# Citing a reference
To cite a reference in your text, use an [**\<xref\>**](/rfcxml-vocabulary#xref) element where the value of its target attribute corresponds to the value of the anchor attribute of the reference element, e.g., `<xref target="RFC2119" />`. For references constructed with  `xi:include`, the values of the anchors are explained above.


## Citing a section in another document such as another RFC

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

## Citing multiple sections within a document 
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
## Citing multiple sections in a different document 
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
<xi:include href="https://bib.ietf.org/public/rfc/bibxml/reference.RFC.7296.xml"/>
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



# Supporting tools

## bibtex2rfc
Authors who often cite academic publications may find the [bibtex2rfc](https://github.com/yaronf/bibtex2rfc) tool, which converts BibTeX references into valid RFCXML references, helpful since most databases include bibliographic entries in BibTex format.
