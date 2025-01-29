---
Description: Go Operators
Notes: W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.
author: 
Url: https://www.w3schools.com/go/go_operators.php
Created: "2025-01-29  02:28:24"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go Operators

source: https://www.w3schools.com/go/go_operators.php

> ## Excerpt
> W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.

---
## Go Operators

___

## Go Operators

Operators are used to perform operations on variables and values.

The `+` **operator** adds together two values, like in the example below:

### Example

package main  
import ("fmt")  
  
func main() {  
  var a = 15 + 25  
  fmt.Println(a)  
}

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_oper)

Although the `+` operator is often used to add together two values, it can also be used to add together a variable and a value, or a variable and another variable:

### Example

package main  
import ("fmt")  
  
func main() {  
  var (  
    sum1 = 100 + 50     sum2 = sum1 + 250     sum3 = sum2 + sum2   )  
  fmt.Println(sum3)  
}

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_oper2)

Go divides the operators into the following groups:

-   [Arithmetic operators](https://www.w3schools.com/go/go_arithmetic_operators.php)
-   [Assignment operators](https://www.w3schools.com/go/go_assignment_operators.php)
-   [Comparison operators](https://www.w3schools.com/go/go_comparison_operators.php)
-   [Logical operators](https://www.w3schools.com/go/go_logical_operators.php)
-   [Bitwise operators](https://www.w3schools.com/go/go_bitwise_operators.php)

  

Track your progress - it's free!
