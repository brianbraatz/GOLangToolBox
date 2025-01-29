---
Description: Go Functions
Notes: W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.
author: 
Url: https://www.w3schools.com/go/go_functions.php
Created: "2025-01-29  02:30:05"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go Functions

source: https://www.w3schools.com/go/go_functions.php

> ## Excerpt
> W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.

---
## Go Functions

___

A function is a block of statements that can be used repeatedly in a program.

A function will not execute automatically when a page loads.

A function will be executed by a call to the function.

___

## Create a Function

To create (often referred to as declare) a function, do the following:

-   Use the `func` keyword.
-   Specify a name for the function, followed by parentheses ().
-   Finally, add code that defines what the function should do, inside curly braces {}.

### Syntax

func _FunctionName_() {  }  

___

## Call a Function

Functions are not executed immediately. They are "saved for later use", and will be executed when they are called.

In the example below, we create a function named "myMessage()". The opening curly brace ( { ) indicates the beginning of the function code, and the closing curly brace ( } ) indicates the end of the function. The function outputs "I just got executed!". To call the function, just write its name followed by two parentheses ():

### Example

package main  
import ("fmt")  
  
func myMessage() {  
  fmt.Println("I just got executed!")  
}

func main() {  
  myMessage() }

Result:

`I just got executed!`

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_func1)

A function can be called multiple times.

### Example

package main  
import ("fmt")  
  
func myMessage() {  
  fmt.Println("I just got executed!")  
}

func main() {  
  myMessage()  
  myMessage()  
  myMessage()  
}

Result:

`I just got executed!   I just got executed!   I just got executed!   `

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_func11)

___

___

## Naming Rules for Go Functions

-   A function name must start with a letter
-   A function name can only contain alpha-numeric characters and underscores (`A-z`, `0-9`, and `_` )
-   Function names are case-sensitive
-   A function name cannot contain spaces
-   If the function name consists of multiple words, techniques introduced for [multi-word variable naming](https://www.w3schools.com/go/go_variable_naming_rules.php) can be used

**Tip:** Give the function a name that reflects what the function does!

___

## Go Exercises

  

Track your progress - it's free!
