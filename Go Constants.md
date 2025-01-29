---
Description: Go Constants
Notes: W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.
author: 
Url: https://www.w3schools.com/go/go_constants.php
Created: "2025-01-29  02:26:22"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go Constants

source: https://www.w3schools.com/go/go_constants.php

> ## Excerpt
> W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.

---
## Go Constants

___

## Go Constants

If a variable should have a fixed value that cannot be changed, you can use the `const` keyword.

The `const` keyword declares the variable as "constant", which means that it is **unchangeable and read-only**.

### Syntax

const _CONSTNAME type_ = _value_

**Note:** The value of a constant must be assigned when you declare it.

___

## Declaring a Constant

Here is an example of declaring a constant in Go:

### Example

package main  
import ("fmt")

const PI = 3.14

func main() {  
  fmt.Println(PI)  
}

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_variable_constants)

___

## Constant Rules

-   Constant names follow the same naming rules as [variables](https://www.w3schools.com/go/go_variable_naming_rules.php)
-   Constant names are usually written in uppercase letters (for easy identification and differentiation from variables)
-   Constants can be declared both inside and outside of a function

___

## Constant Types

There are two types of constants:

-   Typed constants
-   Untyped constants

___

## Typed Constants

Typed constants are declared with a defined type:

### Example

package main  
import ("fmt")

const A int = 1

func main() {  
  fmt.Println(A)  
}

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_variable_constants1)

___

___

## Untyped Constants

Untyped constants are declared without a type:

### Example

package main  
import ("fmt")

const A = 1

func main() {  
  fmt.Println(A)  
}

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_variable_constants2)

**Note:** In this case, the type of the constant is inferred from the value (means the compiler decides the type of the constant, based on the value).

___

## Constants: Unchangeable and Read-only

When a constant is declared, it is not possible to change the value later:

### Example

package main  
import ("fmt")

func main() {  
  const A = 1  
  A = 2  
  fmt.Println(A)  
}

Result:

`./prog.go:8:7: cannot assign to A`

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_variable_constants3)

___

## Multiple Constants Declaration

Multiple constants can be grouped together into a block for readability:

### Example

package main  
import ("fmt")

const (  
  A int = 1  
  B = 3.14  
  C = "Hi!"  
)

func main() {  
  fmt.Println(A)  
  fmt.Println(B)  
  fmt.Println(C)  
}

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_variable_constants4)

  

Track your progress - it's free!

   [![Get Certified](https://www.w3schools.com/images/img_fa_up_300.png)](https://campus.w3schools.com/products/w3schools-full-access-course)
