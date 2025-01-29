---
Description: Go Syntax
Notes: W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.
author: 
Url: https://www.w3schools.com/go/go_syntax.php
Created: "2025-01-29  02:25:17"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go Syntax

source: https://www.w3schools.com/go/go_syntax.php

> ## Excerpt
> W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.

---
## Go Syntax

___

## Go Syntax

A Go file consists of the following parts:

-   Package declaration
-   Import packages
-   Functions
-   Statements and expressions

Look at the following code, to understand it better:

### Example

package main  
import ("fmt")  
  
func main() {  
  fmt.Println("Hello World!")  
}  

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_helloworld)

### Example explained

**Line 1:** In Go, every program is part of a package. We define this using the `package` keyword. In this example, the program belongs to the `main` package.

**Line 2:** `import ("fmt")` lets us import files included in the `fmt` package.

**Line 3:** A blank line. Go ignores white space. Having white spaces in code makes it more readable.

**Line 4:** `func main() {}` is a function. Any code inside its curly brackets `{}` will be executed.

**Line 5:** `fmt.Println()` is a function made available from the `fmt` package. It is used to output/print text. In our example it will output "Hello World!".

**Note:** In Go, any executable code belongs to the `main` package.

___

## Go Statements

`fmt.Println("Hello World!")` is a statement.

In Go, statements are separated by ending a line (hitting the Enter key) or by a semicolon "`;`".

Hitting the Enter key adds "`;`" to the end of the line implicitly (does not show up in the source code).

The left curly bracket `{` cannot come at the start of a line.

Run the following code and see what happens:

### Example

package main  
import ("fmt")  
  
func main()  
{  
  fmt.Println("Hello World!")  
}  

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_helloworld2)

___

## Go Compact Code

You can write more compact code, like shown below (this is not recommended because it makes the code more difficult to read):

### Example

package main; import ("fmt"); func main() { fmt.Println("Hello World!");}  

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_helloworld3)

___

## Go Exercises

## Test Yourself With Exercises

## Exercise:

Insert the missing part of the code below to output "Hello World".

```
package main   
import ("fmt")<br>
func main() {  
  ("Hello World!")
}
```

[Start the Exercise](https://www.w3schools.com/go/exercise.php?filename=exercise_syntax1)

  

Track your progress - it's free!

   [![Get Certified](https://www.w3schools.com/images/img_fa_up_300.png)](https://campus.w3schools.com/products/w3schools-full-access-course)
