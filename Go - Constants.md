---
Description: Go - Constants
Notes: Constants refer to fixed values that the program may not alter during its execution. These fixed values are also called literals.
author: 
Url: https://www.tutorialspoint.com/go/go_constants.htm
Created: "2025-01-29  02:32:36"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go - Constants

source: https://www.tutorialspoint.com/go/go_constants.htm

> ## Excerpt
> Constants refer to fixed values that the program may not alter during its execution. These fixed values are also called literals.

---
___

___

## Constants in Go

Constants refer to fixed values that the program may not alter during its execution. These fixed values are also called **literals**.

Constants can be of any of the basic data types such as:

-   Integer constant
-   Floating constant
-   Character constant
-   String literal

There are also enumeration constants.

Constants are treated just like regular [variables](https://www.tutorialspoint.com/go/go_variables.htm) except that their values **cannot be modified** after their definition.

## Integer Literals

An integer literal can be a decimal, octal, or hexadecimal constant. A prefix specifies the base or radix: 0x or 0X for hexadecimal, 0 for octal, and nothing for decimal.

An integer literal can also have a suffix that is a combination of U and L, for unsigned and long, respectively. The suffix can be uppercase or lowercase and can be in any order.

### Example

Here are some examples of integer literals −

```go
212         
215u        
0xFeeL      
078         
032UU       
```

Following are other examples of various type of Integer literals −

```go
85         
0213       
0x4b       
30         
30u        
30l        
30ul       
```

## Floating-point Literals

A floating-point literal has an integer part, a decimal point, a fractional part, and an exponent part. You can represent floating point literals either in decimal form or exponential form.

While representing using decimal form, you must include the decimal point, the exponent, or both and while representing using exponential form, you must include the integer part, the fractional part, or both. The signed exponent is introduced by e or E.

### Example

Here are some examples of floating-point literals −

```go
3.14159       
314159E-5L    
510E          
210f          
.e55          
```

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

### Example

The following example shows how to use **\\t** in a program −

```go
package main

import "fmt"

func main() {
   fmt.Printf("Hello\tWorld!")
}
```

When the above code is compiled and executed, it produces the following result −

```
Hello World!
```

## String Literals

String literals or constants are enclosed in double quotes "". A [string](https://www.tutorialspoint.com/go/go_strings.htm) contains characters that are similar to character literals: plain characters, escape sequences, and universal characters.

You can break a long line into multiple lines using string literals and separating them using whitespaces.

### Example

Here are some examples of string literals. All the three forms are identical strings.

```go
"hello, dear"

"hello, \

dear"

"hello, " "d" "ear"
```

You can use **const** prefix to declare constants with a specific type as follows −

```
const variable type = value;
```

### Example

The following example shows how to use the **const** keyword −

```go
package main

import "fmt"

func main() {
   const LENGTH int = 10
   const WIDTH int = 5   
   var area int

   area = LENGTH * WIDTH
   fmt.Printf("value of area : %d", area)   
}
```

When the above code is compiled and executed, it produces the following result −

```
value of area : 50
```

Note that it is a good programming practice to define constants in CAPITALS.

## Creating a Constant in Go

In Go language, the constants can be created using the `const` keyword.

### Example

In the below example, we are creating two constants, an integer and a string, and then printing their values:

```go
package main

import "fmt"

const LuckyNumber = 123
const WelcomeMsg = "Hey, H! How're You?"

func main() {
    fmt.Println("LuckyNumber:", LuckyNumber)
    fmt.Println("WelcomeMsg:", WelcomeMsg)
}
```

When the above code is compiled and executed, it produces the following result −

```
LuckyNumber: 123
WelcomeMsg: Hey, H! How're You?
```

## Accessing a Constant

Just like a normal variable, you can access a constant by its name. The following is a code statement where we are accessing a constant and printing its value:

```go
fmt.Println("WelcomeMsg:", WelcomeMsg)
```

When a Go constant is assigned a value, it **cannot be reassigned**. If you try to reassign a value to a constant, it will result in a compilation error.

### Example

Here is an example of reassigning a constant, which is invalid and will result in an error:

```go
package main

import "fmt"

const LuckyNumber = 123

func main() {
    
    LuckyNumber = 100  
    fmt.Println(LuckyNumber)
}
```

When the above code is compiled and executed, it produces the following result −

```
./main.go:9:17: cannot assign to LuckyNumber
```
