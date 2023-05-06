---
title: CSS
---

## **Apply CSS in HTML**

```html
<!-- index.html -->

<head>
  <link rel="stylesheet" href="mystylefile.css">
</head>
```

```css
/* styles.css */

div {
  color: white;
  background-color: black;
}

p {
  color: red;
}
```

* OR:

```html
<head>
  <style>
    div {
      color: white;
      background-color: black;
    }

    p {
      color: red;
    }
  </style>
</head>
<body>...</body>
```

* OR:

```html
<body>
  <div style="color: white; background-color: black;">...</div>
</body>
```

## **Selectors**

### Universal Selectors
* Use `*`

### Type Selectors
* All elements of a given type will be selected.
* Type can be a `div` or `p`, etc.
* Use `<type>`

### Class Selectors 
* All elements of a given class will be selected.
* Use `.<class_name>`
* HTML elements can have multiple classes by a space separated list: `class="alert-text severe-alert"` so never use spaces in class names, only use hyphens.

### ID Selectors 
* An element of a given ID will be selected.
* Use `#<id>`
* An element can only have one ID.

### Attribute Selector
* All elements with a given attribute pair will be selected.
* Use: `selector[attr=value]`

```html
<input type="radio" name="vote" value="one" />
<input type="radio" name="vote" value="one" />
```

```css
input[type="radio"] {
  margin: 0 10px
}
```

### Grouping Selectors
* Use comma separated list:

```css
.read,
.unread {
  color: white;
  background-color: black;
}
```

### Chaining Selectors
* Selects elements with the given attributes. 
* You cannot chain more than one different types.
* For example:

```html
<div>
  <div class="subsection header">Latest Posts</div>
  <p class="subsection" id="preview">This is where a preview for a post might go.</p>
</div>
```

```css
.subsection.header {
  color: red;
}

.subsection#preview {
  color: blue;
}
```

## **Properties**

### Text
* `color` - change the color of the text font-size - change the size of the text
* `font-family ` - specify the list of fonts that will be used to render the text 
* `font-weight ` - sets the boldness of the text
* `font-style` - sets whether the text renders italic/oblique or normal 
* `text-decoration ` - adds decoratives lines on the text

### Background Image
* `background-image` - sets the image as a background
* `backgorund-repeat` - sets how image should repeat if its smaller than the element
* `background-position` - sets the initial position of the image 
* `background-size` - sets the size of the image

### Colour
* `color`: Text colour
* `background-color`: Background colour
* Can accept HEX, RGB, HSL
* Example:

```css
p {
  /* hex example: */
  color: #1100ff;
  /* rgb example: */
  color: rgb(100, 0, 127);
  /* hsl example: */
  color: hsl(15, 82%, 56%);
}
```

### Font
* `font-family`: Single font, or comma separated list of fonts.
    * Can be font family name e.g. `"Times New Roman"` or generic family name e.g. `sans-serif`.
    * If a list is given, the browser will use the first font available
* `font-size`: e.g. `22px`
* `font-weight`: Boldness of the text, e.g. simply `bold` or a number between 1 and 1000 e.g. `700` which is equivalent to `bold`
* `text-align`: e.g. `center`

### Images
* By default an `<img>` element's height and width will be the same as the file's height and width
* To adjust:

```css
img {
  height: auto;
  width: 500px;
}
```

## **Combinators**

```html
<div class="A">
  <span class="B">one</span>
  <span class="C">two</span>
  <span class="B">three</span>
  <span class="B">four</span>
  <div>
    <span class="B">five</span>
  </div>
</div>
<span class="B">six</span>
```

```css
/* Descendant: all .B elements inside .A */ /* one, three, four, five */
.A .B { color: red; }

/* Child: all .B which are direct childs of .A */ /* one, three, four */ 
.A > .B { color: red; }

/* Adjacent sibling: .B that follows immediately after .C */ /* three */
.C + .B { color: red; }

/* General sibling: all sibling .B that follows after .C */ /* three, four */
.C ~ .B { color: red; }
```

## **Pseudos**

### Pseudo-classes

```css
/* The button which is the first/last element in its container */ 
button:first-child { background-color: blue; } 
button:last-child { background-color: blue; }

/* The button over which the user's pointer is hovering */ 
button:hover { background-color: blue; }

/* The input which received focus */ 
input:focus { color: red; }

/* Disabled input */ 
input:disabled { background-color: #ccc; }

/* Links that a user has already visited */ 
a:visited { color: red; }
```

### Pseudo-elements

```css
/**
* Only the first letter in the text elements
* will have a red color
*/ 
.text::first-letter {
color: red;
}

/**
* After the text elements will shown "*"
* with the given styles
*/ 
.text::after {
content: '*';
color: red;
}
```

## **Cascade of CSS**

### Specificity
* Order of priority when there are conflicting styles:
    1. ID selectors
    2. Class selectors
    3. Type selectors
* Count also plays a factor
* <a href="https://www.specifishity.com"> www.specifishity.com</a>

### Inheritance
* Typography based properties (`color`, `font-size`, `font-family`, etc.) are usually inherited, while most other properties aren’t.
* When an element is directly targeted, inheritance does not apply, e.g class `child` will be blue:

```html
<!-- index.html -->

<div id="parent">
  <div class="child"></div>
</div>
```

```css
/* styles.css */

#parent {
  color: red;
}

.child {
  color: blue;
}
```

### Rule Order
* Tie-breaker, last defined is the winner.

## **Layouts**

* Each element is represented as a rectangular box for rendering
* For example, below the total size of the rectangle would be 80x80px

```css
.box {
width: 50px;
height: 50px; 
padding: 10px; 
margin: 10px;
border: 5px solid blue; 
background-color: #aaa;
}
```

### Block Elements
* `display: block`
* Block elements start a new line and stretch to the full width of the container
* Some properties can only be applied to block elements, e.g. width, height, margin, padding ...

### Inline Elements
* `display: inline`
* Inline elements only have the size of their contents

### Inline Block
* `display: inline-block`
* Inline block behaves like a block but flows as inline

### None Display
* `display: none`
* Has no flow

### Visibility
* `visibility: hidden`
* Change visibility of an element, but keeps the flow

### Float
* `float: left/right`
* Removes an element from the normal flow and puts it to the left/right of the container and allows other inline elements to wrap around

### Overflow
* `overflow: visible/hidden/auto`
* Visible will overflow
* Hidden will cut text
* Auto will introduce scrolling

## **Positions**

### Static Position
* Positions an element based on normal flow
* Is default

### Relative Position
* `position: relative`
* Positions an element based on normal flow
* Offset properties will apply it based on its static position

### Absolute Position
* `position: absolute`
* Removes an element from normal flow
* Offset properties will apply it based on its closest parent element that is not static

### Fixed Position
* `position: fixed`
* Removes an element from normal flow
* Offset properties will apply it based on screen/view-point

## Flexbox
* <a href="https://css-tricks.com/snippets/css/a-guide-to-flexbox/">A complete guide to Flexbox</a>

## Media Queries
* Create CSS rules that are applied to the document only when device reach specific criteria

```css
.article {
  padding: 5px 10px;
}

@media (min-width: 600px) {
  .article {
    padding: 10px 20px;
  }
}
```