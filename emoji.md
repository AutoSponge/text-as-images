# Emoji

When standard emoji are used, assistive technology can replace the symbol with its meaning. Since the list of standard emoji annotations have translations, there's no need to provide additional language hints (although cultural context may change meaning) for assistive technology.

However, for better cross-platform support, it might be wise to follow a technique similar to Twitter:

```html
<img class="Emoji Emoji--forText" src="https://abs.twimg.com/emoji/v2/72x72/1f496.png" draggable="false" alt="💖" title="Sparkling heart" aria-label="Emoji: Sparkling heart">
```

Just remember that [aria-label is a xenophobe](http://www.heydonworks.com/article/aria-label-is-a-xenophobe) and will not get translated by something like Google Translate. You'll need to do the translation on the server if you follow this technique, be sure to see the language references lists (example below).

Be aware that the list of emoji is constantly updated. The implementation will vary between browsers and support for a specific symbol or combination may be tricky to determine, at best. The prevailing technique uses some flavor of [this gist](https://gist.github.com/mwunsch/4710561) (specifically the `doesSupportEmoji` function). This means that while testing a page in a supporting browser, techniques like Github's can replace emoji symbols with images for other browsers.

## Translations

Emoji meanings have been translated into many languages. But automatic translators like Google Translate seem to do awful things to them.

Turning emoji into images can increase compatibility with various platforms or older browsers but it can also cause confusion when translated. For example, the ✌️ emoji or "Victory Hand" is marked up in Japanese on a popular social site, mixi.net:

```html
<img src="https://img.mixi.net/img/emoji/41.gif" alt="手（チョキ）" width="16" height="16" class="emoji" border="0">
```

When google translate is applied to the page to translate to English, the markup is changed to:

```html
<img src="https://img.mixi.net/img/emoji/41.gif" alt="Hand (choke)" width="16" height="16" class="emoji" border="0">
```

The Japanese should recognize "チョキ" as snip, cut, or scissors but Google translates it to choke. While there's no direct "choke" emoji, the meaning could have been changed to one of disgust or anger instead of peace and friendliness.

In Twitter's implementation, the emoji as the `alt` value gets changed to 'A' and the title is translated but the `aria-label` is untouched. While the sentiment is correct, it's not translated for the AT user because the `aria-label` is used for the accessible name. Here's the clapping hand emoji loaded from https://twitter.com/?lang=ja then translated to English:

```html
<img class="Emoji Emoji--forText" src="https://abs.twimg.com/emoji/v2/72x72/1f44f-1f3fd.png" draggable="false" alt="A" title="Clapping (flesh color)" aria-label="Emoji: 拍手 (肌色)">
```

and the original:

```html
<img class="Emoji Emoji--forText" src="https://abs.twimg.com/emoji/v2/72x72/1f44f-1f3fd.png" draggable="false" alt="👏🏽" title="拍手 (肌色)" aria-label="Emoji: 拍手 (肌色)">
```

Since it makes no sense to use an emoji as the `aria-label` for an image of the emoji, it may be best to just use the emoji when support can be detected.

For modifiers and joiners, see [Sequences](./sequences.md).

For compositions of emoji (e.g., "the sheriff of..." see [Art](./art.md)).

Suggested test: regexp match against symbols in the standard emoji range. Have human testers confirm meaning matches emoji used. Validate implementations for image fallback for non-supporting browsers. Be careful of translations.

See:

- [unicode chart annotations (Germanic languages example)](https://www.unicode.org/cldr/charts/latest/annotations/germanic.html)
- [emoji-regex](https://github.com/mathiasbynens/emoji-regex)
- [node-emoji](https://www.npmjs.com/package/node-emoji)

Other articles:

- [Listening to Poo, Your Emoji and You](https://blog.iconfactory.com/2018/07/listening-to-poo-your-emoji-and-you)
- [Aria-Label is a Xenophobe](http://www.heydonworks.com/article/aria-label-is-a-xenophobe)

TODO:

- see how https://w3c.github.io/html/dom.html#element-attrdef-global-translate could affect l10n.
