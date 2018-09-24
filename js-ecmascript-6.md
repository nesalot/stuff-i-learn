## [`let`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let) and `const`

* `let` declarations are not hoisted.
* If there's a `var` in an `if` block, it will be declared outside the block [to the nearest function scope](http://ariya.ofilabs.com/2013/05/es6-and-block-scope.html). `let` limits its scope to inside the block (which, if you like brackets, makes some sense)
* `let`s cannot be declared in the same scope twice. So, you cannot use `let`s in multiple `switch` statements.
    * You can use `for(let i = 0;...)` to limit `i` to the `for` block, and jshint won't complain like it does for `var`.
    * You can also use `let` to directly make a block: `let(foo='bar', baz='buz') { /* use foo inside */}`
* `const` [does NOT](http://exploringjs.com/es6/ch_variables.html) mean immutable. If you `const` an object, it is still mutable; the const itself just cannot be reassigned.

## Arrays and array-like things
* [Array comprehension](http://ariya.ofilabs.com/2013/02/es6-and-destructuring-assignment.html):

```
[for (x of ANY_ARRAY) for (y of ANY_ARRAY) for (z of ANY_ARRAY) (x + y + z)];  // unlimited number of `for`s

// these two are the same in what they do:
[console.log(t, a) for ({title: t, author: a} of books)];
[for (book of books) console.log(book.title, book.author)];
```

### New methods

* The equivalent to `all()` is [`.every()`](https://zabanaa.github.io/notes/functional-programming-and-javascript-arrays.html): `let bar: boolean = array.every(x => isTrue(x))`
* The equivalent to `any()` is [`.some()`](https://zabanaa.github.io/notes/functional-programming-and-javascript-arrays.html): `let bar: boolean = array.some(x => isTrue(x))`

## Destructuring

* Destructuring assignment:

```
var [m, d, y] = [3, 14, 1977];  // need to wrap both in array notation
var [,,y] = [3, 14, 1977];  // can ignore variables you don't need
```

[Destructuring objects](https://github.com/DrkSephy/es6-cheatsheet#destructuring-objects)

```
let luke = { occupation: 'jedi', father: 'anakin' }
let {occupation, father} = luke;
console.log(occupation); // 'jedi'
console.log(father); // 'anakin'
```

Such a destructure can be nested:

```
let {a: {b: c}} = {a: {b: 5}};  // c is now 5
```

It can also be done with brackets (`let (a, b, c) = {'a': ..., ...}`).
Do note that this can have a special case with just one unpack:

```
const { foo } = {foo: 'bar'};  // foo is bar because you unpacked foo from the object
```

AND [the special case where you unpack to nothing](http://www.2ality.com/2015/01/es6-destructuring.html):

```
const {} = 'abc';  // "OK, strings are coercible to objects"
const {} = undefined;  // Error
```

Function signatures are no special case. They also automatically destructure an object:

```
function getFullName({ firstName, lastName })  // Extracts firstName and lastName from the first argument object
```

## Functions
* Spread (packing) and Rest (unpacking):

```
function foo(a, b, ...rest) { /* rest is an array */ }
foo(...[1,2,3,4,5]);
```

* Arrow notation: only `=>`, no `->`, and no context binding.

```
array.map((p) => p * 2);
array.reduce((p, q) => (p + q));  // example with two arguments
```

`arguments` cannot be used inside arrow functions, much like `this` cannot be.

* [Arrow functions can be multiline](http://ilikekillnerds.com/2015/01/a-guide-to-es6-arrow-functions/), but they also make the `return` statement compulsary.

```
var a = (foo) => {
    return foo;
};

a(3)  // 3
```

* [Default arguments](http://ariya.ofilabs.com/2013/02/es6-and-default-argument.html):

```
function foo(bar=5) {
    console.log(bar);
}
```

* Keyword unpacking: given an object as the argument, using a ["set notation" from CoffeeScript](https://github.com/jashkenas/coffeescript/issues/2427) unpacks them into the scope:

```
function foo({x, y=5}) {  // note: object notation (y:5) is not valid syntax at this particular location
    console.log(x);  // 4
}
foo({x: 4, y: 5})
```

* [Function in object](https://strongloop.com/strongblog/javascript-es6-object-notation/) shorthands:

```
{
  hello() {
    // ...
  },
  'hello world'() {
    // ...
  }
}
```

is equivalent to

```
{
  hello: function () {
    // ...
  },
  'hello world': function () {
    // ...
  }
}
```

and a clutch to adding dynamic names is, for some reason, done with square brackets:

```
let foo = 'foo'
const obj = {
  [foo + 'bar']: true
}
```

## Classes

* Classes are not hoisted, even if they down-transpile to a function.
* Classes can be anonymous.
* [Class definitions are block-scoped, and cannot be redeclared in the same scope.](https://stackoverflow.com/a/36420130/1558430)
* If you have the balls to have a [class extends `null`](https://github.com/denysdovhan/wtfjs#function-is-not-function), be prepared to see unexpected behaviours ("function is not a function").

## [Proxies](http://ariya.ofilabs.com/2013/07/es6-and-proxy.html)

Proxies: a virtual wrapper that can handle property reads and changes on the original object.

```
var engineer = { name: 'Joe Sixpack', salary: 50 };

var interceptor = {
  set: function (receiver, property, value) {
    console.log(property, 'is changed to', value);
    receiver[property] = value;
  }
};

engineer = Proxy(engineer, interceptor);
```


* Getter and setters in object shorthands:

```
{
  get hello() { ... }
  set hello() { ... }
}
```

was previously available with an awkward syntax in ES5.

* Generators require that ugly asterisk after `function`:

```
   // The asterisk after `function` means that
   // `objectEntries` is a generator
   function* objectEntries(obj) {
        let propKeys = Reflect.ownKeys(obj);

        for (let propKey of propKeys) {
            // `yield` returns a value and then pauses
            // the generator. Later, execution continues
            // where it was previously paused.
            yield [propKey, obj[propKey]];
        }
    }

    for (let [key,value] of objectEntries(jane)) {
        console.log(`${key}: ${value}`);
    }
```

## Imports
Imports and [default imports](http://www.2ality.com/2014/09/es6-modules-final.html) are similar, the only difference being whether the import is wrapped in braces.

```
export default function () { return 4 }
export function foo() { return 5 }
// ---
import CallItAnything, {foo} from 'that_file';
CallItAnything();  // 4
foo();  // 5
```

[Default imports can be mixed with named imports on a single line.](http://stackoverflow.com/a/31098182/1558430)

```
export default function () { .. this is React }
export function Component () { ... }
export function PropTypes () { ... }
---
import React, { Component, PropTypes } from 'react';
===
import React from 'react';
import { Component, PropTypes } from 'react';
===
Importing the default export under the name "React"
Importing the two named exports under the same names
```

* You can also `import * from 'a library'`.
* You [cannot](http://stackoverflow.com/questions/30340005/importing-modules-using-es6-syntax-and-dynamic-path) import dynamic paths. (In python, you `__import__(dynamic)`.)
* `require('a library')` is slower than imports, as the latter can be optimised statically.
* `import` is [not](http://adrianmejia.com/blog/2016/08/12/Getting-started-with-Node-js-modules-require-exports-imports-npm-and-beyond/#Imports) available in node 6.

## Async/Await (ES7)

* `async function`s always return a promise. A `return 5` in an async function returns a promise that resolves with 5.
* `async function`s always reject with the error if an error is thrown in it.
* `await asyncFunction()` always returns the value that the function resolves.

[Only in an `async`-marked function can you use `await`](http://masnun.com/2015/11/11/using-es7-asyncawait-today-with-babel.html). An `await` in a non-`async function` throws a SyntaxError.
If a promise is resolved, then the lines after `await` run. Otherwise, it throws an error and any `catch` blocks run.
If an async function has multiple return points: since a promise can only resolve once, it will always resolve with the first value.

## ES 2017

* RegExp will now support negative lookahead, which uses `(?<!foo)` to ensure a pattern is not preceded by another pattern. `(?<!foo)bar` will never match `foobar`.
