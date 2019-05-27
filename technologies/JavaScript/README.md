### Basics

“Perfection is achieved … when there is nothing left to take away.” — Antoine de Saint Exupéry

- Hoisting: Basically, when Javascript compiles all of your code, all variable declarations using var are hoisted/lifted to the top of their functional/local scope (if declared inside a function) or to the top of their global scope (if declared outside of a function) regardless of where the actual declaration has been made. This is what we mean by “hoisting”.
https://medium.com/javascript-in-plain-english/https-medium-com-javascript-in-plain-english-what-is-hoisting-in-javascript-a63c1b2267a1

- Lexical Scope: Shared/Extended Scope. Lexical Scoping just means that it uses thisfrom the code that contains the Arrow Function.
https://hackernoon.com/javascript-es6-arrow-functions-and-lexical-this-f2a3e2a5e8c4

- Closure: Closure is when a function is able to remember and access its lexical scope even when that function is executing outside its lexical scope.

- Deep Cloning: There is no easy way. You need a solid algorithm to achieve this natively. Easiest is sttringify and parse but it does not work with dates, functions, Infinity etc.

- Using rest operator to omit values:

```javascript
const myObject = {
  a: 1,
  b: 2,
  c: 3
};
const { a, ...noA } = myObject;
console.log(noA); // => { b: 2, c: 3 }
```

- Class & Prototypal Inheritance: Class inheritance may or may not use the `class` keyword from ES6. Constructor functions are used, instead. The ES6 `class` keyword desugars to a constructor function:

```javascript
class Foo {}
typeof Foo // 'function'
```

In JavaScript, class inheritance is implemented on top of prototypal inheritance, but that does not mean that it does the same thing.

There is no clear distinction. We should actually rely on composition over inheritence since while inheriting we have no control over selective inherit. We get everything. Even the stuff we don't need.

https://medium.com/@parsyval/javascript-prototype-vs-class-a7015d5473b

JavaScript classes, introduced in ECMAScript 2015, are primarily syntactical sugar over JavaScript’s existing prototype-based inheritance. The class syntax does not introduce a new object-oriented inheritance model to JavaScript.

One difference between function and class

```
Uncaught TypeError: Class constructor Dog cannot be invoked without 'new'
    at <anonymous>:1:6
```

#### Fibonacci number

History - Fibonacci considers the growth of a hypothetical, idealized (biologically unrealistic) rabbit population.

Applications - Has many applications in science and mathematics e.g. determine the greatest common divisor of two integers. 

https://www.w3resource.com/javascript-exercises/javascript-recursion-function-exercise-6.php

```javascript
// 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, . . .
fibonacci = (num) => {
  let a = 1,
    b = 0,
    v = [0];
  for (let i = 1; i <= num; i++) {
    let c = a + b;
    v.push(c);
    a = b;
    b = c;
  }
  return v;
}

// document.write(fibonacci(8));

fibonacci1 = (num) => {
  let sol = [1,1];
  for (let i = 2; i <= num; i++) {
    sol.push(sol[i-1] + sol[i-2]);
  }
  return sol;
}

// document.write(fibonacci1(8))

fibonacciRec = (n) => {
	if (n == 0) return [0]
  if (n == 1) return [0, 1]
  const arr = fibonacciRec(n - 1);
  return [...arr, arr[n-1] + arr[n-2]];
}

document.write(fibonacciRec(8));

function fibonacciMemo(num, memo) {
  memo = memo || {};

  if (memo[num]) return memo[num];

  if (num <= 1) return 1;

  return memo[num] = fibonacciMemo(num - 1, memo) + fibonacciMemo(num - 2, memo);
}

document.write(fibonacciMemo(2));
```




