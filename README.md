# Modern JavaScript React Application

## VSCode

### Plugins

We'll use some plugins to aid in development, but we want to steer clear of global settings as much as possible. The plugins we want to install are:

- [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
- [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)

### Settings

Here's the barebones setup we'll use for VSCode:

```json
{
  "workbench.colorTheme": "Default Dark+",
  "files.insertFinalNewline": true,
  "editor.tabSize": 2,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.rulers": [80],
  "editor.formatOnSave": true,
  "prettier.arrowParens": "avoid",
  "prettier.jsxBracketSameLine": true,
  "prettier.semi": false,
  "prettier.singleQuote": true,
  "prettier.bracketSpacing": false,
  "eslint.alwaysShowStatus": true
}
```

## TypeScript

We want to write modern, type-safe JavaScript. TypeScript is simply the way to go.

There is a [JSX](https://www.typescriptlang.org/docs/handbook/jsx.html) section in the TypeScript docs which explains the various options of working with JSX. The React docs have a section on [Adding TypeScript to a Project](https://reactjs.org/docs/static-type-checking.html#adding-typescript-to-a-project) as well.

- Step 1: [Download and install TypeScript](https://www.typescriptlang.org/download)

```bash
npm i -D typescript
```

- Step 2: Create a config file

TODO:

- [ ] Look into how [SWC](https://swc.rs/docs/getting-started) (an alternative to Babel) fits in to TypeScript and Webpack.
- [ ] If using SWC, do we need to enable the [jsx](https://www.typescriptlang.org/tsconfig#jsx) option with a value of `preserve`? This leaves the JSX untouched with the expectation that something later in the build process will handle it. An alternative is a value of `react-jsx` which emit's `.js` files with the JSX changed to `_jsx` calls.

## React

## Webpack

## eslint

## prettier
