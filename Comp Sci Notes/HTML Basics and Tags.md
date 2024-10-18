---
---
## [[Table of Contents]]

HTML - Hypertext Markup Language -> The code that provides the instructions on the contents of a web page, that defines the links that characterize web pages.
The basic element of HTML is the tag,  markup codes that act similarly to the walls of a room or the boundaries of a container to store things inside.
The simplest of HTML tags might look something like
```
<tag>content</tag>
```
The / notation within </tag> notates that it is the ending tag, or the tail end of the section. These markers tell web browsers how to parse through a file and convert the code into a tangible appearance. Furthermore, most HTML files will usually start with something that looks like
```
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="utf-8">
        <title>My Home Sweet Home Page</title>
    </head>
    <body>
    </body>
</html>
```
The !DOCTYPE indicates to the web browser that the file is of HTML type and to read it as such. The lang=en indicates that the language for the file is english. The meta charset="utf-8" is what will typically be used in an HTML file as it is a highly inclusive charset that includes most if not all characters that might be needed in a HTML file. The <title> tag indicates what the title of the page will be. For example, the [instagram.com](http://instagram.com) title might be "Instagram".

## HTML Tags (. ❛ ᴗ ❛.)

|     |     |     |     |
| --- | --- | --- | --- |
| **BASIC TAGS** |     | **FORMATTING** |     |
| <html>  </html> | Creates an HTML document | <p>  </p> | Creates a new paragraph |
| <head>  </head> | Sets off the title & other non-displayed information | <br> | Inserts a line break |
| <body>  </body> | Sets off the visible portion of the web page -> displayed information | <blockquote> </blockquote> | Puts content inside quote, creates indentation on either side |
| <title>  </title> | Puts name of document in the title bar, bookmarked page title | <div> </div> | Used to format block content with CSS, often used to file miscellaneous content |
| **BODY ATTRIBUTES** |     | <span> </span> | Used to format in-line content with CSS, can be used to stylize certain parts within a larger tagged section |
| <body bgcolor=?> | Set background color using hex or name | **LISTS** |     |
| <body text=?> | Set text color using hex or name | <ul> </ul> | Creates unordered list (bullet points) |
| <body link=?> | Set link color using hex or name | <ol start =?> </ol> | Creates ordered list (numbers) where start = x and x is a counting number |
| <body vlink=?> | Set visited link color using hex or name | <li> </li> | Encompasses each list item<br>```<br><ul><br>  <li>Lana del Rey</li><br>  <li>Mitski</li><br></ul?<br>``` |
| <body alink=?> | Set active (mouse hover) link color using hex or name | <dl> </dl> | Creates a definition list |
| **TEXT TAGS** |     | <dt> | Precedes definition term |
| <pre> </pre> | Creates preformatted text | <dd> | Precedes definition |
| <h1> </h1>, <h?> /h?> | Creates headlines, 1<=?<=6, h1 being the largest and h6 the smallest | **GRAPHICAL ELEMENTS** |     |
| <b> </b> | Creates bold text, alternatively use <strong> | <hr> | Inserts a horizontal rule in the appearance of a line |
| <i> </i> | Creates italicized text, alternatively use <em> | <hr size=?> | Sets size(height) of horizontal rule |
| <tt> </tt> | Creates typewriter style text | <hr width=?> | Sets width of rule as a % or pixel length |
| <code> </code> | Defines source code, usually monospace | <hr noshade> | Creates horizontal rule without shadow |
| <cite> </cite> | Defines a citation, usually processed in italics |     | Adds an image found at the location of the URL |
| <address> </address> | Creates address section, usually processed in italics | <img src="URL" align=?> | Aligns image left/right/center/bottom/top/middle(use CSS) |
| <font size=?> </font> | Sets font size from 1-7, alternatively done through CSS instead | <img src="URL" border=?> | Sets size of border surrounding image(use CSS) |
| <font face=?> </font> | Defines the font used, alternatively done through CSS instead | <img src="URL" height=?> | Sets height of image in pixels |
| **LINKS** |     | <img src='URL" width=?> | Sets width of image in pixels |
| <a href="URL">clickable text</a> | Creates a hyperlink to the specified URL | <img src="URL" alt=?> | Sets alternative text for  browsers that can't process images(required by ADA) |
| <a href="mailto":EMAIL\_ADDRESS>clickable text</a> | Creates a hyperlink to an email address | **HTML5 INPUT TAG ATTRIBUTES** |     |
| <a name="NAME"><br>or<br><a id="NAME">Section name</a> | Creates a target location within a document | <input type="email" name=?> | Sets a single-line textbox to input email addresses |
| <a href="#NAME">clickable text</a> | Creates a link to target location<br>```<br><a name="PARA_BEGINNING"><br>^<br>\|<br>\|<br>\|<br>\|<br><a href="#PARA_BEGINNING">Paragraph</a><br>``` | <input type="url" name=?> | Sets a single-line textbox to input URLs |
| **FORMS** |     | <input type="number" name=?> | Sets a single-line textbox for a number |
| <form> </form> | Defines a form | <input type="range" name=?> | Sets a single-line text box for a range of numbers |
| <select multiple name=? size=?> </select> | Creates a scrolling menu. Size sets the number of menu items visible before user needs to scroll | <input type="date/month/week/time" name=?> | Sets a single-line text box with a calendar showing the date/month/week/time |
| <select name=?> </select> | Creates a pulldown menu | <input type="search" name=?> | Sets a single-line text box for searching |
| <option> | Sets off each menu item | <input type="color" name=?> | Sets a single-line text box for picking a color |
| <textarea name=? cols="x" rows="y"> </textarea> | Creates a text box area. Columns set the width; rows sets the height | **TABLE ATTRIBUTES** |     |
| <input type="checkbox" name=? value=?> | Creates a checkbox | <table border=?> | Sets the width of the order around table cells |
| <input type="checkbox" name=? value=? checked> | Creates a pre-checked checkbox | <table cellspacing=?> | Sets amount of space between table cells |
| <input type="radio" name=? value=?> | Creates a radio button, adding checked will pre-check it | <table cellpadding=?> | Sets amount of space between cell border and contents |
| <input type="text" name=? size=?> | Creates a one-line text area. Size sets length, in characters | <table width=?> | Sets width of the table in percentage or pixels |
| <input type="submit" value=?> | Creates a submit button. Value sets the text in the submit button | <tr align=?> | Sets alignment for cells within the row(left, center, right) |
| <input type="image" name=? src=? border=? alt=?> | Creates a submit button using an image and taking in the different properties in accordance with the img src tag | <td align=?> | Sets alignment for cells (left, center, right) |
| <input type="reset"> | Creates a reset button | <tr valign=?> | Sets vertical alignment for cells within the row(top, middle, bottom) |
| **TABLES** |     | <td valign=?> | Sets vertical alignment for cell(top, middle, bottom) |
| <table> </table> | Creates a table | <td rowspan=?> | Sets number of rows a cell should span(default=1) |
| <tr> </tr> | Sets off each row in a table | <td colspan=?> | Sets number of columns a cell should span(default=1) |
| <td> </td> | Sets off each cell in a row | <td nowrap> | Prevents lines within a cell from being broken to fit |
| <th> </th> | Sets off the table header (normal cell with bold, centered text) |     |     |

## CSS (⓿\_⓿)

CSS, or cascading style sheets, is a language that accompanies HTML and is used to stylize the objects that HTML creates and changes its properties. For example, by displaying something such as
```
<h1 style="color:red";>This text is red</h1>
```
we can effectively change the attributes of things we create. However, CSS extends beyond in line references and can even extend to external referencing. By doing something such as
```
<head>
    <style>
        h1 {
            color: red;
            font-family: Verdana;
            font-size: 72px;
        }
    </style>
</head>
<body>
    <h1>This header is stylized according to the properties defined above</h1>
</body>
```
In this fashion, all h1 headers within the file will have the color red, font-family Verdana, and font-size of 72 px.
Finally, we can do something called linking to an external style sheet. We can create an external file, name it something such as styles.css, and then use those properties defined wherever we wish. It might look something like:

### styles.css

```
h1 {
    color: red;
    font-family: Verdana;
    font-size: 72px;
}
p {
    color: blue;
    font-size: 32px;
}
```

### page.html

```
<!DOCTYPE HTML>
<html lang="en">
    <head>
        <link rel="stylesheet" href="styles.css">
    </head>
    <body>
        <h1>This is red, font Verdana, and has a font size of 72px</h1>
        <p>This is blue and has a font size of 32px</p>
    </body>
</html>
```
