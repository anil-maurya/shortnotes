# Modules in JavaScripts

A module is a reusable piece of code that encapsulates implementation details and exposes a public API so it can be easily loaded and used by other code.


A module is just a file. One script is one module. As simple as that.

Modules can load each other and use special directives `export` and `import` to interchange functionality, call functions of one module from another one

* `export` keyword labels variables and functions that should be accessible from outside the current module.
* `import` allows the import of functionality from other modules.





Veriiety of ways to orgganize code into modules.

- AMD (Asynchronous module definition)
- UMD -  one more module system, suggested as a universal one, compatible with AMD and CommonJS.
- CommonJS - The module system created for Node.js server
- ES6 Modules (JavaScript Modules/ECMAScript Modules)


## Why Modules ?


## Feature of Modules


## Creating Modules

### Named exports(several per module)

```js
// -----------------Lib.js--------------
export const sqrt = Math.sqrt;
export function square(x) {
	return x * x;
}

export function dialog(x, y){
	return sqrt(square(x) + square(y));
}


// Using named export 

// --------- main.js--------------

import {square, dialog} from 'lib';

// We can also do that

import * as lib from 'lib';

```


### CommonJS syntax for Named exports

For more read in nodejs-modules

```js

// -------lib.js--------
var sqrt = Math.sqrt;

function square(x){
	return x * x;
}

function diag(x, y){
	return sqrt(square(x) + square(y));
}

module.exports = {
	sqrt: sqrt,
	square: square,
	diag: diag
}

// ----------- Main.js---------

var square = require('lib').square;
var diag = require('lib').diag;

console.log(square(11)); //121
console.log(diag(4, 3)) //5

```

### default export (one per module)
Default exports can be done in 2 ways

1. default exporting values directoly
2. labeling declartion

```js
// ------- myFunc.js-----------------

export default function() {} //no semicolon!

//------ Main.js------------

import myFunc from 'myFunc';
myFunc();

```

### Default export class


```js
// ------ MyClass.js--------

export default class {} //no Semicolon!

// -------- main2.js-----------

import MyClass from 'MyClass';
const inst = new MyClass();

````

### Labeling declaration

```js
export default function foo() {} // No semicolon
export default class Bar {} //No semicolon

```

Note -  variable declarations can’t be meaningfully turned into default exports if they declare multiple variables:

```js

export default const foo = 1, bar = 2, baz = 3; // not legal JavaScript!

```


## Imports and exports must be at the top level

 the structure of ES6 modules is static, you can’t conditionally import or export things. That brings a variety of benefits.

This restriction is enforced syntactically by only allowing imports and exports at the top level of a module:


```js
if (Math.random()) {
    import 'foo'; // SyntaxError
}

// You can’t even nest `import` and `export`
// inside a simple block:
{
    import 'foo'; // SyntaxError
}

```

## imports are hoisted

Module imports are hoisted (internally moved to the beginning of the current scope). Therefore, it doesn’t matter where you mention them in a module.


```js

foo();

import { foo } from 'my_module';

````

## imports are read-only views on exports
The imports of an ES6 module are read-only views on the exported entities. That means that the connections to variables declared inside module bodies remain live, as demonstrated in the following code.

```js
//------ lib.js ------
export let counter = 3;
export function incCounter() {
    counter++;
}

//------ main.js ------
import { counter, incCounter } from './lib';

// The imported value `counter` is live
console.log(counter); // 3
incCounter();
console.log(counter); // 4

```

Note - Important to remember when imported function doesn't execute it is being assiged to variable.


## Support for cyclic dependecies

Two modules A and B are cyclically dependent on each other if both A (possibly indirectly/transitively) imports B and B imports A. If possible, cyclic dependencies should be avoided, they lead to A and B being tightly coupled – they can only be used and evolved together.

```js
//------ a.js ------
import {bar} from 'b'; // (i)
export function foo() {
    bar(); // (ii)
}

//------ b.js ------
import {foo} from 'a'; // (iii)
export function bar() {
    if (Math.random()) {
        foo(); // (iv)
    }
}
```

This code works, because, as explained in the previous section, imports are views on exports. That means that even unqualified imports (such as bar in line ii and foo in line iv) are indirections that refer to the original data. Thus, in the face of cyclic dependencies, it doesn’t matter whether you access a named export via an unqualified import or via its module: There is an indirection involved in either case and it always works.


### Importing styles

1. default import

`import localName from 'src/my_lib';`

2. Namespace import 

`import * as my_lib from 'src/my_lib';`

3. Named imports

`import {name1, name2} from 'src/my_lib';`

5. Rename named imports

`import {name1 as localName, name2} from 'src/my_lib';`

6. Compibing imports

`import theDefault, * as my_lib from 'src/my_lib';`

`import theDefault, {name1, name2} from 'src/my_lib';`


### Exporting styles

1. inline e
2. exporting all at once

#### Inline exporting

```js
export var myVar1 = ···;
export let myVar2 = ···;
export const MY_CONST = ···;

export function myFunc() {
    ···
}
export function* myGeneratorFunc() {
    ···
}
export class MyClass {
    ···
}
```

#### Named exporting 
```js
// Exporting all at once

const MY_CONST = ···;
function myFunc() {
    ···
}

export { MY_CONST, myFunc };
export { MY_CONST as FOO, myFunc };
export { foo as default };

```
#### Default export

```js
export default function myFunc() {}
  export default function () {}

  export default function* myGenFunc() {}
  export default function* () {}

```
#### Re-exporting

Re-exporting means adding another module’s exports to those of the current module.

```js
export { foo, bar } from 'src/other_module';

// Renaming: export other_module’s foo as myFoo
export { foo as myFoo, bar } from 'src/other_module';

```

## Using Modules (Integration)

Using modules in browser. To use modules in browser we must pass 

`type="module"` in `<script></script>` tag

Other wise we get  : `cannot use import statement outside a module` error

```html

<script type="module" src="modules/main.js"></script>

````



## <script> tag in JavaScript


1. Script tags are executed in the order they appears

By default <script type="text/javascript"></script> is blocking in nature. 

Elements on the page won't render untill all the scripts tags preceding them have loaded and executed.


To Control script tag HTML5 has added a couple tool
### async (partial non blocking)

async attribute make fetching of script asynchronous, It doesn't block parsing of html while scrpt is being fetched. But as soon as script is available, html parsing stops and script get executed and then html parsing.

oreder of execution may change.


### defer (Non blocking at all)

in case of defer script get fetched asynchronously and script get executed after html parsing is done completely.

So execution order of defer tag is fixed it will not change.


### type attribute

- ommited or a JavaScript MIME type.

This indicates the script is JavaScript. The HTML5 specification urges authors to omit the attribute rather than provide a redundant MIME type.

- `module` 
Causes the code to be treated as a JavaScript module.

### integrity attribute

This attribute contains inline metadata that a user agent can use to verify that a fetched resource has been delivered free of unexpected manipulation

### crossorigin atrribute

Normal script elements pass minimal information to the window.onerror for scripts which do not pass the standard CORS checks. To allow error logging for sites which use a separate domain for static media, use this attribute. See CORS settings attributes for a more descriptive explanation of its valid arguments.


## for/event

## NOSCRIPT
```html
<noscript>
  Please use Internet Explorer 5.5 or above.
</noscript>
<script>
  exploitInternetExplorer0Day();
</script>
```


## Bundling and transpiling


 https://www.sitepoint.com/javascript-modules-bundling-transpiling/



## Tree shaking

 When we import and export modules in JavaScript, most of the time there is unused code floating around. Tree shaking or dead code elimination means that unused modules will not be included in the bundle during the build process.

Tools like webpack will detect dead code and mark it as “unused module” but it won’t remove the code. Webpack relies on minifiers to cleanup dead code, one of them is UglifyJS plugin, which will eliminate the dead code from the bundle.


