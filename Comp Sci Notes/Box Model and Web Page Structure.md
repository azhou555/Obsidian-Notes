---
---
## [[Table of Contents]]

## CSS Box Model 📦

Consider that every single element has an invisible box surrounding it. This applies to not only p, div, h1, h6, article, and so on so forth, but to inline elements as well. Considering it logically, every single element takes up an amount of space, even characters. Recall the highlighter function you might have used while working on a Word document. What it did was simply change the background color of the characters' box models. Now, each and every single box has the following components:

* Content - the stuff inside the box(text, images, etc)
* Padding - The space around the content
* Border - A line surrounding the box padding
* Margin - The space around the border separating the box from other boxes on left, right, above and below
* Dimensions - The height and width of the box
* Position - The location of the box within the page

![[2023 12-57 PM.png]]

### Styling Sizes

Each time the web browser renders in a html file, it has to determine the properties of the box models, including the dimensions. To do this, the browser sets the width equal to the width of the parent. Since the <body> element is naturally set to the width of the browser, unless otherwise changed every other element will inherit its width as well. On the other hand, the height of each box model is adjusted such that it can fit the content.
However, these values can easily be changed by stylizing the height and width properties as such:
```
body {
    height: 50vw;
    width: 50vw;
}
```
**Additional Notes**
By default, the size of the box model is set to equal the content part of the box. This excludes the padding and border. To work around this, you can implement:
```
element {
    box-sizing: border-box;
}
```
This forces the web browser to set the box model's height and width to include the content, padding, and border. To apply this to all the elements, implement the \*:
```
* {
    box-sizing: border-box;
}
```
The \* is a shorthand way to refer to all elements in the file. That effectively adjusts the box model dimensions for all of the elements.
Most of the time however, you won't have to worry too much about the height of the box model. They are extremely difficult to work with and depend on many factors including but not limited to the content, the browser's window size, the user's default font size, and so on. Furthermore, height and width only apply to block-level elements such as <article>, <div>, and <p>, not to inline elements such as <span> and <a>. However, there are methods to transform an inline element to a block-level element. Firstly, we can change the element to an inline block by using:
```
display: inline-block
```
We can also simply turn it into a true block with
```
display: block
```
With this method, the block will no longer flow with the surrounding text.

### Padding 🪕

Padding is the empty space between the content and the border. To change the padding of a box model, we can alter one of its corresponding padding attributes to add padding:
```
element {
    padding-top: top-value;
    padding-right: right-value;
    padding-bottom: bottom-value;
    padding-left: left-value;
}
```
Note that each of the padding values intake a CSS measurement unit such as px, pt, em, rem, vw, or vh.
There are also shorthand methods to adding padding:

|     |     |
| --- | --- |
| **Syntax** | **Description** |
| padding: value1; | Applies value1 amount of padding to all four sides |
| padding: value1 value2; | Applies value1 to the top and bottom and value2 to the sides |
| padding: value1 value2 value3; | Applies value1 to the top, value2 to the sides, and value3 to the bottom |
| padding: value1 value2 value3 value4; | Applies value1 to top, value2 to right, value3 to bottom, and value4 to the left |

The style sheet might look something like this:
```
element {
    padding: 1rem, 1.5rem, .5rem 1.25rem;
}
```

### Borders

Intrinsically similar to padding except that there are some more values:

* Width: Specifies the thickness of the border. Can be done using CSS measurement units, commonly done using px, but can also be done with thin, medium, or thick
* Style: Specifies style of border line; included keywords: dotted, dashed, solid, double, groove, ridge, inset, or outset
* Color: Specifies the color of the border line using color keyword, rgb(), or RGB code

Syntax looks like:
```
element {
    border-top: top-width top-style top-color;
    border-right: right-width right-style right-color;
    border-bottom: bottom-width bottom-style bottom-color;
    border-left: left-width left-style left-color;
}
```

### Margins

Margins are the space in between box models and can be adjusted similarly to padding:
content-> padding = box model-> margin
Editing the margins of an element looks like:
```
element {
    margin-top: top-value;
    margin-right: right-value;
    margin-bottom: bottom-value;
    margin-left: left-value;
}
```
Similarly, we can use the same shorthand as we had with padding:

|     |     |
| --- | --- |
| **Syntax** | **Description** |
| margin: value1; | Applies value1 amount of margin to all four sides |
| margin: value1 value2; | Applies value1 to the top and bottom and value2 to the sides |
| margin: value1 value2 value3; | Applies value1 to the top, value2 to the sides, and value3 to the bottom |
| margin: value1 value2 value3 value4; | Applies value1 to top, value2 to right, value3 to bottom, and value4 to the left |

### Resetting Padding & Margin

The default values for padding & margin are often difficult to work with. As a result, some developers make it a habit to simply reset them to 0 with
```
element {
    padding: 0;
    margin: 0;
}
```
Although this forces you to manually set all the padding and margins yourself, it also gives you the freedom of control over the whitespace of a page.

### Collapsing Margins

When faced with two box models with overlapping margins, instead of adding the respective margins together to create a new value, CSS instead just takes the larger of the two as the margin between the models. When faced with such a situation, it is easiest to just increase the margins on one end of the divide. Alternatively, you can adjust the margin/padding on one of the two elements. This works because the browser doesn't collapse a margin/padding combo, but only margins.

### Page Flow 💮

* Inline elements - Rendered left to right within element's parent container
* Block-level elements - Stacked on top of each other with the first element on top and so on

If we take a piece of code that looks something like
```
<section> Section 1</section>
<section> Section 2</section>
<section> Section 3</section>
<section> Section 4</section>
```

It would render as:

|     |
| --- |
| Section 1 |
| Section 2 |
| Section 3 |
| Section 4 |

Instead. we want something that allows us to more effectively make use of our space and create a more aesthetically pleasing web page.

### Floating

When we float an element, the web browser takes the element out of the default page flow. There are two ways to float:

* Float left - Browser places element as far to the left and as high as possible within parent container
* Float right - Browser places element as far to the right and as high as possible within parent container

Implementation looks like this:
```
element {
    float: left|right|none;
}
```
However, floating one element can also affect the way that the rest of the page flow operates. To get around this, we can do something called clear. The clear property effectively allows the element to clear the floated element:
```
element {
    clear: left|right|both|none;
}
```
clear: left clears left-floated elements, clear:right clears right-floated elements, clear: both clears all floated elements, and clear: none doesn't clear anything.

### Collapsing Containers

If all elements within a parent container are floated, it dos something that is referred to as a container collapse. This happens because all the elements within the parent container disrupt the natural page flow and as a result, the parent container behaves as if it had no content at all. To fix this, we have to force the parent container to clear its children:
**html:**
```
<article class="self-clear">
```
**css:**
```
.self-clear::after {
    content = "";
    display: block;
    clear: both;
}
```
::after is a pseudo-element that tells the browser to create an element and add it to the page flow after whatever element gets the class. This adds an empty string that doesn't disrupt the appearance of the page and resolves the collapsing container issue.

### Positioning Elements

Instead of floating an element, we can directly place it wherever we wish(positioning):
```
element {
    position: static|relative|absolute|fixed;
}
```

* static - Places the element in its default position in page flow(default setting)
* relative - Offsets element from its default position with respect to its parent container while keeping the element in the page flow
* absolute - offsets the element from its default position with respect to its parent or earlier ancestor container while removing the element from the page flow
* fixed - Offsets the element from its default position with respect to the browser window while removing the element from the page flow

The latter 3 position values offset the element. As such, it requires value by which to offset it:
```
element {
    top: top-value;
    right: right-value;
    bottom: bottom-value;
    left: left-value;
}
```
Note that top shifts the element down, right shifts the element from the right, bottom shifts the element up, and left shifts the element from the left.
**Relative Positioning**
Relative positioning offsets the element but retains the elements former place in the default page flow:
										Version 1                                                                                                Offset Version

|     |     |     |     |
| --- | --- | --- | --- |
| 1   |     | 1   |     |
| 2   |     | 2   |     |
| 3   |     |     | 3   |
| 4   |     | 4   |     |
| 5   |     | 5   |     |

**Absolute Positioning**
Absolute positioning will offset the element with respect to the closes ancestor element that uses non-static positioning. It will keep searching up the ancestor tree until it finds an ancestor with a non-static position property and then offsets it with respect to that. If we do something like:
```
section {
    position: relative;
    border: 1px double black
}
img {
    position: absolute;
    top: 0;
    right: 0;
}
```
												Version 1                                                                                        Offset Version

|     |     |     |     |
| --- | --- | --- | --- |
| 1   |     | 2   | 1   |
| 2   |     | 3   |     |
| 3   |     | 4   |     |
| 4   |     | 5   |     |
| 5   |     |     |     |

**Fixed Positioning**
As the name implies, fixed positioning fixes the element to a certain position within the page. This makes it such that even scrolling or moving around the page will not affect the fixed positioning of the element. This is useful for a page header or something of the sort.
