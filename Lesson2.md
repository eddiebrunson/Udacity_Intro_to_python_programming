# Lesson 2: Data Types and Operators

Course outline:

* Data Types: Integers, Floats, Booleans, Strings
* Operators: Arithmetic, Assignment, Comparison, Logical 
* Built-In Functions, Type Conversion 
* Whitespace and Style Guidelines

## 2. Arithemetic Operators

* '+' Addition 
* '-' Subtraction 
* '*' Multipllication 
* '/' Division
* '%' Mod (the remainder after dividing)
* '**' Exponentiation (note that '^' does not do this operation, as other languages)
* '//' Divides and rounds down to the nearest integer

Python follows the usual order or operations: PEMDAS

1. Parentheses 
2. Exponents
3. Multiplication and Division
4. Addition and Subtraction 

___

FAQ: What do the operators `<<, >>, &, |, ~, and ^ do?`

These are **Python's bitwise** operators.

Preamble: Twos-Complement Numbers

All of these operators share something in common -- they are "bitwise" operators. That is, they operate on numbers (normally), but instead of treating that number as if it were a single value, they treat it as if it were a string of bits, written in twos-complement binary. A two's complement binary is same as the classical binary representation for positve integers but is slightly different for negative numbers. Negative numbers are represented by performing the two's complement operation on their absolute value. So a brief summary of twos-complement binary is in order:

Two's Complement binary for Positive Integers:

* 0 is written as "0"
*1 is written as "1"
* 2 is written as "10"
* 3 is "11"
* 4 is "100"
* 5 is "101"
* .
* .
* 1029 is "10000000101" == 2**10 + 2**2 + 2**0 == 1024 + 4 + 1
* Two's Complement binary for Negative Integers:

Negative numbers are written with a leading one instead of a leading zero. So if you are using only 8 bits for your twos-complement numbers, then you treat patterns from "00000000" to "01111111" as the whole numbers from 0 to 127, and reserve "1xxxxxxx" for writing negative numbers. A negative number, -x, is written using the bit pattern for (x-1) with all of the bits complemented (switched from 1 to 0 or 0 to 1). So -1 is complement(1 - 1) = complement(0) = "11111111", and -10 is complement(10 - 1) = complement(9) = complement("00001001") = "11110110". This means that negative numbers go all the way down to -128 ("10000000").

Of course, Python doesn't use 8-bit numbers. It USED to use however many bits were native to your machine, but since that was non-portable, it has recently switched to using an INFINITE number of bits. Thus the number -5 is treated by bitwise operators as if it were written "...1111111111111111111011".

Whew! With that preamble out of the way (and hey, you probably knew this already), the operators are easy to explain:

**The Operators:**

`x << y`

* Returns x with the bits shifted to the left by y places (and new bits on the right-hand-side are zeros). This is the same as multiplying x by 2**y.

`x >> y`

* Returns x with the bits shifted to the right by y places. This is the same as //'ing x by 2**y.

`x & y`

* Does a "bitwise and". Each bit of the output is 1 if the corresponding bit of x AND of y is 1, otherwise it's 0.

`x | y`

* Does a "bitwise or". Each bit of the output is 0 if the corresponding bit of x AND of y is 0, otherwise it's 1.

`~ x`

Returns the complement of x - the number you get by switching each 1 for a 0 and each 0 for a 1. This is the same as -x - 1.

`x ^ y`

Does a "bitwise exclusive or". Each bit of the output is the same as the corresponding bit in x if that bit in y is 0, and it's the complement of the bit in x if that bit in y is 1.

Just remember about that infinite series of 1 bits in a negative number, and these should all make sense.

**Other Classes**

One more point: Python allows operator overloading, so some classes may be written to allow the bitwise operators, but with some other meaning. For instance, the new sets module for Python 2.3 uses | and & for union and intersection.

___

## 5. Variables and Assignment Operators 

**Variables I**

Variables I
Variables are used all the time in Python! Below is the example you saw in the video where we performed the following:

`mv_population = 74728`

Here mv_population is a variable, which holds the value of 74728. This assigns the item on the right to the name on the left, which is actually a little different than mathematical equality, as 74728 does not hold the value of mv_population.

In any case, whatever term is on the left side, is now a name for whatever value is on the right side. Once a value has been assigned to a variable name, you can access the value from the variable name.

However, the above isn't a great way to assign variables in most cases, because our variable names should be descriptive of the values they hold.

Besides writing variable names that are descriptive, there are a few things to watch out for when naming variables in Python.

1. Only use ordinary letters, numbers and underscores in your variable names. They can’t have spaces, and need to start with a letter or underscore.

2. You can’t use reserved words or built-in identifiers that have important purposes in Python, which you’ll learn about throughout this course. A list of python reserved words is described here. Creating names that are descriptive of the values often will help you avoid using any of these words. A quick table of these words is also available below.

3. The pythonic way to name variables is to use all lowercase letters and underscores to separate words.

* YES
```Python
my_height = 58
my_lat = 40
my_long = 105
```
* NO
```Python
my height = 58
MYLONG = 40
MyLat = 105
```

Though the last two of these would work in python, they are not pythonic ways to name variables. The way we name variables is called snake case, because we tend to connect the words with underscores.

## 8. Integers and Float

Integers and Floats
There are two Python data types that could be used for numeric values:

* int - for integer values (whole numbers ex. 4)
* float - for decimal or floating point values (decimals ex. 4.0)
You can create a value that follows the data type by using the following syntax:

x = int(4.7)   # x is now an integer 4
y = float(4)   # y is now a float of 4.0
You can check the type by using the type function:
```Python
>>> print(type(x))
int
>>> print(type(y))
float
```
Because the float, or approximation, for 0.1 is actually slightly more than 0.1, when we add several of them together we can see the difference between the mathematically correct answer and the one that Python creates.
```Python
>>> print(.1 + .1 + .1 == .3)
False
``` 
___

Code style in Python use PEP8 Guidelines 

For Best practices, see [PEP8 Guidlines](https://www.python.org/dev/peps/pep-0008/)
* Keep lines of code between 79-99 characters long
* add spaces correctly to make code more readable 


In general, there are two types of errors to look out for

* Exceptions
* Syntax

An **Exception** is a problem that occurs when the code is running, but a 'Syntax Error' is a problem detected when Python checks the code before it runs it.
 For more details see [Python Tutorial on Errors and Exceptions](https://docs.python.org/3/tutorial/errors.html)

___

## 10. Booleans, Comparison operators, and Logical Operators

**Booleans, Comparison Operators, and Logical** 

The bool data type holds one of the values True or False, which are often encoded as 1 or 0, respectively.

--> Boolean algebra is named for its inventor Goerge Bool. 

There are 6 comparison operators that are common to see in order to obtain a bool value:

**Comparison Operators**

|Symbol Use Case| Bool    |Operation                |
|---------------|:-------:|------------------------:|
| 5 < 3         | False   | Less Than               |
| 5 > 3         | True    | Greater Than            |
| 3 <= 3        | True    | Less Than or Equal To   |
| 3 >= 5        | False   | Greater Than or Equal To|
| 3 == 5        | False   | Equal To                |
| 3 != 5        | True    | Not Equal To            |

And there are three logical operators you need to be familiar with:

|Logical Use| Bool  | Operation                                             | 
| ----------|:-----:| ------------------------------------------------------|
| 5 < 3 'and' 5 == 5| False|'and' - Evaluates if all provided statements are True|
|5 < 3 'or' 5 == 5| True | 'or' - Evaluates if at least one of many statements is True|
|'not' 5 < 3|  True|   'not' - Flips the Bool Value|

11. Quiz: Which is denser, Rio or San Francisco?

```Python 
sf_population, sf_area = 864816, 231.89
rio_population, rio_area = 6453682, 486.5

san_francisco_pop_density = sf_population/sf_area
rio_de_janeiro_pop_density = rio_population/rio_area

# Write code that prints True if San Francisco is denser than Rio, and False otherwise

print(san_francisco_pop_density > rio_de_janeiro_pop_density)

False
```
or, but the above is more simplier to write!!!

```Python
if (san_francisco_pop_density > rio_de_janeiro_pop_density):
    print (True)
else:
    print (False)
```
## 13. Strings

**String Methods**

**Methods** are like some of the some of the following **functions**:

1. `len`("this")
2. `type`(12) 
3. `print`("Hello wordl")

These three above are **functions** - notice they use parentheses, and accept one or more **arguments**. 

A **method** in Python behaves similarly to a function. Methods actually are functions that are colled using dot notation. For example, `lower()` is a string method that can be used like this, on a string called "sample string": `sample_string.lower()`.

Methods are specific to the datat type for a particular variable. So there are some built0in methods that are available for all strings, different methods that are available for all integers, etc. 

Examples of methods that are possible with any string:

```Python

my_string = "sebastian thrun"

my_string.
|capitalize()| encode()| format()| isalpha()| islower()| istitle()|
|casefold()| endswith()| format_map()| isdecimal()| isnumeric()| isupper()|
|center()| expandtabs()| index()| isdigit()| isprintable()| join()|
|count()| find()| isalnum()| isidentifier()|  isspace()| 1just()|
```
Each of the above methods accepts the string itself as the first argument of the method. However, they also could receive additional arguments, that are passed inside the parentheses. For example: 

```Python 

>>> my_string.islower()
True
>>> my_string.count('a')
2
>>> my_string.find('a')
3
```

The `count` and `find` methods both take another argument. However, the `.islower()` method does not accept another argument. 

No professional has all the methods memorized, which is why understanding how to use documentation and find answers is so important. Gaining a string grasp of the foundations of programming will allow you to use those foundations to use documentation to build so much more than someone who tries to memorize all the built-in methods in Python. 

**One important method: `format(`

Usually found in `print` statements. 

For example:

**Example 1**

`print("Mohammed has {} balloons."format(27))`

**Example 1 Output**

`Mohammed has 27 balloons`

**Example 2**

```Python 

animal = "dog"
aciton = "bite"
print("Does your {} {}?".format(animal, action))
```
**Example 2 Output**

`Does your dog bite?`

**Example 3**
```Python
maria_string = "Maria loves {} and {}"
print(maria_string.format("math, "statistics"))
```

**Example 3 Output**

`Maria loves math and statistics`




