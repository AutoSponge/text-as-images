# Look-alike replacement symbols

![Replace a semicolon (;) with a greek question mark (\u037e) in your friend's C# code and watch them pull their hair out over the syntax error](https://pics.me.me/peter-ritchie-follow-peterritchie-mt-replace-a-semicolon-with-a-21793149.png)

To a sited user not using a screen reader, this "prank" would cause frustration. The technique is also refered to as a [homoglyph attack](https://blog.malwarebytes.com/101/2017/10/out-of-character-homograph-attacks-explained/) in cyber security because it can trick users into phishing attacks using look-alike dns names.

As the [powermapper tests](https://www.powermapper.com/tests/screen-readers/content/look-alike-unicode-chars/) show, assistive technology makes no assumptions about look-alikes. Instead, look-alike replacements cause serious readability problems for screen reader users.

Often, in user-generated content, look-alike characters are chosen for a different reason--to stand out. Especially on social media sites where users lack knowledge of HTML or control of font choice, combinations like the following seem common:

- 𝕋𝕖𝕩𝕥
- ꓕǝxʇ
- ᴛᴇxᴛ
- Ⓣⓔⓧⓣ
- 🅣🅔🅧🅣
- 🆃🅴🆇🆃
- 🅃🄴🅇🅃
- 𝒯ℯ𝓍𝓉

The title of [this page](https://pcrix.tumblr.com/) is painful in a screen reader. Sighted users may realize immediately the title spells "PARIS", but to a screen reader user it sounds like "Double-struck capital pee mathematical double-struck capital ay the real set of numbers mathematical double-struck capital one mathematical double-struck capital ess."

"Leetspeak" is another example of look-alike replacement using only numbers to replace letters with similar symbol shape. In the example below, "S", "O", and "I" are replaced with "5", "0", and "1" respectively. Thankfully, for the screen reader user, this example has title text.

```html
<abbr title="Austin Rocks">Au5t1N r0xx0rz</abbr>
```

Suggested test: regexp match against symbols by language declaration and include spelling checks against a language dictionary. If users are allowed to use look-alikes to generate content, the CMS should apply a text alternative.

See:

- [Unicode decomposition](https://www.compart.com/en/unicode/decomposition/%3Cfont%3E)
- [es6-unicode-regex](https://mathiasbynens.be/notes/es6-unicode-regex)
- [Unicode Locale Data Summary](https://www.unicode.org/cldr/charts/latest/summary/root.html)
- [babel-plugin-utf-8-regex](https://github.com/danielberndt/babel-plugin-utf-8-regex/blob/master/src/transformer.js)
- [tell.wtf](http://tell.wtf/)
