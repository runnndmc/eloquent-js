## Summary 

- number values
- string values
- boolean values
- undefined values
- Arthmetic operators (binary) 
- string concatenation
- comparison (==, !=, ===, !==, < > <= >=)
- logic (|| &&)
- urnary operators (typeof  -  !)
- ternary operator (conditional operator) 



# Values Types and Operators Notes

**Bits** are any kind of two valued things usually described as zeros and ones
- bits only have two digits (1 or 0) and the weight of each increases by a factor of 2 from right to left 

example: 13 
 
 0  0  0  0  1  1  0  1
128 64 32 16 8  4  2  1


===> 00001101 ~> 13 
==>     8+4+1 = 13



## Values

A typcial modern computer has more than 30 billion bits in its volatile **data storage** or working memory.
  Nonvolatile storage (the hard disk) tends to have a magnitude more of bits
  
**Values** are chunks of data that represent pieces of information.

Though all values are made of bits, they can play different roles. 
Every value has a _type_ that determines its role.

Value types include: numbers, strings and functions.

Every value has to be stored somewhere. If you want to use a gigantic amount of value types at the same time, you might run out of memory. 
^^ This is only a problem if you need that all simultaneously.

<br></br>

### Numbers

JavaScript uses a fixed number of bits - 64 
These bits are used to store a single number value. These bits also store negative numbers so one bit indicated the sign of the number.
Some bits are also used to stop the position of the decimal point. 

<br></br>

### Arithmetic

When operators appear together without parentheses, the order in which they are applied is determined bu the _precedence_ of the operators. 

example: / & * have the same precedence 
         _ & + have the same precedence 
         
When multiple operators with the same precedence appear next to eachother, they are applied left to right.

When in doubt, just add parentheses!

**Modulo** or the % symbol is used to represent the remainder operation.

example: X % Y is the remainder of dividing X by Y

 314 % 100 ==> 14
 144 % 12 ==> 0
 
<br></br>

### Special Numbers

Infinity    (Infinity - 1 = Infinity)
-Infinity    
NaN    *is a value of the number type  (0/0 = NaN) (Infinify - Infinity = NaN)

<br></br>

## Strings

**Strings** are used to represent text. 

Newlines (the characters you get when you press ENTER) can be included withough escaping quoted text.
This can happen only when the string is quoted with backtics (\')

_escaping_  - Whenever a blackslash (\) is found inside quoted text, it indicates that the character after it has special meaning. 

A quote that is precesed by a backlash will not end the string but be part of it. 
When an N character occurs after a backslash, it is interpreted as a **newline.**
When a T is after a backslash, it means a **tab character**

example:
```
"This is the first line\nAnd this is the second"

==> This is the first line
    And this is the second
    
example:
"A newline character is written like \"\\n\"."

==>   "A newline character is written like \"\\n\"."
```
Strings are modeled as a series of bits to be able to exist inside a computer.

Some characters such as many emoji take up two "character postions"

Strings can be combined using _concatenation_ glueing two strings together

example:
> "con" + "cat" + "e" + "nate" ==> "concatenate"

String valued have _methods_ that can be used to perform other operations on them. 

_temperate literals_ can combine other info together and embed other values

something inside `${}` results in a converted string with the included info within that position.

<br></br>

## Unary Operators

Operators can be symbols and some are written as words.
such as the operator:  typeof 

example: console.log(typeof 4.5)
// → number

operators that use two values are called **binary operators** while those that take one are called **urnary operators**

<br></br>

## Boolean Values
JavaScript has a _Boolean_ type which is either true or false. 

You can create Boolean types by **Comparison**

example:
```
console.log(3 > 2)
// → true
console.log(3 < 2)
// → false
```

The signs > greater than or < less than are ***Binary Operators***

These operators result in a boolean value.

You can use Booleans on Strings. The way strings are ordered is typically:
- Uppercase letters are always less than lowercase 
Ex: "Z" < "a" ==> true

- When comparing JS strings, JS goes over the characters from left to right, comparing the Unicode codes one by one. 

***There is only one value in JS that is not equal to itself: NaN***

```
console.log(NaN == NaN)
==> false
```

- NaN is describing a nonsensical computation and as such is not equal to the result of another nonsensical computation

<br></br>

## Logical Operators

JavaScript supports three logical operators: _and, or_ and _not_

&& - logical operator and. It's result is only true if both values given are true

|| - logical operator or. Produces true if either of the values given to it is true 

_Not_ (!) - is a urnary operator that flips the value given to it. 
```
console.log(!true) ==> false
console.log(!false) ==> true
```

Ternary - logical operator that operates on three values. Can also be called a _Conditional Operator_

```
console.log(true ? 1 : 2) ==> 1
console.log(false ? 1 : 2) ==> 2
```

<br></br>

## Empty Values

There are two values that are used to denote the absence of a menaningful value: 
 - null
 - undefined

They are themselves values but they carry no information.

<br></br>

## Automatic type conversion

type coercion - when an opperator is applied to the wrong type of value, JS will convert that value to the type it needs. 

When something that doesn't map to a number in an obvious way is converted to a number, you get the value NaN


When Null or Undefined occurs on either side of the operator, it produces true only if both sides are one of null or undefined. 

```
console.log(null == undefined) ==> true
console.log(null == 0) ==> false
```

When you want to test whether a value has a **real value** instead of null or undefined you can **compare it to null** with the == or != operator.

```
console.log(0 == false) ==> true
console.log('' == false) ==> true
```

<br></br>

## Short-circuting of logical operators

|| - logical operator or, **will return the value to it's left when that can be converted to true** otherwise it will return the value on the right.

```
console.log( null || "user") ==> "user"
console.log( "Agnes" || "user") ==> "Agnes"
```

**0, NaN and "" - all count as false** All other values count as true. 


With these logical operators: 
 - in the case of (true || X)
  - the result will be true and X will never be evaluated. 

|| - logical operator or, **will return the value to it's left when that can be converted to true** otherwise it will return the value on the right.



- in the case of (false && X)
  - the result will be false and X will never be evaluated 

&& - logical operator and **will return the value to it's left when that value converts to false** otherwise it returns whats on the right. 


<br></br>

