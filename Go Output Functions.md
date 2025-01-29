---
Description: Go Output Functions
Notes: W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.
author: 
Url: https://www.w3schools.com/go/go_output.php
Created: "2025-01-29  02:26:30"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go Output Functions

source: https://www.w3schools.com/go/go_output.php

> ## Excerpt
> W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.

---
## Go Output Functions

___

Go has three functions to output text:

-   `Print()`
-   `Println()`
-   `Printf()`

___

## The Print() Function

The `Print()` function prints its arguments with their default format.

### Example

Print the values of `i` and `j`:

package main  
import ("fmt")  
  
func main() {  
  var i,j string = "Hello","World"  
  
  fmt.Print(i)  
  fmt.Print(j)  
}

Result:

`HelloWorld   `

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_output1)

### Example

If we want to print the arguments in new lines, we need to use `\n`.

package main  
import ("fmt")  
  
func main() {  
  var i,j string = "Hello","World"  
  
  fmt.Print(i, "\\n")  
  fmt.Print(j, "\\n")  
}

Result:

`Hello   World   `

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_output2)

**Tip:** `\n` creates new lines.

### Example

It is also possible to only use one `Print()` for printing multiple variables.

package main  
import ("fmt")  
  
func main() {  
  var i,j string = "Hello","World"  
  
  fmt.Print(i, "\\n",j)  
}

Result:

`Hello   World   `

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_output3)

### Example

If we want to add a space between string arguments, we need to use " ":

package main  
import ("fmt")  
  
func main() {  
  var i,j string = "Hello","World"  
  
  fmt.Print(i, " ", j)  
}

Result:

`Hello World   `

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_output4)

### Example

`Print()` inserts a space between the arguments if **neither** are strings:

package main  
import ("fmt")  
  
func main() {  
  var i,j = 10,20  
  
  fmt.Print(i,j)  
}

Result:

`10 20   `

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_output7)

___

___

## The Println() Function

The `Println()` function is similar to `Print()` with the difference that a whitespace is added between the arguments, and a newline is added at the end:

### Example

package main  
import ("fmt")  
  
func main() {  
  var i,j string = "Hello","World"  
  
  fmt.Println(i,j)  
}

Result:

`Hello World`

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_output5)

___

## The Printf() Function

The `Printf()` function first formats its argument based on the given formatting verb and then prints them.

Here we will use two formatting verbs:

-   `%v` is used to print the **value** of the arguments
-   `%T` is used to print the **type** of the arguments

### Example

package main  
import ("fmt")

func main() {  
  var i string = "Hello"  
  var j int = 15  
  
  fmt.Printf("i has value: %v and type: %T\\n", i, i)  
  fmt.Printf("j has value: %v and type: %T", j, j)  
}

Result:

`i has value: Hello and type: string   j has value: 15 and type: int`

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_output6)

  

Track your progress - it's free!
