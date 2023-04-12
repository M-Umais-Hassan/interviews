## 🟠1. What is event loop?

Event loop is a run time modal in javascript engine which continuosly checks the callback queue and call stack if there is any task in the call back queue it will check if call stack is empty or not if call stack is empty it will move the task from call back queue to call task. Inside here we have setTimeout kind of call back functions.

## 🟠2. What will run first promise or setTimeout?

Call back function which is attached to promise will run first because it goes in micro task queue and it has higher priority than call back queue.
Call back queue -> setTimeout
Micro task queue -> promises (api calls)

## 🟠3. What is hoisitng?

Using a variable before initializing it. Javascript assigns memory to var before run in the execution phase, while let and const goes in temporal dead zone which is not available at global level. So, if we will try to use the variable before initialization var will allowed to do, let and const will not be allowed and it will show up an error of not defined.(var is hoisted)

## 🟠4. Type of scope?

1. Block scope
2. Local scope or function scope
3. Global scope

## 🟠5. Colusure in javascript?

Colusure is a funtion bundled together to its lexical environment. When we have a function declared inside another function and the inner function is using the variables of outer function. Now, when outer function will return so ideally what should happen is, the inner function should not have the access to the variables anymore because the execution context of outer function is removed as the outer function is returned, but what happens is, javascript actually removes the variables from stack memory as the outer function is returned but put those variables in the heap memory and give reference to that variables to the inner function which is why after the outer function returns inner function still hass access to the variables of outer function. Overall inner function remembers that where it lexically present even its parent is not present and this is all colusure is.

## 🟠6. What is call back hell and how to avoid it?

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

## 🔴7. What is call, bind and apply?

It helps us to borrow a function from an object.
Call: 2 arguments, reference and argument to the functioin
Apply: Take arguments in the form of array
Bind: It returns copy of the function rather than the function

## 🟠8. What is this keyword?

This keyword refers to an object.
this keyword alone at global level refers to the javascript window object.

## 🟠9. What is difference between arrow function and normal function?

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

## 🟠10. What is difference between spread operator and rest operator?

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

# Coding Questions

## 🟠1. What will be output of this below code? (relevant to spread operator)

```
let arr = [1,2,3];
let obj = {...arr}
console.log(obj);
```

```
Output: { '0': 1, '1': 2, '2': 3 }
```

## 🟠2. What will be the output of below code? (relevant to promises)

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

```
Output:
2
4
undefined // undefined because finaly does not have any value in the arguments
8
```

## 🟠3. What will be the output? (related to arrays)

```
let arr = [4,5,6];
for(let i in arr) {
  console.log(i);
}
```

```
Output: 0,1,2
```

```
let arr = [4,5,6];
for(let i of arr) {
  console.log(i);
}
```

```
Output: 4,5,6
```

## 🟠4. What will be the output? (related to arrays)

```
let arr = [4,5,6];
arr.foo = 'Hi';
```

```
Output: [ 4, 5, 6, foo: 'Hi' ]
```

## 5. What will be the output for the input value '{}', 'null' and '[]'? (you can ask about typeof first as well)

```
const input = {} && null && [];

if(typeof input === 'object') console.log('Object');
if(typeof input !== 'object') console.log('Not object');
```

```
Output:
Object
Not object
```

Note: null also treats as an object in javascript.
