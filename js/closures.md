# Closures & Lexical Scoping


## Contents
1. Lexical Scoping
2. Closures


**Short Definitions**

Lexical scoping means variables defined in upper/outer scope are automatically available in inner scope. We need not to pass it.


## Lexical Scoping

```js

function init() {
  var name = 'Mozilla'; // name is a local variable created by init
  function displayName() { // displayName() is the inner function, a closure
    alert(name); // use variable declared in the parent function
  }
  displayName();
}

init();


//
let name = "Anil"

function fn(){
    console.log(name)
}

fn()

```

init() creates a local variable called name and a function called displayName(). The displayName() function is an inner function that is defined inside init() and is available only within the body of the init() function. Note that the displayName() function has no local variables of its own. However, since inner functions have access to the variables of outer functions, displayName() can access the variable name declared in the parent function, init().


"Nested functions have access to variables declared in their outer scope."



## Closure

a closure gives access to an outer function’s scope from an inner function. In JavaScript, closures are created every time a function is created, at function creation time.

'''To understand - if outer functions variable is used in inner function then in inner function it is known as closure.' We can check by using `console.dir(innerFunc)`. In [[Scopes]] there is a 'Closure' array. If this variable get updated then value in inner function is also updated. See Example 3


```js

function makeFunc() {
  var name = 'Mozilla';
  function displayName() {
    console.log(name);
  }
  return displayName;
}

var myFunc = makeFunc();

myFunc();


```


At first glance, it might seem unintuitive that this code still works. In some programming languages, the local variables within a function exist for just the duration of that function's execution. Once makeFunc() finishes executing, you might expect that the name variable would no longer be accessible. However, because the code still works as expected, this is obviously not the case in JavaScript.

The reason is that functions in JavaScript form closures. A closure is the combination of a function and the lexical environment within which that function was declared. This environment consists of any local variables that were in-scope at the time the closure was created. In this case, myFunc is a reference to the instance of the function displayName that is created when makeFunc is run. The instance of displayName maintains a reference to its lexical environment, within which the variable name exists. For this reason, when myFunc is invoked, the variable name remains available for use, and "Mozilla" is passed to alert.


Example :

```js
function makeAdder(x) {
  return function(y) {
    return x + y;
  };
}

var add5 = makeAdder(5);
var add10 = makeAdder(10);

console.log(add5(2));  // 7
console.log(add10(2)); // 12

```

we have defined a function makeAdder(x), that takes a single argument x, and returns a new function. The function it returns takes a single argument y, and returns the sum of x and y.

In essence, makeAdder is a function factory. It creates functions that can add a specific value to their argument. In the above example, the function factory creates two new functions—one that adds five to its argument, and one that adds 10.

add5 and add10 are both closures. They share the same function body definition, but store different lexical environments. In add5's lexical environment, x is 5, while in the lexical environment for add10, x is 10


EXAMPLE 3

```js

// Print variables after some pause
function hoc(fun){
    console.log('This is hoc')
    for(let i = 0; i < 10; i++){
        setTimeout(fun, 1000 * i)
    }
}


function init(){

    let firstName = "Anil"
    let lastName = "Maurya"

    function greet(){
        console.log("Hi " + firstName + ' ' + lastName)
    }

    function updateName(name){
        firstName = name
    }

    //Start printing
    // hoc(greet)


    // return updateName

    for(let i=0; i< 10; i++){
        setTimeout(function(){
            updateName(i)
        }, 900*i)
    }

}

init()

```

EXAMPLE 

```js
function show(fn){
    console.log('This is show')
    for(let i = 0; i < 10; i++){
        setTimeout(fn, 1000 * i)
    }
}

function update(fn){
    for(let i=0; i< 10; i++){
        setTimeout(function(){
            fn(i)
        }, 900*i)
    }
}


function init(){

    let firstName = "Anil"
    let lastName = "Maurya"

    function greet(){
        console.log("Hi " + firstName + ' ' + lastName)
    }

    function changeName(name){
        firstName = name
    }

    //Start printing
    // show(greet)

    // return updateName

    // for(let i=0; i< 10; i++){
    //     setTimeout(function(){
    //         updateName(i)
    //     }, 900*i)
    // }

    return {greet, changeName}

}

let {greet, changeName} = init()

show(greet)
update(changeName)

```