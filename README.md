# Frontend snippets
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
    <link rel="stylesheet" href="style.css">
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

You can add an `aria-label` attribute to describe the section.

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

## Social media sharing

Show an image and description when sharing on social media (Facebook, Twitter, LinkedIn, etcetera).

```html
  <meta name="description"
        content="Description of max 200 characters">
  <meta property="og:image" content="https://url-to-image">
  <meta property="og:image:width" content="476">
  <meta property="og:image:height" content="249">
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

For good performance, only animate `transform` and `opacity`.
If performance is still not good, take a look at
the [`will-change`](https://developer.mozilla.org/en-US/docs/Web/CSS/will-change) property.

## Prefers reduced motion / prefers contrast

Improve the accessibility of your website by reducing animations when requested:

```css
@media (prefers-reduced-motion) {  
  * {
    transition-property: none;
  }
}
```

Or increase contrast:

```css
html {
    color: #ccc;
    background-color: white;
}
@media (prefers-contrast: more) {
    html {
        color: black;
    }
}
```

Note: make sure contrast is always good, even without this media query.

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

## Font weights

Which font weight number belongs to which font weight name.

css | name
--- | ---
100 | Thin
300 | Light
350 | Book
400 (normal)| Normal/Regular
500 | Medium
600 | Semi Bold/Demi Bold
700 (bold)| Bold
800 | Extra Bold/Ultra Bold
900 | Black/Heavy

## Responsive design

Every webpage should look good on desktop, tablet and mobile.

```css
/* Mobile */
.box {
  padding: 10px;
}
/* Tablet */
@media screen and (min-width: 768px) {
  .box {
    padding: 40px;
  }
}
/* Desktop */
@media screen and (min-width: 1024px) {
    .box {
      padding: 80px;
    }
}
```

## Dark mode

Switch your color scheme to match the light or dark mode of the user.

```css
html {
    color: black;
    background-color: white;
}
@media (prefers-color-scheme: dark) {
  html {
      color: white;
      background-color: black;
  }
}
```

## CSS stylable icons

Change color, background, border, and size of an icon with CSS. Use a white svg.

```html
  <svg
    viewBox="0 0 100 100"
    aria-label="my icon label"
  >
    <defs>
      <mask id="mask-id">
        <image xlink:href="/path/to/icon.svg" width="100" height="100" />
      </mask>
    </defs>
    <rect
      width="100"
      height="100"
      style="fill: currentColor"
      mask="url(#mask-id)"
    />
  </svg>
```
## Truncate with ellipsis

Instead of wrapping a text, show ...

```css
.text {
    width: 200px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
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

Make a top level element behave like it's not there.

```css
.box {
  pointer-events: none;
}
```

## Remove button styles

Also works with other (ui) elements.

```css
button.my-style {
  padding: 0;
  border: none;
  background-color: transparent;
  /* my styles… */
}
```

You can also reset all styles. Note that this also removes your own inherited styles.

```css
button.my-style {
  all: initial;
  /* my styles… */
}
```

Use flexbox to show text at the top of the button, to make it exchangeable with a `<div>`.

```css
button.my-style {
  /* other reset styles… */
  display: inline-flex;
  align-items: flex-start;
  /* my styles… */
}
```

## Only show focus when applicable

Don't show focus outlines for mouse users. Note that `<input>` and `<textarea>` will always apply the `focus-visible` style.
Use `transparent` as a standard color, as this will become visible in high contrast mode.

```css
* {
  outline-color: transparent;
}

:focus-visible {
  outline: 1px solid #00A1F1;
}
```

## Provide "alt" to background image

Note: don't include text in this element.

```html
<div class="background-image" role="img" aria-label="Alt text"></div>
```

## Remove semantics

Remove the semantics from an element

```html
<h2 role="presentation">Large text, but not a heading</h2>
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

## Scrollbar styling

You can style the scrollbar, but this is very browser and operating system dependent,
so test where necessary.
Apply both classes (`scrollbar-style1` and `styled-scrollbar`) to your container.

```
/* Custom style with configurable parameters */
.scrollbar-style1 {
  overflow: auto; /* enable automatic scrollbars */
  scrollbar-width: thin; /* none, thin or auto (Firefox) */
  --scrollbar-size: 8px; /* 8px when using thin (Webkit) */
  --scrollbar-color: lightblue;
  --scrollbar-thumb-color: blue;
  --scrollbar-thumb-rect: 1; /* add this line for a rectangular thumb (Webkit) */
}

/* You can leave the code below as is */
.styled-scrollbar {
  scrollbar-color: var(--scrollbar-thumb-color) var(--scrollbar-color, transparent);
}

/* WebKit and Chromiums */
.styled-scrollbar::-webkit-scrollbar {
  width: var(--scrollbar-size);
  height: var(--scrollbar-size);
  background-color: var(--scrollbar-color);
}

.styled-scrollbar::-webkit-scrollbar-thumb {
  background: var(--scrollbar-thumb-color);
  border-radius: calc(99px - var(--scrollbar-thumb-rect, 0) * 99px);
}
```

## Copy paste characters

Some symbols are hard to type and sometimes you want to know the HTML entity code.

name | entity code | character
--- | --- | ---
Degree sign| \&deg; | °
Horizontal ellipsis | \&hellip; | …
Bullet | \&bullet; | •
Multiplication sign | \&times; | ×
Euro sign | \&euro; | €
Single left quotation mark | \&lsquo; | ‘
Single right quotation mark | \&rsquo; | ’
Single low-9 quotation mark | \&lsquor; | ‚
Double left quotation mark  | \&ldquo; | “
Double right quotation mark | \&rdquo; | ”
Double low-9 quotation mark | \&ldquor; | „

See also [Character Entity Reference Chart](https://dev.w3.org/html5/html-author/charref)

## Lorem Ipsum

Copy and paste placeholder text.

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Pellentesque varius sem sed nibh pharetra, id ultricies justo sodales. Integer convallis magna lobortis, pulvinar massa et, egestas risus. Nunc ultrices eget nibh convallis auctor. Sed at luctus felis, nec fringilla ante. Aenean facilisis urna eget pellentesque posuere. Maecenas faucibus sem sit amet diam euismod, mollis bibendum quam ornare. Quisque finibus arcu quis molestie pulvinar. Duis sed aliquam nibh, ut pharetra felis. Aenean vel fermentum risus, ac tincidunt enim. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Quisque elementum sit amet libero sed accumsan. Duis nec nunc nec dolor posuere pulvinar. Quisque suscipit congue mi, sed imperdiet libero laoreet non. In sed sodales neque, in bibendum lectus.

Ut nec posuere ipsum. Sed sagittis malesuada dui a blandit. Mauris consectetur consectetur laoreet. Sed erat quam, semper non euismod ut, consequat vitae neque. Sed sodales lorem quis erat iaculis, tristique varius diam tincidunt. Sed venenatis ipsum nec accumsan bibendum. Nulla ac felis sit amet ipsum feugiat viverra non eget erat. Maecenas enim nulla, vehicula eu purus id, lacinia tincidunt leo. Interdum et malesuada fames ac ante ipsum primis in faucibus. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Nulla facilisi. Aliquam suscipit interdum massa. Integer sit amet tincidunt nulla. Proin et ante felis. Pellentesque mauris orci, rutrum sed massa vel, lobortis consequat justo.
