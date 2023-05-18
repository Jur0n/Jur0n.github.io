---
layout: post
title: Markdown Cheat Sheet
tags: [Jekyll, Markdown,blog]
category: [Cheat Sheets]
---

# Markdown - Cheatsheet

To write a Posts on Jekyll Mardown is used. This cheet will provide an list of usefull commands.

## Headings
---

html equivalent: ``` <h1> - <h6>```

To create a heading, add number signs (#) in front of a word or phrase. The number of number signs you use should correspond to the heading level. For example, to create a heading level three (h3), use three number signs (e.g., ### My Header).


```markdown
Avaible Sizes:
# Heading level 1
## Heading level 2
### Heading level 3
#### Heading level 4
##### Heading level 5
###### Heading level 6

Syntax:
- to get a line below the heading, use "---" :

### Heading
---
```

best pratice:
- always put a space after a hastag: # Heading
- Always put blank lines before and after a Heading

## Paragraphs
---

html equivalent:
``` <p> ```

To create paragraphs, use a blank line to separate one or more lines of text.

## Line Breaks
---

html equivalent:
``` <br> ```

To create a line break or new line, end a line with two or more spaces, and then type return.

## Emphasis

---
Text can be made bold oder italic

### *Italic*: `* TEXT *`

### **Bold**: `** TEXT **`

### ***Bold and Italic***: `*** TEXT ***`

## Blockqoutes

To create a blockqoute, add a `>` infront of text:
> Text in a blockqoute

can be extended over multiple paragraphs and can be nested:
> Blockquote
>> nested lockquote

## Lists
---

#### Ordered List:

```Markdown
1.
2.
3.
```
#### Unordered List:

```Markdown
- first 
- second
- third
```

## Code
---
### Denoting words:

Use Backticks to denote a single word:

`` `code` ``

### Words or phrases:

Enclose the words or phrases in double backticks:

``` ``TEXT`` ``` 

### Blocks of Code

To create a code block, at least 3 backticks are required. T
the coding Language can be specified after the first three backticks.

Example:
```
 "```javascript
 log.console("Hello World)
 
 ```"
 ```
 
 Result:

 ```javascript
  log.console("Hello World)
  ```


### Links
---

#### Title Links
Just like in HTML, you can link a word: 
This is my Favourite Search Engine: [swisscows](https://www.swisscows.com "sample title")

`` [swisscows](https://www.swisscows.com "sample title") ``

#### Quick Links and E-Mail

Used to show a URL or E-Mail adress with destination:´

<https://www.swisscows.com>

<j.neumann@neumann-itservice.de>


## Images
---

To link an image, you can use this command:

``![This is my Block Profile Picture!](/img/logo.jpg "My Profile Picture") ``
<img src="/img/logo.jpg" width="100" height="100">

## Escaping Characters
---
To display a literal character that would otherwise be used to format text in a Markdown document, add a backslash `(\)` in front of the character.

\## a h2 heading:

`` \## a h2 heading``

---
[source](https://www.markdownguide.org/basic-syntax#emphasis)

