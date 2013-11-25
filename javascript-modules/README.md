# Understanding JavaScript Modules

JavaScript modules enable modular programming techniques through code
patterns in JavaScript.  Functionality is encapsulated in independent,
interchangeable modules, each contained in a separate file.

The closest analog in the Java language are Java Classes.  However,
JavaScript modules can be of any type.  The most common module types
are object literals, functions, and constructors.

Despite expectations that ECMAScript, the JavaScript standards body,
will ratify the specification for JavaScript modules in EcmaScript 6 (Es6)
by the end of 2014, production use of them will likely not be feasible
until 2016 due to long upgrade cycles of browsers and operating systems.

In the mean time, several *de facto* module patterns have evolved.
Asynchronous Module Definition (AMD) is the most popular for client-side
code, while node.js modules (an extension to CommonJS Modules/1.1)
is the leading pattern in server-side environments.  Universal Module
Definition (UMD) attempts to bridge the differences, allowing
engineers to author their code bases in a single format, rather than
author in or convert to AMD and node formats.

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
of module ids and a factory function.

At run time, the AMD environment ensures that the modules named in the
array, the dependencies, are available before providing the depenencies'
exports as parameters to the factory function.  The
factory function may use the module's exports to produce its own
exports, which it must return from the factory function.

The factory function may export any JavaScript type, but typically
developers export objects, functions, and constructors.  Exporting
HTML templates or CSS stylesheets as strings is also common.

Because AMD fetches dependencies before evaluating the factory function,
it is well suited to browser environments where modules may be remote.

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
variables: `require`, `exports`, and `module`.

The `require` function is used to import other modules' exports by id.
The module reveals its own exports by assigning them as properties
of the `exports` object.  The `module` object provides meta data about the
current module.

Notice that the node.js code snippet doesn't use an `exports` object.
Instead, it assigns a value to `module.exports`.  The CommonJS proposal
does not specify `module.exports`; it is a node.js extension to better
support existing patterns.  `module.exports` allows a module to appear to
other modules as a single function or constructor, rather than as an object.
Modules that do this are called "function-modules" and "constructor-modules"
respectively.

Since node.js supports `exports`, as well, it is compatible with
strictly conforming CommonJS modules.

## ES6 modules

```js
import { load } from 'store/customer';
import when from 'when';

export default = function (id) {
    return when(id).then(load);
};
```

EcmaScript 6 modules use the reserved keywords `import` and `export`.

`import` is used to bind one of more exported variables in another module
into the current module's scope.  The bound variables are listed inside
curly braces and may be mapped to other names.  To bind a module's default
export, often an object that exposes the other exports as properties,
omit the curly braces.

The `export` keyword performs two operations.  It instructs the environment
that a variable is to be exported, but it also declares the variable just
like a `let` statement.














The `require`
function returns another module's exports immediately, blocking
the JavaScript engine's main thread.  Systems that provide client-side
CommonJS Modules must ensure that all potentially
needed modules are available before `require` is called.






Why?
    - "Imagine if Java had no import statement, and all class names were in the default package…"
        - Brian


Address packages in the package manager doc?
