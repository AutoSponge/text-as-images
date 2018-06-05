# Private and unassigned unicode

Some ranges of unicode are assigned for private use or yet to be assigned. This allows vendors and user groups to specify their own meaning for certain code points. For example, [Font Awesome](https://fontawesome.com/how-to-use/web-fonts-with-css) has used this technique to replace css content with glyphs for years.

Testing for the private range is simple:

```js
/[\uf0000-\uffffd]|[\u100000–\u10fffd]/.test(element.textContent);
```

However, testing for unassigned codes may be trickier (and again, ever changing).

While Font Awesome has stuck to the private ranges, an inexperienced developer using a tool like [Icomoon](https://icomoon.io/) could create their own font face with glyphs that use any code point.

Suggested test: regexp test for private and unassigned unicode ranges and have human testers verify the use of glyphs and confirm proper meaning. Text alternatives must be available for these glyphs and it should be clear they are intended as images. Warn against custom font faces when unicode is detected.

See:

- [Private-Use Characters, Noncharacters & Sentinels FAQ](http://www.unicode.org/faq/private_use.html)
