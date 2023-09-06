# CSS

1. **Approach**
    1. CSS MUST be treated as a [progressive enhancement](../../ways-of-working/service-standard/#progressive-enhancement/)
1. **Style**
    1. CSS SHOULD adhere to the [BEM methodology](#bem)
    1. CSS MUST be styled with [Prettier](https://prettier.io/)
    1. Styling CSS with Prettier SHOULD NOT use any custom options ([Prettier's philosophy on options](https://prettier.io/docs/en/option-philosophy))
    1. CSS MUST be linted with [Stylelint](#stylelint)
    1. Stylelint MUST extend `stylelint-config-standard-scss`
    1. Stylelint MUST use the `stylelint-selector-bem-pattern` plugin
    1. Stylelint COULD be set to ignore some rules
    1. CSS colours MUST be defined as either hex values, `rgb` or `rgba`

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
  "ignoreFiles": ["src/nationalarchives/lib/font-awesome/**/*.scss"],
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

## SCSS

- Structure
- Variables
