---
Description: Go - Quick Guide
Notes: Go - Quick Guide - Go is a general-purpose language designed with systems programming in mind. It was initially developed at Google in the year 2007 by Robert Griesemer, Rob Pike, and Ken Thompson. It is strongly and statically typed, provides inbuilt support for garbage collection, and supports concurrent programming
author: 
Url: https://www.tutorialspoint.com/go/go_quick_guide.htm
Created: "2025-01-29  02:38:55"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go - Quick Guide

source: https://www.tutorialspoint.com/go/go_quick_guide.htm

> ## Excerpt
> Go - Quick Guide - Go is a general-purpose language designed with systems programming in mind. It was initially developed at Google in the year 2007 by Robert Griesemer, Rob Pike, and Ken Thompson. It is strongly and statically typed, provides inbuilt support for garbage collection, and supports concurrent programming

---
___

___

## Go - Overview

Go is a general-purpose language designed with systems programming in mind. It was initially developed at Google in the year 2007 by Robert Griesemer, Rob Pike, and Ken Thompson. It is strongly and statically typed, provides inbuilt support for garbage collection, and supports concurrent programming.

Programs are constructed using packages, for efficient management of dependencies. Go programming implementations use a traditional compile and link model to generate executable binaries. The Go programming language was announced in November 2009 and is used in some of the Google's production systems.

## Features of Go Programming

The most important features of Go programming are listed below −

-   Support for environment adopting patterns similar to dynamic languages. For example, type inference (x := 0 is valid declaration of a variable x of type int)
    
-   Compilation time is fast.
    
-   Inbuilt concurrency support: lightweight processes (via go routines), channels, select statement.
    
-   Go programs are simple, concise, and safe.
    
-   Support for Interfaces and Type embedding.
    
-   Production of statically linked native binaries without external dependencies.
    

## Features Excluded Intentionally

To keep the language simple and concise, the following features commonly available in other similar languages are omitted in Go −

-   Support for type inheritance
    
-   Support for method or operator overloading
    
-   Support for circular dependencies among packages
    
-   Support for pointer arithmetic
    
-   Support for assertions
    
-   Support for generic programming
    

[

Explore our **latest online courses** and learn new skills at your own pace. Enroll and become a certified expert to boost your career.

](https://www.tutorialspoint.com/latest/courses?utm_source=tutorialspoint&utm_medium=tutorials_3p&utm_campaign=internal)

## Go Programs

A Go program can vary in length from 3 lines to millions of lines and it should be written into one or more text files with the extension ".go". For example, hello.go.

You can use "vi", "vim" or any other text editor to write your Go program into a file.

## Go - Environment Setup

## Local Environment Setup

If you are still willing to set up your environment for Go programming language, you need the following two software available on your computer −

-   A text editor
-   Go compiler

## Text Editor

You will require a text editor to type your programs. Examples of text editors include Windows Notepad, OS Edit command, Brief, Epsilon, EMACS, and vim or vi.

The name and version of text editors can vary on different operating systems. For example, Notepad is used on Windows, and vim or vi is used on Windows as well as Linux or UNIX.

The files you create with the text editor are called **source files**. They contain program source code. The source files for Go programs are typically named with the extension **".go"**.

Before starting your programming, make sure you have a text editor in place and you have enough experience to write a computer program, save it in a file, compile it, and finally execute it.

## The Go Compiler

The source code written in source file is the human readable source for your program. It needs to be compiled and turned into machine language so that your CPU can actually execute the program as per the instructions given. The Go programming language compiler compiles the source code into its final executable program.

Go distribution comes as a binary installable for FreeBSD (release 8 and above), Linux, Mac OS X (Snow Leopard and above), and Windows operating systems with 32-bit (386) and 64-bit (amd64) x86 processor architectures.

The following section explains how to install Go binary distribution on various OS.

## Download Go Archive

Download the latest version of Go installable archive file from [Go Downloads](https://golang.org/dl/). The following version is used in this tutorial: _go1.4.windows-amd64.msi_.

It is copied it into C:\\>go folder.

| OS | Archive name |
| --- | --- |
| Windows | go1.4.windows-amd64.msi |
| Linux | go1.4.linux-amd64.tar.gz |
| Mac | go1.4.darwin-amd64-osx10.8.pkg |
| FreeBSD | go1.4.freebsd-amd64.tar.gz |

## Installation on UNIX/Linux/Mac OS X, and FreeBSD

Extract the download archive into the folder /usr/local, creating a Go tree in /usr/local/go. For example −

tar -C /usr/local -xzf go1.4.linux-amd64.tar.gz

Add /usr/local/go/bin to the PATH environment variable.

| OS | Output |
| --- | --- |
| Linux | export PATH = $PATH:/usr/local/go/bin |
| Mac | export PATH = $PATH:/usr/local/go/bin |
| FreeBSD | export PATH = $PATH:/usr/local/go/bin |

## Installation on Windows

Use the MSI file and follow the prompts to install the Go tools. By default, the installer uses the Go distribution in c:\\Go. The installer should set the c:\\Go\\bin directory in Window's PATH environment variable. Restart any open command prompts for the change to take effect.

## Verifying the Installation

Create a go file named test.go in **C:\\>Go\_WorkSpace**.

### File: test.go

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

func main</span><span>()</span><span> </span><span>{</span><span>
   fmt</span><span>.</span><span>Println</span><span>(</span><span>"Hello, World!"</span><span>)</span><span>
</span><span>}</span>
```

Now run test.go to see the result −

```
C:\Go_WorkSpace&gt;go run test.go
```

### Output

```
Hello, World!
```

## Go - Program Structure

Before we study the basic building blocks of Go programming language, let us first discuss the bare minimum structure of Go programs so that we can take it as a reference in subsequent chapters.

## Hello World Example

A Go program basically consists of the following parts −

-   Package Declaration
-   Import Packages
-   Functions
-   Variables
-   Statements and Expressions
-   Comments

Let us look at a simple code that would print the words "Hello World" −

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

func main</span><span>()</span><span> </span><span>{</span><span>
   </span><span>/* This is my first sample program. */</span><span>
   fmt</span><span>.</span><span>Println</span><span>(</span><span>"Hello, World!"</span><span>)</span><span>
</span><span>}</span>
```

Let us take a look at the various parts of the above program −

-   The first line of the program package main defines the package name in which this program should lie. It is a mandatory statement, as Go programs run in packages. The main package is the starting point to run the program. Each package has a path and name associated with it.
    
-   The next line import "fmt" is a preprocessor command which tells the Go compiler to include the files lying in the package fmt.
    
-   The next line func main() is the main function where the program execution begins.
    
-   The next line /\*...\*/ is ignored by the compiler and it is there to add comments in the program. Comments are also represented using // similar to Java or C++ comments.
    
-   The next line fmt.Println(...) is another function available in Go which causes the message "Hello, World!" to be displayed on the screen. Here fmt package has exported Println method which is used to display the message on the screen.
    
-   Notice the capital P of Println method. In Go language, a name is exported if it starts with capital letter. Exported means the function or variable/constant is accessible to the importer of the respective package.
    

## Executing a Go Program

Let us discuss how to save the source code in a file, compile it, and finally execute the program. Please follow the steps given below −

-   Open a text editor and add the above-mentioned code.
    
-   Save the file as _hello.go_
    
-   Open the command prompt.
    
-   Go to the directory where you saved the file.
    
-   Type go run _hello.go_ and press enter to run your code.
    
-   If there are no errors in your code, then you will see _"Hello World!"_ printed on the screen.
    

```
$ go run hello.go
Hello, World!
```

Make sure the Go compiler is in your path and that you are running it in the directory containing the source file hello.go.

## Go - Basic Syntax

We discussed the basic structure of a Go program in the previous chapter. Now it will be easy to understand the other basic building blocks of the Go programming language.

## Tokens in Go

A Go program consists of various tokens. A token is either a keyword, an identifier, a constant, a string literal, or a symbol. For example, the following Go statement consists of six tokens −

```
fmt.Println("Hello, World!")
```

The individual tokens are −

```
<span>fmt
</span><span>.</span><span>
</span><span>Println</span><span>
</span><span>(</span><span>
   </span><span>"Hello, World!"</span><span>
</span><span>)</span>
```

## Line Separator

In a Go program, the line separator key is a statement terminator. That is, individual statements don't need a special separator like “;” in C. The Go compiler internally places “;” as the statement terminator to indicate the end of one logical entity.

For example, take a look at the following statements −

```
fmt.Println("Hello, World!")
fmt.Println("I am in Go Programming World!")
```

## Comments

Comments are like helping texts in your Go program and they are ignored by the compiler. They start with /\* and terminates with the characters \*/ as shown below −

```
/* my first program in Go */
```

You cannot have comments within comments and they do not occur within a string or character literals.

## Identifiers

A Go identifier is a name used to identify a variable, function, or any other user-defined item. An identifier starts with a letter A to Z or a to z or an underscore \_ followed by zero or more letters, underscores, and digits (0 to 9).

identifier = letter { letter | unicode\_digit }.

Go does not allow punctuation characters such as @, $, and % within identifiers. Go is a **case-sensitive** programming language. Thus, _Manpower_ and _manpower_ are two different identifiers in Go. Here are some examples of acceptable identifiers −

```
mahesh      kumar   abc   move_name   a_123
myname50   _temp    j      a23b9      retVal
```

## Keywords

The following list shows the reserved words in Go. These reserved words may not be used as constant or variable or any other identifier names.

<table><tbody><tr><td>break</td><td>default</td><td>func</td><td>interface</td><td>select</td></tr><tr><td>case</td><td>defer</td><td>Go</td><td>map</td><td>Struct</td></tr><tr><td>chan</td><td>else</td><td>Goto</td><td>package</td><td>Switch</td></tr><tr><td>const</td><td>fallthrough</td><td>if</td><td>range</td><td>Type</td></tr><tr><td>continue</td><td>for</td><td>import</td><td>return</td><td>Var</td></tr></tbody></table>

## Whitespace in Go

Whitespace is the term used in Go to describe blanks, tabs, newline characters, and comments. A line containing only whitespace, possibly with a comment, is known as a blank line, and a Go compiler totally ignores it.

Whitespaces separate one part of a statement from another and enables the compiler to identify where one element in a statement, such as int, ends and the next element begins. Therefore, in the following statement −

```
var age int;
```

There must be at least one whitespace character (usually a space) between int and age for the compiler to be able to distinguish them. On the other hand, in the following statement −

```
fruit = apples + oranges;   // get the total fruit
```

No whitespace characters are necessary between fruit and =, or between = and apples, although you are free to include some if you wish for readability purpose.

## Go - Data Types

In the Go programming language, data types refer to an extensive system used for declaring variables or functions of different types. The type of a variable determines how much space it occupies in storage and how the bit pattern stored is interpreted.

The types in Go can be classified as follows −

| Sr.No. | Types and Description |
| --- | --- |
| 1 | 
**Boolean types**

They are boolean types and consists of the two predefined constants: (a) true (b) false

 |
| 2 | 

**Numeric types**

They are again arithmetic types and they represents a) integer types or b) floating point values throughout the program.

 |
| 3 | 

**String types**

A string type represents the set of string values. Its value is a sequence of bytes. Strings are immutable types that is once created, it is not possible to change the contents of a string. The predeclared string type is string.

 |
| 4 | 

**Derived types**

They include (a) Pointer types, (b) Array types, (c) Structure types, (d) Union types and (e) Function types f) Slice types g) Interface types h) Map types i) Channel Types

 |

Array types and structure types are collectively referred to as **aggregate types**. The type of a function specifies the set of all functions with the same parameter and result types. We will discuss the basic types in the following section, whereas other types will be covered in the upcoming chapters.

## Integer Types

The predefined architecture-independent integer types are −

| Sr.No. | Types and Description |
| --- | --- |
| 1 | 
**uint8**

Unsigned 8-bit integers (0 to 255)

 |
| 2 | 

**uint16**

Unsigned 16-bit integers (0 to 65535)

 |
| 3 | 

**uint32**

Unsigned 32-bit integers (0 to 4294967295)

 |
| 4 | 

**uint64**

Unsigned 64-bit integers (0 to 18446744073709551615)

 |
| 5 | 

**int8**

Signed 8-bit integers (-128 to 127)

 |
| 6 | 

**int16**

Signed 16-bit integers (-32768 to 32767)

 |
| 7 | 

**int32**

Signed 32-bit integers (-2147483648 to 2147483647)

 |
| 8 | 

**int64**

Signed 64-bit integers (-9223372036854775808 to 9223372036854775807)

 |

## Floating Types

The predefined architecture-independent float types are −

| Sr.No. | Types and Description |
| --- | --- |
| 1 | 
**float32**

IEEE-754 32-bit floating-point numbers

 |
| 2 | 

**float64**

IEEE-754 64-bit floating-point numbers

 |
| 3 | 

**complex64**

Complex numbers with float32 real and imaginary parts

 |
| 4 | 

**complex128**

Complex numbers with float64 real and imaginary parts

 |

The value of an n-bit integer is n bits and is represented using two's complement arithmetic operations.

## Other Numeric Types

There is also a set of numeric types with implementation-specific sizes −

| Sr.No. | Types and Description |
| --- | --- |
| 1 | 
**byte**

same as uint8

 |
| 2 | 

**rune**

same as int32

 |
| 3 | 

**uint**

32 or 64 bits

 |
| 4 | 

**int**

same size as uint

 |
| 5 | 

**uintptr**

an unsigned integer to store the uninterpreted bits of a pointer value

 |

## Go - Variables

A variable is nothing but a name given to a storage area that the programs can manipulate. Each variable in Go has a specific type, which determines the size and layout of the variable's memory, the range of values that can be stored within that memory, and the set of operations that can be applied to the variable.

The name of a variable can be composed of letters, digits, and the underscore character. It must begin with either a letter or an underscore. Upper and lowercase letters are distinct because Go is case-sensitive. Based on the basic types explained in the previous chapter, there will be the following basic variable types −

| Sr.No | Type & Description |
| --- | --- |
| 1 | 
**byte**

Typically a single octet(one byte). This is an byte type.

 |
| 2 | 

**int**

The most natural size of integer for the machine.

 |
| 3 | 

**float32**

A single-precision floating point value.

 |

Go programming language also allows to define various other types of variables such as Enumeration, Pointer, Array, Structure, and Union, which we will discuss in subsequent chapters. In this chapter, we will focus only basic variable types.

## Variable Definition in Go

A variable definition tells the compiler where and how much storage to create for the variable. A variable definition specifies a data type and contains a list of one or more variables of that type as follows −

```
var variable_list optional_data_type;
```

Here, **optional\_data\_type** is a valid Go data type including byte, int, float32, complex64, boolean or any user-defined object, etc., and **variable\_list** may consist of one or more identifier names separated by commas. Some valid declarations are shown here −

```
var  i, j, k int;
var  c, ch byte;
var  f, salary float32;
d =  42;
```

The statement **“var i, j, k;”** declares and defines the variables i, j and k; which instructs the compiler to create variables named i, j, and k of type int.

Variables can be initialized (assigned an initial value) in their declaration. The type of variable is automatically judged by the compiler based on the value passed to it. The initializer consists of an equal sign followed by a constant expression as follows −

```
variable_name = value;
```

For example,

```
d = 3, f = 5;    // declaration of d and f. Here d and f are int 
```

For definition without an initializer: variables with static storage duration are implicitly initialized with nil (all bytes have the value 0); the initial value of all other variables is zero value of their data type.

## Static Type Declaration in Go

A static type variable declaration provides assurance to the compiler that there is one variable available with the given type and name so that the compiler can proceed for further compilation without requiring the complete detail of the variable. A variable declaration has its meaning at the time of compilation only, the compiler needs the actual variable declaration at the time of linking of the program.

### Example

Try the following example, where the variable has been declared with a type and initialized inside the main function −

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

func main</span><span>()</span><span> </span><span>{</span><span>
   </span><span>var</span><span> x float64
   x </span><span>=</span><span> </span><span>20.0</span><span>
   fmt</span><span>.</span><span>Println</span><span>(</span><span>x</span><span>)</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"x is of type %T\n"</span><span>,</span><span> x</span><span>)</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
20
x is of type float64
```

## Dynamic Type Declaration / Type Inference in Go

A dynamic type variable declaration requires the compiler to interpret the type of the variable based on the value passed to it. The compiler does not require a variable to have type statically as a necessary requirement.

### Example

Try the following example, where the variables have been declared without any type. Notice, in case of type inference, we initialized the variable **y** with := operator, whereas **x** is initialized using = operator.

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

func main</span><span>()</span><span> </span><span>{</span><span>
   </span><span>var</span><span> x float64 </span><span>=</span><span> </span><span>20.0</span><span>

   y </span><span>:=</span><span> </span><span>42</span><span> 
   fmt</span><span>.</span><span>Println</span><span>(</span><span>x</span><span>)</span><span>
   fmt</span><span>.</span><span>Println</span><span>(</span><span>y</span><span>)</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"x is of type %T\n"</span><span>,</span><span> x</span><span>)</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"y is of type %T\n"</span><span>,</span><span> y</span><span>)</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
20
42
x is of type float64
y is of type int
```

## Mixed Variable Declaration in Go

Variables of different types can be declared in one go using type inference.

### Example

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

func main</span><span>()</span><span> </span><span>{</span><span>
   </span><span>var</span><span> a</span><span>,</span><span> b</span><span>,</span><span> c </span><span>=</span><span> </span><span>3</span><span>,</span><span> </span><span>4</span><span>,</span><span> </span><span>"foo"</span><span>  

   fmt</span><span>.</span><span>Println</span><span>(</span><span>a</span><span>)</span><span>
   fmt</span><span>.</span><span>Println</span><span>(</span><span>b</span><span>)</span><span>
   fmt</span><span>.</span><span>Println</span><span>(</span><span>c</span><span>)</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"a is of type %T\n"</span><span>,</span><span> a</span><span>)</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"b is of type %T\n"</span><span>,</span><span> b</span><span>)</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"c is of type %T\n"</span><span>,</span><span> c</span><span>)</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
3
4
foo
a is of type int
b is of type int
c is of type string
```

## The lvalues and the rvalues in Go

There are two kinds of expressions in Go −

-   **lvalue** − Expressions that refer to a memory location is called "lvalue" expression. An lvalue may appear as either the left-hand or right-hand side of an assignment.
    
-   **rvalue** − The term rvalue refers to a data value that is stored at some address in memory. An rvalue is an expression that cannot have a value assigned to it which means an rvalue may appear on the right- but not left-hand side of an assignment.
    

Variables are lvalues and so may appear on the left-hand side of an assignment. Numeric literals are rvalues and so may not be assigned and can not appear on the left-hand side.

The following statement is valid −

```
x = 20.0
```

The following statement is not valid. It would generate compile-time error −

```
10 = 20
```

## Go - Constants

Constants refer to fixed values that the program may not alter during its execution. These fixed values are also called **literals**.

Constants can be of any of the basic data types like _an integer constant, a floating constant, a character constant, or a string literal_. There are also enumeration constants as well.

Constants are treated just like regular variables except that their values cannot be modified after their definition.

## Integer Literals

An integer literal can be a decimal, octal, or hexadecimal constant. A prefix specifies the base or radix: 0x or 0X for hexadecimal, 0 for octal, and nothing for decimal.

An integer literal can also have a suffix that is a combination of U and L, for unsigned and long, respectively. The suffix can be uppercase or lowercase and can be in any order.

Here are some examples of integer literals −

```
212         /* Legal */
215u        /* Legal */
0xFeeL      /* Legal */
078         /* Illegal: 8 is not an octal digit */
032UU       /* Illegal: cannot repeat a suffix */
```

Following are other examples of various type of Integer literals −

```
85         /* decimal */
0213       /* octal */
0x4b       /* hexadecimal */
30         /* int */
30u        /* unsigned int */
30l        /* long */
30ul       /* unsigned long */
```

## Floating-point Literals

A floating-point literal has an integer part, a decimal point, a fractional part, and an exponent part. You can represent floating point literals either in decimal form or exponential form.

While representing using decimal form, you must include the decimal point, the exponent, or both and while representing using exponential form, you must include the integer part, the fractional part, or both. The signed exponent is introduced by e or E.

Here are some examples of floating-point literals −

```
3.14159       /* Legal */
314159E-5L    /* Legal */
510E          /* Illegal: incomplete exponent */
210f          /* Illegal: no decimal or exponent */
.e55          /* Illegal: missing integer or fraction */
```

## Escape Sequence

When certain characters are preceded by a backslash, they will have a special meaning in Go. These are known as Escape Sequence codes which are used to represent newline (\\n), tab (\\t), backspace, etc. Here, you have a list of some of such escape sequence codes −

| Escape sequence | Meaning |
| --- | --- |
| \\\\ | \\ character |
| \\' | ' character |
| \\" | " character |
| \\? | ? character |
| \\a | Alert or bell |
| \\b | Backspace |
| \\f | Form feed |
| \\n | Newline |
| \\r | Carriage return |
| \\t | Horizontal tab |
| \\v | Vertical tab |
| \\ooo | Octal number of one to three digits |
| \\xhh . . . | Hexadecimal number of one or more digits |

The following example shows how to use **\\t** in a program −

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

func main</span><span>()</span><span> </span><span>{</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"Hello\tWorld!"</span><span>)</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
Hello World!
```

## String Literals in Go

String literals or constants are enclosed in double quotes "". A string contains characters that are similar to character literals: plain characters, escape sequences, and universal characters.

You can break a long line into multiple lines using string literals and separating them using whitespaces.

Here are some examples of string literals. All the three forms are identical strings.

```
"hello, dear"

"hello, \

dear"

"hello, " "d" "ear"
```

## The _const_ Keyword

You can use **const** prefix to declare constants with a specific type as follows −

```
const variable type = value;
```

The following example shows how to use the **const** keyword −

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

func main</span><span>()</span><span> </span><span>{</span><span>
   </span><span>const</span><span> LENGTH </span><span>int</span><span> </span><span>=</span><span> </span><span>10</span><span>
   </span><span>const</span><span> WIDTH </span><span>int</span><span> </span><span>=</span><span> </span><span>5</span><span>   
   </span><span>var</span><span> area </span><span>int</span><span>

   area </span><span>=</span><span> LENGTH </span><span>*</span><span> WIDTH
   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"value of area : %d"</span><span>,</span><span> area</span><span>)</span><span>   
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
value of area : 50
```

Note that it is a good programming practice to define constants in CAPITALS.

## Go - Operators

An operator is a symbol that tells the compiler to perform specific mathematical or logical manipulations. Go language is rich in built-in operators and provides the following types of operators −

-   Arithmetic Operators
-   Relational Operators
-   Logical Operators
-   Bitwise Operators
-   Assignment Operators
-   Miscellaneous Operators

This tutorial explains arithmetic, relational, logical, bitwise, assignment, and other operators one by one.

## Arithmetic Operators

Following table shows all the arithmetic operators supported by Go language. Assume variable **A** holds 10 and variable **B** holds 20 then −

[Show Examples](https://www.tutorialspoint.com/go/go_arithmetic_operators.htm "Arithmetic Operators in Go")

| Operator | Description | Example |
| --- | --- | --- |
| + | Adds two operands | A + B gives 30 |
| \- | Subtracts second operand from the first | A - B gives -10 |
| \* | Multiplies both operands | A \* B gives 200 |
| / | Divides the numerator by the denominator. | B / A gives 2 |
| % | Modulus operator; gives the remainder after an integer division. | B % A gives 0 |
| ++ | Increment operator. It increases the integer value by one. | A++ gives 11 |
| \-- | Decrement operator. It decreases the integer value by one. | A-- gives 9 |

## Relational Operators

The following table lists all the relational operators supported by Go language. Assume variable **A** holds 10 and variable **B** holds 20, then −

[Show Examples](https://www.tutorialspoint.com/go/go_relational_operators.htm "Relational Operators in Go")

| Operator | Description | Example |
| --- | --- | --- |
| \== | It checks if the values of two operands are equal or not; if yes, the condition becomes true. | (A == B) is not true. |
| != | It checks if the values of two operands are equal or not; if the values are not equal, then the condition becomes true. | (A != B) is true. |
| \> | It checks if the value of left operand is greater than the value of right operand; if yes, the condition becomes true. | (A > B) is not true. |
| < | It checks if the value of left operand is less than the value of the right operand; if yes, the condition becomes true. | (A < B) is true. |
| \>= | It checks if the value of the left operand is greater than or equal to the value of the right operand; if yes, the condition becomes true. | (A >= B) is not true. |
| <= | It checks if the value of left operand is less than or equal to the value of right operand; if yes, the condition becomes true. | (A <= B) is true. |

## Logical Operators

The following table lists all the logical operators supported by Go language. Assume variable **A** holds 1 and variable **B** holds 0, then −

[Show Examples](https://www.tutorialspoint.com/go/go_logical_operators.htm "Logical Operators in Go")

| Operator | Description | Example |
| --- | --- | --- |
| && | Called Logical AND operator. If both the operands are non-zero, then condition becomes true. | (A && B) is false. |
| || | Called Logical OR Operator. If any of the two operands is non-zero, then condition becomes true. | (A || B) is true. |
| ! | Called Logical NOT Operator. Use to reverses the logical state of its operand. If a condition is true then Logical NOT operator will make false. | !(A && B) is true. |

The following table shows all the logical operators supported by Go language. Assume variable **A** holds true and variable **B** holds false, then −

| Operator | Description | Example |
| --- | --- | --- |
| && | Called Logical AND operator. If both the operands are false, then the condition becomes false. | (A && B) is false. |
| || | Called Logical OR Operator. If any of the two operands is true, then the condition becomes true. | (A || B) is true. |
| ! | Called Logical NOT Operator. Use to reverses the logical state of its operand. If a condition is true, then Logical NOT operator will make it false. | !(A && B) is true. |

## Bitwise Operators

Bitwise operators work on bits and perform bit-by-bit operation. The truth tables for &, |, and ^ are as follows −

| p | q | p & q | p | q | p ^ q |
| --- | --- | --- | --- | --- |
| 0 | 0 | 0 | 0 | 0 |
| 0 | 1 | 0 | 1 | 1 |
| 1 | 1 | 1 | 1 | 0 |
| 1 | 0 | 0 | 1 | 1 |

Assume A = 60; and B = 13. In binary format, they will be as follows −

A = 0011 1100

B = 0000 1101

\-----------------

A&B = 0000 1100

A|B = 0011 1101

A^B = 0011 0001

~A  = 1100 0011

The Bitwise operators supported by C language are listed in the following table. Assume variable A holds 60 and variable B holds 13, then −

[Show Examples](https://www.tutorialspoint.com/go/go_bitwise_operators.htm "Bitwise Operators in Go")

| Operator | Description | Example |
| --- | --- | --- |
| & | Binary AND Operator copies a bit to the result if it exists in both operands. | (A & B) will give 12, which is 0000 1100 |
| | | Binary OR Operator copies a bit if it exists in either operand. | (A | B) will give 61, which is 0011 1101 |
| ^ | Binary XOR Operator copies the bit if it is set in one operand but not both. | (A ^ B) will give 49, which is 0011 0001 |
| << | Binary Left Shift Operator. The left operands value is moved left by the number of bits specified by the right operand. | A << 2 will give 240 which is 1111 0000 |
| \>> | Binary Right Shift Operator. The left operands value is moved right by the number of bits specified by the right operand. | A >> 2 will give 15 which is 0000 1111 |

## Assignment Operators

The following table lists all the assignment operators supported by Go language −

[Show Examples](https://www.tutorialspoint.com/go/go_assignment_operators.htm "Assignment Operators in Go")

| Operator | Description | Example |
| --- | --- | --- |
| \= | Simple assignment operator, Assigns values from right side operands to left side operand | C = A + B will assign value of A + B into C |
| += | Add AND assignment operator, It adds right operand to the left operand and assign the result to left operand | C += A is equivalent to C = C + A |
| \-= | Subtract AND assignment operator, It subtracts right operand from the left operand and assign the result to left operand | C -= A is equivalent to C = C - A |
| \*= | Multiply AND assignment operator, It multiplies right operand with the left operand and assign the result to left operand | C \*= A is equivalent to C = C \* A |
| /= | Divide AND assignment operator, It divides left operand with the right operand and assign the result to left operand | C /= A is equivalent to C = C / A |
| %= | Modulus AND assignment operator, It takes modulus using two operands and assign the result to left operand | C %= A is equivalent to C = C % A |
| <<= | Left shift AND assignment operator | C <<= 2 is same as C = C << 2 |
| \>>= | Right shift AND assignment operator | C >>= 2 is same as C = C >> 2 |
| &= | Bitwise AND assignment operator | C &= 2 is same as C = C & 2 |
| ^= | bitwise exclusive OR and assignment operator | C ^= 2 is same as C = C ^ 2 |
| |= | bitwise inclusive OR and assignment operator | C |= 2 is same as C = C | 2 |

## Miscellaneous Operators

There are a few other important operators supported by Go Language including **sizeof** and **?:.**

[Show Examples](https://www.tutorialspoint.com/go/go_misc_operator.htm "Misc operators in Go")

| Operator | Description | Example |
| --- | --- | --- |
| & | Returns the address of a variable. | &a; provides actual address of the variable. |
| \* | Pointer to a variable. | \*a; provides pointer to a variable. |

## Operators Precedence in Go

Operator precedence determines the grouping of terms in an expression. This affects how an expression is evaluated. Certain operators have higher precedence than others; for example, the multiplication operator has higher precedence than the addition operator.

For example x = 7 + 3 \* 2; here, x is assigned 13, not 20 because operator \* has higher precedence than +, so it first gets multiplied with 3\*2 and then adds into 7.

Here, operators with the highest precedence appear at the top of the table, those with the lowest appear at the bottom. Within an expression, higher precedence operators will be evaluated first.

[Show Examples](https://www.tutorialspoint.com/go/go_operators_precedence.htm "Operators Precedence in Go")

| Category | Operator | Associativity |
| --- | --- | --- |
| Postfix | () \[\] -> . ++ - - | Left to right |
| Unary | \+ - ! ~ ++ - - (type)\* & sizeof | Right to left |
| Multiplicative | \* / % | Left to right |
| Additive | \+ - | Left to right |
| Shift | << >> | Left to right |
| Relational | < <= > >= | Left to right |
| Equality | \== != | Left to right |
| Bitwise AND | & | Left to right |
| Bitwise XOR | ^ | Left to right |
| Bitwise OR | | | Left to right |
| Logical AND | && | Left to right |
| Logical OR | || | Left to right |
| Assignment | \= += -= \*= /= %=>>= <<= &= ^= |= | Right to left |
| Comma | , | Left to right |

## Go - Decision Making

Decision making structures require that the programmer specify one or more conditions to be evaluated or tested by the program, along with a statement or statements to be executed if the condition is determined to be true, and optionally, other statements to be executed if the condition is determined to be false.

Following is the general form of a typical decision making structure found in most of the programming languages −

![Decision making statements in Go](https://www.tutorialspoint.com/go/images/decision_making.jpg)

Go programming language provides the following types of decision making statements. Click the following links to check their detail.

| Sr.No | Statement & Description |
| --- | --- |
| 1 | [if statement](https://www.tutorialspoint.com/go/go_if_statement.htm "if statement in Go")
An **if statement** consists of a boolean expression followed by one or more statements.

 |
| 2 | [if...else statement](https://www.tutorialspoint.com/go/go_if_else_statement.htm "if...else statement in Go")

An **if statement** can be followed by an optional **else statement**, which executes when the boolean expression is false.

 |
| 3 | [nested if statements](https://www.tutorialspoint.com/go/go_nested_if_statements.htm "nested if statements in Go")

You can use one **if** or **else if** statement inside another **if** or **else if** statement(s).

 |
| 4 | [switch statement](https://www.tutorialspoint.com/go/go_switch_statement.htm "switch statement in Go")

A **switch** statement allows a variable to be tested for equality against a list of values.

 |
| 5 | [select statement](https://www.tutorialspoint.com/go/go_select_statement.htm "select statement in Go")

A **select** statement is similar to **switch** statement with difference that case statements refers to channel communications.

 |

## Go - Loops

There may be a situation, when you need to execute a block of code several number of times. In general, statements are executed sequentially: The first statement in a function is executed first, followed by the second, and so on.

Programming languages provide various control structures that allow for more complicated execution paths.

A loop statement allows us to execute a statement or group of statements multiple times and following is the general form of a loop statement in most of the programming languages −

![Loop Architecture](https://www.tutorialspoint.com/go/images/loop_architecture.jpg)

Go programming language provides the following types of loop to handle looping requirements.

| Sr.No | Loop Type & Description |
| --- | --- |
| 1 | [for loop](https://www.tutorialspoint.com/go/go_for_loop.htm "for loop in Go")
It executes a sequence of statements multiple times and abbreviates the code that manages the loop variable.

 |
| 2 | [nested loops](https://www.tutorialspoint.com/go/go_nested_loops.htm "nested for loops in Go")

These are one or multiple loops inside any for loop.

 |

## Loop Control Statements

Loop control statements change an execution from its normal sequence. When an execution leaves its scope, all automatic objects that were created in that scope are destroyed.

Go supports the following control statements −

| Sr.No | Control Statement & Description |
| --- | --- |
| 1 | [break statement](https://www.tutorialspoint.com/go/go_break_statement.htm "break statement in Go")
It terminates a **for loop** or **switch** statement and transfers execution to the statement immediately following the for loop or switch.

 |
| 2 | [continue statement](https://www.tutorialspoint.com/go/go_continue_statement.htm "continue statement in Go")

It causes the loop to skip the remainder of its body and immediately retest its condition prior to reiterating.

 |
| 3 | [goto statement](https://www.tutorialspoint.com/go/go_goto_statement.htm "goto statement in Go")

It transfers control to the labeled statement.

 |

## The Infinite Loop

A loop becomes an infinite loop if its condition never becomes false. The for loop is traditionally used for this purpose. Since none of the three expressions that form the for loop are required, you can make an endless loop by leaving the conditional expression empty or by passing true to it.

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

func main</span><span>()</span><span> </span><span>{</span><span>
   </span><span>for</span><span> </span><span>true</span><span>  </span><span>{</span><span>
       fmt</span><span>.</span><span>Printf</span><span>(</span><span>"This loop will run forever.\n"</span><span>);</span><span>
   </span><span>}</span><span>
</span><span>}</span>
```

When the conditional expression is absent, it is assumed to be true. You may have an initialization and increment expression, but C programmers more commonly use the for(;;) construct to signify an infinite loop.

**Note** − You can terminate an infinite loop by pressing Ctrl + C keys.

## Go - Functions

A function is a group of statements that together perform a task. Every Go program has at least one function, which is **main()**. You can divide your code into separate functions. How you divide your code among different functions is up to you, but logically, the division should be such that each function performs a specific task.

A function **declaration** tells the compiler about a function name, return type, and parameters. A function **definition** provides the actual body of the function.

The Go standard library provides numerous built-in functions that your program can call. For example, the function **len()** takes arguments of various types and returns the length of the type. If a string is passed to it, the function returns the length of the string in bytes. If an array is passed to it, the function returns the length of the array.

Functions are also known as **method, sub-routine**, or **procedure**.

## Defining a Function

The general form of a function definition in Go programming language is as follows −

```
func function_name( [parameter list] ) [return_types]
{
   body of the function
}
```

A function definition in Go programming language consists of a _function header_ and a _function body_. Here are all the parts of a function −

-   **Func** − It starts the declaration of a function.
    
-   **Function Name** − It is the actual name of the function. The function name and the parameter list together constitute the function signature.
    
-   **Parameters** − A parameter is like a placeholder. When a function is invoked, you pass a value to the parameter. This value is referred to as actual parameter or argument. The parameter list refers to the type, order, and number of the parameters of a function. Parameters are optional; that is, a function may contain no parameters.
    
-   **Return Type** − A function may return a list of values. The return\_types is the list of data types of the values the function returns. Some functions perform the desired operations without returning a value. In this case, the return\_type is the not required.
    
-   **Function Body** − It contains a collection of statements that define what the function does.
    

## Example

The following source code shows a function called **max()**. This function takes two parameters num1 and num2 and returns the maximum between the two −

```
<span>/* function returning the max between two numbers */</span><span>
func max</span><span>(</span><span>num1</span><span>,</span><span> num2 </span><span>int</span><span>)</span><span> </span><span>int</span><span> </span><span>{</span><span>
   </span><span>/* local variable declaration */</span><span>
   result </span><span>int</span><span>

   </span><span>if</span><span> </span><span>(</span><span>num1 </span><span>&gt;</span><span> num2</span><span>)</span><span> </span><span>{</span><span>
      result </span><span>=</span><span> num1
   </span><span>}</span><span> </span><span>else</span><span> </span><span>{</span><span>
      result </span><span>=</span><span> num2
   </span><span>}</span><span>
   </span><span>return</span><span> result 
</span><span>}</span>
```

## Calling a Function

While creating a Go function, you give a definition of what the function has to do. To use a function, you will have to call that function to perform the defined task.

When a program calls a function, the program control is transferred to the called function. A called function performs a defined task and when its return statement is executed or when its function-ending closing brace is reached, it returns the program control back to the main program.

To call a function, you simply need to pass the required parameters along with its function name. If the function returns a value, then you can store the returned value. For example −

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

func main</span><span>()</span><span> </span><span>{</span><span>
   </span><span>/* local variable definition */</span><span>
   </span><span>var</span><span> a </span><span>int</span><span> </span><span>=</span><span> </span><span>100</span><span>
   </span><span>var</span><span> b </span><span>int</span><span> </span><span>=</span><span> </span><span>200</span><span>
   </span><span>var</span><span> ret </span><span>int</span><span>

   </span><span>/* calling a function to get max value */</span><span>
   ret </span><span>=</span><span> max</span><span>(</span><span>a</span><span>,</span><span> b</span><span>)</span><span>

   fmt</span><span>.</span><span>Printf</span><span>(</span><span> </span><span>"Max value is : %d\n"</span><span>,</span><span> ret </span><span>)</span><span>
</span><span>}</span><span>

</span><span>/* function returning the max between two numbers */</span><span>
func max</span><span>(</span><span>num1</span><span>,</span><span> num2 </span><span>int</span><span>)</span><span> </span><span>int</span><span> </span><span>{</span><span>
   </span><span>/* local variable declaration */</span><span>
   </span><span>var</span><span> result </span><span>int</span><span>

   </span><span>if</span><span> </span><span>(</span><span>num1 </span><span>&gt;</span><span> num2</span><span>)</span><span> </span><span>{</span><span>
      result </span><span>=</span><span> num1
   </span><span>}</span><span> </span><span>else</span><span> </span><span>{</span><span>
      result </span><span>=</span><span> num2
   </span><span>}</span><span>
   </span><span>return</span><span> result 
</span><span>}</span>
```

We have kept the max() function along with the main() function and compiled the source code. While running the final executable, it would produce the following result −

```
Max value is : 200
```

## Returning multiple values from Function

A Go function can return multiple values. For example −

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

func swap</span><span>(</span><span>x</span><span>,</span><span> y </span><span>string</span><span>)</span><span> </span><span>(</span><span>string</span><span>,</span><span> </span><span>string</span><span>)</span><span> </span><span>{</span><span>
   </span><span>return</span><span> y</span><span>,</span><span> x
</span><span>}</span><span>
func main</span><span>()</span><span> </span><span>{</span><span>
   a</span><span>,</span><span> b </span><span>:=</span><span> swap</span><span>(</span><span>"Mahesh"</span><span>,</span><span> </span><span>"Kumar"</span><span>)</span><span>
   fmt</span><span>.</span><span>Println</span><span>(</span><span>a</span><span>,</span><span> b</span><span>)</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
Kumar Mahesh
```

## Function Arguments

If a function is to use arguments, it must declare variables that accept the values of the arguments. These variables are called the **formal parameters** of the function.

The formal parameters behave like other local variables inside the function and are created upon entry into the function and destroyed upon exit.

While calling a function, there are two ways that arguments can be passed to a function −

| Sr.No | Call Type & Description |
| --- | --- |
| 1 | [Call by value](https://www.tutorialspoint.com/go/go_function_call_by_value.htm "Function call by value in Go")
This method copies the actual value of an argument into the formal parameter of the function. In this case, changes made to the parameter inside the function have no effect on the argument.

 |
| 2 | [Call by reference](https://www.tutorialspoint.com/go/go_function_call_by_reference.htm "Function call by reference in Go")

This method copies the address of an argument into the formal parameter. Inside the function, the address is used to access the actual argument used in the call. This means that changes made to the parameter affect the argument.

 |

By default, Go uses call by value to pass arguments. In general, it means the code within a function cannot alter the arguments used to call the function. The above program, while calling the max() function, used the same method.

## Function Usage

A function can be used in the following ways:

| Sr.No | Function Usage & Description |
| --- | --- |
| 1 | [Function as Value](https://www.tutorialspoint.com/go/go_function_as_values.htm "Function as values")
Functions can be created on the fly and can be used as values.

 |
| 2 | [Function Closures](https://www.tutorialspoint.com/go/go_function_closures.htm "Function Closures")

Functions closures are anonymous functions and can be used in dynamic programming.

 |
| 3 | [Method](https://www.tutorialspoint.com/go/go_method.htm "Method")

Methods are special functions with a receiver.

 |

## Go - Scope Rules

A scope in any programming is a region of the program where a defined variable can exist and beyond that the variable cannot be accessed. There are three places where variables can be declared in Go programming language −

-   Inside a function or a block (**local** variables)
    
-   Outside of all functions (**global** variables)
    
-   In the definition of function parameters (**formal** parameters)
    

Let us find out what are **local** and **global** variables and what are **formal** parameters.

## Local Variables

Variables that are declared inside a function or a block are called local variables. They can be used only by statements that are inside that function or block of code. Local variables are not known to functions outside their own. The following example uses local variables. Here all the variables a, b, and c are local to the main() function.

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

func main</span><span>()</span><span> </span><span>{</span><span>
   </span><span>/* local variable declaration */</span><span>
   </span><span>var</span><span> a</span><span>,</span><span> b</span><span>,</span><span> c </span><span>int</span><span> 

   </span><span>/* actual initialization */</span><span>
   a </span><span>=</span><span> </span><span>10</span><span>
   b </span><span>=</span><span> </span><span>20</span><span>
   c </span><span>=</span><span> a </span><span>+</span><span> b

   fmt</span><span>.</span><span>Printf</span><span> </span><span>(</span><span>"value of a = %d, b = %d and c = %d\n"</span><span>,</span><span> a</span><span>,</span><span> b</span><span>,</span><span> c</span><span>)</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
value of a = 10, b = 20 and c = 30
```

## Global Variables

Global variables are defined outside of a function, usually on top of the program. Global variables hold their value throughout the lifetime of the program and they can be accessed inside any of the functions defined for the program.

A global variable can be accessed by any function. That is, a global variable is available for use throughout the program after its declaration. The following example uses both global and local variables −

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>
 
</span><span>/* global variable declaration */</span><span>
</span><span>var</span><span> g </span><span>int</span><span>
 
func main</span><span>()</span><span> </span><span>{</span><span>
   </span><span>/* local variable declaration */</span><span>
   </span><span>var</span><span> a</span><span>,</span><span> b </span><span>int</span><span>

   </span><span>/* actual initialization */</span><span>
   a </span><span>=</span><span> </span><span>10</span><span>
   b </span><span>=</span><span> </span><span>20</span><span>
   g </span><span>=</span><span> a </span><span>+</span><span> b

   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"value of a = %d, b = %d and g = %d\n"</span><span>,</span><span> a</span><span>,</span><span> b</span><span>,</span><span> g</span><span>)</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
value of a = 10, b = 20 and g = 30
```

A program can have the same name for local and global variables but the value of the local variable inside a function takes preference. For example −

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>
 
</span><span>/* global variable declaration */</span><span>
</span><span>var</span><span> g </span><span>int</span><span> </span><span>=</span><span> </span><span>20</span><span>
 
func main</span><span>()</span><span> </span><span>{</span><span>
   </span><span>/* local variable declaration */</span><span>
   </span><span>var</span><span> g </span><span>int</span><span> </span><span>=</span><span> </span><span>10</span><span>
 
   fmt</span><span>.</span><span>Printf</span><span> </span><span>(</span><span>"value of g = %d\n"</span><span>,</span><span>  g</span><span>)</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
value of g = 10
```

## Formal Parameters

Formal parameters are treated as local variables with-in that function and they take preference over the global variables. For example −

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>
 
</span><span>/* global variable declaration */</span><span>
</span><span>var</span><span> a </span><span>int</span><span> </span><span>=</span><span> </span><span>20</span><span>;</span><span>
 
func main</span><span>()</span><span> </span><span>{</span><span>
   </span><span>/* local variable declaration in main function */</span><span>
   </span><span>var</span><span> a </span><span>int</span><span> </span><span>=</span><span> </span><span>10</span><span>
   </span><span>var</span><span> b </span><span>int</span><span> </span><span>=</span><span> </span><span>20</span><span>
   </span><span>var</span><span> c </span><span>int</span><span> </span><span>=</span><span> </span><span>0</span><span>

   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"value of a in main() = %d\n"</span><span>,</span><span>  a</span><span>);</span><span>
   c </span><span>=</span><span> sum</span><span>(</span><span> a</span><span>,</span><span> b</span><span>);</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"value of c in main() = %d\n"</span><span>,</span><span>  c</span><span>);</span><span>
</span><span>}</span><span>
</span><span>/* function to add two integers */</span><span>
func sum</span><span>(</span><span>a</span><span>,</span><span> b </span><span>int</span><span>)</span><span> </span><span>int</span><span> </span><span>{</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"value of a in sum() = %d\n"</span><span>,</span><span>  a</span><span>);</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"value of b in sum() = %d\n"</span><span>,</span><span>  b</span><span>);</span><span>

   </span><span>return</span><span> a </span><span>+</span><span> b</span><span>;</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
value of a in main() = 10
value of a in sum() = 10
value of b in sum() = 20
value of c in main() = 30
```

## Initializing Local and Global Variables

Local and global variables are initialized to their default value, which is 0; while pointers are initialized to nil.

| Data Type | Initial Default Value |
| --- | --- |
| int | 0 |
| float32 | 0 |
| pointer | nil |

## Go - Strings

Strings, which are widely used in Go programming, are a readonly slice of bytes. In the Go programming language, strings are **slices**. The Go platform provides various libraries to manipulate strings.

-   unicode
-   regexp
-   strings

## Creating Strings

The most direct way to create a string is to write −

```
var greeting = "Hello world!"
```

Whenever it encounters a string literal in your code, the compiler creates a string object with its value in this case, "Hello world!'.

A string literal holds a valid UTF-8 sequences called runes. A String holds arbitrary bytes.

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

func main</span><span>()</span><span> </span><span>{</span><span>
   </span><span>var</span><span> greeting </span><span>=</span><span>  </span><span>"Hello world!"</span><span>
   
   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"normal string: "</span><span>)</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"%s"</span><span>,</span><span> greeting</span><span>)</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"\n"</span><span>)</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"hex bytes: "</span><span>)</span><span>
   
   </span><span>for</span><span> i </span><span>:=</span><span> </span><span>0</span><span>;</span><span> i </span><span>&lt;</span><span> len</span><span>(</span><span>greeting</span><span>);</span><span> i</span><span>++</span><span> </span><span>{</span><span>
       fmt</span><span>.</span><span>Printf</span><span>(</span><span>"%x "</span><span>,</span><span> greeting</span><span>[</span><span>i</span><span>])</span><span>
   </span><span>}</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"\n"</span><span>)</span><span>
   
   </span><span>const</span><span> sampleText </span><span>=</span><span> </span><span>"\xbd\xb2\x3d\xbc\x20\xe2\x8c\x98"</span><span> 
   </span><span>/*q flag escapes unprintable characters, with + flag it escapses non-ascii 
   characters as well to make output unambigous  
   */</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"quoted string: "</span><span>)</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"%+q"</span><span>,</span><span> sampleText</span><span>)</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"\n"</span><span>)</span><span>  
</span><span>}</span>
```

This would produce the following result −

```
normal string: Hello world!
hex bytes: 48 65 6c 6c 6f 20 77 6f 72 6c 64 21 
quoted string: "\xbd\xb2=\xbc \u2318"
```

**Note** − The string literal is immutable, so that once it is created a string literal cannot be changed.

## String Length

len(str) method returns the number of bytes contained in the string literal.

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

func main</span><span>()</span><span> </span><span>{</span><span>
   </span><span>var</span><span> greeting </span><span>=</span><span>  </span><span>"Hello world!"</span><span>
   
   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"String Length is: "</span><span>)</span><span>
   fmt</span><span>.</span><span>Println</span><span>(</span><span>len</span><span>(</span><span>greeting</span><span>))</span><span>  
</span><span>}</span>
```

This would produce the following result −

```
String Length is : 12
```

## Concatenating Strings

The strings package includes a method **join** for concatenating multiple strings −

```
strings.Join(sample, " ")
```

Join concatenates the elements of an array to create a single string. Second parameter is seperator which is placed between element of the array.

Let us look at the following example −

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>(</span><span>"fmt"</span><span> </span><span>"math"</span><span> </span><span>)</span><span>"fmt"</span><span> </span><span>"strings"</span><span>)</span><span>

func main</span><span>()</span><span> </span><span>{</span><span>
   greetings </span><span>:=</span><span>  </span><span>[]</span><span>string</span><span>{</span><span>"Hello"</span><span>,</span><span>"world!"</span><span>}</span><span>   
   fmt</span><span>.</span><span>Println</span><span>(</span><span>strings</span><span>.</span><span>Join</span><span>(</span><span>greetings</span><span>,</span><span> </span><span>" "</span><span>))</span><span>
</span><span>}</span>
```

This would produce the following result −

```
Hello world!
```

## Go - Arrays

Go programming language provides a data structure called **the array**, which can store a fixed-size sequential collection of elements of the same type. An array is used to store a collection of data, but it is often more useful to think of an array as a collection of variables of the same type.

Instead of declaring individual variables, such as number0, number1, ..., and number99, you declare one array variable such as numbers and use numbers\[0\], numbers\[1\], and ..., numbers\[99\] to represent individual variables. A specific element in an array is accessed by an index.

All arrays consist of contiguous memory locations. The lowest address corresponds to the first element and the highest address to the last element.

![Arrays in Go](https://www.tutorialspoint.com/go/images/arrays.jpg)

## Declaring Arrays

To declare an array in Go, a programmer specifies the type of the elements and the number of elements required by an array as follows −

```
var variable_name [SIZE] variable_type
```

This is called a _single-dimensional_ array. The **arraySize** must be an integer constant greater than zero and **type** can be any valid Go data type. For example, to declare a 10-element array called **balance** of type float32, use this statement −

```
var balance [10] float32
```

Here, **balance** is a variable array that can hold up to 10 float numbers.

## Initializing Arrays

You can initialize array in Go either one by one or using a single statement as follows −

```
var balance = [5]float32{1000.0, 2.0, 3.4, 7.0, 50.0}
```

The number of values between braces { } can not be larger than the number of elements that we declare for the array between square brackets \[ \].

If you omit the size of the array, an array just big enough to hold the initialization is created. Therefore, if you write −

```
var balance = []float32{1000.0, 2.0, 3.4, 7.0, 50.0}
```

You will create exactly the same array as you did in the previous example. Following is an example to assign a single element of the array −

```
balance[4] = 50.0
```

The above statement assigns element number 5<sup>th</sup> in the array with a value of 50.0. All arrays have 0 as the index of their first element which is also called base index and last index of an array will be total size of the array minus 1. Following is the pictorial representation of the same array we discussed above −

![Array Presentation](https://www.tutorialspoint.com/go/images/array_presentation.jpg)

## Accessing Array Elements

An element is accessed by indexing the array name. This is done by placing the index of the element within square brackets after the name of the array. For example −

```
float32 salary = balance[9]
```

The above statement will take 10<sup>th</sup> element from the array and assign the value to salary variable. Following is an example which will use all the above mentioned three concepts viz. declaration, assignment and accessing arrays −

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

func main</span><span>()</span><span> </span><span>{</span><span>
   </span><span>var</span><span> n </span><span>[</span><span>10</span><span>]</span><span>int</span><span> </span><span>/* n is an array of 10 integers */</span><span>
   </span><span>var</span><span> i</span><span>,</span><span>j </span><span>int</span><span>

   </span><span>/* initialize elements of array n to 0 */</span><span>         
   </span><span>for</span><span> i </span><span>=</span><span> </span><span>0</span><span>;</span><span> i </span><span>&lt;</span><span> </span><span>10</span><span>;</span><span> i</span><span>++</span><span> </span><span>{</span><span>
      n</span><span>[</span><span>i</span><span>]</span><span> </span><span>=</span><span> i </span><span>+</span><span> </span><span>100</span><span> </span><span>/* set element at location i to i + 100 */</span><span>
   </span><span>}</span><span>
   </span><span>/* output each array element's value */</span><span>
   </span><span>for</span><span> j </span><span>=</span><span> </span><span>0</span><span>;</span><span> j </span><span>&lt;</span><span> </span><span>10</span><span>;</span><span> j</span><span>++</span><span> </span><span>{</span><span>
      fmt</span><span>.</span><span>Printf</span><span>(</span><span>"Element[%d] = %d\n"</span><span>,</span><span> j</span><span>,</span><span> n</span><span>[</span><span>j</span><span>]</span><span> </span><span>)</span><span>
   </span><span>}</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
Element[0] = 100
Element[1] = 101
Element[2] = 102
Element[3] = 103
Element[4] = 104
Element[5] = 105
Element[6] = 106
Element[7] = 107
Element[8] = 108
Element[9] = 109
```

## Go Arrays in Detail

There are important concepts related to array which should be clear to a Go programmer −

| Sr.No | Concept & Description |
| --- | --- |
| 1 | [Multi-dimensional arrays](https://www.tutorialspoint.com/go/go_multi_dimensional_arrays.htm "Multi-dimensional arrays in Go")
Go supports multidimensional arrays. The simplest form of a multidimensional array is the two-dimensional array.

 |
| 2 | [Passing arrays to functions](https://www.tutorialspoint.com/go/go_passing_arrays_to_functions.htm "Passing arrays to functions as arguments in Go")

You can pass to the function a pointer to an array by specifying the array's name without an index.

 |

## Go - Pointers

Pointers in Go are easy and fun to learn. Some Go programming tasks are performed more easily with pointers, and other tasks, such as call by reference, cannot be performed without using pointers. So it becomes necessary to learn pointers to become a perfect Go programmer.

As you know, every variable is a memory location and every memory location has its address defined which can be accessed using ampersand (&) operator, which denotes an address in memory. Consider the following example, which will print the address of the variables defined −

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

func main</span><span>()</span><span> </span><span>{</span><span>
   </span><span>var</span><span> a </span><span>int</span><span> </span><span>=</span><span> </span><span>10</span><span>   
   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"Address of a variable: %x\n"</span><span>,</span><span> </span><span>&amp;</span><span>a  </span><span>)</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
Address of a variable: 10328000
```

So you understood what is memory address and how to access it. Now let us see what pointers are.

## What Are Pointers?

A **pointer** is a variable whose value is the address of another variable, i.e., direct address of the memory location. Like any variable or constant, you must declare a pointer before you can use it to store any variable address. The general form of a pointer variable declaration is −

```
var var_name *var-type
```

Here, **type** is the pointer's base type; it must be a valid C data type and **var-name** is the name of the pointer variable. The asterisk \* you used to declare a pointer is the same asterisk that you use for multiplication. However, in this statement the asterisk is being used to designate a variable as a pointer. Following are the valid pointer declaration −

```
var ip *int        /* pointer to an integer */
var fp *float32    /* pointer to a float */
```

The actual data type of the value of all pointers, whether integer, float, or otherwise, is the same, a long hexadecimal number that represents a memory address. The only difference between pointers of different data types is the data type of the variable or constant that the pointer points to.

## How to Use Pointers?

There are a few important operations, which we frequently perform with pointers: (a) we define pointer variables, (b) assign the address of a variable to a pointer, and (c) access the value at the address stored in the pointer variable.

All these operations are carried out using the unary operator \* that returns the value of the variable located at the address specified by its operand. The following example demonstrates how to perform these operations −

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

func main</span><span>()</span><span> </span><span>{</span><span>
   </span><span>var</span><span> a </span><span>int</span><span> </span><span>=</span><span> </span><span>20</span><span>   </span><span>/* actual variable declaration */</span><span>
   </span><span>var</span><span> ip </span><span>*</span><span>int</span><span>      </span><span>/* pointer variable declaration */</span><span>

   ip </span><span>=</span><span> </span><span>&amp;</span><span>a  </span><span>/* store address of a in pointer variable*/</span><span>

   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"Address of a variable: %x\n"</span><span>,</span><span> </span><span>&amp;</span><span>a  </span><span>)</span><span>

   </span><span>/* address stored in pointer variable */</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"Address stored in ip variable: %x\n"</span><span>,</span><span> ip </span><span>)</span><span>

   </span><span>/* access the value using the pointer */</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"Value of *ip variable: %d\n"</span><span>,</span><span> </span><span>*</span><span>ip </span><span>)</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
Address of var variable: 10328000
Address stored in ip variable: 10328000
Value of *ip variable: 20
```

## Nil Pointers in Go

Go compiler assign a Nil value to a pointer variable in case you do not have exact address to be assigned. This is done at the time of variable declaration. A pointer that is assigned nil is called a **nil** pointer.

The nil pointer is a constant with a value of zero defined in several standard libraries. Consider the following program −

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

func main</span><span>()</span><span> </span><span>{</span><span>
   </span><span>var</span><span>  ptr </span><span>*</span><span>int</span><span>

   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"The value of ptr is : %x\n"</span><span>,</span><span> ptr  </span><span>)</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
The value of ptr is 0
```

On most of the operating systems, programs are not permitted to access memory at address 0 because that memory is reserved by the operating system. However, the memory address 0 has special significance; it signals that the pointer is not intended to point to an accessible memory location. But by convention, if a pointer contains the nil (zero) value, it is assumed to point to nothing.

To check for a nil pointer you can use an if statement as follows −

```
if(ptr != nil)     /* succeeds if p is not nil */
if(ptr == nil)    /* succeeds if p is null */
```

## Go Pointers in Detail

Pointers have many but easy concepts and they are very important to Go programming. The following concepts of pointers should be clear to a Go programmer −

## Go - Structures

Go arrays allow you to define variables that can hold several data items of the same kind. **Structure** is another user-defined data type available in Go programming, which allows you to combine data items of different kinds.

Structures are used to represent a record. Suppose you want to keep track of the books in a library. You might want to track the following attributes of each book −

-   Title
-   Author
-   Subject
-   Book ID

In such a scenario, structures are highly useful.

## Defining a Structure

To define a structure, you must use **type** and **struct** statements. The struct statement defines a new data type, with multiple members for your program. The type statement binds a name with the type which is struct in our case. The format of the struct statement is as follows −

```
<span>type struct_variable_type </span><span>struct</span><span> </span><span>{</span><span>
   member definition</span><span>;</span><span>
   member definition</span><span>;</span><span>
   </span><span>...</span><span>
   member definition</span><span>;</span><span>
</span><span>}</span>
```

Once a structure type is defined, it can be used to declare variables of that type using the following syntax.

```
variable_name := structure_variable_type {value1, value2...valuen}
```

## Accessing Structure Members

To access any member of a structure, we use the **member access operator (.).** The member access operator is coded as a period between the structure variable name and the structure member that we wish to access. You would use **struct** keyword to define variables of structure type. The following example explains how to use a structure −

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

type </span><span>Books</span><span> </span><span>struct</span><span> </span><span>{</span><span>
   title </span><span>string</span><span>
   author </span><span>string</span><span>
   subject </span><span>string</span><span>
   book_id </span><span>int</span><span>
</span><span>}</span><span>
func main</span><span>()</span><span> </span><span>{</span><span>
   </span><span>var</span><span> </span><span>Book1</span><span> </span><span>Books</span><span>    </span><span>/* Declare Book1 of type Book */</span><span>
   </span><span>var</span><span> </span><span>Book2</span><span> </span><span>Books</span><span>    </span><span>/* Declare Book2 of type Book */</span><span>
 
   </span><span>/* book 1 specification */</span><span>
   </span><span>Book1</span><span>.</span><span>title </span><span>=</span><span> </span><span>"Go Programming"</span><span>
   </span><span>Book1</span><span>.</span><span>author </span><span>=</span><span> </span><span>"Mahesh Kumar"</span><span>
   </span><span>Book1</span><span>.</span><span>subject </span><span>=</span><span> </span><span>"Go Programming Tutorial"</span><span>
   </span><span>Book1</span><span>.</span><span>book_id </span><span>=</span><span> </span><span>6495407</span><span>

   </span><span>/* book 2 specification */</span><span>
   </span><span>Book2</span><span>.</span><span>title </span><span>=</span><span> </span><span>"Telecom Billing"</span><span>
   </span><span>Book2</span><span>.</span><span>author </span><span>=</span><span> </span><span>"Zara Ali"</span><span>
   </span><span>Book2</span><span>.</span><span>subject </span><span>=</span><span> </span><span>"Telecom Billing Tutorial"</span><span>
   </span><span>Book2</span><span>.</span><span>book_id </span><span>=</span><span> </span><span>6495700</span><span>
 
   </span><span>/* print Book1 info */</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span> </span><span>"Book 1 title : %s\n"</span><span>,</span><span> </span><span>Book1</span><span>.</span><span>title</span><span>)</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span> </span><span>"Book 1 author : %s\n"</span><span>,</span><span> </span><span>Book1</span><span>.</span><span>author</span><span>)</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span> </span><span>"Book 1 subject : %s\n"</span><span>,</span><span> </span><span>Book1</span><span>.</span><span>subject</span><span>)</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span> </span><span>"Book 1 book_id : %d\n"</span><span>,</span><span> </span><span>Book1</span><span>.</span><span>book_id</span><span>)</span><span>

   </span><span>/* print Book2 info */</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span> </span><span>"Book 2 title : %s\n"</span><span>,</span><span> </span><span>Book2</span><span>.</span><span>title</span><span>)</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span> </span><span>"Book 2 author : %s\n"</span><span>,</span><span> </span><span>Book2</span><span>.</span><span>author</span><span>)</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span> </span><span>"Book 2 subject : %s\n"</span><span>,</span><span> </span><span>Book2</span><span>.</span><span>subject</span><span>)</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span> </span><span>"Book 2 book_id : %d\n"</span><span>,</span><span> </span><span>Book2</span><span>.</span><span>book_id</span><span>)</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
Book 1 title      : Go Programming
Book 1 author     : Mahesh Kumar
Book 1 subject    : Go Programming Tutorial
Book 1 book_id    : 6495407
Book 2 title      : Telecom Billing
Book 2 author     : Zara Ali
Book 2 subject    : Telecom Billing Tutorial
Book 2 book_id    : 6495700
```

## Structures as Function Arguments

You can pass a structure as a function argument in very similar way as you pass any other variable or pointer. You would access structure variables in the same way as you did in the above example −

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

type </span><span>Books</span><span> </span><span>struct</span><span> </span><span>{</span><span>
   title </span><span>string</span><span>
   author </span><span>string</span><span>
   subject </span><span>string</span><span>
   book_id </span><span>int</span><span>
</span><span>}</span><span>
func main</span><span>()</span><span> </span><span>{</span><span>
   </span><span>var</span><span> </span><span>Book1</span><span> </span><span>Books</span><span>    </span><span>/* Declare Book1 of type Book */</span><span>
   </span><span>var</span><span> </span><span>Book2</span><span> </span><span>Books</span><span>    </span><span>/* Declare Book2 of type Book */</span><span>
 
   </span><span>/* book 1 specification */</span><span>
   </span><span>Book1</span><span>.</span><span>title </span><span>=</span><span> </span><span>"Go Programming"</span><span>
   </span><span>Book1</span><span>.</span><span>author </span><span>=</span><span> </span><span>"Mahesh Kumar"</span><span>
   </span><span>Book1</span><span>.</span><span>subject </span><span>=</span><span> </span><span>"Go Programming Tutorial"</span><span>
   </span><span>Book1</span><span>.</span><span>book_id </span><span>=</span><span> </span><span>6495407</span><span>

   </span><span>/* book 2 specification */</span><span>
   </span><span>Book2</span><span>.</span><span>title </span><span>=</span><span> </span><span>"Telecom Billing"</span><span>
   </span><span>Book2</span><span>.</span><span>author </span><span>=</span><span> </span><span>"Zara Ali"</span><span>
   </span><span>Book2</span><span>.</span><span>subject </span><span>=</span><span> </span><span>"Telecom Billing Tutorial"</span><span>
   </span><span>Book2</span><span>.</span><span>book_id </span><span>=</span><span> </span><span>6495700</span><span>
 
   </span><span>/* print Book1 info */</span><span>
   printBook</span><span>(</span><span>Book1</span><span>)</span><span>

   </span><span>/* print Book2 info */</span><span>
   printBook</span><span>(</span><span>Book2</span><span>)</span><span>
</span><span>}</span><span>
func printBook</span><span>(</span><span> book </span><span>Books</span><span> </span><span>)</span><span> </span><span>{</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span> </span><span>"Book title : %s\n"</span><span>,</span><span> book</span><span>.</span><span>title</span><span>);</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span> </span><span>"Book author : %s\n"</span><span>,</span><span> book</span><span>.</span><span>author</span><span>);</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span> </span><span>"Book subject : %s\n"</span><span>,</span><span> book</span><span>.</span><span>subject</span><span>);</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span> </span><span>"Book book_id : %d\n"</span><span>,</span><span> book</span><span>.</span><span>book_id</span><span>);</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
Book title     : Go Programming
Book author    : Mahesh Kumar
Book subject   : Go Programming Tutorial
Book book_id   : 6495407
Book title     : Telecom Billing
Book author    : Zara Ali
Book subject   : Telecom Billing Tutorial
Book book_id   : 6495700
```

## Pointers to Structures

You can define pointers to structures in the same way as you define pointer to any other variable as follows −

```
var struct_pointer *Books
```

Now, you can store the address of a structure variable in the above defined pointer variable. To find the address of a structure variable, place the & operator before the structure's name as follows −

```
struct_pointer = &amp;Book1;
```

To access the members of a structure using a pointer to that structure, you must use the "." operator as follows −

```
struct_pointer.title;
```

Let us re-write the above example using structure pointer −

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

type </span><span>Books</span><span> </span><span>struct</span><span> </span><span>{</span><span>
   title </span><span>string</span><span>
   author </span><span>string</span><span>
   subject </span><span>string</span><span>
   book_id </span><span>int</span><span>
</span><span>}</span><span>
func main</span><span>()</span><span> </span><span>{</span><span>
   </span><span>var</span><span> </span><span>Book1</span><span> </span><span>Books</span><span>   </span><span>/* Declare Book1 of type Book */</span><span>
   </span><span>var</span><span> </span><span>Book2</span><span> </span><span>Books</span><span>   </span><span>/* Declare Book2 of type Book */</span><span>
 
   </span><span>/* book 1 specification */</span><span>
   </span><span>Book1</span><span>.</span><span>title </span><span>=</span><span> </span><span>"Go Programming"</span><span>
   </span><span>Book1</span><span>.</span><span>author </span><span>=</span><span> </span><span>"Mahesh Kumar"</span><span>
   </span><span>Book1</span><span>.</span><span>subject </span><span>=</span><span> </span><span>"Go Programming Tutorial"</span><span>
   </span><span>Book1</span><span>.</span><span>book_id </span><span>=</span><span> </span><span>6495407</span><span>

   </span><span>/* book 2 specification */</span><span>
   </span><span>Book2</span><span>.</span><span>title </span><span>=</span><span> </span><span>"Telecom Billing"</span><span>
   </span><span>Book2</span><span>.</span><span>author </span><span>=</span><span> </span><span>"Zara Ali"</span><span>
   </span><span>Book2</span><span>.</span><span>subject </span><span>=</span><span> </span><span>"Telecom Billing Tutorial"</span><span>
   </span><span>Book2</span><span>.</span><span>book_id </span><span>=</span><span> </span><span>6495700</span><span>
 
   </span><span>/* print Book1 info */</span><span>
   printBook</span><span>(&amp;</span><span>Book1</span><span>)</span><span>

   </span><span>/* print Book2 info */</span><span>
   printBook</span><span>(&amp;</span><span>Book2</span><span>)</span><span>
</span><span>}</span><span>
func printBook</span><span>(</span><span> book </span><span>*</span><span>Books</span><span> </span><span>)</span><span> </span><span>{</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span> </span><span>"Book title : %s\n"</span><span>,</span><span> book</span><span>.</span><span>title</span><span>);</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span> </span><span>"Book author : %s\n"</span><span>,</span><span> book</span><span>.</span><span>author</span><span>);</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span> </span><span>"Book subject : %s\n"</span><span>,</span><span> book</span><span>.</span><span>subject</span><span>);</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span> </span><span>"Book book_id : %d\n"</span><span>,</span><span> book</span><span>.</span><span>book_id</span><span>);</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
Book title     : Go Programming
Book author    : Mahesh Kumar
Book subject   : Go Programming Tutorial
Book book_id   : 6495407
Book title     : Telecom Billing
Book author    : Zara Ali
Book subject   : Telecom Billing Tutorial
Book book_id   : 6495700
```

## Go - Slices

Go Slice is an abstraction over Go Array. Go Array allows you to define variables that can hold several data items of the same kind but it does not provide any inbuilt method to increase its size dynamically or get a sub-array of its own. Slices overcome this limitation. It provides many utility functions required on Array and is widely used in Go programming.

## Defining a slice

To define a slice, you can declare it as an array without specifying its size. Alternatively, you can use **make** function to create a slice.

```
var numbers []int /* a slice of unspecified size */
/* numbers == []int{0,0,0,0,0}*/
numbers = make([]int,5,5) /* a slice of length 5 and capacity 5*/
```

## len() and cap() functions

A slice is an abstraction over array. It actually uses arrays as an underlying structure. The **len()** function returns the elements presents in the slice where **cap()** function returns the capacity of the slice (i.e., how many elements it can be accommodate). The following example explains the usage of slice −

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

func main</span><span>()</span><span> </span><span>{</span><span>
   </span><span>var</span><span> numbers </span><span>=</span><span> make</span><span>([]</span><span>int</span><span>,</span><span>3</span><span>,</span><span>5</span><span>)</span><span>
   printSlice</span><span>(</span><span>numbers</span><span>)</span><span>
</span><span>}</span><span>
func printSlice</span><span>(</span><span>x </span><span>[]</span><span>int</span><span>){</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"len=%d cap=%d slice=%v\n"</span><span>,</span><span>len</span><span>(</span><span>x</span><span>),</span><span>cap</span><span>(</span><span>x</span><span>),</span><span>x</span><span>)</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
len = 3 cap = 5 slice = [0 0 0]
```

## Nil slice

If a slice is declared with no inputs, then by default, it is initialized as nil. Its length and capacity are zero. For example −

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

func main</span><span>()</span><span> </span><span>{</span><span>
   </span><span>var</span><span> numbers </span><span>[]</span><span>int</span><span>
   printSlice</span><span>(</span><span>numbers</span><span>)</span><span>
   
   </span><span>if</span><span>(</span><span>numbers </span><span>==</span><span> </span><span>nil</span><span>){</span><span>
      fmt</span><span>.</span><span>Printf</span><span>(</span><span>"slice is nil"</span><span>)</span><span>
   </span><span>}</span><span>
</span><span>}</span><span>
func printSlice</span><span>(</span><span>x </span><span>[]</span><span>int</span><span>){</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"len = %d cap = %d slice = %v\n"</span><span>,</span><span> len</span><span>(</span><span>x</span><span>),</span><span> cap</span><span>(</span><span>x</span><span>),</span><span>x</span><span>)</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
len = 0 cap = 0 slice = []
slice is nil
```

## Subslicing

Slice allows lower-bound and upper bound to be specified to get the subslice of it using**\[lower-bound:upper-bound\]**. For example −

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

func main</span><span>()</span><span> </span><span>{</span><span>
   </span><span>/* create a slice */</span><span>
   numbers </span><span>:=</span><span> </span><span>[]</span><span>int</span><span>{</span><span>0</span><span>,</span><span>1</span><span>,</span><span>2</span><span>,</span><span>3</span><span>,</span><span>4</span><span>,</span><span>5</span><span>,</span><span>6</span><span>,</span><span>7</span><span>,</span><span>8</span><span>}</span><span>   
   printSlice</span><span>(</span><span>numbers</span><span>)</span><span>
   
   </span><span>/* print the original slice */</span><span>
   fmt</span><span>.</span><span>Println</span><span>(</span><span>"numbers =="</span><span>,</span><span> numbers</span><span>)</span><span>
   
   </span><span>/* print the sub slice starting from index 1(included) to index 4(excluded)*/</span><span>
   fmt</span><span>.</span><span>Println</span><span>(</span><span>"numbers[1:4] =="</span><span>,</span><span> numbers</span><span>[</span><span>1</span><span>:</span><span>4</span><span>])</span><span>
   
   </span><span>/* missing lower bound implies 0*/</span><span>
   fmt</span><span>.</span><span>Println</span><span>(</span><span>"numbers[:3] =="</span><span>,</span><span> numbers</span><span>[:</span><span>3</span><span>])</span><span>
   
   </span><span>/* missing upper bound implies len(s)*/</span><span>
   fmt</span><span>.</span><span>Println</span><span>(</span><span>"numbers[4:] =="</span><span>,</span><span> numbers</span><span>[</span><span>4</span><span>:])</span><span>
   
   numbers1 </span><span>:=</span><span> make</span><span>([]</span><span>int</span><span>,</span><span>0</span><span>,</span><span>5</span><span>)</span><span>
   printSlice</span><span>(</span><span>numbers1</span><span>)</span><span>
   
   </span><span>/* print the sub slice starting from index 0(included) to index 2(excluded) */</span><span>
   number2 </span><span>:=</span><span> numbers</span><span>[:</span><span>2</span><span>]</span><span>
   printSlice</span><span>(</span><span>number2</span><span>)</span><span>
   
   </span><span>/* print the sub slice starting from index 2(included) to index 5(excluded) */</span><span>
   number3 </span><span>:=</span><span> numbers</span><span>[</span><span>2</span><span>:</span><span>5</span><span>]</span><span>
   printSlice</span><span>(</span><span>number3</span><span>)</span><span>
   
</span><span>}</span><span>
func printSlice</span><span>(</span><span>x </span><span>[]</span><span>int</span><span>){</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"len = %d cap = %d slice = %v\n"</span><span>,</span><span> len</span><span>(</span><span>x</span><span>),</span><span> cap</span><span>(</span><span>x</span><span>),</span><span>x</span><span>)</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
len = 9 cap = 9 slice = [0 1 2 3 4 5 6 7 8]
numbers == [0 1 2 3 4 5 6 7 8]
numbers[1:4] == [1 2 3]
numbers[:3] == [0 1 2]
numbers[4:] == [4 5 6 7 8]
len = 0 cap = 5 slice = []
len = 2 cap = 9  slice = [0 1]
len = 3 cap = 7 slice = [2 3 4]
```

## append() and copy() Functions

One can increase the capacity of a slice using the **append()** function. Using **copy()**function, the contents of a source slice are copied to a destination slice. For example −

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

func main</span><span>()</span><span> </span><span>{</span><span>
   </span><span>var</span><span> numbers </span><span>[]</span><span>int</span><span>
   printSlice</span><span>(</span><span>numbers</span><span>)</span><span>
   
   </span><span>/* append allows nil slice */</span><span>
   numbers </span><span>=</span><span> append</span><span>(</span><span>numbers</span><span>,</span><span> </span><span>0</span><span>)</span><span>
   printSlice</span><span>(</span><span>numbers</span><span>)</span><span>
   
   </span><span>/* add one element to slice*/</span><span>
   numbers </span><span>=</span><span> append</span><span>(</span><span>numbers</span><span>,</span><span> </span><span>1</span><span>)</span><span>
   printSlice</span><span>(</span><span>numbers</span><span>)</span><span>
   
   </span><span>/* add more than one element at a time*/</span><span>
   numbers </span><span>=</span><span> append</span><span>(</span><span>numbers</span><span>,</span><span> </span><span>2</span><span>,</span><span>3</span><span>,</span><span>4</span><span>)</span><span>
   printSlice</span><span>(</span><span>numbers</span><span>)</span><span>
   
   </span><span>/* create a slice numbers1 with double the capacity of earlier slice*/</span><span>
   numbers1 </span><span>:=</span><span> make</span><span>([]</span><span>int</span><span>,</span><span> len</span><span>(</span><span>numbers</span><span>),</span><span> </span><span>(</span><span>cap</span><span>(</span><span>numbers</span><span>))*</span><span>2</span><span>)</span><span>
   
   </span><span>/* copy content of numbers to numbers1 */</span><span>
   copy</span><span>(</span><span>numbers1</span><span>,</span><span>numbers</span><span>)</span><span>
   printSlice</span><span>(</span><span>numbers1</span><span>)</span><span>   
</span><span>}</span><span>
func printSlice</span><span>(</span><span>x </span><span>[]</span><span>int</span><span>){</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"len=%d cap=%d slice=%v\n"</span><span>,</span><span>len</span><span>(</span><span>x</span><span>),</span><span>cap</span><span>(</span><span>x</span><span>),</span><span>x</span><span>)</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
len = 0 cap = 0 slice = []
len = 1 cap = 2 slice = [0]
len = 2 cap = 2 slice = [0 1]
len = 5 cap = 8 slice = [0 1 2 3 4]
len = 5 cap = 16 slice = [0 1 2 3 4]
```

## Go - Range

The **range** keyword is used in **for** loop to iterate over items of an array, slice, channel or map. With array and slices, it returns the index of the item as integer. With maps, it returns the key of the next key-value pair. Range either returns one value or two. If only one value is used on the left of a range expression, it is the 1st value in the following table.

| Range expression | 1st Value | 2nd Value(Optional) |
| --- | --- | --- |
| Array or slice a \[n\]E | index i int | a\[i\] E |
| String s string type | index i int | rune int |
| map m map\[K\]V | key k K | value m\[k\] V |
| channel c chan E | element e E | none |

## Example

The following paragraph shows how to use range −

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

func main</span><span>()</span><span> </span><span>{</span><span>
   </span><span>/* create a slice */</span><span>
   numbers </span><span>:=</span><span> </span><span>[]</span><span>int</span><span>{</span><span>0</span><span>,</span><span>1</span><span>,</span><span>2</span><span>,</span><span>3</span><span>,</span><span>4</span><span>,</span><span>5</span><span>,</span><span>6</span><span>,</span><span>7</span><span>,</span><span>8</span><span>}</span><span> 
   
   </span><span>/* print the numbers */</span><span>
   </span><span>for</span><span> i</span><span>:=</span><span> range numbers </span><span>{</span><span>
      fmt</span><span>.</span><span>Println</span><span>(</span><span>"Slice item"</span><span>,</span><span>i</span><span>,</span><span>"is"</span><span>,</span><span>numbers</span><span>[</span><span>i</span><span>])</span><span>
   </span><span>}</span><span>
   
   </span><span>/* create a map*/</span><span>
   countryCapitalMap </span><span>:=</span><span> map</span><span>[</span><span>string</span><span>]</span><span> </span><span>string</span><span> </span><span>{</span><span>"France"</span><span>:</span><span>"Paris"</span><span>,</span><span>"Italy"</span><span>:</span><span>"Rome"</span><span>,</span><span>"Japan"</span><span>:</span><span>"Tokyo"</span><span>}</span><span>
   
   </span><span>/* print map using keys*/</span><span>
   </span><span>for</span><span> country </span><span>:=</span><span> range countryCapitalMap </span><span>{</span><span>
      fmt</span><span>.</span><span>Println</span><span>(</span><span>"Capital of"</span><span>,</span><span>country</span><span>,</span><span>"is"</span><span>,</span><span>countryCapitalMap</span><span>[</span><span>country</span><span>])</span><span>
   </span><span>}</span><span>
   
   </span><span>/* print map using key-value*/</span><span>
   </span><span>for</span><span> country</span><span>,</span><span>capital </span><span>:=</span><span> range countryCapitalMap </span><span>{</span><span>
      fmt</span><span>.</span><span>Println</span><span>(</span><span>"Capital of"</span><span>,</span><span>country</span><span>,</span><span>"is"</span><span>,</span><span>capital</span><span>)</span><span>
   </span><span>}</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
Slice item 0 is 0
Slice item 1 is 1
Slice item 2 is 2
Slice item 3 is 3
Slice item 4 is 4
Slice item 5 is 5
Slice item 6 is 6
Slice item 7 is 7
Slice item 8 is 8
Capital of France is Paris
Capital of Italy is Rome
Capital of Japan is Tokyo
Capital of France is Paris
Capital of Italy is Rome
Capital of Japan is Tokyo
```

## Go - Maps

Go provides another important data type named map which maps unique keys to values. A key is an object that you use to retrieve a value at a later date. Given a key and a value, you can store the value in a Map object. After the value is stored, you can retrieve it by using its key.

## Defining a Map

You must use **make** function to create a map.

```
/* declare a variable, by default map will be nil*/
var map_variable map[key_data_type]value_data_type

/* define the map as nil map can not be assigned any value*/
map_variable = make(map[key_data_type]value_data_type)
```

## Example

The following example illustrates how to create and use a map −

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

func main</span><span>()</span><span> </span><span>{</span><span>
   </span><span>var</span><span> countryCapitalMap map</span><span>[</span><span>string</span><span>]</span><span>string</span><span>
   </span><span>/* create a map*/</span><span>
   countryCapitalMap </span><span>=</span><span> make</span><span>(</span><span>map</span><span>[</span><span>string</span><span>]</span><span>string</span><span>)</span><span>
   
   </span><span>/* insert key-value pairs in the map*/</span><span>
   countryCapitalMap</span><span>[</span><span>"France"</span><span>]</span><span> </span><span>=</span><span> </span><span>"Paris"</span><span>
   countryCapitalMap</span><span>[</span><span>"Italy"</span><span>]</span><span> </span><span>=</span><span> </span><span>"Rome"</span><span>
   countryCapitalMap</span><span>[</span><span>"Japan"</span><span>]</span><span> </span><span>=</span><span> </span><span>"Tokyo"</span><span>
   countryCapitalMap</span><span>[</span><span>"India"</span><span>]</span><span> </span><span>=</span><span> </span><span>"New Delhi"</span><span>
   
   </span><span>/* print map using keys*/</span><span>
   </span><span>for</span><span> country </span><span>:=</span><span> range countryCapitalMap </span><span>{</span><span>
      fmt</span><span>.</span><span>Println</span><span>(</span><span>"Capital of"</span><span>,</span><span>country</span><span>,</span><span>"is"</span><span>,</span><span>countryCapitalMap</span><span>[</span><span>country</span><span>])</span><span>
   </span><span>}</span><span>
   
   </span><span>/* test if entry is present in the map or not*/</span><span>
   capital</span><span>,</span><span> ok </span><span>:=</span><span> countryCapitalMap</span><span>[</span><span>"United States"</span><span>]</span><span>
   
   </span><span>/* if ok is true, entry is present otherwise entry is absent*/</span><span>
   </span><span>if</span><span>(</span><span>ok</span><span>){</span><span>
      fmt</span><span>.</span><span>Println</span><span>(</span><span>"Capital of United States is"</span><span>,</span><span> capital</span><span>)</span><span>  
   </span><span>}</span><span> </span><span>else</span><span> </span><span>{</span><span>
      fmt</span><span>.</span><span>Println</span><span>(</span><span>"Capital of United States is not present"</span><span>)</span><span> 
   </span><span>}</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
Capital of India is New Delhi
Capital of France is Paris
Capital of Italy is Rome
Capital of Japan is Tokyo
Capital of United States is not present
```

## delete() Function

delete() function is used to delete an entry from a map. It requires the map and the corresponding key which is to be deleted. For example −

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

func main</span><span>()</span><span> </span><span>{</span><span>   
   </span><span>/* create a map*/</span><span>
   countryCapitalMap </span><span>:=</span><span> map</span><span>[</span><span>string</span><span>]</span><span> </span><span>string</span><span> </span><span>{</span><span>"France"</span><span>:</span><span>"Paris"</span><span>,</span><span>"Italy"</span><span>:</span><span>"Rome"</span><span>,</span><span>"Japan"</span><span>:</span><span>"Tokyo"</span><span>,</span><span>"India"</span><span>:</span><span>"New Delhi"</span><span>}</span><span>
   
   fmt</span><span>.</span><span>Println</span><span>(</span><span>"Original map"</span><span>)</span><span>   
   
   </span><span>/* print map */</span><span>
   </span><span>for</span><span> country </span><span>:=</span><span> range countryCapitalMap </span><span>{</span><span>
      fmt</span><span>.</span><span>Println</span><span>(</span><span>"Capital of"</span><span>,</span><span>country</span><span>,</span><span>"is"</span><span>,</span><span>countryCapitalMap</span><span>[</span><span>country</span><span>])</span><span>
   </span><span>}</span><span>
   
   </span><span>/* delete an entry */</span><span>
   </span><span>delete</span><span>(</span><span>countryCapitalMap</span><span>,</span><span>"France"</span><span>);</span><span>
   fmt</span><span>.</span><span>Println</span><span>(</span><span>"Entry for France is deleted"</span><span>)</span><span>  
   
   fmt</span><span>.</span><span>Println</span><span>(</span><span>"Updated map"</span><span>)</span><span>   
   
   </span><span>/* print map */</span><span>
   </span><span>for</span><span> country </span><span>:=</span><span> range countryCapitalMap </span><span>{</span><span>
      fmt</span><span>.</span><span>Println</span><span>(</span><span>"Capital of"</span><span>,</span><span>country</span><span>,</span><span>"is"</span><span>,</span><span>countryCapitalMap</span><span>[</span><span>country</span><span>])</span><span>
   </span><span>}</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
Original Map
Capital of France is Paris
Capital of Italy is Rome
Capital of Japan is Tokyo
Capital of India is New Delhi
Entry for France is deleted
Updated Map
Capital of India is New Delhi
Capital of Italy is Rome
Capital of Japan is Tokyo
```

## Go - Recursion

Recursion is the process of repeating items in a self-similar way. The same concept applies in programming languages as well. If a program allows to call a function inside the same function, then it is called a recursive function call. Take a look at the following example −

```
<span>func recursion</span><span>()</span><span> </span><span>{</span><span>
   recursion</span><span>()</span><span> </span><span>/* function calls itself */</span><span>
</span><span>}</span><span>
func main</span><span>()</span><span> </span><span>{</span><span>
   recursion</span><span>()</span><span>
</span><span>}</span>
```

The Go programming language supports recursion. That is, it allows a function to call itself. But while using recursion, programmers need to be careful to define an exit condition from the function, otherwise it will go on to become an infinite loop.

## Examples of Recursion in Go

Recursive functions are very useful to solve many mathematical problems such as calculating factorial of a number, generating a Fibonacci series, etc.

### Example 1: Calculating Factorial Using Recursion in Go

The following example calculates the factorial of a given number using a recursive function −

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

func factorial</span><span>(</span><span>i </span><span>int</span><span>)</span><span>int</span><span> </span><span>{</span><span>
   </span><span>if</span><span>(</span><span>i </span><span>&lt;=</span><span> </span><span>1</span><span>)</span><span> </span><span>{</span><span>
      </span><span>return</span><span> </span><span>1</span><span>
   </span><span>}</span><span>
   </span><span>return</span><span> i </span><span>*</span><span> factorial</span><span>(</span><span>i </span><span>-</span><span> </span><span>1</span><span>)</span><span>
</span><span>}</span><span>
func main</span><span>()</span><span> </span><span>{</span><span> 
   </span><span>var</span><span> i </span><span>int</span><span> </span><span>=</span><span> </span><span>15</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"Factorial of %d is %d"</span><span>,</span><span> i</span><span>,</span><span> factorial</span><span>(</span><span>i</span><span>))</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
Factorial of 15 is 1307674368000
```

## Example 2: Fibonacci Series Using Recursion in Go

The following example shows how to generate a Fibonacci series of a given number using a recursive function −

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

func fibonaci</span><span>(</span><span>i </span><span>int</span><span>)</span><span> </span><span>(</span><span>ret </span><span>int</span><span>)</span><span> </span><span>{</span><span>
   </span><span>if</span><span> i </span><span>==</span><span> </span><span>0</span><span> </span><span>{</span><span>
      </span><span>return</span><span> </span><span>0</span><span>
   </span><span>}</span><span>
   </span><span>if</span><span> i </span><span>==</span><span> </span><span>1</span><span> </span><span>{</span><span>
      </span><span>return</span><span> </span><span>1</span><span>
   </span><span>}</span><span>
   </span><span>return</span><span> fibonaci</span><span>(</span><span>i</span><span>-</span><span>1</span><span>)</span><span> </span><span>+</span><span> fibonaci</span><span>(</span><span>i</span><span>-</span><span>2</span><span>)</span><span>
</span><span>}</span><span>
func main</span><span>()</span><span> </span><span>{</span><span>
   </span><span>var</span><span> i </span><span>int</span><span>
   </span><span>for</span><span> i </span><span>=</span><span> </span><span>0</span><span>;</span><span> i </span><span>&lt;</span><span> </span><span>10</span><span>;</span><span> i</span><span>++</span><span> </span><span>{</span><span>
      fmt</span><span>.</span><span>Printf</span><span>(</span><span>"%d "</span><span>,</span><span> fibonaci</span><span>(</span><span>i</span><span>))</span><span>
   </span><span>}</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
0 1 1 2 3 5 8 13 21 34 
```

## Go - Type Casting

Type casting is a way to convert a variable from one data type to another data type. For example, if you want to store a long value into a simple integer then you can type cast long to int. You can convert values from one type to another using the **cast operator**. Its syntax is as follows −

```
type_name(expression)
```

## Example

Consider the following example where the cast operator causes the division of one integer variable by another to be performed as a floating number operation.

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

func main</span><span>()</span><span> </span><span>{</span><span>
   </span><span>var</span><span> sum </span><span>int</span><span> </span><span>=</span><span> </span><span>17</span><span>
   </span><span>var</span><span> count </span><span>int</span><span> </span><span>=</span><span> </span><span>5</span><span>
   </span><span>var</span><span> mean float32
   
   mean </span><span>=</span><span> float32</span><span>(</span><span>sum</span><span>)/</span><span>float32</span><span>(</span><span>count</span><span>)</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"Value of mean : %f\n"</span><span>,</span><span>mean</span><span>)</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
Value of mean : 3.400000
```

## Go - Interfaces

Go programming provides another data type called **interfaces** which represents a set of method signatures. The struct data type implements these interfaces to have method definitions for the method signature of the interfaces.

## Syntax

```
/* define an interface */
type interface_name interface {
   method_name1 [return_type]
   method_name2 [return_type]
   method_name3 [return_type]
   ...
   method_namen [return_type]
}

/* define a struct */
type struct_name struct {
   /* variables */
}

/* implement interface methods*/
func (struct_name_variable struct_name) method_name1() [return_type] {
   /* method implementation */
}
...
func (struct_name_variable struct_name) method_namen() [return_type] {
   /* method implementation */
}
```

## Example

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>(</span><span>
   </span><span>"fmt"</span><span> 
   </span><span>"math"</span><span> 
</span><span>)</span><span>

</span><span>/* define an interface */</span><span>
type </span><span>Shape</span><span> </span><span>interface</span><span> </span><span>{</span><span>
   area</span><span>()</span><span> float64
</span><span>}</span><span>

</span><span>/* define a circle */</span><span>
type </span><span>Circle</span><span> </span><span>struct</span><span> </span><span>{</span><span>
   x</span><span>,</span><span>y</span><span>,</span><span>radius float64
</span><span>}</span><span>

</span><span>/* define a rectangle */</span><span>
type </span><span>Rectangle</span><span> </span><span>struct</span><span> </span><span>{</span><span>
   width</span><span>,</span><span> height float64
</span><span>}</span><span>

</span><span>/* define a method for circle (implementation of Shape.area())*/</span><span>
func</span><span>(</span><span>circle </span><span>Circle</span><span>)</span><span> area</span><span>()</span><span> float64 </span><span>{</span><span>
   </span><span>return</span><span> math</span><span>.</span><span>Pi</span><span> </span><span>*</span><span> circle</span><span>.</span><span>radius </span><span>*</span><span> circle</span><span>.</span><span>radius
</span><span>}</span><span>

</span><span>/* define a method for rectangle (implementation of Shape.area())*/</span><span>
func</span><span>(</span><span>rect </span><span>Rectangle</span><span>)</span><span> area</span><span>()</span><span> float64 </span><span>{</span><span>
   </span><span>return</span><span> rect</span><span>.</span><span>width </span><span>*</span><span> rect</span><span>.</span><span>height
</span><span>}</span><span>

</span><span>/* define a method for shape */</span><span>
func getArea</span><span>(</span><span>shape </span><span>Shape</span><span>)</span><span> float64 </span><span>{</span><span>
   </span><span>return</span><span> shape</span><span>.</span><span>area</span><span>()</span><span>
</span><span>}</span><span>

func main</span><span>()</span><span> </span><span>{</span><span>
   circle </span><span>:=</span><span> </span><span>Circle</span><span>{</span><span>x</span><span>:</span><span>0</span><span>,</span><span>y</span><span>:</span><span>0</span><span>,</span><span>radius</span><span>:</span><span>5</span><span>}</span><span>
   rectangle </span><span>:=</span><span> </span><span>Rectangle</span><span> </span><span>{</span><span>width</span><span>:</span><span>10</span><span>,</span><span> height</span><span>:</span><span>5</span><span>}</span><span>
   
   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"Circle area: %f\n"</span><span>,</span><span>getArea</span><span>(</span><span>circle</span><span>))</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"Rectangle area: %f\n"</span><span>,</span><span>getArea</span><span>(</span><span>rectangle</span><span>))</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
Circle area: 78.539816
Rectangle area: 50.000000
```

## Go - Error Handling

Go programming provides a pretty simple error handling framework with inbuilt error interface type of the following declaration −

```
type error interface {
   Error() string
}
```

Functions normally return error as last return value. Use **errors.New** to construct a basic error message as following −

```
<span>func </span><span>Sqrt</span><span>(</span><span>value</span><span> float64</span><span>)(</span><span>float64</span><span>,</span><span> error</span><span>)</span><span> </span><span>{</span><span>
   </span><span>if</span><span>(</span><span>value</span><span> </span><span>&lt;</span><span> </span><span>0</span><span>){</span><span>
      </span><span>return</span><span> </span><span>0</span><span>,</span><span> errors</span><span>.</span><span>New</span><span>(</span><span>"Math: negative number passed to Sqrt"</span><span>)</span><span>
   </span><span>}</span><span>
   </span><span>return</span><span> math</span><span>.</span><span>Sqrt</span><span>(</span><span>value</span><span>),</span><span> </span><span>nil</span><span>
</span><span>}</span>
```

Use return value and error message.

```
<span>result</span><span>,</span><span> err</span><span>:=</span><span> </span><span>Sqrt</span><span>(-</span><span>1</span><span>)</span><span>

</span><span>if</span><span> err </span><span>!=</span><span> </span><span>nil</span><span> </span><span>{</span><span>
   fmt</span><span>.</span><span>Println</span><span>(</span><span>err</span><span>)</span><span>
</span><span>}</span>
```

## Example

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"errors"</span><span>
</span><span>import</span><span> </span><span>"fmt"</span><span>
</span><span>import</span><span> </span><span>"math"</span><span>

func </span><span>Sqrt</span><span>(</span><span>value</span><span> float64</span><span>)(</span><span>float64</span><span>,</span><span> error</span><span>)</span><span> </span><span>{</span><span>
   </span><span>if</span><span>(</span><span>value</span><span> </span><span>&lt;</span><span> </span><span>0</span><span>){</span><span>
      </span><span>return</span><span> </span><span>0</span><span>,</span><span> errors</span><span>.</span><span>New</span><span>(</span><span>"Math: negative number passed to Sqrt"</span><span>)</span><span>
   </span><span>}</span><span>
   </span><span>return</span><span> math</span><span>.</span><span>Sqrt</span><span>(</span><span>value</span><span>),</span><span> </span><span>nil</span><span>
</span><span>}</span><span>
func main</span><span>()</span><span> </span><span>{</span><span>
   result</span><span>,</span><span> err</span><span>:=</span><span> </span><span>Sqrt</span><span>(-</span><span>1</span><span>)</span><span>

   </span><span>if</span><span> err </span><span>!=</span><span> </span><span>nil</span><span> </span><span>{</span><span>
      fmt</span><span>.</span><span>Println</span><span>(</span><span>err</span><span>)</span><span>
   </span><span>}</span><span> </span><span>else</span><span> </span><span>{</span><span>
      fmt</span><span>.</span><span>Println</span><span>(</span><span>result</span><span>)</span><span>
   </span><span>}</span><span>
   
   result</span><span>,</span><span> err </span><span>=</span><span> </span><span>Sqrt</span><span>(</span><span>9</span><span>)</span><span>

   </span><span>if</span><span> err </span><span>!=</span><span> </span><span>nil</span><span> </span><span>{</span><span>
      fmt</span><span>.</span><span>Println</span><span>(</span><span>err</span><span>)</span><span>
   </span><span>}</span><span> </span><span>else</span><span> </span><span>{</span><span>
      fmt</span><span>.</span><span>Println</span><span>(</span><span>result</span><span>)</span><span>
   </span><span>}</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
Math: negative number passed to Sqrt
3
```
