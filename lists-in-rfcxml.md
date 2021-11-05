---
title: Lists in RFCXML
description: 
published: true
date: 2021-11-05T01:37:10.690Z
tags: 
editor: markdown
dateCreated: 2021-11-05T01:35:56.674Z
---

# Different kinds of lists

For bulleted lists, use the [**\<ul\>**](/rfcxml-vocabulary#ul) element.

For an empty list (indentation only), use the [**\<ul\>**](/rfcxml-vocabulary#ul) element with empty="true".

For definition lists (previously called hanging lists), use the [**\<dl\>**](/rfcxml-vocabulary#dl) element (more info below)

For numbers or letters, use the **type** attribute of the [**\<ol\>**](/rfcxml-vocabulary#ol) element.  For example

* **type** set to "(%d)" 
```
(1)
(2)
(3)
```
* **type** set to "(%c)"
```
(a)
(b)
(c)
```
* **type** set to "REQ%d:"
```
REQ1:
REQ2:
REQ3:
```

# Continuous numbering in a list that is split by text (or across sections)

Set the group attribute to the same value for each [**\<ol\>**](/rfcxml-vocabulary#ol) element. For example:
```xml
 <ol type="REQ%d:" group="reqs">
  <li>do a</li>
  <li>do b</li>
</ol>
<t>Here is text in between.</t>
<ol type="REQ%d:" group="reqs">
  <li>do c</li>
  <li>do d</li>
</ol>
<t>Here is more text in between.</t>
<ol type="REQ%d:" group="reqs">
  <li>do e</li>
  <li>do f</li>
</ol>
```
yields:
```
REQ1: do a
REQ2: do b
Here is text in between.
REQ3: do c
REQ4: do d
Here is more text in between.
REQ5: do e
REQ6: do f
```
# Indentation and definition lists

Use a [**\<dl\>**](/rfcxml-vocabulary#dl) element (definition list), where each [**\<dt\>**](/rfcxml-vocabulary#dt) (definition term) has a corresponding [**\<dd\>**](/rfcxml-vocabulary#dd) (definition description).

For example:
```xml
<dl>
  <dt>Unassigned:</dt>
  <dd>Unused and available for assignment via
  documented procedures.</dd>

  <dt>Reserved:</dt>
  <dd>Not to be assigned.  Reserved values are
  held for special uses, such as to extend the namespace
  when it become exhausted.  Reserved values are not
  available for general assignment.</dd>
</dl>
```
yields:
```
Unassigned: Unused and available for assignment via documented 
  procedures.
Reserved: Not to be assigned. Reserved values are held for special 
  uses, such as to extend the namespace when it become exhausted. 
  Reserved values are not available for general assignment.
```
Set **newline** to "true" to get a line break after the term. For example:
```xml
<dl newline="true">
  <dt>Unassigned:</dt>
  <dd>Unused and available for assignment via
  documented procedures.</dd>

  <dt>Reserved:</dt>
  <dd>Not to be assigned.  Reserved values are
  held for special uses, such as to extend the namespace
  when it become exhausted.  Reserved values are not
  available for general assignment.</dd>
</dl>
```
yields:
```
Unassigned:
  Unused and available for assignment via documented procedures.
Reserved:
  Not to be assigned. Reserved values are held for special uses, such 
  as to extend the namespace when it become exhausted. Reserved values 
  are not available for general assignment.
```
# Nested lists

The key is that any text before or after the inner list must be in a [**\<t\>**](/rfcxml-vocabulary#t) element.

Example: [**\<ol\>**](/rfcxml-vocabulary#ol) nested within [**\<dl\>**](/rfcxml-vocabulary#dl)
```xml
<dl>
[...]
 <dt>Foo validator:</dt>
 <dd>
    <t>It performs the following actions:</t>
    <ol type="1" spacing="compact">
      <li>runs</li>
      <li>jumps</li>
      <li>walks</li>
    </ol>
 </dd>
[...]
</dl>
```
yields:
```
Foo validator: It performs the following actions:
    1. runs
    2. jumps
    3. walks
```
Example: [**\<ul\>**](/rfcxml-vocabulary#ol) nested within [**\<ul\>**](/rfcxml-vocabulary#ul)
```xml
<ol type="Step %d:">
[...]
 <li><t>Send it to</t>
    <ul spacing="compact">
      <li>Alice</li>
      <li>Bob</li>
      <li>Carol</li>
    </ul>
 </li>
[...]
</ol>
```
yields:
```
Step 1: Send it to:
    * Alice
    * Bob
    * Carol
```