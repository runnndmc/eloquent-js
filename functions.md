# Functions

A **function** is a program wrapped in a value.
A function **definition** is a regular binding where the value of the binding is a function. 

```
ex: function definition

const square = function(x){
  return x * x
}

console.log(square(5)) ==> 25
```

A function is created with an expression that starts with the keyword _function_

>(_An expression is a fragment of code that produces a value written literally_)

Functions can have a set of **parameters** or arguments
and a _body_ which contain statements that are to be executed when the function is called.

> (_a statement is a list of program instructions to be executed by the computer._)
```
ex: 
function definition       parameters
       |                   |
const makeNoise = function(){ 
  console.log("BAM!");  <--------function body consisting of statements
}
makeNoise(); ==> "BAM!" <-- side effect
    |
 function call
```

This function does not create a value, it only returns a _side effect_
> (_a side effect is a statement that changes the internal state of the machine in a way that will effect the statements that come after it._)

A return statement determines what value the function returns. 
If you have a return keyword with no value after it the function will return *undefined*

*Parameters* to a function act as regular bindings except their initial values are given by the caller of the function. 

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

let x = 10; --- global scope 

if (true){    --- conditional statement
  let y = 20; --- local block scope
  var z = 30; --- local scope
  console.log(x+y+z); ==> 60; 
}

console.log(x+z) ==> 40; --- z is defined once and is able to be seen inside and outside of the local scope

```

x is visible inside of the block because it was defined as global scope outside of the conditional block

When multiple bindings have the same name, the program can only read the innermost one. 
The below example, the code defined inside the function will only see it's local value and the binding defined globally refers to itself. 

```
ex:
function definition    parameter
      |                |
const half = function(n){
  return n / 2; <--- function body and return value 
 }
 
 let n = 20; --- globally scoped 
 
 console.log(half(10)) ==> 5; --- local scope value
 console.log(n) ==> 20; --- global scope value
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

A function value can do all of the same things as other values can. 
You can use it as an arbitrary expression in addition to using it to call a function. 

For example- you could:
  - store a function in a new binding
  - Pass that new binding as an argument to a function 
  - and utilize that function in another. 
              
Similarly, a binding that holds a function that is not constant can be reassigned a new value.

```
ex:

let launchMissiles = function(){
    missileSystem.launch("now")
}

if(safeMode){
  lanchMissiles = function(){ 
      console.log("nothing")
   }
}
```

## Declaration Notation

A shorter way to create a function binding is to use the keyword _function_ at the start of the statement. 

```
ex: function declaration

function square(n){
  return n * n
}

```

The above example is considered a **function declaration**
The difference is that the above defines the binding _square_ and points it at the given function.

The benefit of function declarations is that once defined, they are conceptually moved to teh top of their scope and can be used by all the code in that scope 

```
ex:

console.log("the cat got scared when:", action());

function action(){
  return "the dog ran towards it"
}

```

## Arrow functions

Another notaion for functions besides declarations and definitions are **arrow functions**

```
ex: arrow function

const power = (base, exponent) => {
  let result = 1;
  for (let count = 0; count < exponent; count ++) {
     result *= base
  }
  return result
}

```
The arrow comes after the parameters. 

This function expresses something like "this input (parameter) produces this result (body)"

Both function expressions and arrow functions do essentially the same things and have little difference to them. 


## The Call Stack

The call stack defines how control flows through a function.

```
simple ex: control flow

function greet(who){          1  3
  console.log("Hello"+ who);  2
}
greet("Harry")                4
console.log("bye!")           5

```
Control flows through this program like so:

    - call to greet lets control start at the beginning of that function
    - the greet function calls the console.log which takes control and does it's job 
    - control returns to the function greet line where it reaches the end of the greet function
    - Then it returns control to the line in which it was called
    - After that it continues to the console.log and once that returns the program reaches its end
    
Because control has to jump back to where the function was called after the function is complete, the computer must remember the context from which the call happened. 
 
 In the above example theres 
    Case 1: console.log returns to the greet function once complete
    Case 2: console.log returns to the end of the program
    
The place where the computer stores this context is called a _call back_

Every time a function is called
the _current context_ is stored on _top_ of the stack. 

When a function returns, it removes the top context from the stack and uses that context to continue execution. 

Storing this stack requires space in the computers memory. 

## Optional Arguments

If there are multiple arguments given to a function as parameters and the call for that function only provides one parameter to that function, the computer will ignore the other arguments and will compute whatever argument is given in the function call. 

If you pass too many arguments to a function, the ones that are not in the function will be ignored. 

If you pass the function too little arguments the missing parameters get assigned the value _undefined_


The upside of having too many arguments in the function is that you can call the same function function with different number of arguments for different results. 

```
ex: multiple arguments

function minus(a, b){
  if (b === undefined) return -a 
  else return a - b
}

console.log( minus(10) ) ==> -10
console.log( minus(10, 5) ) ==> 5

```

If you have an = operator after a parameter, followed by an expression, the value of hat expression will replace the argument when not given. 

In some cases, the second arguments are optional, therefore if you dont provide that argument the argument with the = operator and expression will have a default value as oposed to being undefined. 

## Closure

The ability to treat functions as values 
and the fact that local bindings are re-created every time a function is called,
asks the question, 

what happens to local bindings when the function call that created them is not longer active?

Local bindings are created new for every call. 
Different calls can't trample on one anothers local bindings 

Being able to reference a specific instance of a local binding in an enclosing scope is called **closure**
A function that references bindings from local scopes around it is called **a** _closure_

Using closures frees you from having to worry about lifetimes of bindings and also makes it possible to use function values in creative ways.

```
ex:  a closure

function multiplier(factor){
  return number => number * factor
}

let twice = multpilier(2)

console.log(twice(5)) ==> 10

```

Think of function values as containing both the code in their body - and - the environment in which they are created. 

In the example above:
  - the function multiplier is called
  - that call creates an environment in which it's _factor_ parameter is bound to 2 
  - The function value it returns is stored in the binding _twice_
  - the binding _twice_ remembers the environment in which it was created in 
  - so when that binding is called with an argument, it multiplies it's argument by 2 
  
## Recursion 

A function that calls itself is considered **recursive**

```
ex:

function power(base, exponent){
  if (exponent == 0){
    return 1
  } else {
    return base * power(base, exponent - 1);
  }
}

console.log(power(2,3)) ==> 8

```

In the example above, the function calls itself multiple times with the exponents decreasing by one each time around.

Loops are typically three times faster than recursion 

Recursion is not always an inefficient alternative to looping

Some problems are easier to solve with recursion than with looping. 
Most problems that require exploring or processing several branches are good oportunities for recursion 

Consider this puzzle:

starting at the number 1 and repeatedly either adding 5 or multpilying by 3 
write a function that, given a number, tries to find a sequence of such additions and multiplications that produce that number. 

problem ex: 13 consists of first multiplying by 3 and then adding 5 twice.
            15 can not be reached at all 
            
```
recursive ex:

1                 function findSolution(target) {
2 4 6  10  13       function find(current, history){
    7               if (current == target) {
                        return history;
    8  11           } else if (current > target){
                        return null;
                       } else {
 5  9  12  14           return find( current + 5, `${history} + 5` )|| find( current * 3, `${history} * 3`);
                      }
                    }
3                   return find(1, "1");
                    }

                    console.log( findSolution(24) ) ===> (((1 * 3) + 5) * 3)

```

Let's walk through it:

  - The inner function _find_ is recursive 
  - find takes two arguments, the current number and a string that records how we reached that number
  - if find finds a solution, it returns a string that shows how to get to the target 
  - if no solution can be found it returns null 

To get to these return values, the function goes through three actions:
  - if the current number is the target the current history is the way to get to that target number and the function can end there 
  - if the number is greater than the target, theres no sense in exploring further because adding and multiplying will only increase it's value
  - if the target number is not yet reached, the function tries both possible paths
    - each path starts from the current number by calling itself twice 
    - one call for addition
    - one call for multiplication 
    - if the first call returns something that is not null, it is returned. 
    - Otherwise, the second call is returned - regardless of whether it produces a string or null 
  
This is the break down of what steps are being taken:

find(1, "1")
  find(6, "(1 + 5)")
    find(11, "((1 + 5) + 5)")
      find(16, "(((1 + 5) + 5) + 5)")
        too big
      find(33, "(((1 + 5) + 5) * 3)")
        too big
    find(18, "((1 + 5) * 3)")
      too big
find(3, "(1 * 3)")
  find(8, "((1 * 3) + 5)")
    find(13, "(((1 * 3) + 5) + 5)")
      found!

    
    
The first time _find_ is called, it starts by calling itself to explore the solution that it starts with: (1+5)

  - That call will continue to recurse to explore *every* comntinued solution that yields a number less than or equal to that target number
  - Since it doesn't find a solution that hits the target, it returnd null back to the **first call.** 
  - There the || operator causes the call that explores (1 * 3) to happen
  - It's first recursive call - through another recursive call hits the target number 
  - The innermost call returns a string 
  - and each of the || operators in the intermediate calls passes that string along
  - ultimately returning the solution. 

## Growing Functions

Break down a function into a reuseable function for other programs to use and for you not to repeat yourself
