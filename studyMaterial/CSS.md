# CSS

CSS (an abbreviation of Cascading Style Sheets) is the language that we use to style an HTML file, and tell the browser how it should render the elements on the page.

![img](https://lh4.googleusercontent.com/oZ3wt2-9KVqMxRF_L7uxocjF10MHJ3EXMEdq2NjEqfV4wLywYGoCjwiG5MvE55cICs2lKHK-louAdO9RAk0lJyjCGU4IZa8QXx4CHsCG_b13hM4738aZjdymLXT_RjP-oBOCBBhN)

The selector points to the HTML element you want to style.
The declaration block contains one or more declarations separated by semicolons. Each declaration includes a CSS property name and a value, separated by a colon.
Multiple CSS declarations are separated with semicolons, and declaration blocks are surrounded by curly braces.

## ADDING CSS TO AN HTML PAGE

CSS is attached to an HTML page in different ways.

### 1: Using the link tag

The link tag is the way to include a CSS file. This is the preferred way to use CSS as it's intended to be used: one CSS file is included by all the pages of your site, and changing one line on that file affects the presentation of all the pages in the site.

To use this method, you add a link tag with the href attribute pointing to the CSS file you want to include. You add it inside the head tag of the site (not inside the body tag):

`<link rel="stylesheet" type="text/css" href="myfile.css">`

The rel and type attributes are required too, as they tell the browser which kind of file we are linking to.

### 2: using the style tag

Instead of using the link tag to point to a separate stylesheet containing our CSS, we can add the CSS directly inside a style tag. This is the syntax:

`<style>`

`...our **CSS**...`

`</style> `

### 3: inline styles

Inline styles are the third way to add CSS to a page. We can add a style attribute to any HTML tag, and add CSS into it.

`<div style="">...</div>`

## CASCADE

Cascade is the process, or algorithm, that determines the properties applied to each element on the page. Trying to converge from a list of CSS rules that are defined in various places.

It does so taking in consideration:

- specificity
- importance
- inheritance
- order in the file

It also takes care of resolving conflicts. Two or more competing CSS rules for the same property applied to the same element need to be elaborated according to the CSS spec, to determine which one needs to be applied.
Even if you just have one CSS file loaded by your page, there is another CSS that is going to be part of the process. We have the browser (user agent) CSS. 

Browsers come with a default set of rules, all different between browsers. Then the browser applies any user stylesheet, which might also be applied by browser extensions. All those rules come into play while rendering the page.

### SPECIFICITY

What happens when an element is targeted by multiple rules, with different selectors, that affect the same property?
For example, let’s talk about this element:

`<p class="dog-name">`

` Roger`

`</p>`

We can have

`.dog-name {`

` color: yellow;`

`}`

and another rule that targets p, which sets the color to another value:

`p {`

 `color: red;`
 
`}`

**Which rule is going to take precedence over the others, and why?**

The more specific rule will win. If two or more rules have the same specificity, the one that appears last wins.

#### How to calculate specificity

Specificity is calculated using a convention. We have 4 slots, and each one of them starts at 0: 0 0 0 0 0. The slot at the left is the most important, and the rightmost one is the least important.

*Slot 1*

The first slot, the rightmost one, is the least important. We increase this value when we have an element selector. An element is a tag name. If you have more than one element selector in the rule, you increment accordingly the value stored in this slot.
Examples:

p {}          /* 0 0 0 1 */

span {}         /* 0 0 0 1 */

p span {}        /* 0 0 0 2 */

p > span {}       /* 0 0 0 2 */

div p > span {}     /* 0 0 0 3 */


*Slot 2*

The second slot is incremented by 3 things:

- class selectors
- pseudo-class selectors
- attribute selectors

Every time a rule meets one of those, we increment the value of the second column from the right.

Examples:

.name {}         /* 0 0 1 0 */

.users .name {}     /* 0 0 2 0 */

[href$='.pdf'] {}    /* 0 0 1 0 */

:hover {}        /* 0 0 1 0 */


*Slot 3*

Slot 3 holds the most important thing that can affect your CSS specificity in a CSS file: the id. Every element can have an id attribute assigned, and we can use that in our stylesheet to target the element.

Examples:

#name {}          /* 0 1 0 0 */

.user #name {}       /* 0 1 1 0 */

#name span {}        /* 0 1 0 1 */


*Slot 4*

Slot 4 is affected by inline styles. Any inline style will have precedence over any rule defined in an external CSS file, or inside the style tag in the page header.

Example:

`<p style="color: red">Test</p> `  `/* 1 0 0 0 */`

Even if any other rule in the CSS defines the color, this inline style rule is going to be applied. Except for one case — if !important is used, which fills the slot 5.

*Importance*

Specificity does not matter if a rule ends with !important:

`p {
 font-size: 20px!important;
}`

That rule will take precedence over any rule with more specificity. Adding !important in a CSS rule is going to make that rule more important than any other rule, according to the specificity rules. The only way another rule can take precedence is to have !important as well, and have higher specificity in the other less important slots.

#### Tools to calculate the specificity

You can use the site https://specificity.keegan.st/ to perform the specificity calculation for you automatically.

### INHERITANCE

When you set some properties on a selector in CSS, they are inherited by all the children of that selector. I said some, because not all properties show this behavior. This happens because some properties make sense to be inherited. This helps us write CSS much more concisely, since we don’t have to explicitly set that property again on every single child.
Some other properties make more sense to not be inherited.

#### Forcing properties to inherit

What if you have a property that’s not inherited by default, and you want it to, in a child?
In the children, you set the property value to the special keyword inherit.

`body {
  background-color: yellow;
}`

`p {
 background-color: inherit;
}`

#### Forcing properties to NOT inherit

On the contrary, you might have a property inherited and you want to avoid so. You can use the **revert** keyword to revert it. In this case, the value is reverted to the original value the browser gave it in its default stylesheet. In practice this is rarely used, and most of the time you’ll just set another value for the property to overwrite that inherited value.

#### Other special values

In addition to the inherit and revert special keywords we just saw, you can also set any property to:

initial: use the default browser stylesheet if available. If not, and if the property inherits by default, inherit the value. Otherwise do nothing.

unset: if the property inherits by default, inherit. Otherwise do nothing.

## IMPORT

From any CSS file you can import another CSS file using the @**import** directive. Here is how you use it:

`@import url(myfile.css)`

url() can manage absolute or relative URLs. One important thing you need to know is that @**import** directives must be put before any other CSS in the file, or they will be ignored. You can use media descriptors to only load a CSS file on the specific media:

`@import url(myfile.css) all;`

`@import url(myfile-screen.css) screen;`

`@import url(myfile-print.css) print;`

## SELECTORS

A selector allows us to associate one or more declarations to one or more elements on the page.

### Tag Selector

Every HTML tag has a corresponding selector, for example: div, span, img.

If a selector matches multiple elements, all the elements in the page will be affected by the change.

`p {`

` color: yellow;`

`}`

**Classes are identified using the . symbol, while ids using the # symbol.**

### ID selector

`<p id="dog-name">`

 `Roger`
 
`</p>`

`#dog-name {`

` color: yellow;`

`}`

### Class selector

`<p class="dog-name">`

 `Roger`
 
`</p>`

`.dog-name {`

 `color: yellow;`
 
`}`

### Targeting multiple classes

You can target an element with a specific class using .class-name, as you saw previously. You can target an element with 2 (or more) classes by combining the class names separated with a dot, without spaces.

Example:

`<p class="dog-name roger">`

 `Roger`
 
`</p>`

`.dog-name.roger {`

`color: yellow;`

`}`

### Combining classes and ids

In the same way, you can combine a class and an id.
Example:

`<p class="dog-name" id="roger">`

 `Roger`
 
`</p>`

`.dog-name#roger {`

 `color: yellow;`
 
`}`

### Grouping selectors

You can combine selectors to apply the same declarations to multiple selectors. To do so, you separate them with a comma.

Example:

`<p>`

 `My dog name is:`
 
`</p>`

`<span class="dog-name">`

 `Roger`
 
`</span>`

`p, .dog-name {`

 `color: yellow;`
 
`}`

### Follow the document tree with selectors

You can create a more specific selector by combining multiple items to follow the document tree structure. For example, if you have a span tag nested inside a p tag, you can target that one without applying the style to a span tag not included in a p tag:

`<span>`

 `Hello!`
 
`</span>`

`<p>`

 `My dog name is:`
 
 `<span class="dog-name">`
 
  `Roger`
  
 `</span>`
 
`</p>`

`p span {`

 `color: yellow;`
 
`}`

See how we used a space between the two tokens p and span. This works even if the element on the right is multiple levels deep.

To make the dependency strict on the first level, you can use the **>** symbol between the two tokens: 

`p > span {`

 `color: yellow;`
 
`}`

Adjacent sibling selectors let us style an element only if preceded by a specific element. We do so using the **+** operator:
Example:

`p + span {`

 `color: yellow;`
 
`}`

### ATTRIBUTE SELECTORS

#### Attribute presence selectors

The first selector type is the attribute presence selector. We can check if an element has an attribute using the [] syntax. p[id] will select all p tags in the page that have an id attribute, regardless of its value:

`p[id] {`

 `/* ... */`
 
`}`

#### Exact attribute value selectors

Inside the brackets you can check the attribute value using =, and the CSS will be applied only if the attribute matches the exact value specified:

`p[id="my-id"] {`

 `/* ... */`
 
`}`

#### Match an attribute value portion

While = lets us check for exact value, we have other operators:

*= checks if the attribute contains the partial

^= checks if the attribute starts with the partial

$= checks if the attribute ends with the partial

|= checks if the attribute starts with the partial and it's followed by a dash (common in classes, for example), or just contains the partial

~= checks if the partial is contained in the attribute, but separated by spaces from the rest

All the checks we mentioned are case sensitive. If you add an i just before the closing bracket, the check will be case insensitive. It's supported in many browsers but not in all, check https://caniuse.com/#feat=css-case-insensitive.

### PSEUDO-CLASSES

Pseudo classes are predefined keywords that are used to select an element based on its state, or to target a specific child.

They start with a single colon :.They can be used as part of a selector, and they are very useful to style active or visited links, for example, change the style on hover, focus, or target the first child, or odd rows. Very handy in many cases.

These are the most popular pseudo classes you will likely use:![img](https://lh5.googleusercontent.com/TmXcSe_v_7-fZx8v7dsnHHDdC-fWxWvSMWzzjGBphYktl8_UwWd3H2q1ItIR2sfc3X90ZQzoKp3dWWMUh-wWo9QhFMeSsfi8qm9zdw1TmQprO8ABlwC8tU5wHtWF52Lh4mgfmFcx)

**:nth-child()** deserves a special mention. It can be used to target odd or even children with :nth-child(odd) and :nth-child(even). It is commonly used in lists to color odd lines differently from even lines:

`ul:nth-child(odd) {`

 `color: white;`
 
  `background-color: black;`
  
`}`

You can also use it to target the first 3 children of an element with :nth-child(-n+3). Or you can style 1 in every 5 elements with :nth-child(5n).

Some pseudo classes are just used for printing, like :first, :left, :right, so you can target the first page, all the left pages, and all the right pages, which are usually styled slightly differently.

### PSEUDO-ELEMENTS

Pseudo-elements are used to style a specific part of an element. They start with a double colon ::.
::**before** and ::**after** are probably the most used pseudo-elements. They are used to add content before or after an element, like icons for example.

Here's the list of the pseudo-elements:![img](https://lh5.googleusercontent.com/wGpYQUjgwqOGeAABu2vSioNCCPJ2DrbxD63IaKPR-FgmGQ_a__wqN7X3bAQkk9KdM82FzS4Do1i1ikXKyoCc26e-oeaBYwXjZS8ANrdvGlTYdWNuCorB5uz6AReBZ5dAGxe2YU2p)

Let's do an example. Say you want to make the first line of a paragraph slightly bigger in font size, a common thing in typography:

`p::first-line {`

 `font-size: 2rem;`
 
`}`

Or maybe you want the first letter to be bolder:

`p::first-letter {`

 `font-weight: bolder;`
 
`}`

::after and ::before are a bit less intuitive. I remember using them when I had to add icons using CSS.
You specify the content property to insert any kind of content after or before an element:

`p::before {`

 `content: url(/myimage.png);`
 
`}`

`.myElement::before {`

  `content: "Hey Hey!";`
  
`}`

## BOX MODEL

In CSS, the term "box model" is used when talking about design and layout. The CSS box model is essentially a box that wraps around every HTML element. It consists of: margins, borders, padding, and the actual content. The image below illustrates the box model:
![img](https://lh6.googleusercontent.com/JQzy9Ll3OV7f2eA7DWNOv-krCvMwe4RzjLb5Lgu3Y1NPAQRkxyHVuWnWqbIi4JU43Qg8aUdhOUeksLHPYj9ze0LLDqH8yqqnESGnYrZNtop_DDxiJDXqcOtB3UYZKulCFj511LfZ)
Explanation of the different parts:

Content - The content of the box, where text and images appear

Padding - Clears an area around the content. The padding is transparent

Border - A border that goes around the padding and content

Margin - Clears an area outside the border. The margin is transparent

The total width of an element should be calculated like this:
Total element width = width + left padding + right padding + left border + right border + left margin + right margin

The total height of an element should be calculated like this:
Total element height = height + top padding + bottom padding + top border + bottom border + top margin + bottom margin

## BOX SIZING

The default behavior of browsers when calculating the width of an element is to apply the calculated width and height to the content area, without taking any of the padding, border and margin in consideration. You can change this behavior by setting the box-sizing property. The box-sizing property is a great help. It has 2 values:

- border-box
- content-box

content-box is the default, the one we had for ages before box-sizing became a thing.

border-box is the new and great thing we are looking for.
If you set that on an element:
`.my-div {
 box-sizing: border-box;
}`
width and height calculation include the padding and the border. Only the margin is left out, which is reasonable since in our mind we also typically see that as a separate thing: margin is outside of the box.
This property is a small change but has a big impact. CSS Tricks even declared an [international box-sizing awareness day](https://css-tricks.com/international-box-sizing-awareness-day/), just saying, and it's recommended to apply it to every element on the page, out of the box, with this:

`*, *:before, *:after {`

 `box-sizing: border-box;`
 
`}`

## CSS LAYOUT

CSS page layout techniques allow us to take elements contained in a web page and control where they are positioned relative to their default position in normal layout flow, the other elements around them, their parent container, or the main viewport/window. The page layout techniques we'll be covering in more detail in this module are:

Normal flow

The display property

Flexbox

Grid

Floats

Positioning

Table layout

Each technique has its uses, advantages, and disadvantages, and no technique is designed to be used in isolation. By understanding what each method is designed for you will be in a good place to understand which is the best layout tool for each task.

### Normal flow

Normal flow is how the browser lays out HTML pages by default when you do nothing to control page layout.
Here the HTML is displayed in the exact order in which it appears in the source code, with elements stacked up on top of one another. The elements that appear one below the other are described as block elements, in contrast to inline elements, which appear one beside the other, like the individual words in a paragraph.

### The display property

The display property of an object determines how it is rendered by the browser. Those values include:

- block
- inline
- none
- contents
- flow
- flow-root
- table (and all the table-* ones)
- flex
- grid
- list-item
- inline-block
- inline-table
- inline-flex
- inline-grid
- inline-list-item
- plus others you will not likely use, like ruby.
- Choosing any of those will considerably alter the behavior of the browser with the element and its children.
- In this section we’ll analyze the most important ones not covered elsewhere:
- block
- inline
- inline-block
- none

#### Inline

Inline is the default display value for every element in CSS. All the HTML tags are displayed inline out of the box except some elements like div, p and section, which are set as block by the user agent (the browser).

Inline elements don’t have any margin or padding applied.

Same for height and width. You can add them, but the appearance in the page won’t change — they are calculated and applied automatically by the browser.

#### Inline-block

Similar to inline, but with inline-block width and height applied as you specify.

#### Block

As mentioned, normally elements are displayed inline, with the exception of some elements, including

- div
- p
- section
- ul

which are set as block by the browser. 

With display: block, elements are stacked one after each other, vertically, and every element takes up 100% of the page.

The values assigned to the width and height properties are respected, if you set them, along with margin and padding.

#### None

Using display: none makes an element disappear. It's still there in the HTML, but just not visible in the browser.

### Flexbox

Flexbox is the short name for the Flexible Box Layout Module, designed to make it easy for us to lay things out in one dimension — either as a row or as a column. To use flexbox, you apply `display: flex` to the parent element of the elements you want to lay out; all its direct children then become flex items.

![img](https://lh3.googleusercontent.com/IZ2iU4U3EM1xV9V7vix42LrYtjjUwn3P4gh0A9cnLYyJjS_SujzzeOOGWSsFH_sePFvttxHpYpZUnMAZX5j3UmuT5qIL967NDxhmULH8AXhC5igTZVplvKVjQ7SXTmKDJHV1IoVQ)

#### Properties for the Parent (flex container)

**flex-direction:** This establishes the main-axis, thus defining the direction flex items are placed in the flex container.

**flex-wrap:** By default, flex items will all try to fit onto one line. You can change that and allow the items to wrap as needed with this property.

**justify-content:** This defines the alignment along the main axis. It helps distribute extra free space leftover when either all the flex items on a line are inflexible, or are flexible but have reached their maximum size. It also exerts some control over the alignment of items when they overflow the line.

**align-items:** This defines the default behavior for how flex items are laid out along the cross axis on the current line. 

**align-content:** This aligns a flex container's lines within when there is extra space in the cross-axis, similar to how justify-content aligns individual items within the main-axis.
*Note*: *This property only takes effect on multi-line flexible containers, where flex-flow is set to either wrap or wrap-reverse). A single-line flexible container (i.e. where flex-flow is set to its default value, no-wrap) will not reflect align-content.*

#### Properties for the Children (flex items)

**order:** By default, flex items are laid out in the source order. However, the order property controls the order in which they appear in the flex container.

**flex-grow:** This defines the ability for a flex item to grow if necessary. It accepts a unitless value that serves as a proportion. It dictates what amount of the available space inside the flex container the item should take up.

**flex-shrink:** This defines the ability for a flex item to shrink if necessary.

**flex-basis:** This defines the default size of an element before the remaining space is distributed. 

**align-self:** This allows the default alignment (or the one specified by align-items) to be overridden for individual flex items.

### Grid Layout

While flexbox is designed for one-dimensional layout, Grid Layout is designed for two dimensions — lining things up in rows and columns.
Once again, you can switch on Grid Layout with a specific value of display — `display: grid`. 

#### Properties for the Parent (Grid Container)

**grid-template-columns, grid-template-rows:** Defines the columns and rows of the grid with a space-separated list of values. 

**grid-template-areas:** Defines a grid template by referencing the names of the grid areas which are specified with the `grid-area` property. Repeating the name of a grid area causes the content to span those cells. A period signifies an empty cell. The syntax itself provides a visualization of the structure of the grid.

**column-gap, row-gap, grid-column-gap, grid-row-gap:** Specifies the size of the grid lines. You can think of it like setting the width of the gutters between the columns/rows.

**justify-items:** Aligns grid items along the inline (row) axis (as opposed to align-items which aligns along the block (column) axis). This value applies to all grid items inside the container.

**align-items:** Aligns grid items along the block (column) axis (as opposed to justify-items which aligns along the inline (row) axis). This value applies to all grid items inside the container.

**justify-content:** Sometimes the total size of your grid might be less than the size of its grid container. This could happen if all of your grid items are sized with non-flexible units like px. In this case you can set the alignment of the grid within the grid container. This property aligns the grid along the inline (row) axis (as opposed to align-content which aligns the grid along the block (column) axis).

**grid-auto-columns, grid-auto-rows:** Specifies the size of any auto-generated grid tracks. Implicit tracks get created when there are more grid items than cells in the grid or when a grid item is placed outside of the explicit grid.

#### Properties for the Children (Grid Items)

**grid-column-start, grid-column-end, grid-row-start, grid-row-end:** Determines a grid item's location within the grid by referring to specific grid lines. grid-column-start/grid-row-start is the line where the item begins, and grid-column-end/grid-row-end is the line where the item ends.

**grid-area:** Gives an item a name so that it can be referenced by a template created with the grid-template-areas property. 

**justify-self:** Aligns a grid item inside a cell along the inline (row) axis (as opposed to align-self which aligns along the block (column) axis). This value applies to a grid item inside a single cell.

**align-self:** Aligns a grid item inside a cell along the block (column) axis (as opposed to justify-self which aligns along the inline (row) axis). This value applies to the content inside a single grid item.

### **Floats**

Floating an element changes the behavior of that element and the block level elements that follow it in normal flow. The element is moved to the left or right and removed from normal flow, and the surrounding content floats around the floated item.

The float property has four possible values:

- left — Floats the element to the left.
- right — Floats the element to the right.
- none — Specifies no floating at all. This is the default value.
- inherit — Specifies that the value of the float property should be inherited from the element's parent element.

#### Clear

When we use the float property, and we want the next element below (not on right or left), we will have to use the clear property.

The clear property specifies what should happen with the element that is next to a floating element.

The clear property can have one of the following values:

- none - The element is not pushed below left or right floated elements. This is default
- left - The element is pushed below left floated elements
- right - The element is pushed below right floated elements
- both - The element is pushed below both left and right floated elements
- inherit - The element inherits the clear value from its parent

When clearing floats, you should match the clear to the float: If an element is floated to the left, then you should clear to the left. Your floated element will continue to float, but the cleared element will appear below it on the web page.

### Positioning techniques

Positioning allows you to move an element from where it would be placed when in normal flow to another location. Positioning isn’t a method for creating your main page layouts, it is more about managing and fine-tuning the position of specific items on the page.

Positioning is what makes us determine where elements appear on the screen, and how they appear. You can move elements around, and position them exactly where you want. In this section we’ll also see how things change on a page based on how elements with different position interact with each other.

We have one main CSS property: position. It can have those 5 values:

- static
- relative
- absolute
- fixed
- sticky

#### Static positioning

This is the default value for an element. Static positioned elements are displayed in the normal page flow.

#### Relative positioning

An element with position: relative; is positioned relative to its normal position. Setting the top, right, bottom, and left properties of a relatively-positioned element will cause it to be adjusted away from its normal position. Other content will not be adjusted to fit into any gap left by the element.

#### Absolute positioning

An element with position: absolute; is positioned relative to the nearest positioned ancestor (instead of positioned relative to the viewport, like fixed). However; if an absolute positioned element has no positioned ancestors, it uses the document body, and moves along with page scrolling.

**Note:** A "positioned" element is one whose position is anything except static.

#### Fixed positioning

An element with position: fixed; is positioned relative to the viewport, which means it always stays in the same place even if the page is scrolled. The top, right, bottom, and left properties are used to position the element.

A fixed element does not leave a gap in the page where it would normally have been located.

#### Sticky positioning

An element with position: sticky; is positioned based on the user's scroll position.

A sticky element toggles between relative and fixed, depending on the scroll position. It is positioned relative until a given offset position is met in the viewport - then it "sticks" in place (like position: fixed).

### Table layout

HTML tables are fine for displaying tabular data, but many years ago — before even basic CSS was supported reliably across browsers — web developers used to also use tables for entire web page layouts — putting their headers, footers, different columns, etc. in various table rows and columns. This worked at the time, but it has many problems — table layouts are inflexible, very heavy on markup, difficult to debug, and semantically wrong (e.g., screen reader users have problems navigating table layouts).

## UNITS

One of the things you’ll use every day in CSS are units. They are used to set lengths, paddings, margins, align elements and so on.
Things like px, em, rem, or percentages. 

#### Pixels

The most widely used measurement unit. A pixel does not actually correlate to a physical pixel on your screen, as that varies, a lot, by device (think high-DPI devices vs non-retina devices).There is a convention that makes this unit work consistently across devices.

#### Percentages

Another very useful measure, percentages let you specify values in percentages of that parent element’s corresponding property.Example:

`.parent {
 width: 400px;
}`

`.child {
 width: 50%; /* = 200px */
}`

#### Real-world measurement units

We have those measurement units which are translated from the outside world. Mostly useless on screen, they can be useful for print stylesheets. They are:

- cm a centimeter (maps to 37.8 pixels)
- mm a millimeter (0.1cm)
- q a quarter of a millimeter
- in an inch (maps to 96 pixels)
- pt a point (1 inch = 72 points)
- pc a pica (1 pica = 12 points)

#### Relative units

- em is the value assigned to that element's font-size, therefore its exact value changes between elements. It does not change depending on the font used, just on the font size. In typography this measures the width of the m letter.
- rem is similar to em, but instead of varying on the current element font size, it uses the root element (html) font size. You set that font size once, and rem will be a consistent measure across all the page.
- ex is like em, but inserted of measuring the width of m, it measures the height of the x letter. It can change depending on the font used, and on the font size.
- ch is like ex but instead of measuring the height of x it measures the width of 0 (zero).

#### Viewport units

- vw the viewport width unit represents a percentage of the viewport width. 50vw means 50% of the viewport width.
- vh the viewport height unit represents a percentage of the viewport height. 50vh means 50% of the viewport height.
- vmin the viewport minimum unit represents the minimum between the height or width in terms of percentage. 30vmin is the 30% of the current width or height, depending which one is smaller.
- vmax the viewport maximum unit represents the maximum between the height or width in terms of percentage. 30vmax is the 30% of the current width or height, depending which one is bigger.

#### Fraction units

- fr are fraction units, and they are used in CSS Grid to divide space into fractions.

## MEDIA QUERIES

#### Media types

Used in media queries and @import declarations, media types allow us to determine on which media a CSS file, or a piece of CSS, is loaded. We have the following media types:

- **all** means all the media
- **print** used when printing
- **screen** used when the page is presented on a screen
- **speech** used for screen readersscreen is the default.

In the past we had more of them, but most are deprecated as they proved to be ineffective ways of determining device needs.

We can use them in @import statements like this: 
`@import url(myfile.css) screen`;
`@import url(myfile-print.css) print`;

We can load a CSS file on multiple media types separating each with a comma: `@import url(myfile.css) screen, print`;

The same works for the link tag in HTML:
`<link rel="stylesheet" type="text/css" href="myfile.css" media="screen" />`
`<link rel="stylesheet" type="text/css" href="another.css" media="screen, print" />`

We’re not limited to just using media types in the media attribute and in the @import declaration. 

#### Media feature descriptors

First, let’s introduce media feature descriptors. There are additional keywords that we can add to the media attribute of link or the @import declaration, to express more conditionals over the loading of the CSS.
Here’s the list of them:

- width
- height
- device-width
- device-height
- aspect-ratio
- device-aspect-ratio
- color
- color-index
- monochrome
- resolution
- orientation
- scan
- grid

Each of them has a corresponding min- and max-, for example: `min-width`, `max-width`, `min-device-width`, `max-device-width` and so on.
For example:
`@**import** url(myfile.css) screen **and** (max-width: 800px)`;

Notice that we wrap each block using media feature descriptors in parentheses. Some accept a fixed value. orientation, used to detect the device orientation, accepts portrait or landscape.

Example:
`<link rel="stylesheet" type="text/css" href="myfile.css" media="screen and (orientation: portrait)" />`

#### Logic operators

We can combine rules using and:`<link rel="stylesheet" type="text/css" href="myfile.css" media="screen and (max-width: 800px)" />`
We can perform an “or” type of logic operation using commas, which combines multiple media queries: `@import url(myfile.css) screen, print`;

We can use not to negate a media query:
`@**import** **url**(myfile.css) **not** screen`;

#### Media queries

All those above rules we saw applied to @import or the link HTML tag can be applied inside the CSS, too.
You need to wrap them in a `@media () {} structure`.

Example: 

`@media screen and (max-width: 800px) {`

 `/* enter some CSS */`
 
`}` and this is the foundation for responsive design.

Media queries can be quite complex. This example applies the CSS only if it’s a screen device, the width is between 600 and 800 pixels, and the orientation is landscape:

`@media screen **and** (max-width: 800px) **and** (min-width: 600px) **and** (orientation: landscape) {`

 `/* enter some CSS */`
 
`}`

#### Feature queries

Feature queries are a recent and relatively unknown ability of CSS, but a well supported one.

We can use it to check if a feature is supported by the browser using the **@supports** keyword.I think this is especially useful, at the time of writing, for checking if a browser supports CSS grid, for example, which can be done using:

`@**supports** (display: grid) {`

` /* apply this CSS */`

`}`

We check if the browser supports the grid value for the display property. We can use @supports for any CSS property, to check any value.

We can also use the logical operators and, or and not to build complex feature queries:

`@supports (display: grid) **and** (display: flex) {`

 `/* apply this CSS */`
 
 `}`


## Bibliography

https://www.w3schools.com/css/default.asp

https://www.freecodecamp.org/news/the-css-handbook-a-handy-guide-to-css-for-developers-b56695917d11/

https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Introduction

Flexbox: https://css-tricks.com/snippets/css/a-guide-to-flexbox/

Grid: https://css-tricks.com/snippets/css/complete-guide-grid/
