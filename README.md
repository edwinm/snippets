# snippets
Miscellaneous code snippets for web developers because you can't memorize everything.

## Webpage

Basic HTML to start a website

```html
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <meta name="description" content="Description">
    <link rel="stylesheet" href="/weblog/style.css">
    <script async src='script.js'></script>
</head>
<body>


</body>
</html>

```

## HTML section elements

Make your HTML more semantic by using the right elements.
       
element | description
--- | ---
main | Main content of the page, without header and footer etcetera
article | Part of the page that could stand alone
section | Group related elements together
header | Title, subtitle, author, publication date
footer | Copyright, privacy statement, contact data
nav | Page and site navigation with links
aside | Content that's supplementary to the main content


## Box sizing

Box sizing border box is easier to work with.

```css
html {
  box-sizing: border-box;
}

*,
*::before,
*::after {
  box-sizing: inherit;
}
```

## Hyphenation

Turn on hyphenation for the right elements only.

```css
body {
  -webkit-hyphens: auto;
  hyphens: auto;
}

code, var, kbd, samp, tt, dir,
abbr, acronym, blockquote, q {
  -webkit-hyphens: none;
  hyphens: none;
}
```

## CSS animation

Simple CSS animation using transform and transition.

```css
.block {
  transform: translateX(0);
  transition: all 250ms ease;
}

.block.moved {
  transform: translateX(200px);
}

```

## Custom font

Define a custom font. All modern browsers support WOFF2.

```css
@font-face {
  font-family: MavenPro;
  src: url('fonts/mavenpro/maven_pro_bold-webfont.woff2') format('woff2');
  font-weight: bold;
  font-style: normal;
  font-display: swap;
}
```

## Line clamp

Like `text-overflow: ellipsis`, but for multiple lines.

```css
.box {
  display: -webkit-box;
  -webkit-box-orient: vertical;
  overflow: hidden;
  -webkit-line-clamp: 3;
  line-clamp: 3;
}
```

## Prevent click delays

Don't wait for possible double click.

```css
.box {
  touch-action: manipulation;
}
```

## Click through top element

Make a top level element behave it's not there.

```css
.box {
  pointer-events: none;
}
```

## Remove button styles

Works in all modern browsers.

```css
.some-button {
  padding: 0;
  border: none;
  background: transparent;
}
```

## Only show focus when applicable

Don't show focus outlines for mouse users. Note that `<inpu>` and `<textarea>` will always apply the `focus-visible` style.

```css
button {
  outline: none;
}

button:focus-visible {
   outline: 1px solid steelblue;
}
```

## Provide "alt" to background image

Note: make sure to keep the element empty.

```html
<div class="background-image" role="img" aria-label="Alt text"></div>
```

## Remove semantics

Remove the semantics from an element

```html
<h2 role=presentation>Large text, but not a heading</h2>
```

## Toggle buttons

Make it clear when buttons are toggled on or off.

```html
<ol role="tablist">
  <li><button role="tab" aria-selected="false">One</button></li>
  <li><button role="tab" aria-selected="true">Two</button></li>
</ol>
```

See also [WAI-ARIA Authoring Practices](https://www.w3.org/TR/wai-aria-practices/)

## Copy paste characters

Some symbols are hard to type and sometimes you want to know the HTML entity code.

name | entity code | character
--- | --- | ---
Degree sign| &deg; | °
Horizontal ellipsis | &hellip; | …
Bullet | &bullet; | •
Multiplication sign | &times; | ×
Euro sign | &euro; | €
Single left quotation mark | &lsquo; | ‘
Single right quotation mark | &rsquo; | ’
Single low-9 quotation mark | &lsquor; | ‚
Double left quotation mark  | &ldquo; | “
Double right quotation mark | &rdquo; | ”
Double low-9 quotation mark | &ldquor; | „

See also [Character Entity Reference Chart](https://dev.w3.org/html5/html-author/charref)
