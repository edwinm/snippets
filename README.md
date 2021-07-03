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

| main | Main content of the page, without header and footer etcetera
| article | Part of the page that could stand alone
| section | Group related elements together
| header | Title, subtitle, author, publication date
| footer | Copyright, privacy statement, contact data
| nav | Page and site navigation with links
| aside | Content that's supplementary to the main content


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

```html
<div class="background-image" role="img" aria-label="Alt text"></div>
```

