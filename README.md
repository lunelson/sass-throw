# sass-throw

Make `@error`, `@warn` and `@debug` messages testable in Sass. Sass-Throw provides three `function`s and three `mixin`s, one for each of `error`, `warn` and `debug`, which will function like normal `@error`, `@warn` and `@debug` directives in Sass unless the global variable `$st-catch` is set to `true`, whereupon they will be captured rather than output.

These "caught" directives can be checked with `last-error()` `last-warn()` and `last-debug()` respectively.


```scss
// Sass
$st-catch: true;

.test {
  value: error('something went wrong');
  check: last-error();
}
```
```css
/* CSS */
.test {
  check: "something went wrong";
}
```
