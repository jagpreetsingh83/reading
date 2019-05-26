### Basics

- Hoisting: Basically, when Javascript compiles all of your code, all variable declarations using var are hoisted/lifted to the top of their functional/local scope (if declared inside a function) or to the top of their global scope (if declared outside of a function) regardless of where the actual declaration has been made. This is what we mean by “hoisting”.
https://medium.com/javascript-in-plain-english/https-medium-com-javascript-in-plain-english-what-is-hoisting-in-javascript-a63c1b2267a1

- Lexical Scope: Shared/Extended Scope. Lexical Scoping just means that it uses thisfrom the code that contains the Arrow Function.
https://hackernoon.com/javascript-es6-arrow-functions-and-lexical-this-f2a3e2a5e8c4

- Closure: Closure is when a function is able to remember and access its lexical scope even when that function is executing outside its lexical scope.

- Deep Closing: There is no easy way. You need a solid algorithm to achieve this natively. Easiest is sttringify and parse but it does not work with dates, functions, Infinity etc.

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
