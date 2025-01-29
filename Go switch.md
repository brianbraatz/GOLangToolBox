---
Description: Go switch
Notes: W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.
author: 
Url: https://www.w3schools.com/go/go_switch.php
Created: "2025-01-29  02:29:37"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go switch

source: https://www.w3schools.com/go/go_switch.php

> ## Excerpt
> W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.

---
## Go switch Statement

___

## The switch Statement

Use the `switch` statement to select one of many code blocks to be executed.

The `switch` statement in Go is similar to the ones in C, C++, Java, JavaScript, and PHP. The difference is that it only runs the matched case so it does not need a `break` statement.

___

## Single-Case switch Syntax

### Syntax

switch _expression_ {  
case _x_:  case _y_:  
    
case _z_:  
...  
default:  
    
}

This is how it works:

-   The expression is evaluated once
-   The value of the `switch` expression is compared with the values of each `case`
-   If there is a match, the associated block of code is executed
-   The `default` keyword is optional. It specifies some code to run if there is no `case` match

___

## Single-Case switch Example

The example below uses a weekday number to calculate the weekday name:

### Example

package main  
import ("fmt")  
  
func main() {  
  day := 4

  switch day {  
  case 1:  
    fmt.Println("Monday")  
  case 2:  
    fmt.Println("Tuesday")  
  case 3:  
    fmt.Println("Wednesday")  
  case 4:  
    fmt.Println("Thursday")  
  case 5:  
    fmt.Println("Friday")  
  case 6:  
    fmt.Println("Saturday")  
  case 7:  
    fmt.Println("Sunday")  
  }  
}

Result:

`Thursday   `

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_switch1)

___

___

## The default Keyword

The `default` keyword specifies some code to run if there is no case match:

### Example

package main  
import ("fmt")  
  
func main() {  
  day := 8

  switch day {  
  case 1:  
    fmt.Println("Monday")  
  case 2:  
    fmt.Println("Tuesday")  
  case 3:  
    fmt.Println("Wednesday")  
  case 4:  
    fmt.Println("Thursday")  
  case 5:  
    fmt.Println("Friday")  
  case 6:  
    fmt.Println("Saturday")  
  case 7:  
    fmt.Println("Sunday")  
  default:  
    fmt.Println("Not a weekday")  
  }  
}

Result:

`Not a weekday`

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_switch2)

___

All the `case` values should have the same type as the `switch` expression. Otherwise, the compiler will raise an error:

### Example

package main  
import ("fmt")  
  
func main() {  
  a := 3

  switch a {  
  case 1:  
    fmt.Println("a is one")  
  case "b":  
    fmt.Println("a is b")  
  }  
}

Result:

`./prog.go:11:2: cannot use "b" (type untyped string) as type int   `

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_switch5)

___

## Go Exercises

  

Track your progress - it's free!
