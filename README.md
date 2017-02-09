# sass-throw

Make `@error`, `@warn` and `@debug` messages testable in Sass.

This lib provides a `function` and a `mixin` for each of `error()`, `warn()` and `debug()` to be used instead of the built-in `@error`, `@warn` and `@debug` directives in Sass. These work transparently unless the global variable `$st-catch` is set to `true`, whereupon messages will be captured rather than output. These messages can be inspected with `last-error()` `last-warn()` and `last-debug()` respectively.


```scss
// Sass
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
/* CSS */
.test {
  error: "something went wrong";
  debug: "this is a debug message";
}
```
