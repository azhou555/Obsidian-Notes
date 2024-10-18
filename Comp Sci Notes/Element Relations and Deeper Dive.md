---
---
## [[Table of Contents]]

## Web Page Family & Semantic Structuring 🌳

it is important to understand the structuring of tags within an HTML page and use that to your advantage. Consider <html> as the overarching root node with branches stretching out to <head> and <body>. <head> then connects to <title>, <style>, <link>, etc. <body> has nodes <header>, <nav>, <main>, <footer>, and so on, whereas <main> might contain an <article> consisting of <section>s.
![[Comp Sci Notes/Images/image 1.png]]![[2023 10-43 AM.png]]

### Important Relationships

When working with different tags, it is crucial to understand the relationships that exist between them.

* **Parent**
	* An element that contains one or more other elements within it
	* <html> tag is a parent of the <head> and <body> tag
	* <head> tag is not a parent of the <header> tag, although it may be higher in the tree
* **Child**
	* An element that is contained within another element that sits one level higher than it in the tree
	* <head> and <body> are children of the <html> tag
	* <figure> and <p> are children of the <article> tag
* **Ancestor**
	* An element that contains one or more levels of elements
	* <body> tag is an ancestor of the <aside> tag but not a parent of it
	* <html> is an ancestor of all tags
* **Descendant**
	* An element that is contained within another element that is one or more levels above it in the tree
	* <section> tags are descendants of the <body> tag & <aside> tag is a descendant of the <main> tag

## CSS Selectors 🐲

When defining the styles for different parts of our web page, we might not want all articles or all paragraphs sharing the same style. At the same time, we don't want to have to manually define the style each time. This is where CSS selectors come into play. You will most likely be using one of 4 different selectors:

### Class Selector

A class selector targets all tags of a certain class and applies predefines styles to those tags. The basic syntax for defining a class looks something like:
```
<element class="class-name">
```
That allows us to do something like this:
**style.css**
```
.information {
    color: pink;
    font-size: 32px;
}
```
**page.html**
```
<div class="information">This is how to use a class to stylize our web page</div>
```

### ID Selector

Similarly to the class selector, the id selector can target a tag and apply predefined styles to that tag. However, an id can only be applied to a single object, whereas a class selector can be applied to all objects of the desired class. Defining an id selector looks like:
```
<element id="id-name">
```
Application looks like:
**style.css**
```
#id {
    color: pink;
    font-size: 32px;
}
```
**page.html**
```
<div id="id">This is how to use an id selector to stylize our pages</div>
```

### Descendant Selector

The descendant selector targets elements contained within another element. Syntax looks like
```
ancestor descendant {
    property1: value1;
    property2: value2;
}
```
Here, it selects all elements of descendant tag that are contained within the ancestor tag and applies the indicated style.
Note the usage here:
**style.css**
```
aside a{
    color: red;
    font-style: italic;
    text-decoration: none;
}
```

### Child Selector

Very similar to the descendant selector. However, the child selector only applies to elements that are one level below the parent and are children rather than descendants.
```
p > div {
    color: green;
    font-size: 50px;
    text-decoration: underline;
}
```

## Important Ending Concepts 🦭

### Inheritance

If a parent element is styled with a property, children and descendant elements will likely be stylized with the same property unless specified otherwise. This is what is referred to as inheritance. Note that padding, borders, and margins are not inherited. Make sure to be careful about the possibility of inheritance(or lack thereof) when coding your page.

### Weight

Different ways of sourcing styles for elements have different weights/priorities. That makes it such that if you define the style of an element multiple times, only one will be used and you can predict with one it is. Listed below are the different sources and the weights attached, in ascending order(in-line takes priority over browser style):

1. Browser styles - List of default styles applied by the web browser to HTML tags. Known officially as _user agent style sheet_
2. User-specified styles - Styles that the web browser user has configured such as text size, font, etc. Known as _user style sheet_

4. Internal style sheets - Internal sheets in the <style> tag within the <head> tag
5. Inline styles - <div style="font-size: 24px; color=red">

### Specificity

This occurs when two or more style rules from the same source target the same element. Since they reside in the same source, weight plays no role in deciding the end result. Here, each style rule is assigned a score called specificity and the style rule with the highest specificity takes precedence.

1. Add one point for each element(such as div or span) in the rule's selector
2. Add 10 points for each class in the selector
3. Add 100 points for each ID in the selector
4. If the selector is part of an inline style, add 1,000 points

Specificity can also be used as a debugger of sorts
