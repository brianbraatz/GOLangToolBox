---
Description: Go Multi-case switch
Notes: W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.
author: 
Url: https://www.w3schools.com/go/go_switch_multi.php
Created: "2025-01-29  02:29:43"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go Multi-case switch

source: https://www.w3schools.com/go/go_switch_multi.php

> ## Excerpt
> W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.

---
## Go Multi-case switch Statement

___

## The Multi-case switch Statement

It is possible to have multiple values for each `case` in the `switch` statement:

### Syntax

switch _expression_ {  
case _x_,_y_:  case _v_,_w_:  
    
case _z_:  
...  
default:  
    
}

___

## Multi-case switch Example

The example below uses the weekday number to return different text:

### Example

package main  
import ("fmt")  
  
func main() {  
   day := 5

   switch day {  
   case 1,3,5:  
    fmt.Println("Odd weekday")  
   case 2,4:  
     fmt.Println("Even weekday")  
   case 6,7:  
    fmt.Println("Weekend")  
  default:  
    fmt.Println("Invalid day of day number")  
  }  
}

Result:

`Odd weekday`

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_switch6)

  

Track your progress - it's free!
