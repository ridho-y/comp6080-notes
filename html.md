---
title: HTML
---

## Stub
* We should always name the HTML file that will contain the homepage of our websites `index.html`. This is because web servers will by default look for an `index.html` page when users land on our websites - and not having one will cause big problems.

```html
<!DOCTYPE html>

<html lang="en">

    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Document</title>
        <link rel="stylesheet" href="styles.css">
    </head>

    <body>
    </body>

</html>
```

## Headings and Paragraphs
* `h1`, `h2`, ..., `h6` goes from biggest to smallest
* All whitespaces in paragraphs are reduced to a single space

## Bold, Italics, Underline, Strikethrough
* Bold: `<b> </b>`
* Italics: `<i> </i>`
* Underline: `<u> </u>`
* Strikethrough `<s> </s>`

## Comments
* `<!-- Comment -->`

## Lists
* Unordered list (bullet points): `<ul> <li></li> <li></li> <\ul>`
* Ordered list (has numbering): `<ol> <li></li> <li></li> <\ol>`

## Anchor Tags / Links
* `<a href="https://www.theodinproject.com/about">click me</a>`
* `<a href=./pages/about.html>click me</a>`

## Images
* `<img src="https://www.theodinproject.com/mstile-310x310.png">`
* `<img src="https://www.theodinproject.com/mstile-310x310.png" alt="Odin Project Logo">`
* `<img src="./images/dog.jpg">`
* `<img src="./images/dog.jpg" alt="Dog Picture"> width= "300"`

## Forms
* `<input type="text" placeholder="First name"/>` 
    * <input type="text" placeholder="First name"/>
* `<input type="radio" id="yes" name="answer" value="yes" checked />` 
    * <input type="radio" id="yes" name="answer" value="yes" checked />
* `<input type="checkbox" id="no" name="answer" value="no" checked />`
    * <input type="checkbox" id="no" name="answer" value="no" checked />
* `<textarea> ... </textarea>`
* `<select> ... </select>`
* `<label> ... </label>`
* `<button> ... </button>`



