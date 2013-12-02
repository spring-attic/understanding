# Understanding JavaScript Modules

JavaScript modules are the foundation of modular programming patterns in
JavaScript. The closest analog in the Java language are Java Classes.
However, JavaScript modules can be of any type.  The most common types
are object literals, functions, and constructors.

ECMAScript, the JavaScript standards body, expects to finally ratify
a specification for modules in ECMAScript version 6 by the end of 2014.
*ES6 modules*, however, will likely not be feasible to use in production
until 2016 due to the long upgrade cycles of some browsers and
operating systems.

In the mean time, two *de facto* module patterns have evolved.
Asynchronous Module Definition (AMD) is the most popular for client-side
code, while node.js modules (an extension to CommonJS Modules/1.1)
is the leading pattern in server-side environments.  Universal Module
Definition (UMD) is a set of boilerplate recipes that attempt to bridge the
differences between AMD and node.js, allowing engineers to author their
code bases in a single format, rather than author in both formats or
convert to the other format in a build step.

## Asynchronous Module Definition

```javascript
define(['store/customer', 'when'], function (customerStore, when) {
    return function (id) {
        return when(id).then(customerStore.load);
    };
});
```

An AMD environment provides a single global function, `define`.  The
`define` function has several signatures, including some that
trigger special behavior, but the simplest form accepts an array
of module ids and a factory function.  An AMD module should export
something by returning a value from the factory function.

The factory function may export any JavaScript type, but typically
developers export objects, functions, and constructors.
Modules that export functions or constructors are called
"function-modules" and "constructor-modules", respectively.
Exporting HTML templates or CSS stylesheets as strings is also common.

An AMD module may specify dependencies on other modules by listing the
dependent modules in the array of ids.  Before the factory executes,
the AMD environment ensures that the dependencies are available and
maps their exported values onto the parameter list of the factory function.

Because the AMD environment fetches dependencies before evaluating the
factory function, it is well suited to browser environments where
modules may be remote.

## node.js modules

```javascript
var customerStore = require('store/customer');
var when = require('when');

module.exports = function (id) {
    return when(id).then(customerStore.load);
};
```

The node.js environment roughly follows the CommonJS Modules/1.1 proposal,
which specifies that the environment should inject three locally-scoped
variables: `exports`, `require`, and `module`.

In CommonJS, a module exports values by assigning those values to properties
on the `exports` object.  The `require` function imports other modules'
exports by their module ids. The `module` object provides meta-data about
the current module, such as its id and uri.

Notice, however, that the node.js code snippet above doesn't use an `exports`
object. Instead, it assigns a value to `module.exports`.  `module.exports`
is a node.js extension that allows developers to export non-object values.

> **Note:** The CommonJS proposal does not specify `module.exports`;
> it is a node.js extension to better support existing patterns.
> Since node.js supports `exports`, as well, node.js is compatible with
> strictly-conforming CommonJS modules.

## ES6 modules

```js
import { load } from 'store/customer';
import when from 'when';

export default = function (id) {
    return when(id).then(load);
};
```

ECMAScript 6 modules use the reserved keywords `export` and `import`.

The `export` keyword instructs the environment that a variable is to be
exported.  It also declares the variable locally exactly like a `let`
statement would.

`import` binds one or more exported variables from another module
into the current module's scope.  The bound variables are listed inside
curly braces and the other module's id must be quoted.

Since exported values are variables, they always have a name.  However,
module authors may also specify a default exported value as a convenient
shortcut.  A module may declare up to one default export by simply naming
the exported value "default".

To import and bind to a module's default export, omit the curly braces
in the `import` statement, for example:

```js
import when from 'when';
```

> **Note:** `import` and `export` must be used at the top block scope.
> Nesting `import` or `export` inside blocks will cause the run-time
> environment to throw a SyntaxError.

## Why use JavaScript modules?

Imagine if Java had no import statement and all class names were in
the default package.
