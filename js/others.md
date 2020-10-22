# JavaScript


## Date

Create Date Object

> new Date()

> new Date(year, month, day, hours, minutes, seconds, milliseconds)

> new Date(milliseconds)

> new Date(date string)

Previous Century
One and two digit years will be interpreted as 19xx:

> var d = new Date(99, 11, 24);

Create Date object from string


`var d = new Date("October 13, 2014 11:13:00");`


JavaScript Stores Dates as Milliseconds

`var d = new Date(0);` => 01 January 1970 plus 100 000 000 000 milliseconds is approximately 03 March 1973:



### Date Methods

JavaScript will (by default) output dates in full text string format. it is auto converted to string `toString()`

> Wed Mar 25 2015 05:30:00 GMT+0530 (India Standard Time)

- `toUTCString()` method converts a date to a UTC string (a date display standard) : "Mon, 05 Oct 2020 06:56:35 GMT"

- `toDateString()` => converts a date to a more readable format: "Mon Oct 05 2020"

### Date Formats

Three formats
 
 - ISO Date	"2015-03-25" (The International Standard)
 - Short Date	"03/25/2015"
 - Long Date	"Mar 25 2015" or "25 Mar 2015"

#### ISO Date

```js
var d = new Date("2015-03-25");
 
 //without day
var d = new Date("2015-03");

// Only Year
var d = new Date("2015");

// ISO Dates(Date-time)
var d = new Date("2015-03-25T12:00:00Z");


var d = new Date("2015-03-25T12:00:00-06:30");

```

`Z` at end :

The T separates the date portion from the time-of-day portion. 

The Z on the end means UTC (that is, an offset-from-UTC of zero hours-minutes-seconds). The Z is pronounced “Zulu”.

Time Zones


without specifying the time zone, JavaScript will use the browser's time zone.

#### Long Dates

```js
var d = new Date("25 Mar 2015");

var d = new Date("January 25 2015");

var d = new Date("Jan 25 2015");

var d = new Date("JANUARY, 25, 2015");

```

## Date.parse()

Convert valid date string to millisecond

returns the number of milliseconds between the date and January 1, 1970:

```js
var msec = Date.parse("March 21, 2012");
```

## Get Methods

- `getFullYear()`   :	Get the year as a four digit number (yyyy)
- `getMonth()`   :	Get the month as a number (0-11)
- `getDate()`   :	Get the day as a number (1-31)
- `getHours()`   :	Get the hour (0-23)
- `getMinutes()`   :	Get the minute (0-59)
- `getSeconds()`   :	Get the second (0-59)
- `getMilliseconds()`   :	Get the millisecond (0-999)
- `getTime()`   :	Get the time (milliseconds since January 1, 1970)
- `getDay()`   :	Get the weekday as a number (0-6)
- `Date.now()`   :	Get the time. ECMAScript 5.


## Set Methods

- `setDate()` :	Set the day as a number (1-31)
- `setFullYear()` :	Set the year (optionally month and day)
- `setHours()` :	Set the hour (0-23)
- `setMilliseconds()` :	Set the milliseconds (0-999)
- `setMinutes()` :	Set the minutes (0-59)
- `setMonth()` :	Set the month (0-11)
- `setSeconds()` :	Set the seconds (0-59)
- `setTime()` :	Set the time (milliseconds since January 1, 1970)
