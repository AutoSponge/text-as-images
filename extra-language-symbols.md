# Extra-language characters

A webpage that uses unicode characters outside the language's normal range should provide hints for assistive technology whether or not it should be read and, if it's read, how it should be read.

For example, [jonnyfire](https://www.artstation.com/jonnyfire) displays the artist's name in an `<h1>`:

```html
<html class="en" lang="en" ng-app="app">
<--... omitted -->
  <h1 class="artist-name">Jonny 火火</h1>
```

[The 火 character](https://en.wiktionary.org/wiki/%E7%81%AB) could be Chinese, Japanese, or Korean while the page declares English. Without a language indication in Jonny's name, a screen reader might read "Johnny usch unified ideograph usch unified ideograph" (trying to pronounce "CJK UNIFIED IDEOGRAPH" twice). Obviously, with the proper language it would [sound](https://forvo.com/search/%E7%81%AB) different:

"Johnny huǒ huǒ"

```html
<h1 class="artist-name">Jonny <span lang="zh">火火</span></h1>
```

"Johnny çi çi"

```html
<h1 class="artist-name">Jonny <span lang="ja">火火</span></h1>
```

"Johnny hwa hwa"

```html
<h1 class="artist-name">Jonny <span lang="ko">火火</span></h1>
```

From the page's context, we can guess that the artist is from China. But, since the page is in English and the subdomain referenced on the page is `jonnyfire.artstation.com`, maybe this symbol is acting as an image and should be replaced with "fire" for an English user--no different than "Jonny 🔥". So maybe this:

```html
<!-- Remember that `aria-label` text will need translation. -->
<h1 class="artist-name">Jonny <span role="img" aria-label="fire">火火</span></h1>
<-- OR -->
<h1 class="artist-name">Jonny <abbr title="fire">火火</abbr></h1>
```

In another example, [Mr. Jones Watches](https://mrjoneswatches.com/products/ka) wants you to know the watch's name, "Ka" and describes their inspiration as Japanese. The entire page is in English but it was not declared in the `html` tag. What would be a better screen reader experience? To hear the word "Ka" in the default screen reader voice or to hear "火" as read by the Japanese screen reader voice?

```html
<h1 class="product-single__title" itemprop="name" lang="ja"><span aria-hidden="true">Ka</span> 火</h1>
```

The problem here: the Japanese character "Ka" alone in Japanese sounds more like ["He"](https://jisho.org/search/%22fire%22) (the Rōmaji transcription of ひ, 'hi'). When combined, like in the word for ["volcano"](https://jisho.org/word/%E7%81%AB%E5%B1%B1) (火山) it makes the "Ka" sound in "Kazan." If the user called the company to inquire about the "çi" watch, it might confuse customer service. So, maybe this then:

```html
<h1 class="product-single__title" itemprop="name">Ka <span aria-hidden="true">火</span></h1>
```

If the goal is to associate the pronunciation with the character for sited users and not confuse Japanese users, it could use the `<ruby>` tag:

```html
<h1 class="product-single__title" itemprop="name">
  <ruby>
    <rb aria-hidden="true">火</rb><rp>(</rp><rt>か</rt><rp>)</rp>
    <rtc>Ka</rtc>
  </ruby>
</h1>
```

In some cases, the symbol may only be used for its shape and have no connection to the original language. In those cases, it's best to ensure AT will see it as decorative and prevent translation for visual users. Currently, no browser supports the HTML5 `translate` attribute. However, Google and others respect the `notranslate` class.

```html
<h1><span class="notranslate" translate="no" role="img">亼</span> Campgrounds <span class="notranslate" translate="no" role="img">亼</span></h1>
```

Other uses of extra-language symbols include OCR mistakes. For instance, searching Google for "火火" will yield many PDFs using rows of "\*" as a horizontal line. However, OCR programs misinterpret some of them. If these cases aren't considered [art](./art.md), they should be replaced with the HTML equivalent (e.g., `<hr aria-hidden="true">`).

Suggested test: regexp match against symbols by language declaration.

See:

- [es6-unicode-regex](https://mathiasbynens.be/notes/es6-unicode-regex)
- [Unicode Locale Data Summary](https://www.unicode.org/cldr/charts/latest/summary/root.html)
- [babel-plugin-utf-8-regex](https://github.com/danielberndt/babel-plugin-utf-8-regex/blob/master/src/transformer.js)
