# Sequences

Some unicode symbols are changed by the addition of a ZWJ (zero-width joiner), modifier, or variation symbol.

For example:

```js
// This family is actually 4 separate emoji joined with the ZWJ, "\u200d"
[...'👨‍👩‍👧‍👦'];
// => ["👨", "‍", "👩", "‍", "👧", "‍", "👦"] (length 7)
[..."👨‍👩‍👧‍👦"].map(str => `\\u${str.codePointAt(0).toString(16)}`)
// => ["\u1f468", "\u200d", "\u1f469", "\u200d", "\u1f467", "\u200d", "\u1f466"]

//The "Block up arrow" is actually "Up Arrow" + Variation Selector 16
[...'⬆️'];
// => ["⬆", "️"]
[...'⬆️'].map(str => `\\u${str.codePointAt(0).toString(16)}`);
// => ["\u2b06", "\ufe0f"]

//Modifier example
[...'👮🏿']
// => ["👮", "🏿"]
[...'👮🏿'].map(str => `\\u${str.codePointAt(0).toString(16)}`)
// => ["\u1f46e", "\u1f3ff"]
```

The sheer number of possible combinations combined with the ever growing/changing specifications make detecting valid combinations difficult in code. Where combinations are supported, the meaning becomes clearer or changes.

Suggested test: regexp match against symbol sequences in the standard emoji sequences lists. Have human testers confirm meaning matches the symbols rendered. Validate implementations for image fallback for non-supporting browsers.

See:

- [Emoji ZWJ Sequences](https://emojipedia.org/emoji-zwj-sequences/)
- [Variation Selectors](<https://en.wikipedia.org/wiki/Variation_Selectors_(Unicode_block)>)
- [Emoji Modifer Sequences](http://unicode.org/emoji/charts/emoji-sequences.html#modifier_sequences)
