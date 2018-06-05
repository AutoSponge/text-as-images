# Emoticons

Emoticons predate emoji[^1]. The combination of ":)" often gets converted by authoring tools into the "😀" emoji. If a screen reader would try to pronounce the emoticon, it should be wrapped with `aria-hidden="true"`. However, this seems inconsistent at best when tested with a screen reader. When possible, it might be best to swap known emoticons with their emoji counterpart or just avoid them all together.

Some ideas for markup tested with VO:

```html
<p>My mother-in-law just totaled my car <abbr title="emote: shocked">:o</abbr></p>
<p>My mother-in-law just totaled my car <span role="img" aria-label="emote: shocked">:o</span></p>
```

In the example above, VO reads "...colon oh, emote shocked" for the first option and "...emote shocked image colon oh" for the second. The `<abbr>` example has the added benefit that sighted mouse users can hover to get the title text displayed.

A personal favorite is the "happy guy", "ᕕ( ᐛ )ᕗ". As far as I know, no screen reader tries to pronounce it. However, VO will read "¯\\\_(ツ)\_/¯" and it's awful. One problem with emoticons is that the use of [extra-language symbols](./extra-language-symbols.md) can lead someone to create complex and [creative variations](http://smiley.cool/en/emoticons.php). See also [Art](./art.md).

Because several of the most common emoticon permutations use standard punctuation, it can be difficult to detect their use without sophisticated matching algorithms.

Suggested test: regexp match against symbols by language declaration (or non-letters). Have human testers treat groups as images. Test using assistive technology to verify their "safety". Develop matching algorithms to find patterns that could be emoticons based on existing lists.

See:

- [DeepMoji](https://github.com/bfelbo/DeepMoji) (limited AI emoticon matcher)
- [Information on ASCII Emoticons](https://github.com/wooorm/emoticon) project mapping emoticons to emoji

Footnotes:

[^1: The First Emoticon May Have Appeared in ... 1648.](https://www.theatlantic.com/technology/archive/2014/04/the-first-emoticon-may-have-appeared-in-1648/360622/)
