---
layout: post
title:      "Scope in Javascript"
date:       2019-04-04 19:24:56 -0400
permalink:  scope_in_javascript
---


Originally, I started writing a blog post about variable hoisting in Javascript, but, pretty quickly, I realized that I first needed to explain scope within Javascript first. It is essential to understanding scope in order to fully understand the topic of hoisting. So, here I am, writing a blog post about scope in Javascript. Let’s get started!

Before ES6, there were only two types of scope in Javascript:

* Local/Function Scope
* Global Scope

ES6 introduced a new type of scope to Javascript, which is 

* Block Scope

Before we dive in to the differences of each type of scope, let’s discuss what scope is at it’s most basic level. Scope essentially determines when and where variables can and cannot be accessed. In other terms, “scope determines the accessibility” of variables.

Let’s dive into the complexity of each type of scope, one at a time. 

### Global Scope

A variable that is declared outside of a function is a global variable and exists within the global scope. This means that “all scripts and functions on a web page can access it.” In even simpler terms, you can use this variable anywhere in your program. 

```
var shape = “circle”;
console.log(shape); // “circle”

function changeShape() {
  shape = “triangle”;
}
changeShape();
console.log(shape); // “triangle”
```

### Local/Function Scope

When a function is defined, all variables within the global scope are available to it. A function also has access to the variables declared inside of it, which is local/function scope. So, a variable declared within a function is referred to us a local variable and exists only within the local/function scope. 

```
function exampleFunction() {
  var color = “red”;
  console.log(color); // “red”
}

exampleFunction();
console.log(color); // ReferenceError: color is not defined
```

### Block Scope

Block scope was introduced by ES6 and uses `let` and `const` to declare variables. Block specifically refers to anything inside curly brackets, `{}`. Examples of a block would be an if-statement or a function. So now, functions aren’t the only thing that are able to create their own scope.

When it comes to functions, `let` and `const` work similarly to `var`. 

``` 
function myFunc() {
  let animal = “dog”;
  console.log(animal); // “dog”
}

myFunc();
console.log(animal); // ReferenceError: animal is not defined
```

#### Where Block Scope Gets Confusing

Block scope gets confusing in regards to the same variable name being used twice. When one uses `var` to declare two variables (which isn’t block scope) the first declaration is overridden. 

```
var food = “pizza”;

if (true) {
  var food = “ramen”;
  console.log(food); // “ramen”
}

console.log(food); // “ramen”
```

When utilizing block scope by making use of `let`, the first declaration remains the same and the second declaration is not available outside of the block. 

```
let food = “pizza”;

if (true) {
  let food = “ramen”; // “ramen”
}

console.log(food); // “pizza”
```

While using the same name for two variables isn’t advised, if you ever do it, please make sure to use `let` to declare your variables or else you’ll end up with some very confusing code and outcomes. 

I hope this blog post is helpful for those of you new to Javascript scope! Happy coding. 

### Resources

[ES6: var, let, and const - The battle between function scope and block scope](https://www.deadcoderising.com/2017-04-11-es6-var-let-and-const-the-battle-between-function-scope-and-block-scope/)

[Understand Hoisting in Javascript](https://codeburst.io/understanding-hoisting-in-javascript-c8d35d5db2c2)

[Javascript Scope](https://www.w3schools.com/js/js_scope.asp)

[The Difference Between Function and Block Scope in Javascript](https://medium.com/@josephcardillo/the-difference-between-function-and-block-scope-in-javascript-4296b2322abe)
