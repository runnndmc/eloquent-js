# Data Structures : Objects and Arrays

Objects allow us to group together values, including other objects, to build more complex structures

In order to work with a chunk of data, you would have to find a way to represent it in the machine's memory


## Array's

An **Array** is a data type that is specifically used for storing sequences of value. <br>

The notation for getting at the elements inside an array also uses square brackets.

Ex: a pair of square brackets next to an expression with another expression inside of the brackets will look up the element in the left-hand expression that corresponds to the _index_ given by the expression in the brackets.

> an *expression* is a fragment of code that produces a value that is written literally. 

#### Properties

There are expressions that access a _property_ of some value
```
ex: dogString.length
      |           |
   value       property 
   
In the example, we're accessing the length property of the value in dogString

ex: Math.max(1, 10)
     |    |
   obj  property
```

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

While you can combine them and create new values from them, but when you take a specific string value, that value will always remain the same because the text inside of it can not be changed. 

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


Arrays have an _includes_ method that hecks whether a given value exists in the array. 
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

```
ex:

let toDoList=[];
function remember(task){
      toDoList.push(task);
}

function getTask(task){
      return toDoList.shift(task)
}

function rememberUrgently(task){
      return toDoList.unshift(task);
}

```

This program would manage the queue of tasks.
You would add tasks to the end of the queue by calling the remember() function 
When you're ready todo something you would call getTask() which would also remove the task. 
If you had to do something right away, you would call rememberUrgently() to add to the front of the queue. 

To search a specific value you could use the **indexOf** method.
 - this method searches through the array until it finds the matching index. When it does it returns that index value that was requested 
 - if the value is not found, the indexOf method will return -1 

To search from the end of an array instead of the beginning, you can call **lastIndexOf** 

Both indexOf and lastIndexOf take optional second arguments. These second arguments indicate where to start the search from. 

--- slice. 

Slice is another fundamental array method that takes two arguments, the start and the end of where you want to break the array and returns an array that has only those elements between them. 

- the start of the index is inclusive and the end of the index is exclusive

```
ex:
console.log([0,1,2,3,4,5].slice(2,4))
==> [2,3]
console.log([0,1,2,3,4,5].slice(2))
==> [2,3,4,5]
```

If the end index is not given, the new array will include all elements after the start index. 
You can omit the start argument and it will copy the entire array. 
 
---- concat

The **concat** method is used to glue together arrays and create a new array

```
ex:
function remove(array, index){
   return array.slice(0, index).concat(array.slice(index+1))
}

console.log(remove(["a", "b", "c", "d", "e"], 2)
===> ["a", "b", "d", "e"]
```

If you pass *concat* an element that is not an array, that value will be added to the new array is if it were a one element array.

#### Strings and their Properties

Values:
      - string
      - number
      - boolean 
Are **not** objects - Instead, these values are **immutable** and can not be changed. 

> The value can not be changed. It can be combined, or new values can be created from them but when you take the specific value, that value will always remain the same. 
> Objects are **not** immutable because you can change an objects' property, causing a object property to have different values at different times. 

Though the language doesn't complain if you try to set new properties on them, the computer doesn't actually hold those properties.


Although these values are immutable, they do have built in properties. 

Every String value has a number of **methods**

Some String methods are: **indexOf** and **slice** which resemble that of the array methods. The difference being that a string's *indexOf* method can seach for a string containing more than one character. Where the array method looks only for one single element. 

```
ex:
console.log("one two three".indexOf("ee"))
==> 11

```

Another string method -> **trim** -> removes whitespace from the start and the end of a string (along with new line characters, tabs etc.)

```
ex:
console.log("        okay /n   ". trim())
==> "okay"
```

The -> **padStart** method -> takesthe desired length and padding character as arguments 
```
ex:
console.log(String(6).padStart(3,"0))
==> "006"
```
You can **split** a string on every occurence of another string with **split** and join it again with **join**

```
ex:
let sentence = "bird cat hat"
let words = sentence.split(" ")
console.log(words) ==> ["bird", "cat", "hat"]

console.log(words.join(".")) ==> "bird.cat.hat"

```

A string can be repeated using the **repeat** method to create a new string.

```
ex:
console.log("LA".repeat(3)) ==> "LALALA"
```

There is the length property and you can access individual characters in a string as you can with an array with bracket notation. 

```
ex:
const leaving = "cant eat beans no more"
console.log(leaving[3]) ==> "t"
```

#### Rest Parameters

It is useful for a function to recieve any number of arguments 

- Math.max computes the maximum of *all* of the arguments it's given 

```
ex: 
function max(...numbers){
      let result = -Infinity
      for( let number of numbers){
            if (number > result) result = number
      }
      return result
}

console.log(max(4,1,9,-2)) ==> 9
```

when this function is called, the *rest parameter* is bound to an array containing all further arguments.
If there are other parameters before it, their values aren't included in that array - but with max -  is is the only parameter and it will hold any number of arguments. 


- you can use three *dot notation* to all a function with an array of arguments. 

```
ex: 
let numbers = [1,3,5,7,9]
console.log(max(...numbers))
==> 7
```

Dot notation spreads out the array into a function call, passing its arguments as seperate arguments. 

- you could also include other arguments with a dot notaion in the arguments and the function will accept all of the arguments. 

Square bracket dot notation similarly allows the spread operator to *spread another array into the new array*

```
ex:
let words = ["never", "fully"]
console.log(["will", ...words, "understand"]) ==> ["will", "never", "fully", "understand"]
```

#### The Math Object 

There is only one Math object and it is used as a container to group a bunch of related functionality. 

The Math object provides a *namespace* so that all these functions and values do not have to be global bindings. 

Having too many global bindings "pollutes" the namespace. 

Since JS's built in max function is insode the Math object, there is no need to worry about overwriting it. Many languages will warn or stop you from defining a binding which is already taken.

The Math object can also help with trigonometery. The Math object holds the *cos* (cosine), *sin* (sine), and *tan* (tangent) as well as their inverse functions - *acos, asin, and atan* respectively. 

The Math object also contains a PI function. **Math.PI**

**Math.random** returns a new pseudorandom number between zero (inclusive) and one (exclusive) every time you call it. 

Since computers always act the same way if given the same input, it is possible to have numbers look like they appear at random. To do this, machines keep some hidden value and whenever you ask for a new random number, it performs complicated computions of the hidden value to create a new value. It stores teh new value and returns some numbers derived from it. That way it produces ever new hard-to-predict numbers in a way that seems random. 

**Math.floor** rounds down to the nearest whole number 

```
ex:
console.log(Math.floor(Math.random() * 10));
==> 2
```

Multiplying a random number by 10 gives us a number thats greaterthan or equal to zero and below 10. 

**Math.ceil** rounds up to the nearest whole number and **Math.abs** takes the absolute value of a number (meaning it negates negative values but leaves positive numbers)

#### Destructuring

If you know a value you are binding is an array or an object, you can deconstruct the brackets to the variable in order to "look inside" of a value binding it's contents. 

```
ex:
let {name} = {name: "Dayna", age: "ageless"}
console.log(name) ==> "Dayna"
```

#### JSON

Objects and arrays are stored in the computers memory as sequences of bits holding together addresses of their contents. 

So: 
      - An array inside of an array consists of at least one memory region for the inner array and another for the outter array containing a binary number that represents the position of the inner array. 
      - If you have to convert the tangles of memory addreesses to descriptions that can be stored and sent, you can *serialize* the data 
      
*Serializing* the data converts it into a flat descripton. A popular serialization format is called JSON

JSON stands for *JavaScript Object Notation* and is widely used as a data storage and communication format 

JavaScript Object Notation is written:
      - with all property names in double quotes
      - with no function calls, bindings or anything that involves actual computation
      
```
ex:
{
      "fattyFood": ["pizza", "burgers", "milkshakes"], 
      "healthyFood": ["salad", "fruits", "veggies"],
      "balancedDiet": true
}
```

to convert data to and from JSON format, you can use: 
      - JSON.stringify (takes a JS value and returns a JSON-encoded string)
      - JSON.parse (takes a JSON-encoded string and converts it to the value it encodes)
      
## Sum It Up! 

- Objects and Arrays are a specific kinds of objects that provide ways to group several values into a single value
- Most values in JS have properties with the exception of *null* and *undefined*
- properties are accessed using dot or bracket notation
- Arrays contain varying amounts of conceptually identical values and use numbers starting from 0 as the names of their properties. 
- Arrays have names properties such as *length*
- Arrays also have a number of methods such as *slice*
- Methods are functions that live in properties
- Methods usually act on the value they are a property of
- You can iterate over arrays by looping and can utilize a for of loop. 




