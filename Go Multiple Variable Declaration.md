---
Description: Go Multiple Variable Declaration
Notes: W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.
author: 
Url: https://www.w3schools.com/go/go_variable_multi.php
Created: "2025-01-29  02:25:53"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go Multiple Variable Declaration

source: https://www.w3schools.com/go/go_variable_multi.php

> ## Excerpt
> W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.

---
## Go Multiple Variable Declaration

___

## Go Multiple Variable Declaration

In Go, it is possible to declare multiple variables on the same line.

### Example

This example shows how to declare multiple variables on the same line:

package main  
import ("fmt")

func main() {  
  var a, b, c, d int = 1, 3, 5, 7  
  
  fmt.Println(a)  
  fmt.Println(b)  
  fmt.Println(c)  
  fmt.Println(d)  
}

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_variable_declaration6)

**Note:** If you use the `type` keyword, it is only possible to declare **one type** of variable per line.

If the `type` keyword is not specified, you can declare different types of variables on the same line:

### Example

package main  
import ("fmt")

func main() {  
  var a, b = 6, "Hello"  
  c, d := 7, "World!"  
  
  fmt.Println(a)  
  fmt.Println(b)  
  fmt.Println(c)  
  fmt.Println(d)  
}

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_variable_declaration7)

___

## Go Variable Declaration in a Block

Multiple variable declarations can also be grouped together into a block for greater readability:

### Example

package main  
import ("fmt")

func main() {  
   var (  
     a int  
     b int = 1  
     c string = "hello"  
   )  
  
  fmt.Println(a)  
  fmt.Println(b)  
  fmt.Println(c)  
}

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_variable_declaration8)

  

Track your progress - it's free!
