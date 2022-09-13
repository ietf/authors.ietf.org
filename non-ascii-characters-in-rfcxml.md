---
title: Non-ASCII characters in RFCXML
description: 
published: true
date: 2021-12-16T04:45:35.249Z
tags: 
editor: markdown
dateCreated: 2021-12-16T02:40:30.443Z
---

The use of non-ASCII characters in RFCXML is detailed in RFC 7997. Your file encoding must be set as UTF-8 (the default).

# non-ASCII characters used directly

non-ASCII characters in RFCXML (and I-Ds in general) can be used directly in a restricted set of elements:

* [**\<author\>**](/rfcxml-vocabulary#author) and [**\<contact\>**](/rfcxml-vocabulary#contact) elements (using the **fullname**, **initials**, and **surname** attributes, while the **asciiFullname**, **asciiInitials**, and **asciiSurname** attributes hold the ASCII equivalents). If the non-ASCII characters are in the Unicode Latin blocks, then it's not necessary to use the attributes for ASCII equivalents. (For example, when a **surname** contains "ä" (LATIN SMALL LETTER A WITH DIAERESIS, U+00E4), it's not necessary to include **asciiSurname**.)
* [**\<organization\>**](/rfcxml-vocabulary#organization) element
* author and contact's postal address using [**\<street\>**](/rfcxml-vocabulary#street), [**\<city\>**](/rfcxml-vocabulary#city), [**\<region\>**](/rfcxml-vocabulary#region), [**\<city\>**](/rfcxml-vocabulary#city), [**\<country\>**](/rfcxml-vocabulary#country) and * [**\<email\>**](/rfcxml-vocabulary#email) elements. Each of these elements has an ascii attribute to hold the ASCII equivalent, which will also appear in the output format.
* [**\<sourcecode\>**](/rfcxml-vocabulary#sourcecode) and [**\<artwork\>**](/rfcxml-vocabulary#artwork) elements

# non-ASCII characters wrapped in \<u\>
Other than in the resricted elements, non-ASCII characters must be wrapped by the [**\<u\>**](/rfcxml-vocabulary#u) element with the **format** attribute specifying how it is represented.

The simplified **format** consists of dash-separated keywords, where each keyword represents a possible expansion of the Unicode character or string; use for example `<u format="lit-num-name">foo</u>` to expand the text to its literal value, code point values, and code point names.

A combination of up to 3 of the following keywords may be used, separated by dashes: "num", "lit", "name", "ascii", "char". The keywords are expanded as follows and combined, with the second and third enclosed in parentheses if present:

* "ascii" - The value of the 'ascii' attribute on the [**\<u\>**](/rfcxml-vocabulary#u) element
* "char" - The literal element text, without quotes
* "lit" - The literal element text, enclosed in quotes
* "name" - The Unicode name(s) of the element text
* "num" - The numeric value(s) of the element text, in U+1234 notation

In order to ensure that no specification mistakes can result from rendering methods that cannot render all Unicode code points, "num" MUST always be part of the specified format.

The following RFCXML:

```xml
<t>Temperature changes are indicated by the character <u>Δ</u></t>
``` 
Generates the following outputs depending on the setting of **format**:
* format="num-lit":
  `Temperature changes are indicated by the character U+0394 ("Δ")`
* format="num-name": 
  `Temperature changes are indicated by the character U+0394 (GREEK CAPITAL LETTER DELTA)`
* format="num-lit-name": 
  `Temperature changes are indicated by the character U+0394 ("Δ", GREEK CAPITAL LETTER DELTA)`
* format="num-name-lit": 
  `Temperature changes are indicated by the character U+0394 (GREEK CAPITAL LETTER DELTA, "Δ")`
* format="name-lit-num": 
  `Temperature changes are indicated by the character GREEK CAPITAL LETTER DELTA ("Δ", U+0394)`
* format="lit-name-num": 
  `Temperature changes are indicated by the character "Δ" (GREEK CAPITAL LETTER DELTA, U+0394)`

The default value is "lit-name-num"

## Expansion of [**\<u\>**](/rfcxml-vocabulary#u) multi-codepoint strings

If the [**\<u\>**](/rfcxml-vocabulary#u) element encloses a sequence of Unicode codepoints, rather than a single one, the rendering reflects this. For example:
```xml
   <u format="num-lit">ᏚᎢᎵᎬᎢᎬᏒ</u>
```
will be expanded to "U+13DA U+13A2 U+13B5 U+13AC U+13A2 U+13AC U+13D2 ("ᏚᎢᎵᎬᎢᎬᏒ")".

Unicode characters in document text which are not enclosed in [**\<u\>**](/rfcxml-vocabulary#u) will be replaced with a question mark (?) and a warning will be issued.

## Non-simplified [**\<u\>**](/rfcxml-vocabulary#u) format specifications
In order to provide for cases where the simplified format above is insufficient, without relinquishing the requirement that the number of a code point always must be rendered, the **format** attribute can also accept a full format string. This format uses placeholders which consist of any of the key words above enclosed in curly braces; outside of this, any ascii text is permissible. For example,

```xml
   The <u format="{lit} character ({num})">Δ</u>
```
will be rendered as

```
   The "Δ" character (U+0394).
```

As for the simplified format, "num" MUST always be part of the specified format in order to ensure that no specification mistakes can result for rendering methods that cannot render all Unicode code points,

## Split expansion of [**\<u\>**](/rfcxml-vocabulary#u) elements

There are cases which cannot be handled with either the simplified or full [**\<u\>**](/rfcxml-vocabulary#u) format specifications. One is exemplified in Table 1 of the CSS sample document at [https://rfc-format.github.io/draft-iab-rfc-css-bis/sample2-v2.html#s-3](https://rfc-format.github.io/draft-iab-rfc-css-bis/sample2-v2.html#s-3). Rendering this with [**\<u\>**](/rfcxml-vocabulary#u) elements requires that the non-ascii content be rendered in one place (a table cell in one column) while the expansion is rendered in another cell in a different column. Provision for this has been made by modifying the expansion of [**\<u\>**](/rfcxml-vocabulary#u) when it is referenced by an [**\<xref\>**](/rfcxml-vocabulary#xref). This table, with [**\<u\>**](/rfcxml-vocabulary#u) elements referenced by [**\<xref\>**](/rfcxml-vocabulary#xref) instances:
```xml
   <table>
     <name>A Sample of Legal Nicknames</name>
     <thead>
       <tr>
          <th>#</th>
          <th>Nickname</th>
          <th>Output for comparison</th>
       </tr>
     </thead>
     <tbody>
       <tr>
          <td>1</td>
          <td>&lt;Foo&gt;</td>
          <td>&lt;foo&gt;</td>
       </tr>
       <tr>
          <td>2</td>
          <td>&lt;foo&gt;</td>
          <td>&lt;foo&gt;</td> </tr>
       <tr>
          <td>3</td>
          <td>&lt;Foo Bar&gt;</td>
          <td>&lt;foo bar&gt;</td>
       </tr>
       <tr>
          <td>4</td>
          <td>&lt;foo bar&gt;</td>
          <td>&lt;foo bar&gt;</td>
       </tr>
       <tr>
         <td>5</td>
         <td>
            &lt;
            <u format="name-num" anchor="greek-upper-sigma">Σ</u>
            &gt;
         </td>
         <td> <xref target="greek-upper-sigma" /> </td>
       </tr>
       <tr>
          <td>6</td>
          <td>
             &lt;
             <u format="name-num" anchor="greek-lower-sigma">σ</u>
             &gt;
          </td>
          <td> <xref target="greek-lower-sigma" /> </td>
       </tr>
       <tr>
          <td>7</td>
          <td>
             &lt;
             <u format="name-num" anchor="greek-final-sigma">ς</u>
             &gt;
          </td>
          <td> <xref target="greek-final-sigma" /> </td>
       </tr>
       <tr>
          <td>8</td>
          <td>
             &lt;
             <u format="name-num" anchor="black-chess-king">♚</u>
             &gt;
          </td>
          <td>
             <xref target="black-chess-king" format="default"/>
          </td>
       </tr>
       <tr>
          <td>9</td>
          <td>
             &lt;Richard
             <u format="{char}> ({num})" anchor="richard-iv">Ⅳ</u>
             &gt;
          </td>
          <td>&lt;richard iv&gt;</td>
       </tr>
     </tbody>
   </table>
```
comes out as shown below:
```
| #   | Nickname               | Output for comparison                   |
| --: | :--------------------- | :-------------------------------------- |
| 1   | \<Foo\>                | \<foo\>                                 |
| 2   | \<foo\>                | \<foo\>                                 |
| 3   | \<Foo Bar\>            | \<foo bar\>                             |
| 4   | \<foo bar\>            | \<foo bar\>                             |
| 5   | \<Σ\>                  | GREEK CAPITAL LETTER SIGMA (U+03A3)     |
| 6   | \<σ\>                  | GREEK SMALL LETTER SIGMA (U+03C3)       |
| 7   | \<ς\>                  | GREEK SMALL LETTER FINAL SIGMA (U+03C2) |
| 8   | \<♚\>                  | BLACK CHESS KING (U+265A)               |
| 9   | \<Richard Ⅳ\> (U+2163) | \<richard iv\>                          |
_Table 1: A Sample of Legal Nicknames_
```