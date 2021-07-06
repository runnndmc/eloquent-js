# Functions

A **function** is a program wrapped in a value.
A function **definition** is a regular binding where the value of the binding is a function. 

```
ex:

const square = function(x){
  return x * x
}

console.log(square(5)) ==> 25
```

A function is created with an expression that starts with the keyword _function_

>(_An expression is a fragment of code that produces a value written literally_)

Functions can have a set of **parameters** or arguments
and a _body_ which contain statements that are to be executed when the function is called.

> (_a statement is a list of program instructions to be eexecuted by the computer._)

```
ex: 
const makeNoise = function(){
  console.log("BAM!");
}
makeNoise(); ==> "BAM!"
```

This function does not create a value, it only returns a _side effect_
> (_a side effect is a statement that changes the internal state of the machine in a way that will effect the statements that come after it._)

A return statement determines what value the function returns. 
If you have a return keyword with no value after it the function will return *undefined*

*Parameters* to a functiom act as regular bindings except their initial values are given by the caller of the function. 

## Bindings and Scope 

A binding has **Scope**

> a binding allows the computer to catch and hold values and keep internal state to remember the values. 

**Scope** is a part of the program in which the binding is visible.
For bindings described outside of any function or block, the scope is the entire program. (**Global Scope**)

Bindings created for function parameters or declared inside a function can only be referenced by that function. (**Local Scope**)

Every time a function is called, new instances of these bindings are created.
Each Function call acts in it's own local scope without knowing a lot about what's going on in the global environment.

Bindings declared with **Let** or **Const** are local to the _block_ that they are declared in.
-- so, if you declare a variable with let or const inside a loop, that variable can not be seen before or after that loop.

***PRE-2015 JAVASCRIPT***
Old style bindings created with the **Var** keyword are visible throughout the whole function that they appear in. Or, throughout global scope if they are defined outside of a function. 

```
ex:

let x = 10; 

if (true){
  let y = 20;
  var z = 30;
  console.log(x+y+z); ==> 60;
}

console.log(x+z) ==> 40;

```

x is visible inside of the block because it was defined as global scope outside of the conditional block

When multiple bindings have the same name, the program can only read the innermost one. 
The below example, the code defined inside the function will only see it's local value and the binding defined globally refers to itself. 

```
ex:

const half = function(n){
  return n / 2;
 }
 
 let n = 20;
 
 console.log(half(10)) ==> 5;
 console.log(n) ==> 20;
 ```
 
 ## Nested Scope
 Blocks and functions can be created inside other blocks and functions. 
 For example, you can have a function within a function. 
 
 ```
 ex:
 const hummus = function(factor){
    const ingredient = function(amount, unit, name){
      let ingredientAmount = amount * factor;
      if (ingredientAmount > 1) {
        unit += "s";
      }
      console.log(`${ingredientAmount} ${unit} ${name}`);
    }
    ingredient(1, "can", "chickpeas");
    ingredient(0.25, "cup", "tahini");
    ingredient(0.25, "cup", "lemon juice");
    ingredient(1, "clove", "garlic");
    ingredient(2, "tablespoon", "olive oil");
    ingredient(0.5, "teaspoon", "cumin");
 }
```
The code inside ingredient can see the factor binding from the outer function (hummus). 

The local bindings here are ingredientAmount and unit and are not visible to the outer function (hummus).

The set of bindings visible inside a block of code is determined by the place of that block in the program text. 

Local scope can also see all of the local scopes that contain it and all of these scopes can see the global scope. 

>This approach to biding is called **lexical scoping**

## Functions as Values
