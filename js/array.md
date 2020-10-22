# Array

JavaScript arrays are used to store multiple values in a single variable.
An array is a special variable, which can hold more than one value at a time.



## Creating Array
```js
var cars = [ "Saab", "Volvo", "BMW"];

var cars = new Array("Saab", "Volvo", "BMW");

```


- Array Elements Can Be Objects

```js
myArray[0] = Date.now;
myArray[1] = myFunction;
myArray[2] = myCars;

```


- Arays are special kind of Object.
	* arrays use numbered indexes.  
	* objects use named indexes.


- Recognize an Array

```js
let arr = [1, 2, 3, 4]

typeof arr // object

Array.isArray(arr) // true

// Constructor Function is Array()
arr.constcutor.toString() // "function Array() { [native code] }"

// Object Constrcutor
let obj = {}

obj.constcutor.toString() // "function Object() { [native code] }"
 
```


## Array Methods

### `toString()` / `join()`

The join() method also joins all array elements into a string. but in addition you can specify the separator in join.

```js

var fruits = ["Banana", "Orange", "Apple", "Mango"];

fruits.toString() // "Banana,Orange,Apple,Mango"
fruits.join() //"Banana,Orange,Apple,Mango"

// With separator

fruits.join("-") //"Banana-Orange-Apple-Mango"

fruits.join("*") //"Banana*Orange*Apple*Mango"

```
### indexOf('element')

Return fist ocurance of element. If not found returns -1

### lastIndexOf(element)

Returs last occurance of element. If not found reutns -1 

	* both accept second parameter as search start position=> start_index.
	* If second param is passed both start searching from start_index. start_index is included.
	* Returns actual index number of element in array not reltive to start_index.
Works same as on String.

### pop()

The pop() method removes last element from an array and returns the value that was "popped out" array is modified. `fruits.pop()`

### push()

The push() method adds a new element to an array (at the end) and returns new array length. `fruits.push('grapes')`

### shift()

removes the first array element and "shifts" all other elements to a lower index and returns removed elements `fruits.shift()`

### unshift("elem")
method adds a new element to an array (at the beginning), and "unshifts" older elements and returns new length.

* Updating Element `fruits[0] = 'Apple'`
* Deleting Element `delete fruits[1]`
 - delete returns true/false
 - delete leaves element and set to 'empty'.

### slice(start, end)

- slices out a piece of an array.
- if end is not passed, then end = arr.length or slices out the rest of the array.
- end is optional. 
- end is excluded. 
- Returns an arry of sliced elements. 
- Orignal array is not modified.

```js
var fruits = ["Banana", "Orange", "Lemon", "Apple", "Mango"];
fruits.slice(1, 3) //["Orange", "Lemon"]

fruits //["Banana", "Orange", "Lemon", "Apple", "Mango"]

```

### splice(start, remove_elems, "rest", "of", "elems")

	* method can be used to add new items to an array:
	* The first parameter (start) defines the position where new elements should be added (spliced in).

	* The second parameter (0) defines how many elements should be removed.

    * The rest of the parameters ("Lemon" , "Kiwi") define the new elements to be added.
    * modify orignal array.

```js

let fruits = ["Banana", "Orange", "Lemon", "Apple", "Mango"]

fruits.splice(2, 0, "Lemon", "Kiwi"); //[]

fruits //["Banana", "Orange", "Lemon", "Kiwi", "Lemon", "Apple", "Mango"]

fruits.splice(1, 2, "Batata") //["Orange", "Lemon"]

fruits // ["Banana", "Batata", "Kiwi", "Lemon", "Apple", "Mango"]

// Can be used to remove elements

fruits.splice[0, 1] // "Banana" //Remove 1 element starting at 0

fruits //["Banana", "Batata", "Kiwi", "Lemon", "Apple", "Mango"] 

```

### cancat()

* method creates a new array by merging (concatenating) existing arrays
* does not change the existing arrays. It always returns a new array.
* can take any number of array arguments
* can also take strings as arguments

```js
var arr1 = ["Cecilie", "Lone"];
var arr2 = ["Emil", "Tobias", "Linus"];
var arr3 = ["Robin", "Morgan"];
var myChildren = arr1.concat(arr2, arr3);   // Concatenates arr1 with arr2 and arr3

// string element
var myChildren = arr1.concat("Peter"); 

``` 

### find()

- method returns the value of the first element in an array that pass a test (provided as a function).

- The find() method executes the function once for each element present in the array:

	- If it finds an array element where the function returns a true value, find() returns the value of that array element (and does not check the remaining values)
	
	- Otherwise it returns undefined
	- does not execute the function for empty arrays.
	- does not change the original array.
	- Work just like filter but break on fist match

```js
const arr =  [1, 2, empty, 4, empty]

arr.find(item=>item>2) // 4 first item which is greater than 2

arr.find(item=>item>5) //undefined

````

### findIndex()

	- Works just like find but instead of returning value it reutns index of value


```js
const arr =  [1, 2, empty, 4, empty]

arr.find(item=>item>2) // 3 first item's index which is greater than 2

arr.find(item=>item>5) // -1

````

### every()

returns true only if all items passe test 

	* The every() method executes the function once for each element present in the array

	* If it finds an array element where the function returns a false value, every() returns false (and does not check the remaining values)
	
	* If no false occur, every() returns true

	* Only retuns true if all elements passes condition

	* does not execute the function for array elements without values.
	
	* does not change the original array


```js
let ages = [32, 33, 16, 40];

ages.every(item=> item > 18) // false fails on 16

ages.every(item=> item > 12) // true, all elements passes condition.

```

### some()

retun true if any element pass test

	* The some() method checks if any of the elements in an array pass a test (provided as a function).

	* The some() method executes the function once for each element present in the array:

	* If it finds an array element where the function returns a true value, some() returns true (and does not check the remaining values)
	
	* Otherwise it returns false

	* Opposite of every

	* some() does not execute the function for array elements without values.

	* some() does not change the original array.

```js

let ages = [32, 33, 16, 40];
ages.some(item=>item > 32) // true passed on 33 

```

### Array.from() 

The Array.from() method returns an Array object from any object with a length property or an iterable object.
The Array.from() static method creates a new, shallow-copied Array instance from an array-like or iterable object.

```js

// Create an Array from a String:
let myArr = Array.from("ABCDEF")

// Syntax

Array.from(object, mapFunction, thisValue)


// 
const arr = Array.from([1, 2, 3], x => x + x)

console.log(arr) // [2, 4, 6] 
```



## Sorting Array

* `sort()` : method sorts an array alphabetically, If elements are numbers then sorting will not be correct.
* `reverse()` :  method reverses the elements in an array.

* Both modifie orignal array.


```js

let fruits = ["Mango", "Lemon", "Kiwi", "Batata", "Apple", 45, "23", 2]

fruits.sort() // [2, "23", 45, "Apple", "Batata", "Kiwi", "Lemon", "Mango"]

fruits.reverse() //["Mango", "Lemon", "Kiwi", "Batata", "Apple", 45, "23", 2]

let na = [1, 2, 3, 4, "100", "5", 6]

na.sort() //[1, "100", 2, 3, 4, "5", 6]

na.reverse() //6, "5", 4, 3, 2, "100", 1]

````

### Numeric Sorting

use `compare function` with sort method


```js

var points = [40, 100, 1, 5, 25, 10];
points.sort((a, b)=>a - b);

```

compare function
	*  must return postive/negative/0 => a-b

	* a - b < 0 negative means add before
	
	* a - b > 0 then add a after b
	
	* a - b => Ascending order
	
	* b - a => Descending order

Sorting in Random order

```js

points.sort(()=> 0.1 - Math.random())

// This method works on strings array also for ovious resion
// Here start value can be anything but less than 1 in points.

```


### Finding Max

- Sort in descendingorder and get first element

```js
let points = [40, 100, 1, 5, 25, 10];

points.sort((a, b)=>b-a)[0]

````

### Finding Min
- Sort in ascending order and get first element

```js
let points = [40, 100, 1, 5, 25, 10];

points.sort((a, b)=>a-b)[0]

````


### map, reduce, filter

- map function iterate over all elements of array and returns an new array.
- reduce function iterate over all elements and passes an accumlator to callback function and finally accumalator is retured

- filter iterate over all elements and returns only elements when callback returns true. we can use this to filter elements on array

```js
 const arr = [1, 2, 3, 4] 
 const doubleArray = arr.map(item=>item*2)


 //Reduce syntax
reduce(function(accumalator, element){
	return accumalator + element
}, initial_value)

//example
const sum = arr.reduce((accum, item)=>accum + item, 0)


// filter

const newArr = arr.filter(item=>item > 0) // array of elements greater than 0


```



## iterating over elements of array

1. for loop
2. forEach
3. for-in
4. for-of


```js

let arr = ["mango", "Banana", "Apple", "Tomato"]

for (let i 0; i < arr.length ; i--) {
	console.log(arr[i])
}


arr.forEach(item=>{
	console.log(item)
})


arr.forEach((index, item)=>{
	console.log(index)
	console.log(item)
})


for (let index in arr){
	console.log(index)
}

for (let item of arr){
	console.log(item)
}
```

## When to use what

* forEach 
	- can not be break in middle
	- Only available for Arrays
	- empty elements are skipped

* for-in
	- A for-in statement creates a loop that iterates over all non-Symbol, enumerable properties of an object, sometimes in an arbitrary order.
	- It allows to access 'keys' but doesn't provide reference to values.
	- See more about enumarable below
	- although it give access keys but empty elements are skipped

* for-of
	- Introduced in ES6
	- creates a loop that iterates over iterable objects in iterable order. A common use is looping through values in an array, but it also works on most array-like objects.
	- iterate over values
	- for-of works on iterators. Mean can only used on iterables.
	- empty elements of array are returned


## Iterator
Iterators are a new way to loop over any collection in JavaScript. They were introduced in ES6.
It is an object that allows us to traverse over a list of collection. 

Specifically, an iterator is any object which implements the `Iterator Protocol` by having a next() method that returns an object with two properties 


```js

const ret = iterator.next()	{

console.log(ret) 
/*
{
  'value': Any, 
	done: Boolean 
}
*/

// Done - true have no more element 

```

## Iterable
The data structure which iterator is iterable. In javascript these are iterables

- Array
- Strings
- Maps
- Weak Maps
- Sets
- Weak Sets
- arguments - An array-like special variables in functions

Note - In javascript objects are not iterable.


## how to know if it itrable ?

Get its iterator function using Symbol.iterator property 

```js

const arr = [1, 2, 3, 4]

const iterator = arr[Symbol.iterator]()

interator.next() //{value: 1, done: false}
interator.next() //{value: 2, done: false}
interator.next() //{value: 3, done: false}
interator.next() //{value: 4, done: false}
interator.next() //{value: undefined, done: true}

```


## Generator Functions
(See More in Functions)('./functions.md')


## Enumarable Properties

Objects are collections of properties, and each property has its own set of internal properties that are not user accessible but are used by the JavaScript engine. They are denoted with double square brackets:

for-in loop on object(also array) can iterate only those key/elements whose enumarable property is set to true.


## Associative Array

Associative arrays, also called maps or dictionaries, are an abstract data type that can hold data in (key, value) pairs.

You can think of associative arrays like a list of phone numbers. In this list, you can look up a person's name by finding their phone number. The name is the value and the number is the key. This list would look like the following table:

## Array properties

arr.length