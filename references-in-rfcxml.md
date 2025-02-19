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
RFCXML uses references that are encoded in a format called BibXML, as defined in [RFC 7991](https://www.rfc-editor.org/info/rfc7991). To simplify the process of inserting references, the IETF maintains a set of online citation libraries as follows:
* For RFCs the official site is [rfc-editor.org](https://rfc-editor.org/). The information page for each RFC has a link to the BibXML file.
* For RFCs, Internet-Drafts, and documents produced by the W3C, 3GPP, IANA and NIST, the new site is [bib.ietf.org](https://bib.ietf.org) (at the time of writing, this site has only just gone live and some usability issues are still to be resolved). Many of these sets of references can be downloaded as a set for offline access.

# Creating the References Section
<!-- TH: Do we need a section on creating the References section? -->

## Two sections: Normative and Informative References
To create the two reference sections, use the [**\<name\>**](/rfcxml-vocabulary#name) element (child of the [**\<references\>**](/rfcxml-vocabulary#references) element) as follows:
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

## Listing references in alphabetical order
References can be listed in alphanumeric order by citation tag by setting the attribute **sortRefs** to "true" in the [**\<rfc\>**](/rfcxml-vocabulary#rfc) element. 

Note that **sortRefs** only has an effect if **symRefs** is "true".

For example:
```xml
<rfc ... symRefs="true" sortRefs="true">
```

# Adding reference entries to the References Section
Reference entries can be added to the References Section using two methods:
* Using an `xi:include` to automatically add citation data from the BibXML service
* manually constructing references in a [**\<reference\>**](/rfcxml-vocabulary#reference) element

Manually constructed references in RFCXML generally use the following XML syntax:

```xml
<reference anchor="CITATION-TAG" target="URL">
  <front>
    <title>TITLE</title>
    <author initials="" surname="" fullname="">
       <organization />
    </author>
    <date month="MONTH" year="YEAR"/>
  </front>
  <seriesInfo name="NAME" value="VALUE"/>
  <seriesInfo name="DOI" value="VALUE"/>
  <refcontent>Journal Name, vol. #, no. #, pp. 1-10</refcontent>
</reference>
```

The BibXML service allows for the use of an `xi:include` to insert a given BibXML file's reference information automatically.

An `xi:include` in RFCXML uses the following XML syntax:

```xml
<xi:include href="<URL for the BibXML file>"/>
```

## Using the IETF BibXML service and xi:includes
The [BibXML service](https://bib.ietf.org/) is a database which provides a bibliographic search service. The citation data from the BibXML service can be added to the [**\<references\>**](/rfcxml-vocabulary#references) section of a draft using an `xi:include`. 

Currently, the use of an `xi:include` is recommended when adding references for the following sources:

* RFCs
* I-Ds
* IANA registries and subregistries

An `xi:include` that points to the reference libraries for documents from W3C, IEEE, 3GPP, and NIST may not contain up-to-date or correct information at this time.

## Creating references to Requests for Comments (RFCs)

### Inserting RFC references using an xi:include

An `xi:include` is the recommended method for inserting a reference to an RFC into the References section. The URL for an RFC's BibXML file can be found on the RFC's info page on rfc-editor.org  - for example, https://www.rfc-editor.org/info/rfc7322 - or by searching for the RFC using the [BibXML service](https://bib.ietf.org/).

BibXML URLs for RFC references use the following template:

```xml
<xi:include href="https://bib.ietf.org/public/rfc/bibxml/reference.RFC.7372.xml"/>
```

### Inserting RFC references manually
If it is necessary to insert a reference to an RFC manually, then the following format is recommended:

```xml
<reference anchor="RFC7322" target="https://www.rfc-editor.org/info/rfc7322">
  <front>
    <title>RFC Style Guide</title>
    <author fullname="H. Flanagan" initials="H." surname="Flanagan"/>
    <author fullname="S. Ginoza" initials="S." surname="Ginoza"/>
    <date month="September" year="2014"/>
  </front>
  <seriesInfo name="RFC" value="7322"/>
  <seriesInfo name="DOI" value="10.17487/RFC7322"/>
</reference>	
```

## Creating references to Internet-Drafts (I-Ds)
### Inserting I-D references using bibxml
BibXML URLs for I-Ds use the following template:

```xml
<xi:include href="https://bib.ietf.org/public/rfc/bibxml3/reference.I-D.foo.xml"/>
```

#### Referencing different versions of an I-D
Note there are two ways to create the URL for an I-D `xi:include`. 

The first way, where the draft string is constructed as "I-D.<name without "draft-" or the version number>", will point to the most current version of the I-D.
For example:
```xml
<xi:include href="https://bib.ietf.org/public/rfc/bibxml3/reference.I-D.rpc-rfc7322bis.xml"/>
```

This is helpful if you do not want to track and update the reference entry each time the I-D is updated. 

However, if you want to point to a specific version of an I-D, the draft string should include both "draft-" and the version number. 
For example: 
```xml
<xi:include href="https://bib.ietf.org/public/rfc/bibxml3/reference.I-D.draft-rpc-rfc7322bis-02.xml"/>
```

### Inserting I-D references manually
If it is necessary to insert a reference to an RFC manually, then the following format is recommended:

```xml
<reference anchor="I-D.rpc-rfc7322bis" target="https://datatracker.ietf.org/doc/html/draft-rpc-rfc7322bis-02">
   <front>
      <title>RFC Style Guide</title>
      <author initials="S." surname="Ginoza" fullname="Sandy Ginoza">
         <organization>RFC Production Center</organization>
      </author>
      <author initials="J." surname="Mahoney" fullname="Jean Mahoney">
         <organization>RFC Production Center</organization>
      </author>
      <author initials="A." surname="Russo" fullname="Alice Russo">
         <organization>RFC Production Center</organization>
      </author>
      <date month="January" day="24" year="2025" />
   </front>
   <seriesInfo name="Internet-Draft" value="draft-rpc-rfc7322bis-02" />
   
</reference>
```

## Creating references to BCPs and STDs
### Inserting a Subseries Reference using an xi:include
An `xi:include` is the recommended method for inserting references to RFC subseries documents.

The URL for the `xi:include` can be found on the subseries' info page - for example: https://www.rfc-editor.org/info/bcp195 - or by searching the BibXML database.

```xml
<xi:include href="https://bib.ietf.org/public/rfc/bibxml9/reference.BCP.0195.xml"/> 
```

### Inserting a Subseries Reference manually
<!-- TODO Should we still mention this? -->
If it is necessary to insert a reference to a subseries document manually, then the following format is recommended:

```xml
<referencegroup anchor="BCP195" target="https://www.rfc-editor.org/info/bcp195">
  <xi:include href="https://bib.ietf.org/public/rfc/bibxml/reference.RFC.8996.xml"/>
  <xi:include href="https://bib.ietf.org/public/rfc/bibxml/reference.RFC.9325.xml"/>
</referencegroup>
```

## Creating references to IANA registries and subregistries
### Inserting a IANA reference using an xi:include
For a registry:
```xml 
<xi:include href="https://bib.ietf.org/public/rfc/bibxml8/reference.IANA.xml-registry.xml"/>
```

For a subregistry:
```xml
<xi:include href="https://bib.ietf.org/public/rfc/bibxml8/reference.IANA.xml-registry_publicid.xml"/>
```

### Inserting an IANA reference manually
For a registry:

```xml
<reference anchor="IANA_xml_registry" target="https://www.iana.org/assignments/xml-registry">
  <front>
    <title>IETF XML Registry</title>
    <author>
      <organization>IANA</organization>
    </author>
  </front>
</reference>
```

For a subregistry:

```xml
<reference anchor="IANA_xml_registry_publicid" target="https://www.iana.org/assignments/xml-registry">
  <front>
    <title>publicid</title>
    <author>
      <organization>IANA</organization>
    </author>
  </front>
</reference>

```

### Note on URLs for IANA registries and subregistries
Based on guidance from IANA, URLs for IANA references must use the "short" version of the URL that doesn't include a file extension or a URI fragment.

For example:

This URL is correct: https://www.iana.org/assignments/xml-registry 

While this URL is incorrect: https://www.iana.org/assignments/xml-registry/xml-registry.xhtml

(For more information see IANA's [Guidance for RFC Authors](https://www.iana.org/help/protocol-registration))

# Reference tags and in-text citations
## Editing citation tags
### Changing a reference tag to use a nickname
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

### Changing all reference tags from symbolic to numeric
For example, `[1]` instead of `[RFC2119]`

In the [**\<rfc\>**](/rfcxml-vocabulary#rfc) element, set the attribute **symRefs** to "false" for symbolic references. This makes reference tags be numeric, e.g., `[1]`, instead of symbolic, e.g., `[RFC2119]`.


## Inserting an in-text citation

To cite a reference in the text of the document do the following:

Locate the reference anchor for the reference:

Add an [**\<xref\>**](/rfcxml-vocabulary#xref) element with the target attribute set to the reference anchor (in this case, "RFC7322").

```xml
See <xref target="RFC7322"/> for more information. 
```

Which yields:

```
See [RFC7322] for more information.
```

See [Part 2 of the RFC Style Guide](https://www.rfc-editor.org/styleguide/part2/#citation_usage) for guidance on the correct use of in-text citations.

# Section References
## Cross-referencing to another section within the document
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

## Linking to multiple sections within a document 
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

## Referring to a section in another RFC
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

# Linking to multiple sections in an RFC
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
