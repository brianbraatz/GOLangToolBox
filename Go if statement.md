---
Description: Go if statement
Notes: W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.
author: 
Url: https://www.w3schools.com/go/go_if_statement.php
Created: "2025-01-29  02:29:08"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go if statement

source: https://www.w3schools.com/go/go_if_statement.php

> ## Excerpt
> W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.

---
## Go if statement

___

## The if Statement

Use the `if` statement to specify a block of Go code to be executed if a condition is `true`.

Note that `if` is in lowercase letters. Uppercase letters (If or IF) will generate an error.

In the example below, we test two values to find out if 20 is greater than 18. If the condition is `true`, print some text:

### Example

package main  
import ("fmt")  
  
func main() {  
  if 20 > 18 {  
    fmt.Println("20 is greater than 18")  
  }  
}

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_if1)

We can also test variables:

### Example

package main  
import ("fmt")  
  
func main() {  
  x:= 20  
  y:= 18  
  if x > y {  
    fmt.Println("x is greater than y")  
  }  
}

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_if2)

#### Example explained

In the example above we use two variables, **x** and **y**, to test whether x is greater than y (using the `>` operator). As x is 20, and y is 18, and we know that 20 is greater than 18, we print to the screen that "x is greater than y".

___

___

## Go Exercises

  

Track your progress - it's free!
