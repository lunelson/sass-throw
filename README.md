# sass-throw

Make `@error`, `@warn` and `@debug` messages testable in Sass.

Use `error()`, `warn()` and `debug()` functions (or mixins) instead of the built-in `@error`, `@warn` and `@debug` directives. When the global variable `$st-catch` is set to `true`, messages will be captured rather than output, and can be inspected with `last-error()` `last-warn()` and `last-debug()` respectively.

```sh
# install
npm install --save @lunelson/sass-throw
```
```scss
// test.scss
@import 'sass-throw/index';
$st-catch: true;
.test {
  // error as function
  value: error('something went wrong');
  error: last-error();
  // debug as mixin
  @include debug('this is a debug message');
  debug: last-debug();
}
```
```css
/* test.css */
.test {
  error: "something went wrong";
  debug: "this is a debug message";
}
```

Questions? File an issue, or [tweet at me](https://twitter.com/lunelson).
