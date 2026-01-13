# JavaScript

1. **Approach**
    1. JavaScript MUST only be used for [progressive enhancement](../../ways-of-working/progressive-enhancement.md) - do not rely on libraries such as React, Vue or Angular
    1. JavaScript MUST be served as a static file and MUST NOT be compiled at runtime
    1. Compiled JavaScript MUST NOT contain a source file map in the `.js` file itself
    1. Compiled JavaScript SHOULD contain a link to a separate source file (`.map.js`)
1. **Version**
    1. JavaScript COULD use ESNext
    1. If written in ESNext, JavaScript MUST be transpiled down to ES5 with [Babel](https://babeljs.io/)
    1. Babel SHOULD use the `@babel/preset-env` preset
    1. JavaScript COULD be transpiled with [Webpack](https://webpack.js.org/)
    1. The version of NodeJS MUST be 18 or above
    1. The version of NodeJS SHOULD be 22 or above
    1. The version of NodeJS SHOULD be a [LTS release](https://nodejs.org/en/about/previous-releases)
    1. The version of NodeJS MUST be managed with [nvm](https://github.com/nvm-sh/nvm) and a [`.nvmrc` file](#nvm) in the root of the project
1. **Style/linting**
    1. JavaScript MUST be linted with [ESLint](#eslint)
    1. ESLint MUST extend `eslint:recommended`
    1. JavaScript MUST be styled with [Prettier](https://prettier.io/)
    1. Styling JavaScript with Prettier SHOULD NOT use any custom options ([Prettier's philosophy on options](https://prettier.io/docs/en/option-philosophy))
1. **Dependencies**
    1. JavaScript dependencies MUST be managed with [npm](https://www.npmjs.com/)
1. **Frameworks, tools and libraries**
    1. JavaScript components COULD be developed using [Storybook](https://storybook.js.org/) - ([the rationale behind using Storybook](https://github.com/nationalarchives/tdr-dev-documentation/blob/master/architecture-decision-records/0028-storybook-for-tdr-components-library.md))
    1. JavaScript tests SHOULD be written with [Jest](https://jestjs.io/)
    1. [Single page applications MUST not be developed](../../ways-of-working/progressive-enhancement.md#single-page-applications)
1. **Packages**
    1. JavaScript packages SHOULD be made using npm
    1. JavaScript packages SHOULD be deployed to [npm](../../third-party/npmjs.md)
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

## NVM

Use [nvm](https://github.com/nvm-sh/nvm) to ensure your project can be worked on in the future without having to guess which version of Node.js is required to run it.

Add an `.nvmrc` file in your project to declare the version of Node required. For example:

```
lts/jod
```

LTS releases have codenames. This ensures that you always use the latest version of that release:

| Version | LTS Codename |
| ------- | ------------ |
| `22.x`  | `jod`        |
| `20.x`  | `iron`       |
| `18.x`  | `hydrogen`   |

Check a [full list of latest versions for each branch of Node.js](https://nodejs.org/en/about/previous-releases#looking-for-the-latest-release-of-a-version-branch).

To ensure the correct version of Node is used, you can add the following line to your `.bashrc`, `.zshrc` or similar in order to set up the correct version of Node when you open your terminal for that project:

```sh
# If an .nvmrc file exists then install and use that version of Node
[[ -f .nvmrc ]] && nvm install
```

## ESLint

[ESLint](https://eslint.org/) is a static code analyser for JavaScript.

```sh
npm install eslint
```

An example `.eslintrc.js` file that addresses all the standards above:

```js
module.exports = {
    env: {
        browser: true,
        es2021: true,
    },
    extends: ["eslint:recommended"],
    overrides: [
        {
            env: {
                node: true,
            },
            files: [".eslintrc.{js,cjs}"],
            parserOptions: {
                sourceType: "script",
            },
        },
    ],
    parserOptions: {
        ecmaVersion: "latest",
        sourceType: "module",
    },
    rules: {},
};
```

```sh
# Run eslint against all JS files in the src directory
eslint 'src/**/*.js'
```

### TNA Frontend ESLint config

[TNA Frontend](../../resources/tna-frontend.md) comes with an [ESLint config](https://github.com/nationalarchives/tna-frontend/blob/main/.eslintrc.js) which you can use in your project.
