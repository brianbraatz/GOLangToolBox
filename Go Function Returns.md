---
Description: Go Function Returns
Notes: W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.
author: 
Url: https://www.w3schools.com/go/go_function_returns.php
Created: "2025-01-29  02:30:14"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go Function Returns

source: https://www.w3schools.com/go/go_function_returns.php

> ## Excerpt
> W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.

---
## Go Function Returns

___

## Return Values

If you want the function to return a value, you need to define the data type of the return value (such as `int`, `string`, etc), and also use the `return` keyword inside the function:

### Syntax

func _FunctionName_(_param1_ _type_, _param2_ _type_) _type_ {    return _output_  
}  

___

## Function Return Example

### Example

Here, `myFunction()` receives two integers (`x` and `y`) and returns their addition (`x + y`) as integer (`int`):

package main  
import ("fmt")  
  
func myFunction(x int, y int) int {  
  return x + y  
}

func main() {  
  fmt.Println(myFunction(1, 2))  
}

Result:

`3   `

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_func4)

___

## Named Return Values

In Go, you can name the return values of a function.

### Example

Here, we name the return value as `result` (of type `int`), and return the value with a naked return (means that we use the `return` statement without specifying the variable name):

package main  
import ("fmt")  
  
func myFunction(x int, y int) (result int) {  
  result = x + y  
  return  
}

func main() {  
  fmt.Println(myFunction(1, 2))  
}

Result:

`3   `

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_func5)

The example above can also be written like this. Here, the return statement specifies the variable name:

### Example

package main  
import ("fmt")  
  
func myFunction(x int, y int) (result int) {  
  result = x + y  
  return result  
}

func main() {  
  fmt.Println(myFunction(1, 2))  
}

___

___

## Store the Return Value in a Variable

You can also store the return value in a variable, like this:

### Example

Here, we store the return value in a variable called `total`:

package main  
import ("fmt")  
  
func myFunction(x int, y int) (result int) {  
  result = x + y  
  return  
}

func main() {  
  total := myFunction(1, 2)  
  fmt.Println(total)  
}

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_func6)

___

## Multiple Return Values

Go functions can also return multiple values.

### Example

Here, `myFunction()` returns one integer (`result`) and one string (`txt1`):

package main  
import ("fmt")  
  
func myFunction(x int, y string) (result int, txt1 string) {  
  result = x + x  
  txt1 = y + " World!"  
  return  
}

func main() {  
  fmt.Println(myFunction(5, "Hello"))  
}

Result:

`10 Hello World!   `

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_func7)

### Example

Here, we store the two return values into two variables (`a` and `b`):

package main  
import ("fmt")  
  
func myFunction(x int, y string) (result int, txt1 string) {  
  result = x + x  
  txt1 = y + " World!"  
  return  
}

func main() {  
  a, b := myFunction(5, "Hello")  
  fmt.Println(a, b)  
}

Result:

`10 Hello World!   `

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_func8)

If we (for some reason) do not want to use some of the returned values, we can add an underscore (`_`), to omit this value.

### Example

Here, we want to omit the first returned value (`result` - which is stored in variable `a`):

package main  
import ("fmt")  
  
func myFunction(x int, y string) (result int, txt1 string) {  
  result = x + x  
  txt1 = y + " World!"  
  return  
}

func main() {  
   \_, b := myFunction(5, "Hello")  
  fmt.Println(b)  
}

Result:

`Hello World!   `

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_func9)

### Example

Here, we want to omit the second returned value (`txt1` - which is stored in variable `b`):

package main  
import ("fmt")  
  
func myFunction(x int, y string) (result int, txt1 string) {  
  result = x + x  
  txt1 = y + " World!"  
  return  
}

func main() {  
   a, \_ := myFunction(5, "Hello")  
  fmt.Println(a)  
}

Result:

`10   `

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_func13)

  

Track your progress - it's free!

   [![Get Certified](https://www.w3schools.com/images/img_course_up_300.png)](https://campus.w3schools.com/collections/course-catalog)
