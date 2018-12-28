# sass-throw

[![npm published v](https://img.shields.io/npm/v/@lunelson/sass-throw.svg)]()
[![Build Status](https://travis-ci.org/lunelson/sass-throw.svg?branch=master)](https://travis-ci.org/lunelson/sass-throw)

Make `@error`, `@warn` and `@debug` directives testable in Sass.

Use `error()`, `warn()` and `debug()` functions (or mixins) instead of the built-in `@error`, `@warn` and `@debug` directives, and when the global variable `$sass-throw-catch` is set to `true`, their messages will be output in CSS rather than passed to Sass directives.

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
$sass-throw-catch: true;

.test {
  error: error('this is an error message via function');
  warn: warn('this is a warn message via function');
  debug: debug('this is a debug message via function');
}

@include error('this is an error message via mixin');
@include warn('this is a warn message via mixin');
@include debug('this is a debug message via mixin');
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
