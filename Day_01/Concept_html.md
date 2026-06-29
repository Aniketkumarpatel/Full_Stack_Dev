# 🏷️ HTML Tags — Deep Concept Notes
> Fast revision guide | VS Code friendly | Deep concepts included

---

## 📁 TABLE OF CONTENTS

1. [Document Structure Tags](#1-document-structure-tags)
2. [Head Tags](#2-head-tags)
3. [Text Content Tags](#3-text-content-tags)
4. [Semantic Layout Tags](#4-semantic-layout-tags)
5. [List Tags](#5-list-tags)
6. [Table Tags](#6-table-tags)
7. [Form Tags](#7-form-tags)
8. [Media Tags](#8-media-tags)
9. [Link & Script Tags](#9-link--script-tags)
10. [Inline vs Block Elements](#10-inline-vs-block-elements)
11. [Deep Concepts](#11-deep-concepts)
12. [Global Attributes Cheatsheet](#12-global-attributes-cheatsheet)

---

## 1. Document Structure Tags

```html
<!DOCTYPE html>          <!-- Tells browser: this is HTML5 (not a tag, a declaration) -->
<html lang="en">         <!-- Root element. lang improves SEO + accessibility -->
  <head> ... </head>     <!-- Metadata container (not rendered) -->
  <body> ... </body>     <!-- All visible content lives here -->
</html>
```

> **Deep:** `<!DOCTYPE html>` prevents browsers from entering **Quirks Mode** (legacy rendering).  
> Without it, browsers mimic old IE behavior — layout breaks!

---

## 2. Head Tags

```html
<head>
  <meta charset="UTF-8">                          <!-- Character encoding -->
  <meta name="viewport" content="width=device-width, initial-scale=1.0">  <!-- Responsive -->
  <meta name="description" content="Page summary"> <!-- SEO snippet -->
  <meta name="author" content="Your Name">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">

  <title>Page Title</title>                        <!-- Browser tab + SEO title -->

  <link rel="stylesheet" href="style.css">         <!-- External CSS -->
  <link rel="icon" href="favicon.ico" type="image/x-icon"> <!-- Favicon -->
  <link rel="canonical" href="https://example.com"> <!-- SEO: avoid duplicate content -->

  <script src="app.js" defer></script>             <!-- JS loaded after HTML parse -->
  <style> /* Internal CSS */ </style>
</head>
```

> **Deep: `defer` vs `async`**
> | Attribute | Downloads | Executes | Use Case |
> |-----------|-----------|----------|----------|
> | (none)    | Blocks HTML | Immediately | Avoid |
> | `async`   | Parallel | As soon as ready | Analytics |
> | `defer`   | Parallel | After HTML parsed | Most scripts |

---

## 3. Text Content Tags

### Headings
```html
<h1>Main Title</h1>       <!-- ONE per page — SEO critical -->
<h2>Section</h2>          <!-- Subsections -->
<h3>Sub-section</h3>
<h4> <h5> <h6>            <!-- Deeper nesting -->
```
> **Deep:** Search engines use `<h1>` as the page topic. Never skip heading levels (h1 → h3).  
> Screen readers use headings to navigate the page.

---

### Paragraph & Text Formatting
```html
<p>Paragraph text</p>

<strong>Bold (semantic importance)</strong>     <!-- Bold + meaning -->
<b>Bold (visual only)</b>                       <!-- No semantic weight -->
<em>Italic (emphasis)</em>                      <!-- Italic + meaning -->
<i>Italic (visual / alternate voice)</i>        <!-- Style only -->
<u>Underline</u>
<s>Strikethrough</s>
<mark>Highlighted text</mark>
<small>Fine print / legal</small>
<del>Deleted text</del>       <!-- Shows removed content -->
<ins>Inserted text</ins>      <!-- Shows added content -->
<abbr title="HyperText Markup Language">HTML</abbr>  <!-- Tooltip on hover -->
<cite>Book Title</cite>       <!-- Reference to a creative work -->
<q>Inline quote</q>           <!-- Short inline quotation (adds " ") -->
<blockquote cite="url">       <!-- Long multi-line quotation -->
  Quoted text here...
</blockquote>

<sup>Superscript</sup>  <!-- x² -->
<sub>Subscript</sub>    <!-- H₂O -->
```

> **Deep:** `<strong>` vs `<b>` — both look bold but `<strong>` tells assistive tech  
> "this is important". Always prefer semantic tags over visual tags.

---

### Code & Preformatted
```html
<code>inline code snippet</code>    <!-- Inline: one-liner -->
<pre>                                <!-- Preserves whitespace + newlines -->
  <code>
    Multi-line
    code block
  </code>
</pre>
<kbd>Ctrl + C</kbd>      <!-- Keyboard input -->
<samp>Output text</samp> <!-- Program output -->
<var>x = y + z</var>     <!-- Mathematical variable -->
```

---

### Line & Divider
```html
<br>    <!-- Line break (no closing tag needed) — inline -->
<hr>    <!-- Horizontal rule / thematic break — block -->
```

---

## 4. Semantic Layout Tags

> **Why semantic?** Helps SEO, screen readers, and code readability.

```html
<header>     <!-- Site/section header, logo, nav -->
<nav>        <!-- Navigation links ONLY -->
<main>       <!-- ONE per page — primary content -->
<article>    <!-- Self-contained content (blog post, news) -->
<section>    <!-- Thematic group with a heading -->
<aside>      <!-- Sidebar, related info, ads -->
<footer>     <!-- Footer: links, copyright, contact -->
<figure>     <!-- Image + its caption grouped -->
  <figcaption>Caption text</figcaption>
</figure>
<address>    <!-- Contact info for nearest article/body -->
<time datetime="2024-01-01">January 1, 2024</time>  <!-- Machine-readable date -->
<details>    <!-- Collapsible section (no JS needed!) -->
  <summary>Click to expand</summary>
  Hidden content here...
</details>
<dialog>     <!-- Native modal/popup (open attribute shows it) -->
```

> **Deep — `<article>` vs `<section>`**
> - `<article>`: Could be lifted out and republished independently (blog post, tweet)
> - `<section>`: Grouped content that needs context of the surrounding page

---

### Generic Containers (non-semantic)
```html
<div>   <!-- Block-level container — layout/grouping -->
<span>  <!-- Inline container — style a word/phrase -->
```

---

## 5. List Tags

```html
<!-- Unordered List -->
<ul>
  <li>Item</li>
  <li>Item</li>
</ul>

<!-- Ordered List -->
<ol type="1" start="1">   <!-- type: 1, A, a, I, i -->
  <li>First</li>
  <li>Second</li>
</ol>

<!-- Description List (term + definition) -->
<dl>
  <dt>HTML</dt>
  <dd>HyperText Markup Language</dd>
  <dt>CSS</dt>
  <dd>Cascading Style Sheets</dd>
</dl>
```

> **Deep:** Lists can be nested. `<ol>` attributes:  
> `type="A"` → A, B, C | `type="i"` → i, ii, iii | `reversed` → counts down

---

## 6. Table Tags

```html
<table>
  <caption>Table Title</caption>       <!-- Describes the table (accessibility) -->

  <thead>                              <!-- Header rows group -->
    <tr>
      <th scope="col">Name</th>        <!-- scope: col/row for accessibility -->
      <th scope="col">Age</th>
    </tr>
  </thead>

  <tbody>                              <!-- Body rows group -->
    <tr>
      <td>Alice</td>
      <td>25</td>
    </tr>
    <tr>
      <td colspan="2">Merged cell (spans 2 cols)</td>
    </tr>
  </tbody>

  <tfoot>                              <!-- Summary/total row -->
    <tr>
      <td>Total</td>
      <td>25</td>
    </tr>
  </tfoot>
</table>
```

> **Deep:** `colspan` merges columns, `rowspan` merges rows.  
> `scope="col"` on `<th>` tells screen readers which column the header applies to.

---

## 7. Form Tags

```html
<form action="/submit" method="POST" enctype="multipart/form-data">
  <!-- enctype needed for file uploads -->

  <label for="username">Username:</label>
  <input type="text" id="username" name="username"
         placeholder="Enter name"
         required
         minlength="3"
         maxlength="20"
         autocomplete="username">

  <!-- Input Types -->
  <input type="text">
  <input type="email">          <!-- Validates @ format -->
  <input type="password">       <!-- Hides characters -->
  <input type="number" min="1" max="100" step="1">
  <input type="range" min="0" max="10">
  <input type="date">
  <input type="datetime-local">
  <input type="time">
  <input type="checkbox" checked>
  <input type="radio" name="group" value="a">
  <input type="file" accept=".jpg,.png" multiple>
  <input type="color">
  <input type="url">
  <input type="search">
  <input type="tel">
  <input type="hidden" value="csrf-token-here">   <!-- Invisible to user -->
  <input type="submit" value="Send">
  <input type="reset">
  <input type="button" value="Click">

  <!-- Textarea -->
  <textarea name="message" rows="4" cols="50" placeholder="Type here..."></textarea>

  <!-- Dropdown -->
  <select name="city" multiple>              <!-- multiple = multi-select -->
    <optgroup label="North">                 <!-- Groups options -->
      <option value="del" selected>Delhi</option>
      <option value="lko">Lucknow</option>
    </optgroup>
  </select>

  <!-- Datalist (autocomplete suggestions) -->
  <input list="browsers" name="browser">
  <datalist id="browsers">
    <option value="Chrome">
    <option value="Firefox">
  </datalist>

  <!-- Fieldset (group related inputs) -->
  <fieldset>
    <legend>Personal Info</legend>
    <!-- inputs here -->
  </fieldset>

  <!-- Output (shows result of calculation) -->
  <output name="result" for="a b">0</output>

  <!-- Button types -->
  <button type="submit">Submit</button>
  <button type="reset">Reset</button>
  <button type="button">Just a button</button>  <!-- Does NOT submit form -->

</form>
```

> **Deep — `method="GET"` vs `method="POST"`**
> | | GET | POST |
> |---|---|---|
> | Data in | URL (`?name=val`) | Request body |
> | Visible | Yes | No |
> | Cached | Yes | No |
> | Use for | Search, filters | Login, data submit |

> **Deep — `for` attribute on `<label>`:**  
> Must match the `id` of the input. Clicking the label focuses the input.  
> Improves usability + accessibility.

---

## 8. Media Tags

### Image
```html
<img
  src="photo.jpg"
  alt="Descriptive text"     <!-- REQUIRED for accessibility + SEO -->
  width="800"
  height="600"               <!-- Prevents layout shift (CLS) -->
  loading="lazy"             <!-- Defer off-screen images -->
  decoding="async"
  srcset="img-400.jpg 400w, img-800.jpg 800w"   <!-- Responsive images -->
  sizes="(max-width: 600px) 400px, 800px">
```

> **Deep:** Always set `width` + `height` → browser reserves space → no Cumulative Layout Shift (CLS).  
> `loading="lazy"` = browser skips image until user scrolls near it.

---

### Picture (art direction)
```html
<picture>
  <source media="(max-width: 600px)" srcset="small.jpg">
  <source media="(max-width: 1200px)" srcset="medium.jpg">
  <img src="large.jpg" alt="Fallback">     <!-- Always include <img> fallback -->
</picture>
```

---

### Audio
```html
<audio controls autoplay loop muted preload="auto">
  <source src="audio.mp3" type="audio/mpeg">
  <source src="audio.ogg" type="audio/ogg">
  Your browser does not support audio.    <!-- Fallback text -->
</audio>
```

---

### Video
```html
<video
  controls
  autoplay
  muted          <!-- Required for autoplay in most browsers -->
  loop
  poster="thumbnail.jpg"     <!-- Shown before play -->
  width="720" height="480"
  preload="metadata">        <!-- none | metadata | auto -->
  <source src="video.mp4" type="video/mp4">
  <source src="video.webm" type="video/webm">
  <track src="captions.vtt" kind="subtitles" srclang="en" label="English">
</video>
```

---

### Iframe (embed)
```html
<iframe
  src="https://example.com"
  title="Description"               <!-- Accessibility requirement -->
  width="600"
  height="400"
  loading="lazy"
  sandbox="allow-scripts allow-same-origin"    <!-- Security restriction -->
  allow="fullscreen"
  referrerpolicy="no-referrer">
</iframe>
```

> **Deep: `sandbox` attribute** restricts what iframe can do:
> - No `sandbox` → full trust (dangerous)
> - `sandbox` alone → maximum restrictions
> - `allow-scripts` → JS allowed but no same-origin access
> - `allow-same-origin` → treated as same origin

---

## 9. Link & Script Tags

```html
<!-- Anchor / Hyperlink -->
<a href="https://example.com"
   target="_blank"                   <!-- Opens in new tab -->
   rel="noopener noreferrer"         <!-- Security: prevents tab hijacking -->
   download="filename.pdf"           <!-- Forces download instead of navigate -->
   title="Tooltip text">
  Link Text
</a>

<!-- Internal page jump -->
<a href="#section-id">Jump to section</a>
<section id="section-id">Target</section>

<!-- Email / Phone -->
<a href="mailto:user@example.com">Email us</a>
<a href="tel:+919876543210">Call us</a>

<!-- Script -->
<script src="app.js" defer></script>
<script src="analytics.js" async></script>
<script>
  // Inline JS (runs immediately — blocks parsing)
  console.log("Hello");
</script>

<!-- Noscript fallback -->
<noscript>
  <p>Please enable JavaScript.</p>
</noscript>
```

> **Deep: `rel="noopener noreferrer"` with `target="_blank"`**  
> Without it, the new tab gets a reference to the opener via `window.opener`  
> → malicious site can redirect your page! Always use both together.

---

## 10. Inline vs Block Elements

| Type | Behavior | Examples |
|------|----------|---------|
| **Block** | Full width, new line | `<div>` `<p>` `<h1-h6>` `<ul>` `<table>` `<form>` `<section>` |
| **Inline** | Only as wide as content, no new line | `<span>` `<a>` `<img>` `<strong>` `<em>` `<code>` `<input>` |
| **Inline-Block** | Inline flow + block sizing | `<img>` `<button>` (behave like this) |

> **Deep:** You cannot put a block element inside an inline element.  
> ❌ `<span><div>wrong</div></span>`  
> ✅ `<div><span>correct</span></div>`  
> Exception: `<a>` can wrap block elements in HTML5.

---

## 11. Deep Concepts

### 🔹 The DOM (Document Object Model)
```
HTML is parsed → Browser builds a tree → That tree = the DOM
JavaScript manipulates the DOM (not the raw HTML file)
Every tag = a Node in the tree
```

---

### 🔹 Void Elements (Self-closing tags)
These tags have NO closing tag and NO children:
```html
<br>  <hr>  <img>  <input>  <link>  <meta>  <source>  <track>  <wbr>  <area>  <col>
```
> In HTML5: `<br>` is correct. `<br/>` is XML/XHTML style (both work but `<br>` is preferred).

---

### 🔹 HTML Entities
```html
&lt;     →  <
&gt;     →  >
&amp;    →  &
&nbsp;   →  (non-breaking space)
&quot;   →  "
&apos;   →  '
&copy;   →  ©
&reg;    →  ®
&trade;  →  ™
&#9829;  →  ♥  (decimal code)
&#x2665; →  ♥  (hex code)
```

---

### 🔹 Data Attributes (Custom Data)
```html
<div data-user-id="42" data-role="admin">User</div>

<script>
  const el = document.querySelector('div');
  console.log(el.dataset.userId);  // "42"
  console.log(el.dataset.role);    // "admin"
</script>
```
> `data-*` stores custom info in HTML without affecting rendering.  
> Accessed via JS using `element.dataset.keyName` (camelCase auto-conversion).

---

### 🔹 ARIA (Accessibility)
```html
<button aria-label="Close dialog">✕</button>        <!-- Describes element -->
<div role="alert">Error occurred!</div>              <!-- Announces to screen reader -->
<input aria-required="true" aria-invalid="false">
<nav aria-label="Main navigation">...</nav>
<div aria-hidden="true">Decorative only</div>        <!-- Hidden from screen readers -->
<div aria-live="polite">Dynamic content here</div>   <!-- Announces when updated -->
```
> ARIA fills semantic gaps. First rule: use native HTML elements over ARIA.  
> `<button>` > `<div role="button">` always.

---

### 🔹 Meta for SEO & Social
```html
<!-- SEO -->
<meta name="description" content="150-160 char page summary">
<meta name="robots" content="index, follow">

<!-- Open Graph (Facebook, WhatsApp, LinkedIn) -->
<meta property="og:title" content="Page Title">
<meta property="og:description" content="Description">
<meta property="og:image" content="https://example.com/img.jpg">
<meta property="og:url" content="https://example.com">
<meta property="og:type" content="website">

<!-- Twitter Card -->
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="Title">
<meta name="twitter:image" content="https://example.com/img.jpg">
```

---

### 🔹 Template & Web Components
```html
<!-- Template: not rendered until used via JS -->
<template id="card-template">
  <div class="card">
    <h2></h2>
    <p></p>
  </div>
</template>

<script>
  const tmpl = document.getElementById('card-template');
  const clone = tmpl.content.cloneNode(true);
  document.body.appendChild(clone);
</script>

<!-- Slot: used inside Custom Elements (Web Components) -->
<my-card>
  <span slot="title">Hello</span>
</my-card>
```

---

### 🔹 Input Validation Attributes
```html
<input type="text"
  required                  <!-- Cannot be empty -->
  minlength="3"             <!-- Min characters -->
  maxlength="50"            <!-- Max characters -->
  pattern="[A-Za-z]+"      <!-- Regex pattern -->
  min="1"                   <!-- Min value (number/date) -->
  max="100"                 <!-- Max value -->
  step="5"                  <!-- Step increment -->
  autocomplete="off"        <!-- Disable browser autofill -->
  readonly                  <!-- Visible, not editable -->
  disabled                  <!-- Not editable, not submitted -->
  autofocus>                <!-- Auto-focused on page load -->
```

> **Deep — `readonly` vs `disabled`**  
> `readonly`: value IS submitted with form  
> `disabled`: value is NOT submitted with form

---

### 🔹 Character Encoding
```html
<meta charset="UTF-8">
```
> UTF-8 supports ALL languages + emojis (1.1M+ characters).  
> Must be within first 1024 bytes of HTML (first tag in `<head>`).

---

## 12. Global Attributes Cheatsheet

These work on **ANY** HTML element:

```html
id="unique-id"              <!-- Unique identifier on page -->
class="one two three"       <!-- CSS/JS hook (multiple allowed) -->
style="color: red"          <!-- Inline CSS (avoid in production) -->
title="Tooltip text"        <!-- Hover tooltip -->
lang="hi"                   <!-- Language of that element -->
dir="rtl"                   <!-- Text direction: ltr | rtl | auto -->
tabindex="0"                <!-- Keyboard tab order (0=natural, -1=skip, 1+=priority) -->
hidden                      <!-- Hides element (like display:none) -->
contenteditable="true"      <!-- Makes element editable in browser -->
draggable="true"            <!-- Element can be dragged -->
spellcheck="true"           <!-- Browser spell-check -->
translate="no"              <!-- Don't translate (e.g. brand names) -->
data-*="value"              <!-- Custom data attributes -->
aria-*                      <!-- Accessibility attributes -->

<!-- Event attributes -->
onclick="fn()"
onmouseover="fn()"
onkeydown="fn()"
onchange="fn()"
onsubmit="fn()"
onload="fn()"
```

---

## ⚡ Quick Reference — Tag Groups

```
STRUCTURE    : html, head, body, main, header, footer, nav, aside, section, article
HEADING      : h1, h2, h3, h4, h5, h6
TEXT         : p, span, strong, em, b, i, u, s, mark, small, del, ins, abbr, cite, q
BLOCK/QUOTE  : blockquote, pre, code, kbd, samp, var, address
GROUPING     : div, figure, figcaption, details, summary, dialog, template
LIST         : ul, ol, li, dl, dt, dd
TABLE        : table, thead, tbody, tfoot, tr, th, td, caption, col, colgroup
FORM         : form, input, label, button, select, option, optgroup, textarea,
               fieldset, legend, datalist, output, progress, meter
MEDIA        : img, picture, source, audio, video, track, canvas, svg
EMBED        : iframe, object, embed
LINK         : a, link
META         : meta, title, base
SCRIPT       : script, noscript, style
SEMANTIC     : time, data, mark, ruby, rt, rp, bdi, bdo, wbr
```

---

*Last updated: 2024 | HTML5 Standard*