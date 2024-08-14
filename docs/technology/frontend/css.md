# CSS

1. **Approach**
    1. CSS MUST be treated as a [progressive enhancement](../../ways-of-working/progressive-enhancement.md)
    1. CSS MUST be served as a static file and MUST NOT be compiled at runtime
    1. Compiled CSS MUST NOT contain a source file map in the `.css` file itself
    1. Compiled CSS SHOULD contain a link to a separate source file (`.map.css`)
    1. Compiled CSS SHOULD be compressed (e.g. `sass --style=compressed [src] [dest]`)
1. **Style/linting**
    1. CSS SHOULD adhere to the [BEM methodology](#bem)
    1. CSS MUST be styled with [Prettier](https://prettier.io/)
        1. Styling CSS with Prettier SHOULD NOT use any custom options ([Prettier's philosophy on options](https://prettier.io/docs/en/option-philosophy))
    1. CSS MUST be linted with [Stylelint](#stylelint)
        1. Stylelint MUST use the `stylelint-selector-bem-pattern` plugin
        1. Stylelint COULD be configured to ignore some rules
1. **Style content**
    1. CSS colours MUST be defined as either hex values or `rgb`
    1. CSS colours defined using `rgb` SHOULD use the newer syntax (`rgb(255 128 0)` rather than `rgb(255, 128, 0)`)
    1. CSS colours with alpha MUST use the newer `rgb` syntax (e.g. `rgb(255 128 0/0.5)`)
    1. CSS MUST work without support for [CSS variables](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties)
    1. CSS variables COULD be used to enhance customisability
1. **Media**
    1. If we expect the web content to be printed or saved to a PDF, CSS print styles SHOULD be considered

## SASS/SCSS

SASS is a preprocessor that compiles SASS syntax to CSS. It comes with a loose, indentation-based syntax.

SCSS is a newer SASS syntax and is more aligned to CSS, requiring braces and semicolons and allowing comments.

1. **Approach**
    1. SCSS COULD be used as an enhancement to CSS
    1. As SCSS is a superset of CSS, the same CSS standards above MUST also apply to SCSS
1. **Style/linting**
    1. The SCSS syntax MUST be used over the SASS syntax
    1. Stylelint MUST extend `stylelint-config-standard-scss`
1. **Frameworks, tools and libraries**
    1. The [Dart Sass](https://sass-lang.com/dart-sass/) library MUST be used instead of [Node Sass](https://www.npmjs.com/package/node-sass) or [LibSass](https://sass-lang.com/blog/libsass-is-deprecated/) to compile SCSS into CSS

## BEM

The CSS methodology we use is [BEM](https://getbem.com/).

On 4th February 2021, frontend developers met to agree a CSS methodology. Having considered a recommendation for utility CSS (as represented in [tailwindcss](https://tailwindcss.com/)) and results of the most recent [state of CSS survey](https://2020.stateofcss.com/en-US/technologies/), the team agreed that the BEM methodology would best reflect the needs of the team at this time.

[TNA Frontend](../../resources/tna-frontend.md) uses a mix of BEM and classless strategies. Simple "top-level" elements such as `<ul>` have a class (`tna-ul`) while the `<li>` elements within it do not, as the `<ul>` element should only contain `<li>`. For more information, see details of the [structure of TNA Frontend](https://github.com/nationalarchives/tna-frontend/wiki/Structure).

## Stylelint

[Stylelint](https://stylelint.io/) is "a mighty CSS linter that helps you avoid errors and enforce conventions".

```sh
npm install stylelint stylelint-config-standard-scss stylelint-selector-bem-pattern stylelint-order
```

An example `.stylelintrc` file that addresses all the standards above:

```json
{
  "extends": [
    "stylelint-config-standard-scss"
  ],
  "plugins": [
    "stylelint-selector-bem-pattern"
  ],
  "rules": {
    "at-rule-empty-line-before": null,
    "block-no-empty": null,
    "declaration-empty-line-before": null,
    "property-no-vendor-prefix": null,
    "value-keyword-case": null,
    "scss/dollar-variable-empty-line-before": null,
    "scss/double-slash-comment-empty-line-before": null,
    "selector-class-pattern": null,
    "plugin/selector-bem-pattern": {
      "preset": "bem"
    }
  }
}
```

```sh
# Run stylelint against all CSS files in the src directory...
stylelint 'src/**/*.css'

# ...or all SCSS files
stylelint 'src/**/*.scss'
```

### TNA Frontend Stylelint config

[TNA Frontend](../../resources/tna-frontend.md) comes with a [Stylelint config](https://github.com/nationalarchives/tna-frontend/blob/main/stylelint.config.js) which you can use in your project.

It includes property ordering for which you will need to install the `stylelint-order` module:

```sh
npm install stylelint-order
```

You can then change your `stylelint.config.mjs` to extend the TNA Frontend config:

```js
import data from "./node_modules/@nationalarchives/frontend/config/stylelint.config.js";

// Add your own rules
data.ignoreFiles = ["app/**/*.css", "tmp/**/*"];

export default data;
```

## Working with high contrast environments

There are two ways of requesting and setting high contrast views in a web application. They use the CSS media features of:

- `prefers-contrast`
- `forced-colors`

### `prefers-contrast`

The TNA Frontend's ["system" theme](https://nationalarchives.github.io/design-system/styles/colours/#system-theme) follows the preference for `prefers-contrast` which can be `no-preference`, `more`, `less` or `custom`. See [MDN Web Docs - prefers-contrast](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-contrast).

TNA Frontend currently only supports the `prefers-contrast` values of `no-preference` and `more`.

You can use this media feature to make designs with increased contrast.

### `forced-colors`

Windows offers a "High Contrast Mode" which allows a user to choose their own colour palette. This can be queried using the `forced-colors` CSS media feature.

Using `forced-colors` has some [accessibility concerns](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/forced-colors#accessibility_concerns) because the browser has no visibility of the colour palette.

Read the article [The difference between Increased Contrast Mode and Windows High Contrast Mode (Forced Colours Mode)](https://www.tempertemper.net/blog/the-difference-between-increased-contrast-mode-and-windows-high-contrast-mode) for more information.

Use this media feature only to make small changes such as adding extra borders. Do not set colours using `forced-colors`.
