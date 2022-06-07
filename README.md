# Webpack Syntax Resolver Plugin

[![npm version](https://badge.fury.io/js/webpack-syntax-resolver-plugin.svg)](https://badge.fury.io/js/webpack-syntax-resolver-plugin)

## Why

> Do not use this, this was a reaction to a proposal made for syntax fields on the package json field which allowed package authors to specify
> newer versions of the ECMA spec for their distributed files

This automates resolving the plugin on a more modern syntax field, this field
is derived from the package.json.

Example: pkg X would normally be imported as an ES5 module, this plugin sees
that pkg X exports a more modern ES6 bundle because syntax.esmodule leads
to that bundle.
Then this package will rewrite this resolver call to use the modern lib
instead.

Caution: not all browsers support ES6 features, this lib is intended to be 
used with a [module nomodule build](https://github.com/JoviDeCroock/webpack-module-nomodule-plugin)

## How to use

```javascript
const syntaxResolverPlugin = require('webpack-syntax-resolver-plugin');

{
  ...webpackConfig,
  resolve: {
    plugins: [new syntaxResolverPlugin()],
  },
}

```

And let it to the magic, if you find a package that is causing issues you
can ignore it by passing an option to this plugin named: ignoredModules,
this expects an array.

The rest will be handled for you!

## Example

https://github.com/JoviDeCroock/POC-ModularLegacyBuild

## Installation

`npm install --save-dev webpack-syntax-resolver-plugin`
