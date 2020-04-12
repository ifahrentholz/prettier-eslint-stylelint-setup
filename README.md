# 0. Configuration files

Each "plugin" has a individual configuration file. You find it in the root of this repository.

| Plugin    | Config                        |
| --------- | ----------------------------- |
| ESLint    | .eslintrc                     |
| Prettier  | .prettierrc & .prettierignore |
| Stylelint | .stylelintrc                  |

### .eslintrc example for Typescript and React
```
{
  "parser": "@typescript-eslint/parser",
  "extends": [
    "plugin:react/recommended",
    "plugin:@typescript-eslint/recommended",
    "prettier/@typescript-eslint",
    "plugin:prettier/recommended"
  ],
  "parserOptions": {
    "ecmaFeatures": {
      "jsx": true
    }
  },
  "rules": {},
  "settings": {
    "react": {
      "version": "detect"
    }
  }
}
```

# 1. Install dependencies

Install prettier, eslint and stylelint

```
npm i -DE prettier eslint eslint-config-prettier eslint-plugin-prettier stylelint stylelint-config-prettier stylelint-declaration-use-variable stylelint-order stylelint-prettier stylelint-scss @pro-vision/stylelint-config-pv
```

## 1.1 Install dependencies Typescript

Install prettier, eslint, typescript-eslint and stylelint 

```
npm i -DE prettier eslint eslint-config-prettier eslint-plugin-prettier @typescript-eslint/parser @typescript-eslint/eslint-plugin stylelint stylelint-config-prettier stylelint-declaration-use-variable stylelint-order stylelint-prettier stylelint-scss @pro-vision/stylelint-config-pv
```

# 2. VSCode setup

### Necessary VSCode plugins

- [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
- [Prettier - Code formatter](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
- [stylelint](https://marketplace.visualstudio.com/items?itemName=stylelint.vscode-stylelint)

### VSCode configuration settings

```
...
"editor.codeActionsOnSave": {
  "source.fixAll": true,
},
"editor.defaultFormatter": "esbenp.prettier-vscode",
"editor.formatOnPaste": true,
"editor.formatOnSave": true,
"editor.formatOnType": true,
"eslint.format.enable": true,
...
```

# 3. Webstorm setup

### Prettier Settings

- **Goto:** _Languages & Frameworks > Javascript > Prettier_
  - Check the _Run on save for files_ checkbox
  - set the value to: `{**/*,*}.{js,ts,jsx,tsx}`
    ![Prettier config](__meta__/Prettier-Config.png)

### Stylelint Settings

I could only manage to enable autofix for css/scss files using File Watchers.

- **Goto:** _Tools > File Watchers_
  - Add new file watcher for CSS with the following settins:
    ![CSS File Watcher](__meta__/File-Watcher-CSS.png)
  - Add new file watcher for CSS with the following settins:
    ![SCSS File Watcher](__meta__/File-Watcher-SCSS.png)

# 4. Prevent ESLint and format errors from being committed

Install [lint-staged](https://github.com/okonet/lint-staged) and [husky](https://github.com/typicode/husky)

```
npm i -DE lint-staged husky
```

### 4.1 update package.json

Add a pre-commit hook via husky and run the lint-staged module

```
...
"husky": {
  "hooks": {
    "pre-commit": "lint-staged"
  }
},
"lint-staged": {
  "*.{js,ts,tsx}": [
    "eslint --cache --fix",
    "gid add"
  ]
}
...
```

Install (lint-staged)[https://github.com/okonet/lint-staged] and (husky)[https://github.com/typicode/husky]
Install (lint-staged)[https://github.com/okonet/lint-staged] and (husky)[https://github.com/typicode/husky]
