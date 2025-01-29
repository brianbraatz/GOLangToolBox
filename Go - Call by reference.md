---
Description: Go - Call by reference
Notes: Go - Call by reference - The call by reference method of passing arguments to a function copies the address of an argument into the formal parameter. Inside the function, the address is used to access the actual argument used in the call. This means that changes made to the parameter affect the passed argument.
author: 
Url: https://www.tutorialspoint.com/go/go_function_call_by_reference.htm
Created: "2025-01-29  02:35:54"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go - Call by reference

source: https://www.tutorialspoint.com/go/go_function_call_by_reference.htm

> ## Excerpt
> Go - Call by reference - The call by reference method of passing arguments to a function copies the address of an argument into the formal parameter. Inside the function, the address is used to access the actual argument used in the call. This means that changes made to the parameter affect the passed argument.

---
___

___

The **call by reference** method of passing arguments to a function copies the address of an argument into the formal parameter. Inside the function, the address is used to access the actual argument used in the call. This means that changes made to the parameter affect the passed argument.

To pass the value by reference, argument pointers are passed to the functions just like any other value. Accordingly you need to declare the function parameters as pointer types as in the following function **swap()**, which exchanges the values of the two integer variables pointed to by its arguments.

## Syntax

The function definition for the call by reference argument passing is as follows:

```go

func swap(x *int, y *int) {
   var temp int
   temp = *x    
   *x = *y      
   *y = temp    
}
```

## Call by Reference Example

For now, let us call the function swap() by passing values by reference as in the following example −

```go
package main

import "fmt"

func main() {
   
   var a int = 100
   var b int = 200

   fmt.Printf("Before swap, value of a : %d\n", a )
   fmt.Printf("Before swap, value of b : %d\n", b )

   
   swap(&a, &b)

   fmt.Printf("After swap, value of a : %d\n", a )
   fmt.Printf("After swap, value of b : %d\n", b )
}
func swap(x *int, y *int) {
   var temp int
   temp = *x    
   *x = *y    
   *y = temp    
}
```

Put the above code in a single Go file, and then compile and execute it. It produces the following result −

```
Before swap, value of a :100
Before swap, value of b :200
After swap, value of a :200
After swap, value of b :100
```

It shows that the change has reflected outside the function as well, unlike call by value where the changes do not reflect outside the function.

[

Explore our **latest online courses** and learn new skills at your own pace. Enroll and become a certified expert to boost your career.

](https://www.tutorialspoint.com/latest/courses?utm_source=tutorialspoint&utm_medium=tutorials_3p&utm_campaign=internal)

## Example: Call by Reference with Structs

In this example, we are demonstrating how you can use the call by reference with structs:

```go
package main

import "fmt"


type Student struct {
    name  string
    age   int
    grade string
}


func changeStudentData(s *Student) {
    s.name = "Prakash Joshi"
    s.age = 21
    s.grade = "B"
    fmt.Println("Student Data Inside changeStudentData():\n", *s)
}

func main() {
    student := Student{name: "Reese Witherspoon", age: 23, grade: "A"}
    fmt.Println("Student data before function call:\n", student)

    
    changeStudentData(&student)

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
 {Prakash Joshi 21 B}
```

As you can see in the output, that student data is changed after the function call because we are calling the function by reference.
