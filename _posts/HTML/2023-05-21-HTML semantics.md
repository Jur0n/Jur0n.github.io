---
layout: post
title: HTML Semantics
tags: [HTML, Web dev, coding]
category: [HTMl]
---
Welcome to my personal overview for HTML basics.
Index:

- Typical Start
- Tags
- Structures
- Attributes


free learning course: freecodecamp.org

# Typical start of an HTML page


```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>Page Title</title>
    <meta name="description" content="Roughly 155 characters">
    <link rel="stylesheet" type="text/css" href="mystyle.css">
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.7.1/jquery.min.js"></script>
    <script src="script.js"></script>
  </head>
  <body>
    <!-- Content -->
  </body>
</html>
```
## Head Tags

```html
<!doctype html>
<html lang="en" class="no-js">
 <head>
  <meta charset="utf-8">
  <meta http-equiv="x-ua-compatible" content="ie=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="canonical" href="https://htmlcheatsheet.com/" />
  <title>HTML CheatSheet</title>
  <meta name="description" content="A brief page description">
  <meta name="keywords" content="html,cheatsheet" />
  <meta property="fb:admins" content="YourFacebookUsername" />
  <meta property="og:title" content="HTML CheatSheet" />
  <meta property="og:type" content="website" />
  <meta property="og:url" content="https://htmlcheatsheet.com/" />
  <meta property="og:image" content="https://htmlcheatsheet.com/images/html-cheatsheet.jpg" />
  <meta property="og:description" content="A brief page description" />
  <link rel="apple-touch-icon" href="apple-touch-icon.png">
  <link rel="alternate" hreflang="es" href="https://htmlcheatsheet.com/spanish/" />
  <link rel="stylesheet" href="/styles.css">
  <script src="/script.js"></script>
 </head>
```

# Tags

## Div Section

<div>Block element</div>

## Headings
```html
<h1>Page title</h1>
<h2>Subheading</h2>
<h3>Sub subheading</h3>
<h4>Quaternary heading</h4>
```

## Paragraph with style

```html
<p style="text-align: center;">text</p>
```

## Image

```html
<img src="/demo.jpg" alt="description" height="48" width="100">
```

## Mailto link

```html
<a href="mailto:me@ruwix.com?Subject=Hi%20mate" target="_top">Send Mail</a>
```

## Inner anchor (jump to ID)

```html
<a href="#footer">Jump to footnote</a>
<br />
<a name="footer"></a>Footnote content
```

## Bold text

```html
<strong>Bold text</strong>
```

## Italic text

```html
<em>Italic text</em>
```

## Underlined text

```html
<span style="text-decoration: underline;">Underlined text</span>
```

## Iframe

```html
<iframe src="link.html" width="200" height="200">
</iframe> 
```

## Abbreviation

```html
<abbr title="Hypertext Markup Language">HTML</abbr>
```

## Comment

```html
<!-- HTML
Comment -->
```

## Horizontal Line

```html
<hr />
```

## Line break

```html
<br />
```

## Quotation

```html
<q>Success is a journey not a destination.</q>

<blockquote cite="https://ruwix.com/">
The Rubik's Cube is the World’s best selling puzzle toy.
</blockquote> 
```

## Video

```html
<video width="200" height="150" controls>
  <source src="vid.mp4" type="video/mp4">
  <source src="vid.ogg" type="video/ogg">
</video>
```

## Audio

```html
<audio controls>
  <source src="sound.ogg" type="audio/ogg">
  <source src="sound.mp3" type="audio/mpeg">
  No audio support.
</audio> 
```

# Structures

## Table

```html
<table><caption>Phone numbers</caption>
 <thead>
   <tr>
	<th>Name</th>
	<th colspan="2">Phone</th>
   </tr>
 </thead>
 <tbody>
   <tr>
	<td>John</td>
	<td>577854</td>
	<td>577855</td>
   </tr>
   <tr>
	<td>Jack</td>
	<td>577856</td>
	<td>577857</td>
   </tr>
 </tbody>
 <tfoot>
   <tr>
	<td>&nbsp;</td>
	<td>Personal</td>
	<td>Office</td>
   </tr>
 </tfoot>
</table>
```

## Unordered list

```html
<ul>
  <li>First</li>
  <li>Second</li>
  <li>Third</li>
</ul>
```

## Definition list

```html
<dl>
  <dt>HTML</dt>
  <dd>Hypertext Markup Language</dd>
  <dt>CSS</dt>
  <dd>Cascading Style Sheets </dd>
</dl>
```

## Form

```html
<form action="/action.php" method="post">
  Name: <input name="name" type="text" /> <br /> 
  Age: <input max="99" min="1" name="age" step="1" type="number" value="18" /> <br />
  <select name="gender">
    <option selected="selected" value="male">Male</option>
    <option value="female">Female</option>
  </select><br /> 
  <input checked="checked" name="newsletter" type="radio" value="daily" /> Daily <input name="newsletter" type="radio" value="weekly" /> Weekly<br />
  <textarea cols="20" name="comments" rows="5">Comment</textarea><br />
  <label><input name="terms" type="checkbox" value="tandc" />Accept terms</label> <br />
<input type="submit" value="Submit" />
</form>
```

# Attributes

## SYNTAX

``<tag attributename="value" />``

- lowecase attributes, quote values
Global attributes
accesskey, class, contenteditable, data-*, dir, draggable, hidden, id, lang, spellcheck, style, tabindex, title

Internationalization: dir, lang, xml:lang

```html
<html lang="en-US">
<p dir="rtl">Right to left (Arabic)</p> 
</html>
```

Link: download, href, hreflang, media, rel, target, type

```html
<a href="https://htmlg.com/" target="_blank" rel="external" hreflang="en" type="text/html">
Link
</a>
```

Image: src, alt, height, ismap, longdesc, src, srcset, usemap, width

```html
<img src="/demo.jpg" alt="description" 
height="48" width="100" longdesc="desc.txt" />
```

All attributes
acceptform, input
accept-charsetform
accesskeyGlobal attribute
actionform
alignapplet, caption, col, colgroup, hr, iframe, img, table, tbody, td, tfoot , th, thead, tr
altapplet, area, img, input
asyncscript
autocompleteform, input
autofocusbutton, input, keygen, select, textarea
autoplayaudio, video
autosaveinput
bgcolorbody, col, colgroup, marquee, table, tbody, tfoot, td, th, tr
bufferedaudio, video
challengekeygen
charsetmeta, script
checkedcommand, input
citeblockquote, del, ins, q
classGlobal attribute
codeapplet
codebaseapplet
colorbasefont, font, hr
colstextarea
colspantd, th
contentmeta
contenteditableGlobal attribute
contextmenuGlobal attribute
controlsaudio, video
coordsarea
dataobject
data-*Global attribute
datetimedel, ins, time
defaulttrack
deferscript
dirGlobal attribute
dirnameinput, textarea
disabledbutton, command, fieldset, input, keygen, optgroup, option, select, textarea
downloada, area
draggableGlobal attribute
dropzoneGlobal attribute
enctypeform
forlabel, output
formbutton, fieldset, input, keygen, label, meter, object, output, progress, select, textarea
formactioninput, button
headerstd, th
heightcanvas, embed, iframe, img, input, object, video
hiddenGlobal attribute
highmeter
hrefa, area, base, link
hreflanga, area, link
http-equivmeta
iconcommand
idGlobal attribute
integritylink, script
ismapimg
itempropGlobal attribute
keytypekeygen
kindtrack
labeltrack
langGlobal attribute
languagescript
listinput
loopaudio, bgsound, marquee, video
lowmeter
manifesthtml
maxinput, meter, progress
maxlengthinput, textarea
mediaa, area, link, source, style
methodform
mininput, meter
multipleinput, select
mutedvideo
namebutton, form, fieldset, iframe, input, keygen, object, output, select, textarea, map, meta, param
novalidateform
opendetails
optimummeter
patterninput
pinga, area
placeholderinput, textarea
postervideo
preloadaudio, video
radiogroupcommand
readonlyinput, textarea
rela, area, link
requiredinput, select, textarea
reversedol
rowstextarea
rowspantd, th
sandboxiframe
selectedoption
sizeinput, select
slotGlobal attribute
spancol, colgroup
spellcheckGlobal attribute
srcaudio, embed, iframe, img, input, script, source, track, video
startol
stepinput
styleGlobal attribute
tabindexGlobal attribute
targeta, area, base, form
titleGlobal attribute
typebutton, input, command, embed, object, script, source, style, menu
usemapimg, input, object
valuebutton, option, input, li, meter, progress, param
widthcanvas, embed, iframe, img, input, object, video
wraptextarea
