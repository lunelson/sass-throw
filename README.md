# sass-throw

[![](https://img.shields.io/travis/lunelson/sass-throw.svg?style=flat-square)](#travis)
[![](https://img.shields.io/npm/v/@lunelson/sass-throw.svg?style=flat-square)](#releases)
[![](https://img.shields.io/github/license/lunelson/sass-throw.svg?style=flat-square)](#license)
<!-- [![](https://img.shields.io/npm/dt/@lunelson/sass-throw.svg?style=flat-square)](#download) -->

Make `@error`, `@warn` and `@debug` directives testable in Sass.

Use `error()`, `warn()` and `debug()` functions (or mixins) instead of the built-in `@error`, `@warn` and `@debug` directives, and when the global variable `$throw-catch` is set to `true`, their messages will be output in CSS rather than passed to Sass directives.

```sh
# in your project
npm install --save @lunelson/sass-throw
```
```scss
// in your sass file, assuming you have 'node_modules' in Sass' search path
@import '@lunelson/sass-throw/index';
```
```scss
/* input: test.scss */
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
/* output: test.css */
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
