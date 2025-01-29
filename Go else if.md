---
Description: Go else if
Notes: W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.
author: 
Url: https://www.w3schools.com/go/go_elseif_statement.php
Created: "2025-01-29  02:29:20"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go else if

source: https://www.w3schools.com/go/go_elseif_statement.php

> ## Excerpt
> W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.

---
## Go else if Statement

___

## The else if Statement

Use the `else if` statement to specify a new condition if the first condition is `false`.

### Syntax

if _condition1_ {  } else if _condition2_ {  
    
} else {  
    
}

___

## Using The else if Statement

### Example

This example shows how to use an `else if` statement.

package main  
import ("fmt")  
  
func main() {  
  time := 22  
  if time < 10 {  
    fmt.Println("Good morning.")  
  } else if time < 20 {  
    fmt.Println("Good day.")  
  } else {  
    fmt.Println("Good evening.")  
  }  
}

Result:

`Good evening.`

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_elseif1)

#### Example explained

In the example above, time (22) is greater than 10, so the **first condition** is `false`. The next condition, in the `else if` statement, is also `false`, so we move on to `else` condition since **condition1** and **condition2** are both `false` - and print to the screen "Good evening".

However, if the time was 14, our program would print "Good day."

### Example

Another example for the use of `else if`.

package main  
import ("fmt")  
  
func main() {  
  a := 14  
  b := 14  
  if a < b {  
    fmt.Println("a is less than b.")  
  } else if a > b {  
    fmt.Println("a is more than b.")  
  } else {  
    fmt.Println("a and b are equal.")  
  }  
}

Result:

`a and b are equal.`

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_elseif2)

### Example

**Note:** If condition1 and condition2 are BOTH true, only the code for condition1 are executed:

package main  
import ("fmt")  
  
func main() {  
  x := 30  
  if x >= 10 {  
    fmt.Println("x is larger than or equal to 10.")  
  } else if x > 20 {  
    fmt.Println("x is larger than 20.")  
  } else {  
    fmt.Println("x is less than 10.")  
  }  
}

Result:

`x is larger than or equal to 10.`

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_elseif3)

  

Track your progress - it's free!
