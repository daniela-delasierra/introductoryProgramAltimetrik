

# HTML

HTML (HyperText Markup Language) is the most basic building block of the Web. It defines the meaning and structure of web content."Hypertext" refers to links that connect web pages to one another, either within a single website or between websites. HTML consists of a series of elements, which you use to enclose, or wrap, different parts of the content to make it appear a certain way, or act a certain way. Elements![img](https://lh5.googleusercontent.com/JbpJz_GH7Da0VQB6ejcCIFQqzNPg7v9Sex3YQNftGhrnoEO8fMoiCrB9bd_Sn4QHSnEHdalTGXTnCEMTLn1LSTSxZTz7l0vVlRqEO8QtUMdpgc4oSMjLs4hdcxLfWdBJpyPJzJQn)

The main parts of our element are as follows:

**The opening tag:** This consists of the name of the element (in this case, p), wrapped in opening and closing angle brackets. This states where the element begins or starts to take effect — in this case where the paragraph begins.

**The closing tag:** This is the same as the opening tag, except that it includes a forward slash before the element name. This states where the element ends — in this case where the paragraph ends. Failing to add a closing tag is one of the standard beginner errors and can lead to strange results.

**The content:** This is the content of the element, which in this case, is just text.

**The element:** The opening tag, the closing tag, and the content together comprise the element.AttributesElements can also have attributes that look like the following:![img](https://lh6.googleusercontent.com/o6BoUb5FCV6nilEw_zH2MlxTuDvVaRqxq8O_WlI7pDqH6hE8kvgKk7BSlvO7d8PEQkQyPRv0dcj6d_e9v2XLjGohbqenya4ZBHUawglCJV2zpzlkpTNh85sHFfMshIN5a7u7ubs7)Attributes contain extra information about the element that you don't want to appear in the actual content.

- All HTML elements can have attributes
- Attributes provide additional information about elements
- Attributes are always specified in the start tag
- Attributes usually come in name/value pairs like: name="value"

## HTML Comments

HTML comments are not displayed in the browser, but they can help document your HTML source code.

You can add comments to your HTML source by using the following syntax:*<!-- Write your comments here -->*

## HTML Documents

All HTML documents must start with a document type declaration: <!DOCTYPE html>.
The HTML document itself begins with <html> and ends with </html>.
The visible part of the HTML document is between <body> and </body>.
`<!DOCTYPE html>`

`<html>`

`<head>`

`<title>Page Title</title>`

`</head>`

`<body>`

`<h1>This is a Heading</h1>`

`<p>This is a paragraph.</p>`

`</body>`

`</html>`

## The <!DOCTYPE> Declaration

The <!DOCTYPE> declaration represents the document type, and helps browsers to display web pages correctly.
It must only appear once, at the top of the page (before any HTML tags).
The <!DOCTYPE> declaration is not case sensitive.
The <!DOCTYPE> declaration for HTML5 is: <!DOCTYPE html>

## HTML <meta> Tag

The <meta> tag defines metadata about an HTML document. Metadata is data (information) about data.

The <meta> tag defines metadata about an HTML document. Metadata is data (information) about data. 

<meta> tags always go inside the <head> element, and are typically used to specify character set, page description, keywords, author of the document, and viewport settings. Metadata will not be displayed on the page, but is machine parsable. Metadata is used by browsers (how to display content or reload page), search engines (keywords), and other web services. There is a method to let web designers take control over the viewport (the user's visible area of a web page), through the <meta> tag (See "Setting The Viewport" example below).

Metadata will not be displayed on the page, but is machine parsable. Metadata is used by browsers (how to display content or reload page), search engines (keywords), and other web services. There is a method to let web designers take control over the viewport (the user's visible area of a web page), through the <meta> tag (See "Setting The Viewport" example below).<head>

<head>
 <meta charset="UTF-8">
 <meta name="description" content="Free Web tutorials">
 <meta name="keywords" content="HTML, CSS, JavaScript">
 <meta name="author" content="John Doe">
 <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>

**Attribute**

1. charset
2. content
3. http-equiv
4. name

**Value**

1. character_set
2. text
3. content-security-policy / content-type /default-style / refresh
4. application-name / author / description / generator / keywords / viewport

**Description**

1. Specifies the character encoding for the HTML document
2. Specifies the value associated with the http-equiv or name attribute.
3. Provides an HTTP header for the information/value of the content attribute.
4. Specifies a name for the metadata.

## Headings

HTML headings are defined with the <h1> to <h6> tags. <h1> defines the most important heading. <h6> defines the least important heading.

## Paragraphs

The HTML <p> element defines a paragraph. A paragraph always starts on a new line, and browsers automatically add some white space (a margin) before and after a paragraph.
The browser will automatically remove any extra spaces and lines when the page is displayed.

## HTML Horizontal Rules

The <hr> tag defines a thematic break in an HTML page, and is most often displayed as a horizontal rule. The <hr> element is used to separate content (or define a change) in an HTML page.

## HTML Line Breaks

The HTML \<br> element defines a line break.
Use \<br> if you want a line break (a new line) without starting a new paragraph. 
The \<br> tag is an empty tag, which means that it has no end tag.

## The HTML <pre> Element

The text inside a <pre> element is displayed in a fixed-width font (usually Courier), and it preserves both spaces and line breaks.

## HTML Quotation and Citation Elements

**Tag**

- [<abbr>](https://www.w3schools.com/tags/tag_abbr.asp)
- [<address>](https://www.w3schools.com/tags/tag_address.asp)
- [<bdo>](https://www.w3schools.com/tags/tag_bdo.asp)
- [<blockquote>](https://www.w3schools.com/tags/tag_blockquote.asp)
- [<cite>](https://www.w3schools.com/tags/tag_cite.asp)
- [<q>](https://www.w3schools.com/tags/tag_q.asp)

**Description**

- Defines an abbreviation or acronym
- Defines contact information for the author/owner of a document
- Defines the text direction
- Defines a section that is quoted from another source
- Defines the title of a work
- Defines a short inline quotation

## HTML Links

The HTML <a> tag defines a hyperlink. It has the following syntax:`<a href="url">link text</a>`

The most important attribute of the <a> element is the href attribute, which indicates the link's destination.
The link text is the part that will be visible to the reader.
Clicking on the link text, will send the reader to the specified URL address.

### Absolute URLs vs. Relative URLs

A local link (a link to a page within the same website) is specified with a relative URL (without the "https://www" part)

`<h2>Absolute URLs</h2>`

`<p><a href="https://www.w3.org/">W3C</a></p>`

`<p><a href="https://www.google.com/">Google</a></p>`

`<h2>Relative URLs</h2>`

`<p><a href="html_images.asp">HTML Images</a></p>`

`<p><a href="/css/default.asp">CSS Tutorial</a></p>`

## HTML Images

The HTML <img> tag is used to embed an image in a web page.
Images are not technically inserted into a web page; images are linked to web pages. 
The <img> tag creates a holding space for the referenced image.
The <img> tag is empty, it contains attributes only, and does not have a closing tag.
The <img> tag has two required attributes: 

- src - Specifies the path to the image
- alt - Specifies an alternate text for the image

### The src Attribute

The required src attribute specifies the path (URL) to the image.

### The alt Attribute

The required alt attribute provides an alternate text for an image, if the user for some reason cannot view it (because of slow connection, an error in the src attribute, or if the user uses a screen reader).
The value of the alt attribute should describe the image.

### Image Size - Width and Height

You can use the style attribute to specify the width and height of an image.

`<img src="img_girl.jpg" alt="Girl in a jacket" width="500" height="600">`
Alternatively, you can use the width and height attributes:

`<img src="img_girl.jpg" alt="Girl in a jacket" width="500" height="600">`

## HTML Tables

The <table> tag defines an HTML table.
Each table row is defined with a <tr> tag. Each table header is defined with a <th> tag. 
Each table data/cell is defined with a <td> tag.
By default, the text in <th> elements are bold and centered.
By default, the text in <td> elements are regular and left-aligned.

`<table style="width:100%">
 <tr>
  <th>Firstname</th>
  <th>Lastname</th>
  <th>Age</th>
 </tr>
 <tr>
  <td>Jill</td>
  <td>Smith</td>
  <td>50</td>
 </tr>
 <tr>
  <td>Eve</td>
  <td>Jackson</td>
  <td>94</td>
 </tr>
</table>`

## HTML Lists

### Unordered HTML List

An unordered list starts with the <ul> tag. Each list item starts with the <li> tag.
The list items will be marked with bullets (small black circles) by default.

`<ul>
 <li>Coffee</li>
 <li>Tea</li>
 <li>Milk</li>
</ul>`

### Ordered HTML List

An ordered list starts with the <ol> tag. Each list item starts with the <li> tag.
The list items will be marked with numbers by default:

`<ol>
 <li>Coffee</li>
 <li>Tea</li>
 <li>Milk</li>
</ol>`

### HTML Description Lists

A description list is a list of terms, with a description of each term.
The <dl> tag defines the description list, the <dt> tag defines the term (name), and the <dd> tag describes each term.

`<dl>
 <dt>Coffee</dt>
 <dd>- black hot drink</dd>
 <dt>Milk</dt>
 <dd>- white cold drink</dd>
</dl>`

## HTML Forms

An HTML form is used to collect user input. The user input is most often sent to a server for processing.
The HTML <form> element is used to create an HTML form for user input.
An <input> element can be displayed in many ways, depending on the type attribute.

### The HTML <form> Elements

The HTML <form> element can contain one or more of the following form elements:

- \<input>
- \<label>

The <label> element defines a label for several form elements.
The <label> element is useful for screen-reader users, because the screen-reader will read out loud the label when the user focus on the input element.
The <label> element also help users who have difficulty clicking on very small regions (such as radio buttons or checkboxes) - because when the user clicks the text within the <label> element, it toggles the radio button/checkbox.
The for attribute of the <label> tag should be equal to the id attribute of the <input> element to bind them together.

- \<select>

The \<select> element defines a drop-down list.
The <option> elements defines an option that can be selected.
By default, the first item in the drop-down list is selected.
To define a pre-selected option, add the selected attribute to the option.
`<label **for**="cars">Choose a car:</label>`
`<select id="cars" name="cars">
 <**option** **value**="volvo">Volvo</**option**>
 <**option** **value**="saab">Saab</**option**>
 <**option** **value**="fiat">Fiat</**option**>
 <**option** **value**="audi">Audi</**option**>
</select>`

`<**option** **value**="fiat" selected>Fiat</**option**>`

Use the size attribute to specify the number of visible values.
Use the multiple attribute to allow the user to select more than one value.

- \<textarea>

The <textarea> element defines a multi-line input field (a text area).
The rows attribute specifies the visible number of lines in a text area.
The cols attribute specifies the visible width of a text area.
`<textarea name="message" rows="10" cols="30">
The cat was playing in the garden.
</textarea>`

- \<button>

The \<button> element defines a clickable button
`<button type="button" onclick="alert('Hello World!')">Click Me!</button>`

- \<fieldset>
- \<legend>

The <fieldset> element is used to group related data in a form.
The <legend> element defines a caption for the <fieldset> element.
`<form action="/action_page.php">
 <fieldset>
  <legend>Personalia:</legend>
  <label for="fname">First name:</label><br>
  <input type="text" id="fname" name="fname" value="John"><br>
  <label for="lname">Last name:</label><br>
  <input type="text" id="lname" name="lname" value="Doe"><br><br>
  <input type="submit" value="Submit">
 </fieldset>
</form>`

- \<datalist>

- \<option>

- \<optgroup>

  The <datalist> element specifies a list of pre-defined options for an <input> element.
  The <optgroup> tag is used to group related options in a [<select>](https://www.w3schools.com/tags/tag_select.asp) element (drop-down list).
  If you have a long list of options, groups of related options are easier to handle for a user.

`<form action="/action_page.php">`
   `<input list="browsers">`
   ` <datalist id="browsers">`
      `  <option value="Internet Explorer">`
      `<option value="Firefox">`
      `option value="Chrome">`
      `  <option value="Opera">`
      `  <option value="Safari">`
   ` </datalist>`
`</form>`

- \<output>

  The <output> element represents the result of a calculation (like one performed by a script).
  `<form action="/action_page.php"``
  ``oninput="x.value=parseInt(a.value)+parseInt(b.value)">
   0
   <input type="range" id="a" name="a" value="50">
   100 +
   <input type="number" id="b" name="b" value="50">
   =
   <output name="x" for="a b"></output>
   <br><br>
   <input type="submit">
  </form>`

## HTML Input Types

Here are the different input types you can use in HTML:

<input type="button">

<input type="checkbox">

<input type="color">

<input type="date">

<input type="datetime-local">

<input type="email">

<input type="file">

<input type="hidden">

<input type="image">

<input type="month">

<input type="number">

<input type="password">

<input type="radio">

<input type="range">

<input type="reset">

<input type="search">

<input type="submit">

<input type="tel">

<input type="text">

<input type="time">

<input type="url">

<input type="week">

## Form Validation

Before submitting data to the server, it is important to ensure all required form controls are filled out, in the correct format. This is called **client-side form validation**, and helps ensure data submitted matches the requirements set forth in the various form controls. 

*More about form inputs and HTML5 form validation:*

https://developer.mozilla.org/en-US/docs/Learn/Forms/Form_validation

https://tutorial.techaltum.com/html5-form.html

## HTML Versus XHTML

### What is XHTML?

XHTML stands for EXtensible HyperText Markup Language
XHTML is a stricter, more XML-based version of HTML
XHTML is HTML defined as an XML application
XHTML is supported by all major browsers

Main differences between HTML and XHTML: https://www.mclibre.org/consultar/htmlcss/html/html-xhtml-diferencias.html

## Bibliography:

### HTML

https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/HTML_basics

https://www.mclibre.org/consultar/htmlcss/html/html-xhtml-diferencias.html

https://www.w3schools.com/html/

 Other tags: https://developer.mozilla.org/en-US/docs/Web/HTML/Element