# Whitespace

Clever designers/developers can use combinations of color and space to create "images" that clearly mean something. Automated detection of these patterns seems difficult.

For example, in this [codepen](https://codepen.io/vailjoy/full/vggbmO/), the designer has placed a stack of divs with a contrasting `background-color` in a label. The label acts like a trigger for a hidden checkbox. This clearly "looks" like a "hamburger" menu icon (except that it animates) but assistive technology can't see it at all.

Suggested test: Check that all `<label>` elements with type checkbox or radio have `textContent`. If the associated input is hidden (or otherwise `tabIndex="-1"`), ensure that the label can gain focus and has an accessible name.
