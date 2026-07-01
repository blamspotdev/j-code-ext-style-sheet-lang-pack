# j-code-ext-style-sheet-lang-pack

A JCode **language** extension bundling **style sheet** languages in one pack —
installed through the
[JCode Marketplace](https://github.com/blamspotdev/j-code-marketplace) and shipped
**pre-installed** with the JCode app.

| Language | Extensions |
|---|---|
| CSS | `.css` `.pcss` `.postcss` |
| SCSS | `.scss` |
| SASS | `.sass` |
| LESS | `.less` |
| Stylus | `.styl` `.stylus` |
| XSL / XSLT / XSL-FO | `.xsl` `.xslt` `.fo` |
| DSSSL | `.dsl` `.dsssl` |

Each language provides syntax **coloring** (properties, values/units, at-rules like
`@media`/`@mixin`/`@include` as annotations, strings, numbers, comments), as-you-type
**completions + snippet helpers** (selector block, flex-center, media query, SCSS
`@mixin`/`@include`, an `<xsl:template>`), and the built-in **Format Document**.

Plain HTML / XML / SVG / YAML / JSON / TOML / INI are handled by the companion
[**Markup Language Pack**](https://github.com/blamspotdev/j-code-ext-markup-pack-1).

## Manifest shape — one extension, many languages

`extension.yaml` uses a `languages:` array; each entry is a self-contained language
pack resolved by file extension (a YAML anchor shares the common CSS value/unit set):

```yaml
type: language
languages:
  - id: css
    extensions: [".css"]
    comment: { blockStart: "/*", blockEnd: "*/" }
    keywords: [color, background, margin, padding]   # colored as keywords + offered as completions
    types: &cssvalues [px, em, rem, flex, grid]      # colored as types
    formatter: { indent: 2, trimTrailingWhitespace: true, insertFinalNewline: true }
  - id: scss
    extensions: [".scss"]
    comment: { line: "//", blockStart: "/*", blockEnd: "*/" }
    types: *cssvalues
    completions:
      - { label: mixin, detail: "@mixin", insert: "@mixin $1 {\n  $0\n}" }
```

See the marketplace's
[`CREATING-EXTENSIONS.md`](https://github.com/blamspotdev/j-code-marketplace/blob/main/CREATING-EXTENSIONS.md)
for the full authoring flow.

## License

MIT. © 2026 blamspotdev (Janrick Samorin).
