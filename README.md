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

- The TypeScript docs provide a [comprehensive list of all configuration options](https://www.typescriptlang.org/tsconfig) and what they do. These are available as a [JSON schema](https://json.schemastore.org/tsconfig) as well.
- There is a [JSX](https://www.typescriptlang.org/docs/handbook/jsx.html) section in the docs which explains the various options of working with JSX.
- The docs also link to a [repo of base configurations](https://github.com/tsconfig/bases/) for different target environments, marketed as _Definitely Typed for TSConfigs_. It's recommended to start by extending one of these bases.
- The React docs have a section on [Adding TypeScript to a Project](https://reactjs.org/docs/static-type-checking.html#adding-typescript-to-a-project) as well.
- Webpack also has a [TypeScript guide](https://webpack.js.org/guides/typescript/).

TODO:

- [ ] Look into how [SWC](https://swc.rs/docs/getting-started) (an alternative to Babel) fits in to TypeScript and Webpack.
- [ ] If using SWC, do we need to enable the [jsx](https://www.typescriptlang.org/tsconfig#jsx) option with a value of `preserve`? This leaves the JSX untouched with the expectation that something later in the build process will handle it. An alternative is a value of `react-jsx` which emit's `.js` files with the JSX changed to `_jsx` calls.

## React

## Webpack

## eslint

## prettier

## Setting The Project Up

- Step 1: [Download and install TypeScript](https://www.typescriptlang.org/download).

```bash
npm i -D typescript
```

- Step 2: Create `tsconfig.js` - our TypeScript config file.

Running `npx tsc --init` will create a `tsconfig.json` file populated with tons of comments concerning the configuration options available. We'll look to extend a provided [base](https://github.com/tsconfig/bases/) file instead.

```bash
# Create the config file.
touch tsconfig.json

# Install the recommended base config.
npm i - D @tsconfig/recommended
```

- Step 3: Update the contets of `tsconfig.json` to be:

```json
{
  "compilerOptions": {
    "target": "ES2015",
    "module": "commonjs",
    "strict": true,
    "esModuleInterop": true,
    "skipLibCheck": true,
    "forceConsistentCasingInFileNames": true
  },
  "$schema": "https://json.schemastore.org/tsconfig",
  "display": "Recommended",
  "extends": "@tsconfig/recommended/tsconfig.json"
}
```