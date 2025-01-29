---
Description: Go - Function Closure
Notes: Go - Function Closure - Go function closure is a function value that references variables from outside its body. The closures bind these variables and make them accessible even after closing the outer function.
author: 
Url: https://www.tutorialspoint.com/go/go_function_closures.htm
Created: "2025-01-29  02:36:07"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go - Function Closure

source: https://www.tutorialspoint.com/go/go_function_closures.htm

> ## Excerpt
> Go - Function Closure - Go function closure is a function value that references variables from outside its body. The closures bind these variables and make them accessible even after closing the outer function.

---
___

___

**Go function closure** is a function value that references variables from outside its body. The closures bind these variables and make them accessible even after closing the outer function.

## Creating a Closure in Go

A closure is created when an inner function captures and retains access to the variables of its enclosing function. You can create a closure by following the below syntax:

```
// Creation
counter := func() func() int {
count := 0
return func() int {
count++
return count
}
}
// Use
increment := counter()
```

Here, the `counter` function defines a local variable `count`, and the returned inner function, which will be known as closure, has access to `count` and modifies it on each call.

## Example to Create a Simple Closure

In the following example we are creating a simple closure:

```go
package main
import "fmt"

func main() {
    
    updateCounter := func() func() int {
        
        count := 100
        return func() int {
            count++
            return count
        }
    }

    
    increment := updateCounter()

    
    fmt.Println(increment())
    fmt.Println(increment())
}
```

When the above code is compiled and executed, it produces the following result −

```
101
102
```

[

Explore our **latest online courses** and learn new skills at your own pace. Enroll and become a certified expert to boost your career.

](https://www.tutorialspoint.com/latest/courses?utm_source=tutorialspoint&utm_medium=tutorials_3p&utm_campaign=internal)

## Passing Values into Closures

You can pass values into the closure while calling the function; you need to define the argument type during defining the nested function.

### Example

The following example demonstrates passing the values to a closure:

```go
package main
import "fmt"

func main() {
    
    updateCounter := func(initial int) func() int {
        count := initial 
        return func() int {
            count++
            return count
        }
    }

    
    inc_x := updateCounter(100)

    
    fmt.Println(inc_x())
    fmt.Println(inc_x())

    
    inc_y := updateCounter(200)

    
    fmt.Println(inc_y())
    fmt.Println(inc_y())    
}
```

When the above code is compiled and executed, it produces the following result −

```
101
102
201
202
```
