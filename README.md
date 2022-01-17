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
- The docs also link to a [repo of base configurations](https://github.com/tsconfig/bases/) for different target environments, marketed as _Definitely Typed for TSConfigs_. It's recommended to start by extending one of these bases. One issue is that you can't extend more than one. For this project, we'll simply create a TS config that has everything we need.
- The React docs have a section on [Adding TypeScript to a Project](https://reactjs.org/docs/static-type-checking.html#adding-typescript-to-a-project) as well.
- Webpack also has a [TypeScript guide](https://webpack.js.org/guides/typescript/).

## Prettier

[Prettier](https://prettier.io/) is an opinionated code formatter which we'll use to maintain consistent looking code.

- Since we're going to use ESlint, we'll want the [eslint-config-prettier](https://github.com/prettier/eslint-config-prettier#installation) package to make ESLint and Prettier play nice with eachother.
- There is a [JSON schema](http://json.schemastore.org/prettierrc) showing all the Prettier options, as well as the [official docs](https://prettier.io/docs/en/options.html).

## React

Our front end library of choice!

- The React docs have a section on [adding TypeScript support](https://reactjs.org/docs/static-type-checking.html#typescript).
- For global state management, [Recoil.js](https://recoiljs.org/) is an excellent option.
- [React Query](https://react-query.tanstack.com/) is popular as a data layer choice.
- [React Router](https://reactrouter.com/) is a go-to solution for routing. Tanstack also offers [React Location](https://react-location.tanstack.com/), which looks promising.
- [DefinintlyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped) is a repository with _high quality_ TypeScript type definitions. They have packages for [React types](https://github.com/DefinitelyTyped/DefinitelyTyped/tree/master/types/react) and [ReactDOM types](https://github.com/DefinitelyTyped/DefinitelyTyped/tree/master/types/react-dom).

## ESlint

We want to catch bugs in our code so ESLint will help us do that. We'll leave all the formatting to Prettier.

## Webpack

## Setting The Project Up

- Step 1: [Download and install TypeScript](https://www.typescriptlang.org/download).

```bash
npm i -D typescript
```

- Step 2: Create [`tsconfig.js`](https://www.typescriptlang.org/tsconfig) with the following settings:

```json
{
  "include": ["src/**/*"],
  "exclude": ["node_modules"],
  "compilerOptions": {
    "exactOptionalPropertyTypes": true,
    "strictNullChecks": true,
    "noFallthroughCasesInSwitch": true,
    "noImplicitAny": true,
    "noImplicitOverride": true,
    "noUncheckedIndexedAccess": true,
    "strictBindCallApply": true,
    "strictFunctionTypes": true,
    "useUnknownInCatchVariables": true,
    "module": "esnext",
    "moduleResolution": "node",
    "resolveJsonModule": true,
    "allowJs": true,
    "allowSyntheticDefaultImports": true,
    "esModuleInterop": true,
    "forceConsistentCasingInFileNames": true,
    "noEmit": true, // We'll use SWC or Babel instead of TS to compile TS => JS.
    "jsx": "react-jsx",
    "target": "es5",
    "baseUrl": "./src",
    "lib": ["esnext", "dom"]
  }
}
```

- Step 3: [Install Prettier](https://prettier.io/docs/en/install.html)

```bash
npm i -D prettier
```

- Step 4: Create `.prettierignore` (this should generally reflect your `.gitignore`):

```bash
node_modules
dist
```

- Step 5: Create [`.prettierrc.json`](https://prettier.io/docs/en/options.html). We explicitly state settings even though some are the same as the defaults:

```json
{
  "printWidth": 80,
  "tabWidth": 2,
  "useTabs": false,
  "semi": false,
  "singleQuote": true,
  "quoteProps": "as-needed",
  "jsxSingleQuote": false,
  "trailingComma": "es5",
  "bracketSpacing": false,
  "bracketSameLine": true,
  "arrowParens": "avoid",
  "requirePragma": false,
  "insertPragma": false,
  "proseWrap": "preserve",
  "htmlWhitespaceSensitivity": "css",
  "endOfLine": "lf",
  "embeddedLanguageFormatting": "off"
}
```

- Step 6: Install React and related type packages:

```bash
npm i -D react react-dom @types/react-dom @types/react
```

---

---

---

## TODO's

- [ ] Look into how [SWC](https://swc.rs/docs/getting-started) (an alternative to Babel) fits in to TypeScript and Webpack.
- [ ] If using SWC, do we need to enable the [jsx](https://www.typescriptlang.org/tsconfig#jsx) option with a value of `preserve`? This leaves the JSX untouched with the expectation that something later in the build process will handle it. An alternative is a value of `react-jsx` which emit's `.js` files with the JSX changed to `_jsx` calls.
- [ ] Add a testing solution (and section in this doc) to the project. React Testing Library? Cypress? Jest?
- [ ] Should we include a `.vscode` folder with a config in this project?
- [ ] Do we need to use [overrides](https://prettier.io/docs/en/configuration.html#configuration-overrides) in Prettier for test files?
- [ ] Check out the various TypeScript [plugins](https://www.typescriptlang.org/tsconfig#plugins). In particular, [typescript-styled-plugin](https://github.com/Microsoft/typescript-styled-plugin) and [typescript-eslint-language-service](https://github.com/Quramy/typescript-eslint-language-service).
