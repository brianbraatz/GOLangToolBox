---
Description: Go Function Parameters and Arguments
Notes: W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.
author: 
Url: https://www.w3schools.com/go/go_function_parameters.php
Created: "2025-01-29  02:30:10"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go Function Parameters and Arguments

source: https://www.w3schools.com/go/go_function_parameters.php

> ## Excerpt
> W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.

---
## Go Function Parameters and Arguments

___

## Parameters and Arguments

Information can be passed to functions as a parameter. Parameters act as variables inside the function.

Parameters and their types are specified after the function name, inside the parentheses. You can add as many parameters as you want, just separate them with a comma:

### Syntax

func _FunctionName_(_param1_ _type_, _param2_ _type_, _param3_ _type_) {  }  

___

## Function With Parameter Example

The following example has a function with one parameter (`fname`) of type `string`. When the familyName() function is called, we also pass along a name (e.g. Liam), and the name is used inside the function, which outputs several different first names, but an equal last name:

### Example

package main  
import ("fmt")  
  
func familyName(fname string) {  
  fmt.Println("Hello", fname, "Refsnes")  
}

func main() {  
  familyName("Liam")  
  familyName("Jenny")  
  familyName("Anja")  
}

Result:

`Hello Liam Refsnes   Hello Jenny Refsnes   Hello Anja Refsnes   `

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_func2)

**Note:** When a **parameter** is passed to the function, it is called an **argument**. So, from the example above: `fname` is a **parameter**, while `Liam`, `Jenny` and `Anja` are **arguments**.

___

___

## Multiple Parameters

Inside the function, you can add as many parameters as you want:

### Example

package main  
import ("fmt")  
  
func familyName(fname string, age int) {  
  fmt.Println("Hello", age, "year old", fname, "Refsnes")  
}

func main() {  
  familyName("Liam", 3)  
  familyName("Jenny", 14)  
  familyName("Anja", 30)  
}

Result:

`Hello 3 year old Liam Refsnes   Hello 14 year old Jenny Refsnes   Hello 30 year old Anja Refsnes   `

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_func3)

**Note:** When you are working with multiple parameters, the function call must have the same number of arguments as there are parameters, and the arguments must be passed in the same order.

  

Track your progress - it's free!

   [![Get Certified](https://www.w3schools.com/images/img_fa_up_300.png)](https://campus.w3schools.com/products/w3schools-full-access-course)
