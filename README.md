
# Browser incompatibilities

This repository aims to keep track of various browser incompatibilities that I stumbled across, document them, and file issues for the specifications and/or browser vendors.

- 🚧 **Spec bug**: The specification is ambiguous and does not clearly state what the browser should do
- 🐛 **Browser bug**: The specification is clear on what to do, but some browser(s) do(es) not follow it

## Selection, caret, ranges, contenteditable & line breaks
- 🚧 client rect handling of ranges near automatic line break
- 🚧 range creation & client rect handling with offsets in whitespace before/after first/last text
- 🚧 client rect handling of ranges with multiple collapsed whitespace
- 🚧 what happens when caret in `contenteditable` is moved up/down to a shorter line with automatic break?
- 🐛 Firefox: left/right arrow keys at automatic line break don't do anything once
- 🚧 where does the caret jump to when clicking under/over/between text elements in `contenteditable`?
- 🚧 where does the page scroll to when you start typing in `contenteditable` or `<input>`/`<textarea>` while the caret is focused on on area not currently visible?
- 🚧 whether or not and when `selectionchange` events get fired when deleting letters/words/etc with Backspace/Del in `contenteditable` and `<input>`/`<textarea>`
- 🚧 wrapped spans with underline: does underline expand across the line's last (broken) space?
- 🚧 WebKit weirdness where the automatic-line-break-space gets its own client rect
- 🚧 range client rect handling when span-like element is directly before/after automatic line break
- 🚧 does selection get un-focused (therefore removed) when clicking a button outside of a `contenteditable`?
- 🐛 WebKit: 3 `selectionchange` events (instead of one) get fired after `execCommand()` in `contenteditable`
- 🚧 when caret exactly at edge between two span-like elements in `contenteditable`: what is the caret's container?
- 🚧 client rect behavior when line ends with space & range is at the end
- 🚧 caret navigation with `display: inline flow-root` elements in `contenteditable`

## SVG
- 🚧 `context2d.drawImage()` with SVG without width/height attributes (only `viewBox`)
- 🚧 SVG in `context2d.drawImage()`: does `@media (prefers-color-scheme)` get respected?
- 🐛 `<img>` with SVG src: does `@media (prefers-color-scheme)` get respected?
- 🐛 does CSS `color-scheme` affect `@media (prefers-color-scheme)` queries in SVGs embedded in `<img>`s?

## XML, DOM parsing, HTML/XML serialization
- 🐛 Chromium, WebKit: `<parsererror>` is not root node of parsed invalid XML
- 🐛 Firefox: `xmlns` attribute does not get serialized with `XMLSerializer` if specified after document creation
- 🐛 Chromium: `<![CDATA[ ]]>` sections in HTML-embedded MathML not recognized (& wrongly treated as comments)

## Pointer & touch events
- 🐛 `{pointer/mouse}move` events with touch
- 🚧 does `.preventDefault()` on `{pointer/mouse}down` event prevent CSS `:active` selector from applying?

## CSS & Layout
- 🚧 exact border colors with `border-style: {groove/ridge/inset/outset}`
- 🐛 column width in multicolumn layout with `column-fill: auto` & `inline-size: {fit/max}-content` ([crbug.com/1348295](https://bugs.chromium.org/p/chromium/issues/detail?id=1348295))
- 🚧 default thickness of `text-decoration-line: {underline/overline/line-through}`
- 🚧 exact `text-decoration-style: {dotted/dashed/wavy}` renderings
- 🐛 multiple background layers, some of which contain `background-clip: text`
- 🐛 Chromium, WebKit: `getComputedStyle(element).webkitTextStroke` always returns the empty string
- 🐛 WebKit: `getComputedStyle(element).webkitMask` always returns the empty string
- 🐛 WebKit: `position: relative` on table row elements gets ignored for absolutely positioned elements inside
- 🚧 `<br>` linebreak height styling via `display: block`, `content: ""`, `block-size` and `margin-block-end`?
- 🐛 highlight pseudos handling (see [csswg-drafts#6641](https://github.com/w3c/csswg-drafts/issues/6641#issuecomment-1642386369))

## Files & directories
- 🐛 Chromium: `.webkitEntries` doesn't get populated with `<input type=file webkitdirectory>`

## ECMAScript
- 🚧 `Error.prototype.stack`

## Printing
- 🐛 `display: table-header-group` shown on every page when printing? ([crbug.com/1348526](https://bugs.chromium.org/p/chromium/issues/detail?id=1348526))
- 🚧 event firing behavior and order of `beforeprint`/`afterprint` and the `change` event of `matchMedia("(prefers-color-scheme: light)")` when printing while OS is in dark mode
