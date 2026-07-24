---
title: RFCXML and Markdown Syntax Comparison Tables
description: The Rosetta stone of RFCXML and Markdown
published: true
date: 2026-07-24T08:23:13.166Z
tags: 
editor: markdown
dateCreated: 2026-07-23T11:54:17.943Z
---

# RFCXML vs. kramdown-rfc syntax

A simplistic translation (a.k.a. Rosetta Stone) is below. For details and examples, please see:
- kramdown-rfc documentation: [Syntax](https://github.com/cabo/kramdown-rfc/wiki/Syntax) and [Syntax2](https://github.com/cabo/kramdown-rfc/wiki/Syntax2)
- [RFCXML vocabulary reference](https://authors.ietf.org/en/rfcxml-vocabulary)

## Common Features

<table class="inline">
	<thead>
	<tr class="row0">
		<th class="col0 leftalign"> <strong>Concept</strong>      </th><th class="col1 leftalign"> <strong>RFCXML</strong>          </th><th class="col2 leftalign"> <strong>kramdown-rfc</strong>     </th>
	</tr>
	</thead>
	<tr class="row1">
		<td class="col0 leftalign"> Abstract, middle, back  </td><td class="col1 leftalign"> &lt;abstract&gt;<br/>
&lt;middle&gt;<br/>
&lt;back&gt;<br/>
    </td><td class="col2 leftalign"> <code>--- abstract</code><br/>
 <code>--- middle</code><br/>
<code>--- back</code>  </td>
	</tr>
	<tr class="row2">
		<td class="col0 leftalign"> Artwork in figure  </td><td class="col1 leftalign"> <pre class="code">&lt;figure&gt;
 &lt;artwork&gt;foo&lt;/artwork&gt;
&lt;/figure&gt;</pre>
</td><td class="col2"> <pre class="code">~~~
foo
~~~</pre>
</td>
	</tr>
	<tr class="row3">
		<td class="col0"> Artwork with anchor </td><td class="col1 leftalign"> <pre class="code">&lt;figure title=&quot;Sample&quot; anchor=&quot;sample-fig&quot;&gt;
&lt;artwork&gt;&lt;![CDATA[ 
0 1 2 3 
+-+-+-+-+
| Label |
+-+-+-+-+
]]&gt;&lt;/artwork&gt;
&lt;/figure&gt;</pre>
</td><td class="col2 leftalign"> <pre class="code">~~~
0 1 2 3 
+-+-+-+-+
| Label |
+-+-+-+-+
~~~
{: title=&quot;Sample&quot; #sample-fig}</pre>
</td>
	</tr>
	<tr class="row4">
		<td class="col0"> SVG artwork </td><td class="col1"> <pre class="code">&lt;figure&gt;
  &lt;artset&gt;
    &lt;artwork type=&quot;svg&quot;&gt;
      &lt;svg...
      {SVG code} 
      &lt;/svg&gt;
    &lt;/artwork&gt;
    &lt;artwork type=&quot;ascii-art&quot;&gt;&lt;&lt;![CDATA[
    {ASCII artwork}
    ]]&gt;&lt;/artwork&gt;
  &lt;/artset&gt;
&lt;/figure&gt;</pre>
</td><td class="col2"> <pre class="code">~~~ aasvg
+----------+
|  a box   |
+----------+
~~~</pre>

<p>
  Add “aasvg” to the ascii-art indicator (~~~)
</p>
</td>
	</tr>
	<tr class="row5">
		<td class="col0 leftalign"> Aside  </td><td class="col1 leftalign"> &lt;aside&gt;      </td><td class="col2"> <pre class="code">{:aside}
&gt; foo</pre>
</td>
	</tr>
	<tr class="row6">
		<td class="col0 leftalign"> Blockquote  </td><td class="col1 leftalign"> &lt;blockquote&gt;      </td><td class="col2"> <pre class="code">{:quote}
&gt; foo</pre>
</td>
	</tr>
	<tr class="row7">
		<td class="col0 leftalign"> Citation  </td><td class="col1 leftalign">
    	<pre class="prismjs"><code>&lt;xref target=“RFC9999”/&gt;<br/>
&lt;xref target=“I-D.ietf-blah-blah”/&gt;
</code></pre>
    	</td>
    	<td class="col2 leftalign">
    		<pre class="prismjs"><code>{{RFC9999}}<br/>
{{I-D.ietf-blah-blah}}</code></pre></td>
	</tr>
	<tr class="row8">
		<td class="col0 leftalign"> Citation with section number  </td><td class="col1 leftalign"> &lt;xref target=“RFC9999” section=“5”/&gt;      </td><td class="col2 leftalign"> <pre class="code">{{Section 5 of RFC9999}}</pre>
<pre class="code">{{RFC9999, Section 5}}</pre>
<pre class="code">{{!RFC9999, Section 5}}</pre>
</td>
	</tr>
	<tr class="row9">
		<td class="col0 leftalign"> Citation with multiple section numbers  </td><td class="col1 leftalign"> Sections &lt;xref target=“RFC9999” section=“5” sectionFormat=“bare”/&gt; and &lt;xref target=“RFC9999” section=“6” sectionFormat=“bare”/&gt; of &lt;xref target=“RFC9999”/&gt;    </td><td class="col2 leftalign"> <pre class="code">{{Sections 5 and 6 of RFC9999}}</pre>
<pre class="code">{{Sections 5 and 6 of ?RFC9999}}</pre>
</td>
	</tr>
	<tr class="row10">
		<td class="col0 leftalign"> Section, figure, or table pointer  </td><td class="col1 leftalign"> &lt;xref target=“intro”/&gt;      </td><td class="col2 leftalign"> <pre class="code">{{intro}}</pre>

<p>
where “intro” is the anchor for the Introduction section.  
</p>
</td>
	</tr>
	<tr class="row11">
		<td class="col0 leftalign"> Point to multiple sections<br/>
within the document  </td><td class="col1 leftalign"> Sections &lt;xref target=“iana_cons” format=“counter” /&gt;<br/>
and &lt;xref target=“sec_cons” format=“counter” /&gt;  </td><td class="col2 centeralign">  <pre class="code">Sections {{iana_cons}}{: format=&quot;counter&quot;}
and {{sec_cons}}{: format=&quot;counter&quot;}</pre>
</td>
	</tr>
	<tr class="row12">
		<td class="col0 leftalign"> Comments  </td><td class="col1 leftalign"> &lt;!-- foo –-&gt;  </td><td class="col2"> <pre class="code">&lt;!-- foo –-&gt;</pre>

<p>
 or 
</p>
<pre class="code">{::comment}foo{:/comment}</pre>

<p>
 Note: The latter will not appear in the XML file after running xml2rfc. 
</p>
</td>
	</tr>
	<tr class="row13">
		<td class="col0 leftalign"> Contact  </td><td class="col1 leftalign"> &lt;contact fullname=“Jane Doe”/&gt;  </td><td class="col2 leftalign"> {{{Jane Doe}}}    </td>
	</tr>
	<tr class="row14">
		<td class="col0"> External reference (inline with angle brackets) </td><td class="col1 leftalign"> &lt;eref target=&quot;https://example.com&quot; brackets=&quot;angle&quot;/&gt;   </td><td class="col2 leftalign"> [](https://example.com/){: brackets=&quot;angle&quot;}   </td>
	</tr>
	<tr class="row15">
		<td class="col0"> External reference (linked text) </td><td class="col1 leftalign"> &lt;eref target=“https://example.com”&gt;An example&lt;/eref&gt; is blah.  </td><td class="col2 leftalign"> [An example](https://example.com) is blah.   </td>
	</tr>
	<tr class="row16">
		<td class="col0 leftalign"> Index reference     </td><td class="col1 leftalign"> &lt;iref item=“Foo” /&gt;  </td><td class="col2 leftalign"> <pre class="code">(((Foo)))</pre>
</td>
	</tr>
	<tr class="row17">
		<td class="col0 leftalign"> Indent text         </td><td class="col1 leftalign"> &lt;t indent=“3”&gt;foo&lt;/t&gt;       </td><td class="col2 leftalign"> No direct equivalent.<br/>
This yields indented text, but not the desired XML: <pre class="code">&gt; foo</pre>
</td>
	</tr>
	<tr class="row18">
		<td class="col0 leftalign"> List:<br/>
Definition list  </td><td class="col1 leftalign"> <pre class="code">&lt;dl&gt;
   &lt;dt&gt;First term:&lt;/dt&gt;
   &lt;dd&gt;First def&lt;/dd&gt;
   &lt;dt&gt;Second term:&lt;/dt&gt; 
   &lt;dd&gt;
     &lt;t&gt;Second def P1&lt;/t&gt;
     &lt;t&gt;Second def P2&lt;/t&gt;
   &lt;/dd&gt;
&lt;/dl&gt;</pre>

<p>
 For same line: 
</p>
<pre class="code">&lt;dl newline=&quot;false&quot;&gt;</pre>
</td><td class="col2 leftalign"> <pre class="code">{:vspace}
First term:
: First def

Second term:
: Second def P1
: Second def P2</pre>

<p>
 For same line: 
</p>
<pre class="code">omit the leading {:vspace}</pre>
</td>
	</tr>
	<tr class="row19">
		<td class="col0 leftalign"> List:<br/>
Ordered list  </td><td class="col1 leftalign"> <pre class="code">&lt;ol&gt;
   &lt;li&gt;Foo&lt;/li&gt;
   &lt;li&gt;Bar&lt;/li&gt;
&lt;/ol&gt;</pre>
</td><td class="col2 leftalign"> <pre class="code">1. Foo
2. Bar</pre>

<p>
 Note: For list items with multiple paragraphs, indent first line of <br/>
second paragraph to align with first letter in first paragraph.   
</p>
</td>
	</tr>
<tr class="row20">
		<td class="col0 leftalign"> List:<br/>
Unordered list  </td><td class="col1 leftalign"> <pre class="code">&lt;ul&gt;
   &lt;li&gt;Foo&lt;/li&gt;
   &lt;li&gt;Bar&lt;/li&gt;
&lt;/ul&gt;</pre>
</td><td class="col2 leftalign"> <pre class="code">* Foo
* Bar</pre>

<p>
 or 
</p>
<pre class="code">- Foo
- Bar
</pre>

<p>
 Note: For list items with multiple paragraphs, indent first line of <br/>
second paragraph to align with first letter in first paragraph.   
</p>
</td>
	</tr>
	<tr class="row21">
		<td class="col0 leftalign"> Reference  </td><td class="col1 leftalign"> [see below]  </td><td class="col2 leftalign">     </td>
	</tr>
	<tr class="row22">
		<td class="col0"> Sourcecode with type </td><td class="col1 leftalign"> &lt;sourcecode type=“abnf”&gt;      </td><td class="col2"> <pre class="code">~~~ abnf
foo
~~~</pre>
</td>
	</tr>
	<tr class="row23">
		<td class="col0"> Sourcecode with no type </td><td class="col1 leftalign"> &lt;sourcecode type=“”&gt;      </td><td class="col2"> <pre class="code">~~~
foo
~~~
{: gi=&quot;sourcecode&quot;}</pre>
</td>
	</tr>
	<tr class="row24">
		<td class="col0"> Sourcecode in figure<br/>
w/ markers and filename </td><td class="col1 leftalign"> <pre class="code">&lt;figure title=&quot;Sample&quot;&gt;
&lt;sourcecode type=&quot;xml&quot;
            markers=&quot;true&quot;
            name=&quot;sample.xml&quot;&gt;
foo
&lt;/sourcecode&gt;
&lt;/figure&gt;</pre>
</td><td class="col2"> <pre class="code">~~~ xml
foo
~~~
{: title=&#039;Sample&#039; sourcecode-markers=&quot;true&quot; sourcecode-name=&quot;sample.xml&quot;}</pre>
</td>
	</tr>
	<tr class="row25">
		<td class="col0 leftalign"> Section with anchor  </td><td class="col1 leftalign"> &lt;section anchor=“intro”&gt;<br/>
&lt;name&gt;Introduction&lt;/name&gt;  </td><td class="col2 leftalign"> # Introduction {#intro}    </td>
	</tr>
	<tr class="row26">
		<td class="col0 leftalign"> Section unnumbered<br/>
with anchor  </td><td class="col1 leftalign"> &lt;section numbered=“false”<br/>
  anchor=“acks”&gt;<br/>
&lt;name&gt;Acknowledgements&lt;/name&gt;  </td><td class="col2 leftalign"> <pre class="code"># Acknowledgments {#acks}
{:numbered=&quot;false&quot;}</pre>
</td>
	</tr>
	<tr class="row27">
		<td class="col0"> Table with anchor </td><td class="col1 leftalign"> <pre class="code">&lt;table anchor=&quot;totals&quot;&gt;
 &lt;name&gt;Annual Totals&lt;/name&gt;
   &lt;thead&gt;
      &lt;th&gt;Year&lt;/th&gt;&lt;th&gt;Total&lt;/th&gt;
   &lt;/thead&gt;
   &lt;tbody&gt;
      &lt;tr&gt;&lt;td&gt;2018&lt;/td&gt;&lt;td&gt;208&lt;/td&gt;&lt;/tr&gt;
      &lt;tr&gt;&lt;td&gt;2019&lt;/td&gt;&lt;td&gt;180&lt;/td&gt;&lt;/tr&gt;
   &lt;/tbody&gt;
&lt;/table&gt;</pre>
</td><td class="col2 leftalign"> <pre class="code">| Year   | Total  |
-------------------
| 2018   | 208    |
| 2019   | 180    |
{: title=&quot;Annual Totals&quot; #totals}</pre>
</td>
	</tr>
	<tr class="row28">
		<td class="col0"> Table column alignment </td><td class="col1"> <pre class="code">&lt;table&gt;
  &lt;thead&gt;
    &lt;th&gt;Item #&lt;/th&gt;&lt;th&gt;Year&lt;/th&gt;&lt;th&gt;Total&lt;/th&gt;
  &lt;/thead&gt;
  &lt;tbody&gt;
    &lt;tr&gt;
      &lt;td align=&quot;left&quot;&gt;Item 1&lt;/td&gt;
      &lt;td align=&quot;center&quot;&gt;2018&lt;/td&gt;
      &lt;td align=&quot;right&quot;&gt;208&lt;/td&gt;
    &lt;/tr&gt;
    &lt;tr&gt;
      &lt;td align=&quot;left&quot;&gt;Item 2&lt;/td&gt;
      &lt;td align=&quot;center&quot;&gt;2019&lt;/td&gt;
      &lt;td align=&quot;right&quot;&gt;180&lt;/td&gt;
    &lt;/tr&gt;
  &lt;/tbody&gt;
&lt;/table</pre>
</td><td class="col2"> <pre class="code">| Item # | Year   | Total  |
|:-------|:------:|-------:|
| Item 1 | 2018   | 208    |
| Item 2 | 2019   | 180    |</pre>

<p>
 Note: The headings will also correspond to the column alignment.
</p>
</td>
	</tr>
	<tr class="row29">
		<td class="col0 leftalign"> Text styling   </td><td class="col1 leftalign"> &lt;strong&gt;bold&lt;/strong&gt;<br/>
&lt;em&gt;italics&lt;/em&gt;<br/>
&lt;tt&gt;fixed width&lt;/tt&gt;  </td><td class="col2 leftalign"> 
**bold**<br/>
*italics*<br/>
`fixed width`     </td>
	</tr>
	<tr class="row30">
		<td class="col0 leftalign"> Subscript and superscript   </td><td class="col1 leftalign"> W&lt;sub&gt;max&lt;/sub&gt;<br/>
2&lt;sup&gt;16&lt;/sup&gt;    </td><td class="col2 leftalign"> [the same as XML]     </td>
	</tr>
</table>

## The YAML Header

<table class="inline">
	<thead>
	<tr class="row0">
		<th class="col0 leftalign"> <strong>Concept</strong>      </th><th class="col1 leftalign"> <strong>RFCXML</strong>          </th><th class="col2 leftalign"> <strong>kramdown-rfc</strong>     </th>
	</tr>
	</thead>
	<tr class="row1">
		<td class="col0 leftalign"> Document basics   </td><td class="col1 leftalign"> <pre class="code">&lt;rfc xmlns:xi=&quot;http://www.w3.org/2001/XInclude&quot; 
category=&quot;info&quot; ipr=&quot;trust200902&quot; 
docName=&quot;draft-foo-00&quot;
number=&quot;0000&quot;
consensus=&quot;true&quot; 
obsoletes=&quot;YYYY&quot;
updates=&quot;ZZZZ&quot; 
submissionType=&quot;IETF&quot; 
tocInclude=&quot;true&quot; 
symRefs=&quot;true&quot; 
sortRefs=&quot;true&quot; 
version=&quot;3&quot;  
xml:lang=&quot;en&quot;&gt;

&lt;front&gt;
&lt;title abbrev=&quot;FOOP&quot;&gt;The Foo Protocol&lt;/title&gt;
&lt;seriesInfo name=&quot;RFC&quot; number=&quot;0000&quot;&gt;</pre>
</td><td class="col2 leftalign"> <pre class="code">title: The Foo Protocol
abbrev: FOOP
number: 0000
docname: draft-foo-00
category: info
submissiontype: IETF 
consensus: true
ipr: trust200902
obsoletes: YYYY
updates: ZZZZ
pi: [toc, symrefs, sortrefs]
v: 3
lang: en</pre>
</td>
	</tr>
	<tr class="row2">
		<td class="col0 leftalign"> More metadata   </td><td class="col1 leftalign"> &lt;date year=“2025” month=“July”/&gt;<br/>
&lt;area&gt;OPS&lt;/area&gt;<br/>
&lt;workgroup&gt;DNSOP&lt;/workgroup&gt;<br/>
&lt;keyword&gt;foo&lt;/keyword&gt;<br/>
&lt;keyword&gt;bar&lt;/keyword&gt;   </td><td class="col2 leftalign"> <pre class="code">date: 2025-07
area: OPS
workgroup: DNSOP
keyword: 
  - foo
  - bar</pre>
</td>
	</tr>
	<tr class="row3">
		<td class="col0 leftalign"> Author block    </td><td class="col1 leftalign"> <pre class="code">&lt;author initials=&quot;J.&quot; surname=&quot;Doe&quot; fullname=&quot;Jane Doe&quot;
role=&quot;editor&quot;&gt;
  &lt;organization&gt;Acme&lt;/organization&gt;
  &lt;address&gt;
    &lt;postal&gt;
      &lt;street&gt;123 Main Street&lt;/street&gt;
      &lt;city&gt;Anytown&lt;/city&gt;
      &lt;region&gt;CA&lt;/region&gt;
      &lt;Code&gt;12345&lt;/Code&gt;
      &lt;country&gt;United States of America&lt;/country&gt;
    &lt;/postal&gt;
    &lt;email&gt;jdoe@example.com&lt;/email&gt;
    &lt;uri&gt; https://www.example.com&lt;/uri&gt;
  &lt;/address&gt;
&lt;/author&gt;</pre>
</td><td class="col2 leftalign"> <pre class="code">author:
- name: Jane Doe
  ins: J. Doe    
  role: editor
  org: Acme
  street: 123 Main Street
  city: Anytown
  region: CA
  code: 12345
  country: United States of America
  email: jdoe@example.com
  uri: https://www.example.com</pre>
</td>
	</tr>
	<tr class="row4">
		<td class="col0 leftalign"> Contributors block (if list of names with contact info   </td><td class="col1 leftalign"> <pre class="code">&lt;contact fullname=&quot;Jane Doe&quot; &gt;
  &lt;organization&gt;Acme&lt;/organization&gt;
  &lt;address&gt;
    &lt;postal&gt;
      &lt;street&gt;123 Main Street&lt;/street&gt;
      &lt;city&gt;Anytown&lt;/city&gt;
      &lt;region&gt;CA&lt;/region&gt;&lt;Code&gt;12345&lt;/Code&gt;
      &lt;country&gt;United States of America&lt;/country&gt;
    &lt;/postal&gt;
    &lt;email&gt;jdoe@example.com&lt;/email&gt;
    &lt;uri&gt;https://www.example.com&lt;/uri&gt;
  &lt;/address&gt;
&lt;/contact&gt;</pre>
</td><td class="col2"> <pre class="code">contributor:
- name: Jane Doe
  ins: J. Doe
  org: Acme
  street: 123 Main Street
  city: Anytown
  region: CA
  code: 12345
  country: United States of America
  email: jdoe@example.com
  uri: https://www.example.com</pre>
</td>
	</tr>
	<tr class="row5">
		<td class="col0 leftalign"> Comments  </td><td class="col1 leftalign"> &lt;!-- foo –-&gt;  </td><td class="col2"> <pre class="code"># foo</pre>

<p>
 Note: This will not appear in the XML file after running xml2rfc. 
</p>
</td>
	</tr>
</table></div>

</div>

## References

See [documentation on references](https://github.com/cabo/kramdown-rfc#references) for details.

<table class="inline">
	<thead>
	<tr class="row0">
		<th class="col0 leftalign"> <strong>Concept</strong>      </th><th class="col1 leftalign"> <strong>RFCXML</strong>          </th><th class="col2 leftalign"> <strong>kramdown-rfc</strong>     </th>
	</tr>
	</thead>
	<tr class="row1">
		<td class="col0 leftalign"> Normative Ref       </td><td class="col1 leftalign"> <pre class="code">&lt;xi:include href=&quot;https://bib.ietf.org/
public/rfc/bibxml/reference.RFC.9200.xml&quot;/&gt;</pre>
</td><td class="col2 leftalign"> {{!RFC9200}} (in the body) or <pre class="code">normative:
  RFC9200:</pre>
</td>
	</tr>
	<tr class="row2">
		<td class="col0 leftalign"> Informative Ref     </td><td class="col1 leftalign"> <pre class="code">&lt;xi:include href=&quot;https://bib.ietf.org/
public/rfc/bibxml/reference.RFC.8032.xml&quot;/&gt;
&lt;xi:include href=&quot;https://bib.ietf.org/
public/rfc/bibxml3/reference.I-D.ietf-mpls-rmr.xml&quot;/&gt;</pre>
</td><td class="col2 leftalign"> {{?RFC8032}}<br/>
{{?I-D.ietf-mpls-rmr}} (in the body) or <pre class="code">informative:
  RFC8032:
  I-D.ietf-mpls-rmr:</pre>
</td>
	</tr>
	<tr class="row3">
		<td class="col0 leftalign"> Non-<abbr title="Request for Comments">RFC</abbr> Ref   </td><td class="col1 leftalign"> <pre class="code">&lt;reference anchor=&quot;X.690&quot; 
           target=&quot;https://www.itu.int/rec/T-REC-X.690&quot;&gt;
  &lt;front&gt;
    &lt;title&gt;Information technology - ASN.1 [...]&lt;/title&gt;
    &lt;author&gt;
      &lt;organization&gt;ITU-T&lt;/organization&gt;
    &lt;/author&gt;
    &lt;date year=&quot;2021&quot; month=&quot;February&quot;/&gt;
  &lt;/front&gt;
  &lt;seriesInfo name=&quot;ITU-T&quot; value=&quot;Recommendation X.690&quot;/&gt;
  &lt;seriesInfo name=&quot;ISO/IEC&quot; value=&quot;8825-1:2021&quot;/&gt;
  &lt;refcontent&gt;Ref content goes here&lt;/refcontent&gt;
&lt;/reference&gt;</pre>
</td><td class="col2 leftalign"> <pre class="code">  X.690:
    target: https://www.itu.int/rec/T-REC-X.690
    title: &quot;Information technology - ASN.1 [...]&quot;
    date: 2021-02
    author:
      org: ITU-T
    seriesinfo:
      ITU-T: Recommendation X.690
      ISO/IEC: 8825-1:2021
    rc:
      Ref content goes here</pre>
</td>
	</tr>
	<tr class="row4">
		<td class="col0 leftalign"> A symbolic name<br/>
using displayreference   </td><td class="col1 leftalign"> &lt;displayreference target=“RFC5234” to=“ABNF”/&gt;<br/>
&lt;displayreference target=“I-D.ietf-mpls-rmr” to “RMR”/&gt;   </td><td class="col2 leftalign"> <pre class="code">RFC5234:
  display: ABNF
   
I-D.ietf-mpls-rmr:
  display: RMR</pre>

<p>
 In the body, cite as: {{RFC5234}} and {{I-D.ietf-mpls-rmr}} 
</p>
</td>
	</tr>
	<tr class="row5">
		<td class="col0 leftalign"> A symbolic name<br/>
without displayreference  </td><td class="col1 leftalign"> <pre class="code">&lt;reference anchor=&quot;ABNF&quot;&gt;
   &lt;title&gt;Augmented BNF for Syntax Specifications: ABNF&lt;/title&gt;
   [...the rest of the RFC5234 ref from the citation library]</pre>
</td><td class="col2 leftalign"> <pre class="code">ABNF: RFC5234</pre>

<p>
 In the body, cite as: {{ABNF}}<br/>
Note: <code>v: 3</code> must be in the YAML header for this to work.   
</p>
</td>
	</tr>
	<tr class="row6">
		<td class="col0"> A de-aliased reference with symbolic name (kramdown-rfc only) </td><td class="col1"> n/a </td><td class="col2"> <pre class="code"> I-D.bormann-cbor-notable-tags:
    -: notable
    display: NOTABLE-TAGS
    </pre>
</td>
	</tr>
</table>

        


