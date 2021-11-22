# typescript-eslint-prettier-config
Minimal Typescript, ESLint and Prettier configuration.

ESLint and Prettier configurations are pretty standard in Javascript world. The intention of this package is to create a minimal setup with recommendations for [eslint](https://eslint.org/docs/rules/) and [prettier](https://prettier.io/docs/en/integrating-with-linters.html#notes) from the authors. According to them, we don't even need advance plugins that tries to get the best of both the worlds. Typescript config is cherry on top and gels easily with them.

## Installation
To install:
```bash
npm i typescript-eslint-prettier-config
```
or 
```bash
yarn add typescript-eslint-prettier-config
```

## How to use this package
1. To extend your existing Typescript configuration
<details><summary><strong>click to see example</strong></summary>

- `**/tsconfig.json`:

```json
{
    "extends": "**/node_modules/typescript-eslint-prettier-config/tsconfig.json",
    "compilerOptions": {
        ...
    },
    "exclude": ["**/node_modules/**", "build/**", "dist/**"],
    "include": ["src"]
}
```
</details>

2. To extend your existing ESLint configuration

<details><summary><strong>click to see example</strong></summary>

- `**/.eslintrc`:

```json
{
    "root": true,
    "extends": "**/node_modules/typescript-eslint-prettier-config/.eslintrc",
    "parserOptions": {
        "project": ["./tsconfig.json"] // this is your typescript configuration that you extended in the previous step
    }
}
```
</details>

## Further ideas to use the setup optimally
### VSCode
`eslint --fix` can be configured in the settings.json file in VSCode to automatically fix the linting errors.
```json
{
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  },
}
```
### Lint staging
`lint-staged` in combination with `husky` can be used in package.json to avoid accidentally committing non-linted files on github.
```json
{
  "husky": {
      "hooks": {
          "pre-commit": "lint-staged"
      }
  },
  "lint-staged": {
      "*.{js,ts,tsx}": [
          "eslint --fix"
      ]
  }
}
```
## Inspiration and Thanks
- [eslint-prettier-typescript-config](https://github.com/moia-oss/eslint-prettier-typescript-config)
- [Using ESLint and Prettier in a TypeScript Project](https://robertcooper.me/post/using-eslint-and-prettier-in-a-typescript-project)
- [How to use Prettier with ESLint and TypeScript in VSCode](https://khalilstemmler.com/blogs/tooling/prettier/)
