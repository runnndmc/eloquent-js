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
