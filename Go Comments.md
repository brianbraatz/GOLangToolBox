---
Description: Go Comments
Notes: W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.
author: 
Url: https://www.w3schools.com/go/go_comments.php
Created: "2025-01-29  02:25:32"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go Comments

source: https://www.w3schools.com/go/go_comments.php

> ## Excerpt
> W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.

---
## Go Comments

___

## Go Comments

A comment is a text that is ignored upon execution.

Comments can be used to explain the code, and to make it more readable.

Comments can also be used to prevent code execution when testing an alternative code.

Go supports single-line or multi-line comments.

___

## Go Single-line Comments

Single-line comments start with two forward slashes (`//`).

Any text between `//` and the end of the line is ignored by the compiler (will not be executed).

### Example

  
package main  
import ("fmt")  
  
func main() {  
    
  fmt.Println("Hello World!")  
}  

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_helloworld4)

The following example uses a single-line comment at the end of a code line:

### Example

package main  
import ("fmt")  
  
func main() {  
  fmt.Println("Hello World!")  
}  

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_helloworld5)

___

## Go Multi-line Comments

Multi-line comments start with `/*` and ends with `*/`.

Any text between `/*` and `*/` will be ignored by the compiler:

### Example

package main  
import ("fmt")  
  
func main() {  
    
  _to the screen, and it is amazing \*/_  
  fmt.Println("Hello World!")  
}  

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_helloworld6)

**Tip:** It is up to you which you want to use. Normally, we use `//` for short comments, and `/* */` for longer comments.

___

___

## Comment to Prevent Code Execution

You can also use comments to prevent the code from being executed.

The commented code can be saved for later reference and troubleshooting.

### Example

package main  
import ("fmt")  
  
func main() {  
  fmt.Println("Hello World!")  }  

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_helloworld7)

___

## Go Exercises

## Test Yourself With Exercises

## Exercise:

Comments in Go are written with a special character, which one?

```
package main   
import ("fmt") <br>
func main() {
   this is a comment  
  fmt.Println("Hello World!")
}
```

[Start the Exercise](https://www.w3schools.com/go/exercise.php?filename=exercise_comments1)

  

Track your progress - it's free!

   [![Get Certified](https://www.w3schools.com/images/img_deal_up_300.png)](https://campus.w3schools.com/collections/todays-deals)
