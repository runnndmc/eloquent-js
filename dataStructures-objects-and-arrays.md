# Data Structures : Objects and Arrays

Objects allow us to group together values, including other objects, to build more complex structures

In order to work with a chunk of data, you would have to find a way to represent it in the machine's memory

An **Array** is a data type that is specifically used for storing sequences of value. Typycally written with square values and seperated by commas.

The notation for getting at the elements inside an array also uses square brackets.

Ex: a pair of square brackets next to an expression with another expression inside of the brackets will look up the element in the left-hand expression that corresponds to the _index_ given by the expression in the brackets.

> an expression is a fragment of code that produces a value that is written literally. 

#### Properties

There are expressions that access a _property_ of some value

ex: dogString.length
      |           |
   value       property 
   
In the exaple, we're accessing the length property of the value in dogString

ex: Math.max(1, 10)
     |    |
   obj  property
   
In the example, you're accessing the max property of the Math object. The Math ojbect is a collection of mathematics related constants and functions 

Almost all JavaScript values have properties 
The only JavaScript values that don't have properties are *null* and *undefined*

If you were to try and pass properties onto either null or undeefined you would come back with an error.

ex: null.length ==> TypeError: null has no properties.

Accessing Properties:

You can access a property by either dot or bracket notation. 

Both myValue.x and myValue[x] can access a property. 
But they don't necessarily access the _same_ property.

> when using dot notation, the expression after the dot is the literal property name. 
> when using bracket notation, the expression inside of the brackets is _evaluated_ to get the property name

So in the case of bracket notation, value[x] tries to evaluate the expression "x" and uses the result, converted to a string as the property name. 

If you know the property name you can call it with dot notation. 
ex: value.color

Because dot notation is liteeral, it is looing for exact binding names. Therefor, if you wanted to access a propeerty names 2 or John Doe you would use bracket notation. 

ex: value[2] or value["john doe"]

#### Methods

In addition to properties, both string and array objects contain properties that hold function values.
```
ex: let homer = "Doh"
console.log(typeof homer.toUpperCase) ==> function
console.log(homer.toUpperCase()) ==> "DOH"
```

Every string has a .toUpperCase property that returns a copy of the string value in all uppercase letters.

Even though the call to (.toUpperCase) does not havee any arguments, it still has access to the value of the homer binding 

Properties that contain functions are called **methods** of the values they belong to. 

```
ex: 
let myArr = [1,2,3,4,5]
myArr.pop()
console.log(myArr) ==> [1,2,3,4]
myArr.push(6)
console.log(myArr) ==> [1,2,3,4,6]
```

The _push_ method adds a value into the end of an array
The _pop_ method removes the last value at the end of the array and returns it

A **stack** in programming is a data structure that allows you to push and pop values into and out of them so that the thing that was added last into the stack is removed first 

#### Objects

Values of the type _object_ are arbitrary collection of properties. 

Objects also group values together into a single value and then put these grouped values into an array of log entries. 

```
ex: 
let day1 = {
  squirrel: false, 
  events: ["work", "touched tree", "pizza", "ran"]
}

```

Inside the braces are a list of *properties* separated by commas.
Each property as a name followed by  colon and a *value*

Braces in JS have two meanings:
  - at the start of a statement, they start a block of statements. 
  - in any other position, they describe an object, 

With objects, it is possible to assign a value to a property with the = operator. This will replace the property's value if it already existed or create a new property on the object if it didn't. 

**priperty bindings** grasp values while other properties or values may be holding on to the same values. 

You can utilize the delete operator to remove a property from an object . The delete operator is a unary operator that when applied to an object property, will remove the named property from the object.

> a unary operator is an operator that takes one value. 
> a binary operator is an operator that takes two values. 

The **in** operator, when applied to a string and an object, tells you whether that object has a property with that name. 

To find out what properties are in an object, you can use the: Object.keys function. With this function, you give it an object and it returns an array of strings. 
```
ex: 
console.log(Object.keys({x:1, y:2, z:5})) ==> ["x", "y", "z"]
```

There is also an Object.assign function that copies all keys from one object into another:

```
ex:
let myObj = {a:1, b:2}
Object.assign(myObj, {b:3, c:5})

console.log(myObj) ==> {a:1, b:3, c:5}
```

Arrays are utilized for objects that store sequences of things. 

#### Mutability

Numbers, Strings and Booleans are all *Immutable* - it is impossible to change the values of those types.

WHile you can combine them and creeate new values from them, but when you take a specific string value, that value will always remain the same because the text inside of it can not be changed. 

Objects work differently than immutable values in that you can change an objects properties. 
This causes a single object value to have different content at different times. 
```
ex: 
let obj1 = {value: 10}

obj2 = obj1

let obj3 = {value:10}

console.log(obj1 == obj2) ==> true
console.log(obj2 == obj3) ==> false

obj1.value = 15

console.log(obj2.value) ==> 15
console.log(obj3.value) ==> 10
```

obj1 & obj2 both grasp the same object
where as obj3 points to a different object 


Similarly, though const binding to an object can not be changed, the _contents_ of that object might change

```
ex:
const score = {visitors: 1, home: 0}
score.visitors = 2;

console.log(score) ==> {visitors: 2, home: 0}

score = {visitors: 3, home: 1} ====> ERROR
```

There is no deep comparison operation build into JS to compare objects by contents. 

#### Squirrel World

``` 
let journal = []
function addEntry() {
      journal.push({events, squirrel})
 }
 
 ```
 
 In the above example, the object being pushed into journal does not have any values attached to the keys. This is short hand that means, if a property name is not followed by a value, it's value is taken from the binding with the same name. 
 
 A _correlation_ is a measure of dependence between statistical variables. In statistics, you typically have a set of measurements and each variable is measured for every measurement. 
 
 #### Computing Correlation
 
-  We can represent a two by two table in JS by writing a 4 element array ([76, 4, 21, 1])
- We can also use other represenations such as an array with arrays ([[76, 4], [21,1]]) 
- Or an object with property namees such as "11" or "01"


Arrays have an _includes_ method that hecks whether a given akue exists in the array. 
A common way to loop over an array and pick out each element in turn, you could do a **for of** loop
```
ex:
for (let entry of JOURNAL) {
      console.log(`${entry.events.length} events.`)
 }
 
 ```

a for of loop works with arrays, strings and some other data structures

#### More Array Methods

To add and remove items from the beginning of an array you can utilize **shift** and **unshift**

**shift** - removes from the front of the array
**unshift** - adds to the beginning of the array 



