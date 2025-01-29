---
Description: Go - Functions
Notes: A function is a group of statements that together perform a task. Every Go program has at least one function, which is main(). You can divide your code into separate functions. How you divide your code among different functions is up to you, but logically, the division should be such that each funct
author: 
Url: https://www.tutorialspoint.com/go/go_functions.htm
Created: "2025-01-29  02:35:39"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go - Functions

source: https://www.tutorialspoint.com/go/go_functions.htm

> ## Excerpt
> A function is a group of statements that together perform a task. Every Go program has at least one function, which is main(). You can divide your code into separate functions. How you divide your code among different functions is up to you, but logically, the division should be such that each funct

---
___

___

A function is a group of statements that together perform a task. Every Go program has at least one function, which is **main()**. You can divide your code into separate functions. How you divide your code among different functions is up to you, but logically, the division should be such that each function performs a specific task.

A function **declaration** tells the compiler about a function name, return type, and parameters. A function **definition** provides the actual body of the function.

The Go standard library provides numerous built-in functions that your program can call. For example, the function **len()** takes arguments of various types and returns the length of the type. If a string is passed to it, the function returns the length of the string in bytes. If an array is passed to it, the function returns the length of the array.

Functions are also known as **method, sub-routine**, or **procedure**.

## Defining a Function in Go Language

A function is defined in Go language by using the `func` keyword followed by the `function_name`, parameter list, and the return type.

### Syntax

The general form of a function definition in Go programming language is as follows −

```go
func function_name( [parameter list] ) [return_types]
{
   body of the function
}
```

A function definition in Go programming language consists of a _function header_ and a _function body_. Here are all the parts of a function −

-   **Func** − It starts the declaration of a function.
    
-   **Function Name** − It is the actual name of the function. The function name and the parameter list together constitute the function signature.
    
-   **Parameters** − A parameter is like a placeholder. When a function is invoked, you pass a value to the parameter. This value is referred to as actual parameter or argument. The parameter list refers to the type, order, and number of the parameters of a function. Parameters are optional; that is, a function may contain no parameters.
    
-   **Return Type** − A function may return a list of values. The return\_types is the list of data types of the values the function returns. Some functions perform the desired operations without returning a value. In this case, the return\_type is the not required.
    
-   **Function Body** − It contains a collection of statements that define what the function does.
    

### Example

The following source code shows a function called **max()**. This function takes two parameters num1 and num2 and returns the maximum between the two −

```go

func max(num1, num2 int) int {
   
   result int

   if (num1 > num2) {
      result = num1
   } else {
      result = num2
   }
   return result 
}
```

## Calling a Function

While creating a Go function, you give a definition of what the function has to do. To use a function, you will have to call that function to perform the defined task.

When a program calls a function, the program control is transferred to the called function. A called function performs a defined task and when its return statement is executed or when its function-ending closing brace is reached, it returns the program control back to the main program.

To call a function, you simply need to pass the required parameters along with its function name. If the function returns a value, then you can store the returned value.

### Example

The following example demonstrates calling a function in the Go language:

```go
package main

import "fmt"

func main() {
   
   var a int = 100
   var b int = 200
   var ret int

   
   ret = max(a, b)

   fmt.Printf( "Max value is : %d\n", ret )
}


func max(num1, num2 int) int {
   
   var result int

   if (num1 > num2) {
      result = num1
   } else {
      result = num2
   }
   return result 
}
```

We have kept the max() function along with the main() function and compiled the source code. While running the final executable, it would produce the following result −

```
Max value is : 200
```

## Returning Multiple Values from Function

Go language functions can return multiple values by defining multiple return types, and then inside the function definition, you need to return multiple values separated by the commas using the `return` keyword.

### Example

The following example demonstrates how you can define a function to return multiple values:

```go
package main

import "fmt"

func swap(x, y string) (string, string) {
   return y, x
}
func main() {
   a, b := swap("Mahesh", "Kumar")
   fmt.Println(a, b)
}
```

When the above code is compiled and executed, it produces the following result −

```
Kumar Mahesh
```

## Function Arguments

If a function is to use arguments, it must declare variables that accept the values of the arguments. These variables are called the **formal parameters** of the function.

The formal parameters behave like other local variables inside the function and are created upon entry into the function and destroyed upon exit.

## Argument Passing: Call by Value and Call by Reference

While calling a function, there are two ways that arguments can be passed to a function −

| Sr.No | Call Type & Description |
| --- | --- |
| 1 | [Call by value](https://www.tutorialspoint.com/go/go_function_call_by_value.htm "Function call by value in Go")
This method copies the actual value of an argument into the formal parameter of the function. In this case, changes made to the parameter inside the function have no effect on the argument.

 |
| 2 | [Call by reference](https://www.tutorialspoint.com/go/go_function_call_by_reference.htm "Function call by reference in Go")

This method copies the address of an argument into the formal parameter. Inside the function, the address is used to access the actual argument used in the call. This means that changes made to the parameter affect the argument.

 |

By default, Go uses call by value to pass arguments. In general, it means the code within a function cannot alter the arguments used to call the function. The above program, while calling the max() function, used the same method.

### Example: Call by Value

This example demonstrates calling a function by value:

```go
package main
import "fmt"

func updateValue(x int) {
    x = x * x
    fmt.Println("Inside updateValue Function, x =", x)
}

func main() {
    num := 10
    fmt.Println("Before function call, num =", num)

    
    updateValue(num)

    fmt.Println("After function call, num =", num)
}
```

When the above code is compiled and executed, it produces the following result −

```
Before function call, num = 10
Inside updateValue Function, x = 100
After function call, num = 10
```

### Example: Call by Reference

This example demonstrates calling a function by reference:

```go
package main
import "fmt"

func updateValue(x *int) {
    *x = *x * *x
    fmt.Println("Inside updateValue Function, x =", *x)
}

func main() {
    num := 10
    fmt.Println("Before function call, num =", num)

    
    updateValue(&num)

    fmt.Println("After function call, num =", num)
}
```

When the above code is compiled and executed, it produces the following result −

```
Before function call, num = 10
Inside updateValue Function, x = 100
After function call, num = 100
```

## Function Usage

A function can be used in the following ways:

| Sr.No | Function Usage & Description |
| --- | --- |
| 1 | [Function as Value](https://www.tutorialspoint.com/go/go_function_as_values.htm "Function as values")
Functions can be created on the fly and can be used as values.

 |
| 2 | [Function Closures](https://www.tutorialspoint.com/go/go_function_closures.htm "Function Closures")

Functions closures are anonymous functions and can be used in dynamic programming.

 |
| 3 | [Method](https://www.tutorialspoint.com/go/go_method.htm "Method")

Methods are special functions with a receiver.

 |
