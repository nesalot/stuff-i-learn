* Declaring a variable: `$something: anything;`
* Importing another SCSS file: `@import "something";` (relative path, no extensions)
* Nested styles (besides `@media`): both elements (without colon) and attribute shorthands (with colon) can be nested
* Conditionals and nested conditionals: `@if`, `@else if`, and `@else` the way you expect. No `@end if`.
* [The SASS website](http://sass-lang.com/) says that SCSS is a more "css-like" dialect of SASS, with semicolons and everything.
* *mixins*: something (e.g. `left`), possibly with arguments (e.g. `left($dist)`), that you can `@include` to anything as style.
* [The ampersand can be anywhere](http://www.joeloliveira.com/2011/06/28/the-ampersand-a-killer-sass-feature/):

```
ul {
    ...
    .pages &  {
        // .pages ul
    }
}
```
