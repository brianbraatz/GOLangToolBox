---
Description: Go - Functions as Values
Notes: Go programming language provides the flexibility to create functions on the fly and use them as values. In the following example, we've initialized a variable with a function definition. Purpose of this function variable is just to use inbuilt math.sqrt() function.
author: 
Url: https://www.tutorialspoint.com/go/go_function_as_values.htm
Created: "2025-01-29  02:36:01"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go - Functions as Values

source: https://www.tutorialspoint.com/go/go_function_as_values.htm

> ## Excerpt
> Go programming language provides the flexibility to create functions on the fly and use them as values. In the following example, we've initialized a variable with a function definition. Purpose of this function variable is just to use inbuilt math.sqrt() function.

---
___

___

## Functions as Values

Go programming language provides the flexibility to create functions on the fly and use them as values. In the following example, we've initialized a variable with a function definition. Purpose of this function variable is just to use inbuilt math.sqrt() function.

### Example

For example −

```go
package main

import ("fmt" "math")

func main(){
   
   getSquareRoot := func(x float64) float64 {
      return math.Sqrt(x)
   }

   
   fmt.Println(getSquareRoot(9))
}
```

When the above code is compiled and executed, it produces the following result −

```
3
```

In Go language, the functions can be assigned to variables, passed as arguments to other functions, or returned as values from functions. Let's understand each concept in detail.

## Assigning a Function to a Variable

Go language allows you to assign a function directly to a variable. The function should have a return type.

### Example

```go
package main

import "fmt"


func addTwoNumbers(a int, b int) int {
    return a + b
}

func main() {
    
    sum := addTwoNumbers

    
    
    result := sum(100, 200)
    fmt.Println("Sum:", result)
}
```

When the above code is compiled and executed, it produces the following result −

```
Sum: 300
```

[

Explore our **latest online courses** and learn new skills at your own pace. Enroll and become a certified expert to boost your career.

](https://www.tutorialspoint.com/latest/courses?utm_source=tutorialspoint&utm_medium=tutorials_3p&utm_campaign=internal)

## Passing a Function as an Argument

You can pass a function to a function as an argument; you just need to use the function declaration as an argument.

### Example

```go
package main

import "fmt"


func calculation(x int, y int, op func(int, int) int) int {
    return op(x, y)
}

func multiplyNumbers(x int, y int) int {
    return x * y
}

func main() {
    result := calculation (2, 5, multiplyNumbers)
    fmt.Println("Result:", result)
}
```

When the above code is compiled and executed, it produces the following result −

```
Result: 10
```

## Returning a Function as a Value

A function can also return a function as a value in the Go language. It is useful when you want to return an expression calculated by creating any function.

### Example

```go
package main
import "fmt"


func calculation(factor int) func(int) int {
    return func(value int) int {
        return factor * value
    }
}

func main() {
    multiplyByTwo := calculation(2)
    result := multiplyByTwo(20)
    fmt.Println("Result:", result)
}
```

When the above code is compiled and executed, it produces the following result −

```
Result: 40
```
