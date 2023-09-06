# CSS

1. **Approach**
    1. CSS MUST be treated as a [progressive enhancement](../../ways-of-working/service-standard/#progressive-enhancement/)
1. **Style/linting**
    1. CSS SHOULD adhere to the [BEM methodology](#bem)
    1. CSS MUST be styled with [Prettier](https://prettier.io/)
    1. Styling CSS with Prettier SHOULD NOT use any custom options ([Prettier's philosophy on options](https://prettier.io/docs/en/option-philosophy))
    1. CSS MUST be linted with [Stylelint](#stylelint)
    1. Stylelint MUST use the `stylelint-selector-bem-pattern` plugin
    1. Stylelint COULD be configured to ignore some rules
1. **Style content**
    1. CSS colours MUST be defined as either hex values, `rgb` or `rgba`
    1. CSS MUST work without support for [CSS variables](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties)
    1. CSS variables COULD be used to enhance customisability

## SASS/SCSS

SASS is a preprocessor that compiles SASS syntax to CSS. It comes with a loose, indentation-based syntax.

SCSS is a newer SASS syntax and is more aligned to CSS, requiring braces and semicolons and allowing comments.

1. **Approach**
    1. The SCSS syntax MUST be used over the SASS syntax
    1. As SCSS is a superset of CSS, the same CSS standards above MUST also apply to SCSS
    1. SCSS COULD be used as an enhancement to CSS
1. **Style/linting**
    1. Stylelint MUST extend `stylelint-config-standard-scss`
1. **Frameworks, tools and libraries**
    1. The [Dart Sass](https://sass-lang.com/dart-sass/) library MUST be used instead of [Node Sass](https://www.npmjs.com/package/node-sass) or [LibSass](https://sass-lang.com/blog/libsass-is-deprecated/) to compile SCSS into CSS

## BEM

The CSS methodology we use is [BEM](https://getbem.com/).

On 4th February 2021, frontend developers met to agree a CSS methodology.

Having considered a recommendation for utility CSS (as represented in Tailwind.css) and results of the most recent state of CSS survey, the team agreed that the BEM methodology would best reflect the needs of the team at this time.

## Stylelint

[Stylelint](https://stylelint.io/) is "a mighty CSS linter that helps you avoid errors and enforce conventions".

```sh
npm install stylelint stylelint-config-standard-scss stylelint-selector-bem-pattern
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

## Print styles

If we expect the web content to be printed or saved to a PDF, CSS print styles SHOULD be considered
