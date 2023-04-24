## What is event loop?

Event loop is a run time modal in javascript engine which continuosly checks the callback queue and call stack if there is any task in the call back queue it will check if call stack is empty or not if call stack is empty it will move the task from call back queue to call task. Inside here we have setTimeout kind of call back functions.

<hr />

## What will run first promise or setTimeout?

Call back function which is attached to promise will run first because it goes in micro task queue and it has higher priority than call back queue.
Call back queue -> setTimeout
Micro task queue -> promises (api calls)

<hr />

## What is hoisitng?

Using a variable before initializing it. Javascript assigns memory to var before run in the execution phase, while let and const goes in temporal dead zone which is not available at global level. So, if we will try to use the variable before initialization var will allowed to do, let and const will not be allowed and it will show up an error of not defined.(var is hoisted)

<hr />

## Type of scope?

1. Block scope
2. Local scope or function scope
3. Global scope

<hr />

## Colusure in javascript?

Colusure is a funtion bundled together to its lexical environment. When we have a function declared inside another function and the inner function is using the variables of outer function. Now, when outer function will return so ideally what should happen is, the inner function should not have the access to the variables anymore because the execution context of outer function is removed as the outer function is returned, but what happens is, javascript actually removes the variables from stack memory as the outer function is returned but put those variables in the heap memory and give reference to that variables to the inner function which is why after the outer function returns inner function still hass access to the variables of outer function. Overall inner function remembers that where it lexically present even its parent is not present and this is all colusure is.

<hr />

## What is call back hell and how to avoid it?

chain of a lot of call backs, where code start growing horizontally rather than vertically,

```
first().then(() => {
  second().then(() => {
    third().then(() => {
      four().then(() => {
        Hey something happening;
      })
    })
  })
})
```

**Solution**

```
first()
.then((firstRes) => {
  return second()
})
.then((secondRes) => {
  return third()
})
.then((thirdRes) => {
  return four()
})
.then((fourthRes) => {
  END;
})
```

<hr />

## What is call, bind and apply?

It helps us to borrow a function from an object.
Call: 2 arguments, reference and argument to the functioin
Apply: Take arguments in the form of array
Bind: It returns copy of the function rather than the function

<hr />

## What is this keyword?

This keyword refers to an object.
this keyword alone at global level refers to the javascript window object.

<hr />

## What is difference between arrow function and normal function?

1. Sytax differnce
2. Arrow function is not hoisted, normal function is hoisted
3. Regular functions are constructable means we can create them using new keyword, but arrow functions are only callable
4. We cannot have duplicate names of arguments in arrow functions but in normal function not strict mode we can have,

```
function(x,x){} - Valid
```

```
use-strict;
function(x,x){} - In-valid
```

```
use-strict;
const fun = (x,x) => {} - In-valid
```

5. Arrow functions don't have their own this keyword, this keyword in arrow function points to nearest parent non arrow function or global function if there no parent function, while function has its own this

```
let me = {
  name: "Umais",
  thisInArrow:() => {
    console.log("My name is " + this.name); // no 'this' binding here
  },
  thisInRegular(){
    console.log("My name is " + this.name); // 'this' binding works here
  }
};
```

<hr />

## What is difference between spread operator and rest operator?

Spread operator: Use to spread the elements of an array, it will eliminate the elemnts of array and provide as a separate elements that is why it named as spread. Also it makes copy rather than the referencing the same array.

```
function abc(a,b,c) {
  return a + b + c;
}

let variables = [2, 8, 1];
abc(...variables);
```

Rest operator: Oposite to spread operate rather than spreading elements it will condense multiple elements into an array.

```
function abc(...variables) {
  return variables.reduce((sum, item) => sum += item);
}

abc(1,2,3);
```

Note: Here 1,2,3 will be taken as array in the function arguments rather than variables, due to rest operator

<hr />

# <mark>Debounce and Throattling</mark>

## What is debounce?

Debouncing is a programming pattern or a technique to restrict the calling of a time-consuming function frequently, by delaying the execution of the function until a specified time to avoid unnecessary CPU cycles, and API calls and improve performance.

## How to implement the debounce? (Both answers can be acceptable)

1. Implemented using lodash or some other library.

```
import _ from 'lodash';

_.debounce(callback, 1000);
```

2. Without using lodash or any library:

```
function debounce(cb, delay=1000) {
	let timeout;
	return (...args) => {
  	clearTimeout(timeout);
		timeout = setTimeout(() => {
    	cb(...args);
    }, delay);
	}
}

debounce(callback, 1000);
```

## How will you implement search field, to avoid api calls on change of input data?

We can use debounce for this, and reload function will be debounced.

## What is throattling?

Throttling implies limiting the number of times a function gets called in a certain time period.

## Implement code for throattling?

## Real time use case for throattling?

Infinite loader on scroll, we will need scroll pointer location, so we will throattle the mouse event so that only at specific location we will apply reload method, let say when the scroll is at 200 px above the end of screen call reload function, so it will be like an infinite scroll effect.

# <mark>Coding Questions</mark>

## What will be output of this below code? (relevant to spread operator)

```
let arr = [1,2,3];
let obj = {...arr}
console.log(obj);
```

**Output**

```
{ '0': 1, '1': 2, '2': 3 }
```

<hr />

## What will be the output of below code? (relevant to promises)

```
const promise = new Promise((resolve) => resolve(2));

promise
.then((res) => {
    console.log(res);
    return res * 2;
})
.then((res) => {
    console.log(res);
    return res * 2;
})
.finally((res) => {
    console.log(res);
    return;
})
.then((res) => {
    console.log(res);
});
```

**Output**

```
2
4
undefined // undefined because finaly does not have any value in the arguments
8
```

<hr />

## What will be the output? (related to arrays)

```
let arr = [4,5,6];
for(let i in arr) {
  console.log(i);
}
```

**Output**

```
0,1,2
```

```
let arr = [4,5,6];
for(let i of arr) {
  console.log(i);
}
```

**Output**

```
4,5,6
```

<hr />

## What will be the output? (related to arrays)

```
let arr = [4,5,6];
arr.foo = 'Hi';
```

**Output**

```
[ 4, 5, 6, foo: 'Hi' ]
```

<hr />

## What will be the output for the input value '{}', 'null' and '[]'? (you can ask about typeof first as well)

```
const input = {} && null && [];

if(typeof input === 'object') console.log('Object');
if(typeof input !== 'object') console.log('Not object');
```

**Output**

```
Object
Not object
```

Note: null also treats as an object in javascript.

<hr />

## Can you guess the output?

```
setTimeout(() => console.log("1"), 0);
console.log("2");
setTimeout(() => console.log("3"), 2000);
const promise = new Promise((resolve, reject) => resolve(4));
promise.then((res) => console.log(res));
console.log("5");
```

**Output**

```
2
5
4
1
3
```

<hr />

## Can you guess the output?

```
console.log(a);
console.log(b);
var a = 1;
let b = 2;
```

**Output**

```
undefined
ERROR!
/tmp/gqf2juHRWx.js:2
console.log(b);
            ^
ReferenceError: Cannot access 'b' before initialization
    at Object.<anonymous> (/tmp/gqf2juHRWx.js:2:13)
    at Module._compile (internal/modules/cjs/loader.js:999:30)
    at Object.Module._extensions..js (internal/modules/cjs/loader.js:1027:10)
    at Module.load (internal/modules/cjs/loader.js:863:32)
    at Function.Module._load (internal/modules/cjs/loader.js:708:14)
    at Function.executeUserEntryPoint [as runMain] (internal/modules/run_main.js:60:12)
    at internal/main/run_main_module.js:17:47
```

<hr />

## Can you guess the output?

```
function xyz() {
    setTimeout(() => {
        console.log(a);
    }, 0);
    setTimeout(() => {
        console.log(a);
    }, 2000);
    var a = 1;
}

xyz();
```

**Output**

```
1
1
```

## Can you achieve the expected output for below code?

```
const json = [
    {
        name: "umais-1",
        age: 23,
        subItem: [
            {
                name: "umais-1-1",
                age: 23,
                subItem: [
                    {
                        name: "umais-1-1-1",
                        age: 23,
                    },
                    {
                        name: "umais-1-1-2",
                        age: 23,
                    },
                ],
            }
        ],
    },
    {
        name: "umais-2",
        age: 23,
        subItem: [
            {
                name: "umais-2-1",
                age: 23,
            }
        ]
    }
];
```

**Expected Output**

```
['umais-1', 'umais-1-1', 'umais-1-1-1', 'umais-1-1-2', 'umais-2', 'umais-2-1']
```

**Solution**

```
let result = [];

function getNames(data) {
    for(let item of data) {
        result.push(item.name);
        if(item.subItem) getNames(item.subItem);
    }
}

getNames(json);

console.log(result);
```
