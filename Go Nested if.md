---
Description: Go Nested if
Notes: W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.
author: 
Url: https://www.w3schools.com/go/go_nested_if.php
Created: "2025-01-29  02:29:32"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go Nested if

source: https://www.w3schools.com/go/go_nested_if.php

> ## Excerpt
> W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.

---
## Go Nested if Statement

___

## The Nested if Statement

You can have `if` statements inside `if` statements, this is called a nested if.

### Syntax

if _condition1_ {    if _condition2_ {  
      
  }  
}

### Example

This example shows how to use nested `if` statements:

package main  
import ("fmt")  
  
func main() {  
  num := 20  
  if num >= 10 {  
    fmt.Println("Num is more than 10.")  
    if num > 15 {  
      fmt.Println("Num is also more than 15.")  
     }  
  } else {  
    fmt.Println("Num is less than 10.")  
  }  
}

Result:

`Num is more than 10.   Num is also more than 15.   `

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_nestedif1)

  

Track your progress - it's free!
