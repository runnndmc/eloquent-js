# Program Structure

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
 <li>Can be any word except for reserved JS words</li>
 <li>Can not start with a number</li>
 <li>Can only have special characters $ or _ but none other</li>
 <li>Keywords can not be used as binding names</li>
</ul>

Check if you're using a reserved word if the binding comes back with a syntax error.



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

console.log is not a simple binding

instead, console.log is actually an *expession* that retrieves the _log_ *property* from the *value* held by the _console_ *binding*.



## Return Values

A _side effect_ is showing a dialog box or writing text to a screen. 

Functions may produce side effets or values. 

In JS anything that produces a value is an _expression_ 
(_reminder: An **expression** is a fragment of code that produces a value which is written literally.)

This means that function calls can be used within larger expressions. 

ex:
> console.log(Math.max(2, 10) + 100) ==> 110 

^^ this function call is being used as a part of an addition expression 



## Control Flow

When your program has more than one statement, the statements are executed from top to bottom. 

ex:
```
let setNumber = Number(prompt("Pick a number"))
console.log("You're number is the square root of" + setNumber * setNumber)
```

Here, the _function_ Number transforms it's given value to a number form.
Similar functions in JS are: String or Boolean 

**Straight line control-flow** is when a program executes statements from top to bottom with no break. 

When a program takes the proper branch based on the situation at hand, it is called a **conditional execution**

Conditional executions are created using _if_ statements. 
If statements executes or skips a statement depending on the value of the boolean expression.

ex:
```
let setNumber = Number(prompt("Pick a number"))

if(!Number.isNaN(setNumber)){
  console.log("You're number is the square root of" + setNumber * setNumber)
}
```
The function **Number.isNaN** returns true only if the argument given is not a number. 
Therefore, the condition states, "unless the Number is Not a Number, do this"

Braces are used to connect and number of statements into a single statement - these are called **blocks**

You can use the _else_ keyword to create two alternate execution paths. 

**Chaining** together multiple if/else statements gives you more than two paths to choose from. 




### While and Do loops

The form of control flow that runs a piecee of code multiple times is called a **loop**

Looping flow control allows us to go back to some point in a program and repeat it with the current program state.

ex:
```
let num = 0; 
while (num <= 12){
 console.log(num)
 num = num +2
}

==> 0
==> 2
==> ... etc.
```

The loop keeps entering the statement as long as the boolean expression produces a value which returns _true_.

In the example above, you can see how the binding : number  keeps track of theprogress of a program. 

In the next example, we're looking to write a program that calculates and shows the value of 2 to the 10th power. In this example, theree needs to be two bindings, one to keep track of the result and one to count how often we've multiplied. The loop tests whether we've reached 10 yet. 

```
let total = 1
let mult = 0

while ( mult < 10 ) {
  total = total * 2
  mult ++
}
==>1024
```

It is a good idea to start a counter at 0.

**Do Loop**

A do loop is similar to a while loop. 
This loop always executes it's body at least once. It starts texting whether it should stop only after the first execution.

ex:
```
let yourName;
do {
 yourName = prompt("Who are you?");
} while (!yourName);

console.log(yourName)
```

This will ask a user of their name continuously until it gets something that is not an empty string. 

All strings except "" convert to _true_

**For Loops**

similar to all other loops except, a for loop has all of the statements that are related to the state of the loop are grouped together and included in the statement after _for_

ex:
```
for ( let i=0; i < 10; i = i + 2) {
 console.log(i)
}

==> 0
==> 2
==> ... etc
```

Breaking down a for loop: 

i=0; <-- _initializer_ (usually defining a binding)
i<10; <-- _expression_ (to check if the loop should continue)
i = i + 2 <-- _updates the state_ (after every iteration)

 
**Breaking Out of a Loop**

There is a special statement **break** that will take you out of a loop immediately once read.


ex:
```
for (let current = 20; current = current + 2){
 if ( current % 7 === 0 ){
   console.log(current);
   break;
 }
}
```

The example above doesn't have an expression that would check for the end of the loop, therefore, the loop will never stop unless the _break_ statement inside of the if statement is executed. 

The _continue_ keyword is similar to break keyword accept it influences the loop to progress.

When continue is encountered by a loop body, the control flow jumps ut of the body and continues with the loops next iteration. 



***Updating Bindings Succinctly***

Programs often need to update bindings value based on that bindings previous value.

shortcuts for succinctly updating a binding:
* ++
* +=
* --
* -=
* *=

Using *( *= 2 )* would double the bindings value succinctly


## Dispatching on a Value with Switch

When you have a statement with if/ else if/ else if/ else 

There is a way to dispatch the statement in a more direct way. This construct is called a *switch*
Switch is inherited from the C/Java languages

ex:
```
switch(prompt("what is the weather like today?")){
 case "rainy": 
   console.log("bring an umbrella");
   break;
 case "sunny":
   console.log("wear sun screen!");
 case "cloudy":
   console.log("dress lightly");
 break;
 default:
   console.log("who knows?! call mom.")
 break;
}
```

You can put a number of case labels inside the block opened by switch.

The program starts executing at the label the corresponds to the value switch was given. 
If no matching value is found, it will execute at the label default. 

It will execute all labels until it hits a break statement.

In some cases, you can share code between cases by not including a break between them (like in the example above)


## Capitalization

In JS you can define a binding in a few different ways:
* alltogetherlikethis
* with_breaks_in_between
* EveryWordCapsFirstLetter
* everythingButTheFirstLetterCaps


In a few cases such as the Number function the word is capitalized so as to mark it as a *constructor*



## Sum It Up!

* A program is made up of statements.
* Statements can contain more statements.
* Statements contain expressions which can be built out of smaller expressions
* You can introduce disturbance in control flow by adding conditional statements or looping statements
* Bindings are used to store data under a name - they can track the state in your program
* The environment is the set of bindings that are defined
* Functions are special values that encapsulate a piece of a program
* A function call is an expression d may produce a value

