# Sass Throw

[![](https://img.shields.io/travis/lunelson/sass-throw.svg?style=flat-square)](https://travis-ci.org/lunelson/sass-throw)
[![](https://img.shields.io/npm/v/@lunelson/sass-throw.svg?style=flat-square)](https://www.npmjs.com/package/@lunelson/sass-throw)
[![](https://img.shields.io/github/license/lunelson/sass-throw.svg?style=flat-square)](https://github.com/lunelson/sass-throw/blob/master/LICENSE)

Functions for using Sass' `@error` `@warn` and `@debug` directives in a way that is capturable and testable.

## Installation
```sh
# install in your project

npm i @lunelson/sass-throw
```
## Basic Usage

The basic API consists of the following functions and mixins, which receive a string, and  will trigger their corresponding directive (e.g. `@warn`) with the given string when the `$throw-catch` global variable is `false`, but will return the string when `$throw-catch` is true.

```scss
// Sass input file
// NB: you need 'node_modules' in Sass' `importPaths` option

@import '@lunelson/sass-throw/index';

$throw-catch: true;

.test {
  error: throw-error('this is an error message via function');
  warn: throw-warn('this is a warn message via function');
  debug: throw-debug('this is a debug message via function');
}

@include throw-error('this is an error message via mixin');
@include throw-warn('this is a warn message via mixin');
@include throw-debug('this is a debug message via mixin');
```
```css
/* CSS output file */

.test {
  error: "this is an error message via function";
  warn: "this is a warn message via function";
  debug: "this is a debug message via function";
}

.sass-throw .error {
  message: "this is an error message via mixin";
}

.sass-throw .warn {
  message: "this is a warn message via mixin";
}

.sass-throw .debug {
  message: "this is a debug message via mixin";
}
```

Questions? File an issue, or [tweet at me](https://twitter.com/lunelson).
