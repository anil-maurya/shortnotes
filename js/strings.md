
# Strings

JavaScript strings are used for storing and manipulating text. Strings are useful for holding data that can be represented in text form

## Creating String

Strings can be created as primitives, from string literals, or as objects, using the String() constructor:

```js

const string1 = "A string primitive";
const string2 = 'Also a string primitive';

const string4 = new String("A String object");

```

Note - Don't create strings as objects. It slows down execution speed. The new keyword complicates the code. This can produce some unexpected results, comparision of two strings created with new keyword always returns false.

**String()** 
The String constructor is used to create a new String object. It performs type conversion when called as a function, rather than as a constructor, which is usually more useful.

```js
typeof String('Hello world'); // string
typeof new String('Hello world'); // object
```


## String Methods

**length**

* `indexOf()` : method returns the index of (the position of) the first occurrence of a specified text in a string or returns '-1'
* `lastIndexOf()` : returns the index of the last occurrence of a specified text in a string. There could be multiple occurance or returns '-1'
    
    * Both methods accept a second parameter as the starting position for the search
    * The `indexOf()` methods searchs forward (from start/startPosition to end)
    * The `lastIndexOf()` methods searches backwards (from the end to the beginning), 
    * meaning: if the second parameter is 15, the search starts at position 15, and searches to the beginning of the string.


* `search()` : The search() method searches a string for a specified value and returns the position of the match:


**indexOf vs search**

- The search() method cannot take a second start position argument.
- The indexOf() method cannot take powerful search values (regular expressions).

**slice(start, end)**  

- extracts a part of a string and returns the extracted part in a new string. 
- end is not included.
- end is optional and default value is length of string

```js

var str = "1234567890";
var res = str.slice(7, 13); //banana
```

**substring(start, end)**

**slice vs substring**

COMMON

  - If start equals stop: returns an empty string
  - If stop is omitted: extracts characters to the end of the string
  - If either argument is greater than the string's length, the string's length will be used instead.

Differences

  - If `start > stop`  slice() will return the empty string. ("")
  - If `start is negative` : sets char from the end of string, exactly like substr() in Firefox. This behavior is observed in both Firefox and IE.
   - If stop is negative: sets stop to: string.length – Math.abs(stop) (original value), except bounded at 0 (thus, Math.max(0, string.length + stop))

Distinctions of substring():

If start > stop, then substring will swap those 2 arguments.
If either argument is negative or is NaN, it is treated as if it were 0.



**replace()** 
  - method replaces a specified value with another value in a string. 
  - The replace() method does not change the string it is called on. It returns a new string.
  - By default, the replace() method replaces only the first match:
  - By default, the replace() method is case sensitive. Writing MICROSOFT (with upper-case) will not work:
  - To replace case insensitive, use a regular expression with an /i flag (insensitive). 
  - regular expressions are written without quotes.
  - To replace all matches, use a regular expression with a /g flag (global match):

Examples
```js

str = "Please visit Microsoft!";
var n = str.replace("MICROSOFT", "W3Schools");

//ignore case
str = "Please visit Microsoft!";
var n = str.replace(/MICROSOFT/i, "W3Schools");

//Replace all occurance
str = "Please visit Microsoft and Microsoft!";
var n = str.replace(/Microsoft/g, "W3Schools");

````
**toUpperCase**

**toLowerCase()**

**concat()** : joins two or more strings, The concat() method can be used instead of the plus operator. These two lines do the same:

```js
var text = "Hello" + " " + "World!";
var text = "Hello".concat(" ", "World!");
```

**trim()**

The trim() method removes whitespace from both sides of a string:

**charAt(index)**

  - If index is greater than length it returns NaN

**charCodeAd(index)**

* The charCodeAt() method returns the unicode of the character at a specified index in a string:
* The method returns a UTF-16 code (an integer between 0 and 65535).
* If index is greater than length it returns NaN

`* split('')`

- Splits string from delimiter and convert it to array