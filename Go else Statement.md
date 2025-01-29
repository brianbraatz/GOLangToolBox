---
Description: Go else Statement
Notes: W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.
author: 
Url: https://www.w3schools.com/go/go_else_statement.php
Created: "2025-01-29  02:29:14"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go else Statement

source: https://www.w3schools.com/go/go_else_statement.php

> ## Excerpt
> W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.

---
## Go if else Statement

___

## The else Statement

Use the `else` statement to specify a block of code to be executed if the condition is `false`.

### Syntax

if _condition_ {  } else {  
    
}

___

## Using The if else Statement

### Example

In this example, time (20) is greater than 18, so the `if` condition is `false`. Because of this, we move on to the `else` condition and print to the screen "Good evening". If the time was less than 18, the program would print "Good day":

package main  
import ("fmt")  
  
func main() {  
  time := 20  
  if (time < 18) {  
    fmt.Println("Good day.")  
  } else {  
    fmt.Println("Good evening.")  
  }  
}

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_if_else1)

### Example

In this example, the temperature is 14 so the condition for `if` is `false` so the code line inside the `else` statement is executed:

package main  
import ("fmt")  
  
func main() {  
  temperature := 14  
  if (temperature > 15) {  
    fmt.Println("It is warm out there")  
  } else {  
    fmt.Println("It is cold out there")  
  }  
}

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_if_else2)

The brackets in the `else` statement should be like `} else {`:

### Example

Having the else brackets in a different line will raise an error:

package main  
import ("fmt")  
  
func main() {  
  temperature := 14  
  if (temperature > 15) {  
    fmt.Println("It is warm out there.")  
  }  
  else {  
    fmt.Println("It is cold out there.")  
  }  
}

Result:

`./prog.go:9:3: syntax error: unexpected else, expecting }   `

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_if_else3)

  

Track your progress - it's free!
