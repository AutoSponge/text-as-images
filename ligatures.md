# Ligatures and Stacks

Similar to the issues in [Private range](./private-range.md), developers and designers have great power to create their own font faces and apply them to replace text with glyphs.

Ligatures can be a better alternative for screen readers because the word "map" gets converted into an image of a map. Since the page gets progressively enhanced to replace the text with a glyph, it should even survive an external translation (like from a browser/plugin). The image will be lost, but the meaning will still be there and a screen reader won't get tripped up.

Similar to ligatures, someone could combine multiple glyphs in a "stack", the way [Font Awesome suggests](https://fontawesome.com/v4.7.0/examples/#stacked). The sheer number of permutations means only human testers will be equipped to dissect the meaning of these useage patterns.

Suggested test: regexp match against symbols in the private and unassigned unicde ranges. Have human testers confirm meaning matches the symbols rendered. Validate implementations for alternative text.

See:

- [CSS-Tricks: Ligature Icons](https://css-tricks.com/ligature-icons/)
- [Seriously, Don't Use Icon Fonts](https://cloudfour.com/thinks/seriously-dont-use-icon-fonts/)
- [Death to Icon Fonts](https://speakerdeck.com/ninjanails/death-to-icon-fonts)
