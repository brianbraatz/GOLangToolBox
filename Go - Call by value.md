---
Description: Go - Call by value
Notes: The call by value method of passing arguments to a function copies the actual value of an argument into the formal parameter of the function. In this case, changes made to the parameter inside the function have no effect on the argument.
author: 
Url: https://www.tutorialspoint.com/go/go_function_call_by_value.htm
Created: "2025-01-29  02:35:46"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go - Call by value

source: https://www.tutorialspoint.com/go/go_function_call_by_value.htm

> ## Excerpt
> The call by value method of passing arguments to a function copies the actual value of an argument into the formal parameter of the function. In this case, changes made to the parameter inside the function have no effect on the argument.

---
___

___

The **call by value** method of passing arguments to a function copies the actual value of an argument into the formal parameter of the function. In this case, changes made to the parameter inside the function have no effect on the argument.

By default, Go programming language uses _call by value_ method to pass arguments. In general, this means that code within a function cannot alter the arguments used to call the function. Consider the function **swap()** definition as follows.

## Syntax

The function definition for the call by value argument passing is as follows:

```go

func swap(int x, int y) int {
   var temp int

   temp = x 
   x = y    
   y = temp 

   return temp;
}
```

Now, let us call the function **swap()** by passing actual values as in the following example −

```go
package main

import "fmt"

func main() {
   
   var a int = 100
   var b int = 200

   fmt.Printf("Before swap, value of a : %d\n", a )
   fmt.Printf("Before swap, value of b : %d\n", b )

   
   swap(a, b)

   fmt.Printf("After swap, value of a : %d\n", a )
   fmt.Printf("After swap, value of b : %d\n", b )
}
func swap(x, y int) int {
   var temp int

   temp = x 
   x = y    
   y = temp 

   return temp;
}
```

Put the above code in a single go file, and then compile and execute it. It will produce the following result −

```
Before swap, value of a :100
Before swap, value of b :200
After swap, value of a :100
After swap, value of b :200
```

It shows that there is no change in the values though they had been changed inside the function.

[

Explore our **latest online courses** and learn new skills at your own pace. Enroll and become a certified expert to boost your career.

](https://www.tutorialspoint.com/latest/courses?utm_source=tutorialspoint&utm_medium=tutorials_3p&utm_campaign=internal)

## Example: Call by Value with Structs

In this example, we are demonstrating how you can use the call by value with structs:

```go
package main
import "fmt"


type Student struct {
    name  string
    age   int
    grade string
}


func changeStudentData(s Student) {
    s.name = "Prakash Joshi"
    s.age = 21
    s.grade = "B"
    fmt.Println("Student Data Inside changeStudentData():\n", s)
}

func main() {
    student := Student{name: "Reese Witherspoon", age: 23, grade: "A"}
    fmt.Println("Student data before function call:\n", student)

    
    changeStudentData(student)

    fmt.Println("Student data after function call:\n", student)
}
```

When the above code is compiled and executed, it produces the following result −

```
Student data before function call:
 {Reese Witherspoon 23 A}
Student Data Inside changeStudentData():
 {Prakash Joshi 21 B}
Student data after function call:
 {Reese Witherspoon 23 A}
```

As you can see in the output, that student data is not changed after the function call because we are calling the function by value. If you want to update the data on a function call, you must use the call by reference technique; you can read it in detail in the next chapter ([Call by reference in Go language](https://www.tutorialspoint.com/go/go_function_call_by_reference.htm)).
