# @mouji/eslint-config

[![npm](https://img.shields.io/npm/v/@mouji/eslint-config?color=a1b858&label=)](https://npmjs.com/package/@mouji/eslint-config)


## Usage

### Install

```bash
pnpm add -D eslint @mouji/eslint-config
```

### Config `.eslintrc`

```json
{
  "extends": "@mouji"
}
```

> You don't need `.eslintignore` normally as it has been provided by the preset.

### Add script for package.json

For example:

```json
{
  "scripts": {
    "lint": "eslint .",
    "lint:fix": "eslint . --fix"
  }
}
```

### Config VS Code auto fix

Install [VS Code ESLint extension](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint) and create `.vscode/settings.json`

```json
{
  "prettier.enable": false,
  "editor.formatOnSave": false,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  }
}
```

### TypeScript Aware Rules

Type aware rules are enabled when a `tsconfig.eslint.json` is found in the project root, which will introduce some stricter rules into your project. If you want to enable it while have no `tsconfig.eslint.json` in the project root, you can change tsconfig name by modifying `ESLINT_TSCONFIG` env. 

```js
// .eslintrc.js
process.env.ESLINT_TSCONFIG = 'tsconfig.json'

module.exports = {
  extends: '@mouji'
}
```

### Lint Staged

If you want to apply lint and auto-fix before every commit, you can add the following to your `package.json`:

```json
{
  "simple-git-hooks": {
    "pre-commit": "pnpm lint-staged"
  },
  "lint-staged": {
    "*": "eslint --fix"
  }
}
```

and then

```bash
pnpm i -D lint-staged simple-git-hooks
```

### I prefer XXX...

Sure, you can override the rules in your `.eslintrc` file.

<!-- eslint-skip -->

```jsonc
{
  "extends": "@mouji",
  "rules": {
    // your rules...
  }
}
```