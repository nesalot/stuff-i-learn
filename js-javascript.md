![Wat](http://i.imgur.com/IppKJ.jpg)

* Whitespace in between symbols don't matter: `console   .    log    (   'lol'   )  // lol`
* "You need to use yarn in flat mode with `yarn install --flat`"
* The codename for ionic v1 is [`hong kong`](https://github.com/ionic-team/ionic-v1/blob/master/package.json#L5).
* [JSX in excruciating depth](http://blog.klipse.tech/javascript/2016/12/14/jsx.html)
* If some npm package keeps complaining about unmet peer dependencies, even though you installed the dependencies first, [it might just need to be installed together, at the same time](https://github.com/palantir/tslint/issues/2647#issuecomment-298005316), like `npm install -g typescript tslint`.
* [HEIF](https://en.wikipedia.org/wiki/High_Efficiency_Image_File_Format) uses HEVC (patented) for encoding by default.
* Both [nodejs/node](https://github.com/nodejs/node) and [ayojs/ayo](https://github.com/ayojs/ayo#core-team) have custom "pronouns" for every team member, and not ironically.
* [According to Crockford, Netscape called it LiveScript, originally.](https://news.ycombinator.com/item?id=8344100) In their attempt to 'destroy Microsoft', they teamed up with Sun. One of Sun's original goals with Java was making it the client-side scripting language for the browser. However, Netscape had LiveScript. Apparently the negotiations almost broke down over this point. In an enlightened moment, (probably) Marc Andreessen proposed renaming LiveScript to JavaScript (despite the fact that the languages have very little in common), and joy was had. Sun got the JavaScript trademark (and passed it on to Oracle), and Netscape got a perpetual exclusive license to use it. When JavaScript was standardized to avoid Embrace, Extend, Extinguish, Netscape refused to share its license, and so the official language was renamed to ECMAScript, after the standards body. When Sun was bought by Oracle, it also got the trademark, and presumably, Mozilla inherited the exclusive license from Netscape.
* [The article about NodeJS 8 release](https://nodejs.org/en/blog/release/v8.0.0/), saying *'Note that, when referring to Node.js release versions, we have dropped the "v" in Node.js 8. Previous versions were commonly referred to as v0.10, v0.12, v4, v6, etc. In order to avoid confusion with V8, the underlying JavaScript engine, we've dropped the "v" and call it Node.js 8'*, was titled *'Node v8.0.0 (Current)'*.
* `window.location.reload()` accepts either `true` or `false` for hard reload.
* `window.location.reload()` does not accept arguments across all browsers.
* You can't send code to the server by POST and have the browser run the same code. (Refused to execute a JavaScript script. Source code of script found within request.)
* The window's `storage` event is fired on [every window using the storage except the window that modified storage][stackoverflow].
* `in` compares by reference, apparently. `'e' in 'hello'.split('')` returns false.
*  You also shouldn't blindly `in` everything; [`for (var i in window.external)`](http://andrew.hedges.name/experiments/in/) throws exceptions in IE.
* NaN always compares to false. Only isNaN can compare NaN.
* Delegated selectors save memory (most of the time): `$(parentObject).on(events, selector[, data], function (event) {})`
* Delegated events can be triggered by `.trigger("myCustomEvent", [data])`.
* jQuery will ignore the `data` option when creating an element from string if the element already has data attribute(s).
* `void 0 === undefined`.
* It was possible to define the global `undefined`; not possible anymore, because people were screwing around with it.
* `$([...]).each` is faster when `for` loops when it contains elements, and slower when it contains an ordinary iterable.
* `new Object`, or any object in general (e.g. `Date`), does not require `()` to initialise. Strict mode will throw a warning, though.
* It is possible to run a WebSocket inside a worker.
* `+almostAnything` converts it to an integer. (except objects, arrays, strings... so, almost nothing.)
* A named closure (which is NOT an oxymoron: `(function abc() {... }())` has its function name scoped inside the closure.
* One use of the named closure (`(function abc() {}())`) is that `abc` is defined only inside the scope, which means recursive closures can be built without using an outside variable.
* Another use of named closures is if you want to return an object instantiator:

```
return function IndexError(msg) {
    // then do whatever you want with this 'class' outside the function 
    // and all instances will at least have a name
};
```

* `function abc()` in IE8 or above are declared twice, due to a bug in [hoisting and initialisation][github].
* Youtube disables autoplay on mobile devices, even when `autoplay: 1`.
* Detecting document zoom level [is a piece of ass][stackoverflow 2].
* In an [AngularJS][angularjs] controller definition, the variable name for the scope must be `$scope`.
* `Object.defineProperty` creates immutable object constants. [Everything except IE8][mozilla] does it correctly.
* Since the deprecation of IE6 and IE7, `window.elementFromPoint(clientX, clientY)` and `window.getClientRects() -> [t, l, r, b]` are available to you.
* `~~` is a [fast Math.floor][stackoverflow 3], noting some differences about negative numbers ("in that it actually just removes anything to the right of the decimal. This makes a difference when used against a negative number. Also, it will always return a number, and will never give you NaN. If it can't be converted to a number, you'll get 0").
* Ember.js will first render whichever nameless template with the string `{{ outlet }}` in it.
* Ember.js: namespaces must begin with an upper case letter.
* Ember.js: `model` is a keyword. You cannot replace it with `context`.
* In backbone.js, [a `View` is actually a controller][backbonejs].
* `return a, b` returns whichever value is true first.
* [Scroll events do not bubble.][quirksmode]
* There are [typed arrays][mozilla 2].
* `inputElement.selectionStart` is not cross-browser compatible.
* As it turns out, there is a [documented way][wikipedia] of validating JSON.
* `$(":last")` does not require an element.
* `_.bindAll` binds for all future calls, too.
* Although it is always true that a script tag with both src and content will not execute its content, [it doesn't mean it is pretty to tell the src to execute its innerHTML][ejohn].
* `new function () { return ... }` returns the return value instead of an object when the value is an object.
* `typeof null` is `"object"`.
* [The simplest inheritance example out there][stackoverflow 4]
* [data uris are not worth pursuing][mobify]
* There is a built-in [self][stackoverflow 5] keyword, but usually pointing at `window`, it's not all that useful.
* The `with` statement was banned [before it was even cool][mozilla 3].
* A `setTimeout` with a delay of 0 calls the function when the call stack is empty.
* [The 3 snapshot technique][google]: First take a snapshot, then do something and take another snapshot. Repeat the exact same things and take snapshot 3. Finally, "filter objects allocated between snapshots 1 and 2 in snapshot 3's summary view"
* `_.once` keeps returning the value of the original call in subsequent calls.
* Terminology: `_gaq.push(['_trackEvent', 'category', 'action', 'label', 'value']);` [source][google 2]
* ~~[No such thing as tail call optimization][stackoverflow 6]... not one that works, anyway~~ES6 has tail call optimisation.
* [Trampolines][raganwald] are `while` wrappers that call an inner function for as long as the function remains a function, not a primitive value.
* `undefined == null` === `true`. Die in a fire, JS!
* [Second parameter of `JSON.parse`][stackoverflow 7] (reverse applies to `.stringify`, too)
* CORS is not supported before IE8; hence JSONP.
* `$.each(string)` [stopped working][stackoverflow 8]. Now you will need to split the string first.
* [Detecting `{}.__proto__`][zurb] is one of the fastest ways to tell if a browser is running on a [browser that also runs on mobiles][stackoverflow 9].
* [`debugger`][microsoft].aspx)
* `_.result(a)` returns `a()` if it is a function, or just `a`.
* `Number()` returns 1 or 0.
* If desperate, `_.omit(obj)` makes a copy of the object. `_.omit(obj, key1, key2, ...)` creates a copy without attributes key1 and key2.
* `navigator.onLine` is `true` when the browser is actually online, unless you are on a mobile device, in which case it is always `false`.
* Backbone: `Collection.parse` is called *only* if you resolve the `fetch` XHR with remote JSON. It doesn't do anything if you resolve with an object.
* [JSON on IE8? Nope][stackoverflow 10]
* AJAX on IE? Nope. Need to use `this.response || this.responseText` for any AJAX objects made.
* [Dispatching keyboard events without jQuery][stackoverflow 11]
* Clone an array: [`arr.slice(0)`][stackoverflow 12]
* [Marionette's UI hash][github 2] keeps references to UI elements; `this.ui.checkbox` anywhere in any method means `this.$(the checkbox selector`. This has no use for regions, whose elements are already defined using selectors.
* Apparently [$.Deferred is a monad][voisen].
* There's a [Promises 2.0][msdn], but who uses it?
* >Note that the `bower_components` folder would normally be installed in the root folder but (angular-seed) changes this location through the `.bowerrc` file. Putting it in the app folder makes it easier to serve the files by a webserver.
* Placing `"scripts": { "postinstall": "bower install" }` in `package.json` (npm) installs `bower_components` right after npm finishes.
* `EADDRINUSE` is node's very polite way of saying "port is taken".
* [Promises are streams][github 3].
* `$.fn.not` is [**not** the opposite of `$.fn.is`][ajpiano] -- `$.fn.not` always gives you a truthy return.
* `(An error).stack` gives you the stack.
* Jinja2 and AngularJS template tags can conflict, which prevents Jinja2 from rendering the page. [Solution][blogspot] is to override Jinja2's settings with some other tag: `JINJA_ENVIRONMENT=jinja2.Environment( loader=jinja2.FileSystemLoader(os.path.dirname(__file__)), extensions=['jinja2.ext.autoescape'], variable_start_string='((', variable_end_string='))', autoescape=True)` (I think it's a bit hacky, however)
* **NaCl** in tech usually stands for **Na**tive **Cl**ient.
* `"use strict";` in global scope affects the entire script file, but not other scripts on the page.
* To generate revisions of assets, you might need [gulp-rev][npmjs] (see also: the "Works with gulp-rev" section)
* `npm` has a [dedupe](https://www.npmjs.org/doc/cli/npm-dedupe.html) option that groups common dependencies higher up the dependency tree.
* Use `bower` in place of npm for client side packaging to [avoid multiple versions of the same library sent to the client](http://stackoverflow.com/a/18652918).
* [`{} + {}`](http://stackoverflow.com/a/9033306/1558430), when run as-is, is the addition of an [empty block](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/block) and an empty object. While two empty objects added together is `[object Object][object Object]`, because empty blocks are not empty objects (and it is entirely up to the interpreter and [the spec](http://www.ecma-international.org/ecma-262/5.1/#sec-12.1) to decide which one it is), the explicit construction of objects matters (`(a = {}) + {}` is adding two objects, for example)
* Relatedly, *blocks* (`{...}`) are mere syntax for command groups. The `if` statement executes anything after it, which is either a single command, or a block, which is a group of commands.
* node has a [debugger](http://nodejs.org/api/debugger.html). To use it, run `node debug` where you normally run `node`.
* "[Every function in Node.js is asynchronous](http://code.tutsplus.com/tutorials/node-js-for-beginners--net-26314)", even the ones that are normally blocking.
* `npm ls` lists installed packages.
* Angular has a [`copy` that does deep copy](https://docs.angularjs.org/api/ng/function/angular.copy). But would you trust it?
* `list[list.length] = 5` *is* faster than `list.push(5)`, but [the gap is closing](http://jsperf.com/array-push-vs-index-push webtricksandtreats.com/javascript-array-push/)
* [Webpack](https://github.com/webpack/webpack) is browserify for AMD modules. (more accurately, it is the other way around.)
* Because [object keys are always toString'd](https://mathiasbynens.be/notes/javascript-properties), `{ .12e3: 'wut' }` can be retrieved using the key `120`.
* Assigning `someArray.length = 0` removes all items from the array. You can also assign other numbers, and if the array length goes from 0 to e.g. 3, the array is `[undefined, undefined, undefined]`.
* jQuery has a `$.fn.queue(function () { ... })` that is called whenever something gets dequeued, presumably because an operation is done.
* [The spec](http://stackoverflow.com/questions/13294658/throw-errormsg-vs-throw-new-errormsg) allows `throw Error()` as well as `throw new Error()`. The two are identical.
* javascriptkit.com still exists.
* `(new Date).getYear()` returns 115 for year 2015. To get 2015 instead of something useless, call `getFullyear()` instead.
* It is possible to give properties to a boolean, but because it has no prototype, it is impossible to read them again.

```
>var a = true
>a.foo = 'bar'
>a.foo
undefined
>true.prototype
undefined
```

* [Generators](http://www.2ality.com/2015/03/es6-generators.html) (good article) must be called `function*`s, with that ugly asterisk after the keyword. 
* To provide fallback URLs for a library you reference, just [change its path to a list of paths](http://stackoverflow.com/a/12075285/1558430).
* `$('#password').val()` works on Firefox's autocompleted password fields!
* The square brackets in `@param {type} [thing]` mean optional parameter in JSDoc.
* In addition to the public/private use distinction, ["a deferred (which generally extends Promise) can resolve itself, while a promise *might* not be able to do so."](http://stackoverflow.com/a/6824836) (emphasis mine/yours)
* (and) *Futures* are deprecated implementations of Promises.
* [Shebangs are permitted in server-side `.js` files](http://stackoverflow.com/questions/10696222/how-to-make-javascript-support-shebang) run by nodejs or js.
* You know how you can't just pass `console.log` as a function? Use [`console.log.bind(console)`](http://stackoverflow.com/questions/6789689/javascript-abstract-console-logging) instead.
* [`\S` is negated `\s`](http://stackoverflow.com/questions/4377480/what-does-this-s-regex-mean-in-javascript) (so anything but whitespaces)
* Depending on which browser version you have, you can already do these: `a = () => 'bar'`, `a = function() 'bar'`.
* You can't `angular.copy` an HTML5 `Geoposition` object. It will lose all coordinate information.
* Adding a [label](https://www.reddit.com/r/javascript/comments/3cxkex/til_you_can_break_continue_to_a_label/) on top of a do/for/while loop allows `break` statements to specify how many levels to break, much like PHP's `break n`.
* [Setting any `window.onunload` handler](http://stackoverflow.com/questions/2638292/after-travelling-back-in-firefox-history-javascript-wont-run) forces javascript to be re-run when the page is loaded from a back button.
* Changing any part of `window.location` (e.g. `window.location.search = ''`), understandably, navigates away from the current location.
* MDN: ["When defining a variable that is meant to later hold an object, it is advisable to initialize the variable to null as opposed to anything else. That way, you can explicitly check for the value null to determine if the variable has been filled with an object reference at a later time."](http://stackoverflow.com/a/13143055/1558430)
* [Since Cordova 5.0.0](http://stackoverflow.com/a/30028686/1558430), [apps must declare `Content-Security-Policy`](https://github.com/apache/cordova-plugin-whitelist/blob/master/README.md) in order to go online.
* [HTTP PATCH](https://tools.ietf.org/html/rfc5789) is not meant to accept parts of an object; instead, it accepts a list of [JSON operation object](http://williamdurand.fr/2014/02/14/please-do-not-patch-like-an-idiot/) describing actions to be taken on the server, e.g. `PATCH /users/123 [{ "op": "replace", "path": "/email", "value": "new.email@example.org" }]` (replaces user 123's email to that.)
* The "e" in "yeoman" is silent. Probably why Yeoman is called "yo".
* Relatedly, if "bower" came from "[bowerbird](https://en.wikipedia.org/wiki/Bowerbird)", then bower is homophonous with "bauer", technically a German word.
* [`switch` is in fact coersion-safe](http://stackoverflow.com/questions/6989902/is-it-safe-to-assume-strict-comparison-in-a-javascript-switch-statement).
* Jasmine has both [`createSpy` and `createSpyObj`](http://stackoverflow.com/questions/24321307/what-is-the-difference-between-createspy-and-createspyobj). The former gives a function; the latter is an object with methods.
* `npm install linux` is [finally possible](http://hyperos.io/), thanks to HyperCore Linux.
* Lodash's `_.curry()` allows the use of itself as placeholders. `_.curry(func, _, 'foo')` curries `func` with the second argument specified.
* Assigning a property to `"a string"` and expecting it not to persist is [all well and good](http://stackoverflow.com/questions/5201138/why-cant-i-add-properties-to-a-string-object-in-javascript), but only AngularJS throws an Error when you do it. In other cases, the property simply reads `undefined`.
* You can `throw` anything. You can even `throw 'Hi';`. The argument given to the `catch` block is exactly what was thrown.
* Douglas Crockford is [actually a moron](https://github.com/douglascrockford/JSLint/commits/master).
* Running just `karma start` without `--single-run` predictably runs karma whenever a file is changed.
* `String(null)` works; `null.toString()` doesn't.
* [ALWAYS](http://blog.heroku.com/archives/2015/11/10/node-habits-2016) make an `.npmrc` that sets `save=true` and `save-exact=true`.
* [`includes()` rather than `contains()`](http://www.2ality.com/2015/11/tc39-process.html?m=1), because MooTools, apparently. Incidentally, `[NaN, NaN].indexOf(NaN)` never finds any, and `includes()` does.
* > [sessionStorage is just like localStorage, but it's local to the tab](https://github.com/mozilla/localforage/issues/2#issuecomment-27452423), so if you have two tabs on the same site they won't see each other's sessionStorage. [Opening a page in a new tab or window will cause a new session to be initiated.](https://developer.mozilla.org/en/docs/Web/API/Window/sessionStorage)
* TypeScript had the audacity to create a `void` type, which is `null ∪ undefined`.
* The modulo operator (`%`) does not do type checking. So, in an interesting way, one can write `"Hello %s" % "world"` in JS as if it does something, but in fact simply creating a `NaN`.
* [`n`](http://askubuntu.com/questions/426750/how-can-i-update-my-nodejs-to-the-latest-version) is the npm package that upgrades nodejs.
* For supporting the delusional "more choices is better" ideology, [npm allows its JS engine to be swapped out](http://www.marcusoft.net/2015/03/packagejson-and-engines-and-enginestrict.html) using either `engines` in `package.json`, or [an `.npmrc` file](http://blog.npmjs.org/post/110924823920/npm-weekly-5) that does the same.
* `karma start --reporters dots,coverage` runs `karma` without the annoying long list of successes.
* JS Dates can be [invalid](http://stackoverflow.com/questions/1353684/detecting-an-invalid-date-date-instance-in-javascript). They are invalid if you add like a billion years to it, or the 30th of February, such that `isNaN(dateObj.getTime()) === true` (except in IE8, which [does not work](http://stackoverflow.com/questions/13878515/javascript-valid-date-checking-does-not-work-in-ie8-and-firefox) ).
* [There are no leap seconds](http://www.ecma-international.org/ecma-262/5.1/#sec-15.9.1.1).
* Calling [`url = URL.createObjectURL(blobOrFile)`](https://developer.mozilla.org/en/docs/Web/API/URL/createObjectURL) and opening it (either through `window.open` or some link-clicking means) will allow a file to be downloaded. Afterwards, remember to call `URL.revokeObjectURL(url)`
* [Karma is for testing client code only](http://stackoverflow.com/questions/16660670/how-to-test-nodejs-backend-code-with-karma-testacular),
* Replacing `it(...)` with `fit(...)` in a karma test suite will skip all tests except those marked with `fit`.
* No special case: `'yes' === 'yes' === 'yes'  // false`
* `_.curry`  returns a value only when all arguments are specified (so you can go `foo(1)(2)(3)` for a 3-argument function). `_.partial` is a single-layer wrapper.
* [Bower is dead](https://github.com/reactjs/redux/issues/944#issuecomment-154858804) because either bower fragments client/server libraries, or because people don't know how to resolve multiple-version dependencies with npm. I don't, for one.
* `fetch`ing with `mode: 'no-cors'` apparently [makes the request, but does not tell the client whether it succeeded or failed](http://stackoverflow.com/a/40182952/1558430).
* `bind()` is literally partialling, except maybe powerful. `console.log.bind(console, 'hello world').bind(console, 'eh')()` logs `hello world eh`.
* [`$.type()`](http://api.jquery.com/jQuery.type/) will tell you what type something is, including... object vs array/regexp/date/error.
* For some reason, [synchronous AJAX is allowed on window unload.](https://stackoverflow.com/questions/1821625/ajax-request-with-jquery-on-page-unload)
* [Try to be explicit](https://blog.scottnonnenberg.com/hard-won-lessons-five-years-with-node-js/) when it comes to imports. Finding usages of `foo.bar()` is much harder than `require('bar')`.
* [Web workers don't run if the procotol is file://.](https://stackoverflow.com/questions/21408510/chrome-cant-load-web-worker)
* If you `a = function () {}`, the function's name will be `a` (not sure why, but there you go.) If you `a = function b() {}`, the function's name will be `b`. If you `(function () {}).name`, that is an empty string. If you `(function (a) { console.log(a.name) }(function () {}))`, you will end up printing an empty string, but return undefined.
* `<!--` are intentionally allowed as comment markers in JS. [It is part of the spec.](https://github.com/denysdovhan/wtfjs#html-comments-are-valid-in-javascript) To get fired, you need to insert a space in between your mental gymnastics, like so: `if (5 < !--i) { ... }`
* To `apply` a constructor, you [need](https://stackoverflow.com/questions/1606797/use-of-apply-with-new-operator-is-this-possible) to `new (Function.prototype.bind.apply(Foo, [null, a, b, c]));`
* `new RegExp(/already a regexp literal/)` can still be useful if you want to [add a flag to it](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/RegExp), like `new RegExp(/already a regexp literal/, 'i')`.
* `clobber: true` when using `fs.copy` or `copySync` would overwrite the destination file if it exists. The term [clobber](https://stackoverflow.com/a/9392784/1558430) might have come from `cp`, where `cp -n` has a man page saying "do not overwrite an existing file (overrides a previous -i option)".
* "Node JS" pronunciations [include](https://groups.google.com/forum/#!msg/nodejs/-d5LcWlQrxI/CarozdtVP3MJ) Node Jay Ess (commonly), No der Jay Ess, and most importantly, Node Dot Jizz.
* Use `Object.prototype.hasOwnProperty.call(obj, prop)` instead of `obj.hasOwnProperty`, [because](https://stackoverflow.com/a/12017703/1558430) anyone can define a `hasOwnProperty` on an object.

## Deferred API

* `$.when(<Deferred, Promise, or any object really>, another, another...) => <Promise>`
* `<Deferred>.then(done, fail, progress)`
* `<Deferred>.done(function, function, ...)`
* `<Deferred>.always(function, function, ...)`
* `<Deferred>.fail(function, function, ...)`

## [Promise API](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Promise)

* An executor is `function(resolve, reject) { ... }`
* A *Promise* is `new Promise(executor);`
* `Promise.all([Promise, Promise, ...]) => <Promise>`
* If all promises in a `.all()` succeed, the call is resolved with an *array* of their resolves.
* If any promise in a `.all()` fails, the entire call fails. The error in the `.catch()` is the error from the first failed call.
* `Promise.race([Promise, Promise, ...]) => <Promise>`  aka `Promise.any` if it existed
* `Promise.resolve(value) => <Promise>`, `Promise.reject(value) => <Promise>` that are pre-resolved/pre-rejected
* `<Promise>.then(function succeed, function fail) => <Promise>`  If any of these functions return anything, [the new promise will resolve/reject with their return values.](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/then)
* `<Promise>.catch(function error)`  If any of `(succeed, fail)` throws an Error, [the `function error` will receive the same Error.](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/catch)

## WebRTC

* Feeling evil? Great! WebRTC allows you to [get the user's internal IP](http://stackoverflow.com/questions/391979/how-to-get-clients-ip-address-using-javascript-only/32841164#32841164), track people without [having the network request show up on the network panel](http://www.imanevilblogger.net/tag/disable-webrtc/), take [pictures of heads](http://auduno.com/post/25125149521/head-tracking-with-webrtc) (?), and more!

## [Writing memory-efficient JavaScript][smashingmagazine]

* Dereferencing (`delete object.key`) does not free memory immediately, but it does take CPU to modify the object, so use sparingly.
* Setting something to `null` does not null the object; it merely sets the reference to `null`, which does not free memory immediately.
* Global objects are never garbage-collected.
* Function-scoped variables are cleaned up when it can no longer be reached (like, if it stays inside the function).
* Unbind event listeners when they're no longer used. This is not done automatically -- you need to keep track.
* Functions that return functions can never be garbage-collected, because the reference to the inner function can be called.
* (However,) any variables no longer used in the function that returns a function will be garbage collected in some cases (V8).
* Anything referenced by timers (`setTimeout` or `setInterval`) will not be garbage collected.
* Try-catches will cause V8 to cancel optimization.
* Don't write large functions; they are hard to optimize (both by humans and engines)
* To store many things of the same type (e.g. Number, String, ...) use an Array, because they are faster to iterate over [than objects with integer keys].
* Sparse arrays (most values are 0) are [slower on V8 than full arrays][jsperf].
* [Except in Safari][jsperf 2], never pre-allocate arrays.
* Avoid element reflowing/redrawing (but this is more of a DOM thing rather than JS)
* Trig (`sin`, `cos`) is [*MUCH slower*](http://jsperf.com/sin-cos-vs-sqrt) than `sqrt`, in cases where the former is applicable.
* Consider WebAssembly, which is "closer to binary". Files are also sent as binary rather than text, which is faster to load.

## [Lesser console methods](http://www.mitchrobb.com/chromes-console-api-greatest-hits/)

* `console.assert(true, 'This text will never be displayed');`
* `console.dir(object)  // contents may change as code executes`
* `console.group()  // starts a group (groupCollapsed starts a collapsed group)`
* `console.groupEnd() // ends a group`
* `console.table(objOfObjs, listOfKeys)  // prints out a table of these things`

## [Riot.js](https://muut.com/riotjs/)

* Missed the headline. Riot is a UI library, not an MVC framework.
* Digest cycles are manual. You can change attributes in an element's mounting options all you like, but it will get updated only when the next time any of the tag's internal methods are run.
* Nested tags do not need to be mounted. They also don't work properly (e.g. adding extra elements onto the page) if they are mounted.
* Nested tags seem to inherit scopes implicitly, with `this.parent` always being the parent tag. Not sure if it is possible to have isolate scopes yet.
* There are things that Riot cannot do, like AJAX; the docs recommend using jQuery, and then [`trigger()`ing an observable()](https://muut.com/riotjs/guide/#example-riot-application-de).
* Putting a `debugger` statement somewhere in Riot tags does trigger the debugger, where the current `this` is some Riot object; however, it cannot direct the debugger to the correct line of execution.

## Node

* [Assigning anything to `process.env`](http://stackoverflow.com/questions/42170365/how-do-i-remove-a-value-in-process-env), even if it is `null` or `undefined`, converts it to their strings `"null"` and `"undefined"`. To delete a key from `process.env`, `delete` it.
* If you run `--save-exact` without `--save`, it doesn't save.
* Semver's `~` upgrades to any patch version. `^` upgrades to any minor version. npm stopped defaulting to the tilde because it assumes minor versions are all compatible with each other. In the real world (where npm is used), this is false.
* [Jeremy Ashkenas on semantic versioning](https://gist.github.com/jashkenas/cbd2b088e20279ae2c8e): *"SemVer tries to compress a huge amount of information — the nature of the change, the percentage of users that will be affected by the change, the severity of the change, into a single number." "SemVer is a false promise that appeals to many developers — the promise of pain-free, don't-have-to-think-about-it, updates to dependencies. But it simply isn't true." "It's alright for robots, but bad for us."*
* `0.1 + 0.2 = 0.30000000000000004` (over). `0.7 + 0.2 = 0.8999999999999999` (under).

### Webpack

* The correct usage is `webpack your/index.js dist/bundle.js`. Just make sure you have one of those and you're good to go. Alternatively, make yourself a `webpack.config.js`, and run `webpack (--config webpack.config.js)` again. Also fine.

[ajpiano]: http://ajpiano.com/the-opposite-of-jquerys-is-method-is-not-not-it-is-is/
[angularjs]: http://angularjs.org/
[backbonejs]: http://backbonejs.org/#FAQ-mvc
[blogspot]: http://zhangyelei.blogspot.ca/2013/10/variable-placeholder-conflict-between.html
[ejohn]: http://ejohn.org/blog/degrading-script-tags/
[github]: http://kangax.github.io/nfe/
[github 2]: https://github.com/marionettejs/backbone.marionette/blob/master/docs/marionette.itemview.md#organizing-ui-elements
[github 3]: https://gist.github.com/staltz/868e7e9bc2a7b8c1f754#request-and-response
[google]: https://docs.google.com/a/willetinc.com/presentation/d/1wUVmf78gG-ra5aOxvTfYdiLkdGaR9OhXRnOlIcEmu2s/pub?start=false&loop=false&delayms=3000#slide=id.g31ec7af_0_58
[google 2]: https://developers.google.com/analytics/devguides/collection/gajs/eventTrackerGuide#Anatomy
[jsperf]: http://jsperf.com/sparse-arrays-vs-full-arrays
[jsperf 2]: http://jsperf.com/pre-allocated-arrays
[microsoft]: http://msdn.microsoft.com/en-us/library/ie/0bwt76sk\(v=vs.94\
[mobify]: http://www.mobify.com/blog/css-sprites-vs-data-uris-which-is-faster-on-mobile/
[mozilla]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/defineProperty?redirectlocale=en-US&redirectslug=JavaScript%2FReference%2FGlobal_Objects%2FObject%2FdefineProperty
[mozilla 2]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Typed_arrays/Int32Array
[mozilla 3]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/with
[msdn]: http://blogs.msdn.com/b/rbuckton/archive/2011/08/15/promise-js-2-0-promise-framework-for-javascript.aspx
[npmjs]: https://www.npmjs.org/package/gulp-rev
[quirksmode]: http://www.quirksmode.org/dom/events/scroll.html
[raganwald]: http://raganwald.com/2013/03/28/trampolines-in-javascript.html
[smashingmagazine]: http://www.smashingmagazine.com/2012/11/05/writing-fast-memory-efficient-javascript/
[stackoverflow]: http://stackoverflow.com/a/4689033
[stackoverflow 10]: http://stackoverflow.com/a/4715399/1558430
[stackoverflow 11]: http://stackoverflow.com/a/5920206/1558430
[stackoverflow 12]: http://stackoverflow.com/questions/5024085/whats-the-point-of-slice0-here
[stackoverflow 2]: http://stackoverflow.com/questions/1713771/how-to-detect-page-zoom-level-in-all-modern-browsers
[stackoverflow 3]: http://stackoverflow.com/a/5971668/1558430
[stackoverflow 4]: http://stackoverflow.com/a/1204386/1558430
[stackoverflow 5]: http://stackoverflow.com/questions/3309516/when-to-use-self-in-javascript
[stackoverflow 6]: http://stackoverflow.com/questions/3660577/are-any-javascript-engines-tail-call-optimized
[stackoverflow 7]: http://stackoverflow.com/questions/19281820/deserialization-of-partially-flattened-json/19281911?noredirect=1#19281911
[stackoverflow 8]: http://stackoverflow.com/questions/20075938/jquery-each-to-iterate-over-a-string-in-newer-versions
[stackoverflow 9]: http://stackoverflow.com/a/3082878/1558430
[voisen]: http://sean.voisen.org/blog/2013/10/intro-monads-maybe/
[wikipedia]: http://en.wikipedia.org/wiki/JSON#JavaScript_eval.28.29
[zurb]: http://foundation.zurb.com/docs/upgrading.html
