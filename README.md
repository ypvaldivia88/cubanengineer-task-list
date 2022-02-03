# template-base-nuxt

If you're starting a new project, you can simply use this repository as a template and start developing with no additional effort - yay!

In an effort to standardize our repos, if you have already started a project please use this guide to add the necessary linting configuration to keep our code clean & consitent :)

## Adding Husky and commitlint to an existing Nuxt project

1. Install the packages

```bash
yarn add -D @commitlint/cli @commitlint/config-conventional @commitlint/config-conventional @nuxtjs/stylelint-module lint-staged stylelint stylelint-config-prettier stylelint-config-standard
```

2. Add this configuration to the package.json

```javascript
  "lint-staged": {
    "*.{js,vue}": "eslint",
    "*.{css,vue}": "stylelint"
  },
  "husky": {
    "hooks": {
      "commit-msg": "commitlint -E HUSKY_GIT_PARAMS",
      "pre-commit": "lint-staged"
    }
  },
```

3. Add these scripts to your package.json scripts property

```javascript
    "lint:js": "eslint --ext \".js,.vue\" --ignore-path .gitignore .",
    "lint:style": "stylelint \"**/*.{vue,css}\" --ignore-path .gitignore",
    "lint": "yarn lint:js && yarn lint:style",
```

⚠️ NOTE: to make commits that follow the recommended format it is easiest to use commitizen as a CLI tool to structure the messages

## Adding ESLint configuration to an existing Nuxt project

```bash
yarn add -D @vue/eslint-config-airbnb eslint-config-airbnb-base eslint-plugin-import eslint-plugin-nuxt
```

## Build Setup

```bash
# install dependencies
$ yarn install

# serve with hot reload at localhost:3000
$ yarn dev

# build for production and launch server
$ yarn build
$ yarn start

# generate static project
$ yarn generate
```

For detailed explanation on how things work, check out [Nuxt.js docs](https://nuxtjs.org).
