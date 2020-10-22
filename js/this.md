# Trying to understand

'this' keyword


CASES						'this'
default

	browser		  		window object

	node		  		global object

	'use strickt'	 	undefined

	function			window/object/undefined

	method				object

	constructor			instance


## Execution Context

Execution Context (EC) is defined as the environment in which the JavaScript code is executed.
Environment has following things
- `this`
- variables
- objects
- function

Three Type of execution context

1. Global Execution Context (GEC)
2. Functional Execution Context(FEC)
3. Eval

## Global Execution Context (GEC)

This is the default execution context. When first javascript file loads it starts in Gloabl Execution Context. Any code which is not inside any function is executed in Global execution context. 

GEC can not be more than one because JavaScript engine is single threaded.


## Function Execution Context (FEC)

FEC get created by JavaScript engine whenever it finds any function call. Each function has its own execution context. 

- Unlike Global Execution context FEC can be more than one.
- FEC has access to GEC (Gloabl Execution Context) but GEC doesn't
- JavaScript create new FEC when it find a function call.

## Execution Context Stack

 Execution context stack is a stack data structure, i.e. last in first out data structure, to store all the execution stacks created during the life cycle of the script. Global execution context is present by default in execution context stack and it is at the bottom of the stack. While executing the global execution context code, if JS engines find a function call, it creates a functional execution context for that function and pushes it on top of the execution context stack. JS engine executes the function whose execution context is at the top of the execution context stack. Once all the code of the function is executed, JS engines pop out that function’s execution context and start’s executing the function 

## Creation of Execution Context

JavaScript Engine create the execution context in two stages :

1. Creation Phase
2. Execution phase


### Creation Phase
Phase in which the JS engine has called a function but its execution has not started. In the creation phase, JS engine is in the compilation phase and it just scans over the function code to compile the code, it doesn't execute any code

In this phase, JS engine performs the following tasks:

1. Creates the Activation object or the Variable Object
2. Creates the scope chain
3. Determines the value of this


## Finish It........