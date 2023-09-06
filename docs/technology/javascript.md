# JavaScript

1. **Approach**
    1. JavaScript MUST only be used for [progressive enhancement](../../ways-of-working/service-standard/#progressive-enhancement/) - do not rely on libraries such as React, Vue or Angular
1. **Version**
    1. JavaScript COULD use ESNext
    1. If written in ESNext, JavaScript MUST be transpiled down to ES5 with [Babel](https://babeljs.io/)
    1. Babel SHOULD use the `@babel/preset-env` preset
    1. JavaScript COULD be transpiled with [Webpack](https://webpack.js.org/)
    1. The version of NodeJS MUST be 18 or above
    1. The version of NodeJS SHOULD be a [LTS release](https://nodejs.dev/en/about/releases/)
    1. The version of NodeJS MUST be managed with [nvm](https://github.com/nvm-sh/nvm) and a `.nvmrc` file in the root of the project
1. **Style/linting**
    1. JavaScript MUST be linted with [ESLint](https://eslint.org/)
    1. ESLint MUST extend `eslint:recommended`
    1. JavaScript MUST be styled with [Prettier](https://prettier.io/)
    1. Styling JavaScript with Prettier SHOULD NOT use any custom options ([Prettier's philosophy on options](https://prettier.io/docs/en/option-philosophy))
1. **Dependencies**
    1. JavaScript dependencies MUST be managed with [npm](https://www.npmjs.com/)
1. **Frameworks, tools and libraries**
    1. JavaScript components COULD be developed using [Storybook](https://storybook.js.org/) - ([the rationale behind using Storybook](https://github.com/nationalarchives/tdr-dev-documentation/blob/master/architecture-decision-records/0028-storybook-for-tdr-components-library.md))
    1. JavaScript tests SHOULD be written with [Jest](https://jestjs.io/)
1. **Packages**
    1. JavaScript packages SHOULD be made using npm
    1. JavaScript packages SHOULD be deployed to [npm](../../third-party/npmjs/)
    1. If using NPM, packages MUST be published under the [`@nationalarchives` organisation]()
    1. JavaScript packages COULD be hosted in [AWS CodeArtifact](https://aws.amazon.com/codeartifact/)
    1. JavaScript MUST be compiled down to ES5 before distribution
    1. Source files COULD be included in distributed packages alongside the compiled ES5 to allow for the consumer to compile

## TypeScript

1. **Approach**
    1. As TypeScript is a superset of JavaScript, the same JavaScript standards above MUST also apply to TypeScript
    1. TypeScript COULD be used as an enhancement to JavaScript
1. **Packages**
    1. TypeScript MUST be compiled down to ES5 before distribution
