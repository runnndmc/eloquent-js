### Program Structure

## Expressions and Statements

An **expression** is a fragment of code that produces a value that is written literally. This can just produce a value. 

ex: 22 or "dadadada"

A JavaScript **program** is a list of statements

A **statement** is a list of program instructions to be executed by the computer. 

A statement that changes internal state of the machine in a way that will affect the statements that come after it is called a **side effect**

## Bindings

A **binding** (or _variable_) allows the computer to catch and hold values to keep internal state and remember the values. 

A **keyword** indicates that a sentence is going to define a binding. (let, const, var)

ex:
 ```
                 
 let    caught     =    5 * 5 <-- expression (binding value)
 ^         ^       ^       
 keyword  binding operator

```

After a binding has been defined its name can be used as an expression whos value is whatever value the binding currently holds. 

ex: 
```
let ten = 10
console.log(ten * ten) ==> 100
```

The = operator on existing bindings disconnects them from their current value and points them to a new value. 

ex:
```
let mood = "light"
mood = "dark" 
console.log(mood) ==> "dark"
```

Two bindings can refer to the same value. 

A program can only access a binding that it has reference to. 

You can also re-assign a binding value. 

ex:
```
let daynaDebt = 150
daynaDebt = daynaDebt - 50
console.log(daynaDebt) ==> 100
```

If you ask for the value of an empty binding, it will return undefined

A single _let_ statement can define multiple bindings at once when separated by commas.

ex: 
> let one = 1, two = 2
> console.log(one + two) ==> 3 

**Var** is short for variable. Var was declared in pre-2015 JS
**Const** is short for constant. This binds the same value for as long as it lives. 

**Binding Names**

<ul>
 <li>Can be any word exceot for reserved JS words</li>
 <li>Can not start with a number</li>
 <li>Can only have special characters $ or _ but none other</li>
 <li>Keywords can not be used as binding names</li>
</ul>

Check for reserved workds if the binding comes back with a syntax error.


## Environment

A collection of bindings and their values that exist at a given time is called an **environment**

When a program starts, the environment is not empty. This is because there are bindings that are a part of the language standard.

Bindings provide a way to interact with the surrounding system 

ex: 
> In a browser, there are functions to interact with the currently loaded website to observe key or mouse inputs. 

## Functions

A **function** is a program wrapped in a value. _(reminder: A **program** is a list of statements)_

These values can be applied in order to run the wrapped program. 

Executing a function is called _invoking_ , _calling_ , or _applying_ it. 

Putting parethecies after a **expression** that produces a function value will call the function. 

ex:
```
function callMom(phoneNum){
 console.log("ring ring")
}

callMom(8455555555) <-- arguments
^
function expression

```

## Console.log

