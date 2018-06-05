# Meaningful Formatting

Using the `Intl.NumberFormat` API, we can format currency in modern browsers in a way that's expected by users and assistive technology.

However, accountants (at least in the US) often express negative values (debits) as:

```
$(2,000.00)
```

instead of

```
-$2,000.00
```

A screen reader will likely skip the parenthesis around the number causing confusion for the user about which numbers are credits and which are debits.

So, in this case, the text is skipped because it is assumed to be trivial, like if it were decorative.

```html
<style>
.currency:before {
  content: '$';
}
.currency .debit {
  display: none;
}
.currency[data-value^="-"] {
  color: red;
}
.currency[data-value^="-"] .debit {
  display: block;
}
.currency[data-value^="-"] .credit {
  display: none;
}
.currency[data-value^="-"]:before {
  content: '$(';
  margin-left: -0.333em;
}
.currency[data-value^="-"]:after {
  content: ')';
}
</style>
<p>
  <span class="currency" data-value="2000">
    <!-- this could be deposit/withdraw for a different context -->
    <span class="off-screen-text debit">debit</span>
    <span class="off-screen-text credit">credit</span>
    <span>2,000</span>
</p>
<p>
  <span class="currency" data-value="-2000">
    <span class="off-screen-text debit">debit</span>
    <span class="off-screen-text credit">credit</span>
    <span>2,000</span>
</p>
```
