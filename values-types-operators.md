**static is not generated on the database - hosetd on server input files are prebuilt and the source code isnt changed
- html, css, js - not dynamiclly generated infor can change in js but not on serveer
**dynamic generated on the server every new req would generate a new updated info which adjusts the html on the server
- info generated though node and the server returns.a dynamically generated page - can have js that is also being changed


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
  
**Values* chuncks of data that represent pieces of information.

Though all values are made of bits, they can play different roles. 
Every value has a _type_ that determines its role.

Value types include: numbers, strings and functions.

Every value has to be stored somewhere. If you want to use a gigantic amount of value types at the same time, you might run out of memory. 
^^ This is only a problem if you need that all simultaneously.

### Numbers

JavaScript uses a fixed number of bits - 64 
These bits are used to store a single number value. These bits also store negative numbers so one bit indicated the sign of the number.
Some bits are also used to stope the position of the decimal point. 

### Arithmetic

When operators appear together without parentheses, the order in which they are applied is determined bu the _precedence_of the operators. 

example: / & * have the same precedence 
         _ & + have the same precedence 
         
When multiple operators with the same precedence appear next to eachother, they are applied left to right.

When in doubt, just add paretheses!

**Modulo** or the % symbol is used to represent the remander operation.

example: X % Y is the remainder of dividing X by Y

 314 % 100 ==> 14
 144 % 12 ==> 0

### Special Numbers

Infinity    (Infinity - 1 = Infinity)
-Infinity    
NaN    *is a value of the number type  (0/0 = NaN) (Infinify - Infinity = NaN)


## Strings

**Strings** are used to represent text. 

Newlines (the characters you get when you press ENTER) can be included withough escaping quoted text.
This can happen only when the string is quoted with backtics (\')

_escaping_  - Whenever a blackslash (\) is found inside quoted text, it indicates that the character after it has special meaning. 

A quote that is precesed by a backlash will not end the string but be part of it. 
When an N character occurs after a backslash, it is interpreted as a newline. 
When a T is after a backslash, it means a tab character

example:
"This is the first line\nAnd this is the second"

==> This is the first line
    And this is the second
    
example:
"A newline character is written like \"\\n\"."

==>   "A newline character is written like \"\\n\"."

Strings are modeled as a series of bits to be able to exist inside a computer.

Some characters such as many emoji take up two "character postions"

Strings can be combined using _concatenation_ glueing two strings together

example:
"con" + "cat" + "e" + "nate" ==> "concatenate"

String valued have _methods_ that can be used to perform other operations on them. 

_temperate literals_ can combine other info together and embed other values

something inside `${}` results in a converted string with the included info within that position.

##Unary Operators

Operators can be symbols and some are written as words.
such as the operator:  typeof 

example: console.log(typeof 4.5)
// → number

operators that use two valued are called ** binary operators** while those that take one are called **urnary operators**

