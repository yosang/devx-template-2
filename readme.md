This template build upon my previous [repo](https://github.com/yosang/dev-template/tree/main).

The goal is to provide a reusablke development ready template with the following tooling:

- Testing environment with `jest`.
- Proper coding style with `prettier`.
- Proper coding syntax with `eslint`.
- Pre-commit hook with `husky` and `lint-staged` to stop bad code from arriving the repository
- Github actions workflow that runs another check on all the above once the code has arrived the repository.

## Husky configuration

Install husky `npm i -D husky`

Configure husky with `npx husky init`

Add `npx lint-staged` to `pre-commit` inside `.husky/pre-commit`

## lint-staged configuration

Install lint-staged with `npm i -D lint-staged`

Create a configuration file named `.lintstagedrc` and add the following commands for `js` files.

```json
{
  "*.js": ["prettier --write", "eslint --fix"]
}
```

## Prettier configuration

Install prettier with `npm i -D prettier`

Create a configuration file named `.prettierrc` and add preferred rules, for this example im just using

```json
{
  "singleQuote": true
}
```

Add a script to `package.json` for github actions: `"format": "prettier --check ."`

## ESLint configuration

Install prettier with `npm i -D eslint`

Create a configuration by running `npx eslint --init`

Add a script to `package.json` for github actions: `"lint": "eslint ."`

## Jest configuration

Install jest with `npm i -D jest`

Add jest global keywords like `describe`, `it`, `expect` to ESLint config file:

```js
  {
    files: ['**/*.test.js'],
    languageOptions: { globals: globals.jest },
  },
```

Add a script to `package.json` for github actions: `"test": "jest"`

## Github Actions configuration
