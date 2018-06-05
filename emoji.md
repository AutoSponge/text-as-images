# Emoji

When standard emoji are used, assistive technology can replace the symbol with its meaning based. Since the list of standard emoji annotations have translations, there's no need to provide additional language hints (although cultural context may change meaning) for assistive technology.

Be aware that the list of emoji is constantly updated. The implementation will vary between browsers and support for a specific symbol or combination may be tricky to determine, at best. The prevailing technique uses some flavor of [this gist](https://gist.github.com/mwunsch/4710561) (specifically the `doesSupportEmoji` function). This means that while testing a page in a supporting browser, techniques like Github's can replace emoji symbols with images for other browsers.

For modifiers and joiners, see [Sequences](./sequences.md).

For compositions of emoji (e.g., "the sheriff of..." see [Art](./art.md)).

Suggested test: regexp match against symbols in the standard emoji range. Have human testers confirm meaning matches emoji used. Validate implementations for image fallback for non-supporting browsers.

See:

- [unicode chart annotations (Germanic languages example)](https://www.unicode.org/cldr/charts/latest/annotations/germanic.html)
- [emoji-regex](https://github.com/mathiasbynens/emoji-regex)
