# Prettier, the format script

install prettier to dev dependencies&#x20;

```
npm install --sade-dev prettier
```

```
yarn add -D prettier
```

Create prettier config file

```
// prettier.config.js or .prettierrc.js

module.exports = {
  trailingComma: "es5",
  tabWidth: 4,
  semi: false,
  singleQuote: true,
};
```

Edit package.json

```
"scripts": {
    "format": "prettier --config .prettier.config.js '**/*.{ts,tsx,json,js,jsx,css}' --write"
},
```

run format

```
npm run format
yarn format
```
