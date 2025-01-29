---
Description: Go - Method
Notes: Go - Method - Go programming language supports special types of functions called methods. In method declaration syntax, a receiver is present to represent the container of the function. This receiver can be used to call a function using . operator. For example ?
author: 
Url: https://www.tutorialspoint.com/go/go_method.htm
Created: "2025-01-29  02:36:14"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go - Method

source: https://www.tutorialspoint.com/go/go_method.htm

> ## Excerpt
> Go - Method - Go programming language supports special types of functions called methods. In method declaration syntax, a receiver is present to represent the container of the function. This receiver can be used to call a function using . operator. For example ?

---
___

___

Go programming language supports special types of functions called methods. In method declaration syntax, a "receiver" is present to represent the container of the function. This receiver can be used to call a function using "." operator. For example −

## Syntax of a Method

```go
func (variable_name variable_data_type) function_name() [return_type]{
   
}
```

```go
package main

import (
   "fmt" 
   "math" 
)


type Circle struct {
   x,y,radius float64
}


func(circle Circle) area() float64 {
   return math.Pi * circle.radius * circle.radius
}

func main(){
   circle := Circle{x:0, y:0, radius:5}
   fmt.Printf("Circle area: %f", circle.area())
}
```

When the above code is compiled and executed, it produces the following result −

```
Circle area: 78.539816
```

[

Explore our **latest online courses** and learn new skills at your own pace. Enroll and become a certified expert to boost your career.

](https://www.tutorialspoint.com/latest/courses?utm_source=tutorialspoint&utm_medium=tutorials_3p&utm_campaign=internal)

## Methods with Struct Type Receiver

You can create a method with a struct type receiver that operates on a copy of the struct, so whatever changes will be done in the method, they do not affect the original struct.

### Example

```go
package main
import "fmt"


type Rectangle struct {
    width, height float64
}


func (rect Rectangle) Area() float64 {
    return rect.width * rect.height
}

func main() {
    rectObj := Rectangle{width: 2.4, height: 4.5}
    fmt.Println("Area of Rectangle:", rectObj.Area())
}
```

When the above code is compiled and executed, it produces the following result −

```
Area of Rectangle: 10.799999999999999
```

## Methods with Non-Struct Type Receiver

You can also create a method with non-struct type receivers of such type whose definition is present in the same package.

### Example

```go
package main
import "fmt"


type value int


func (v value) cube() value {
    return v * v * v
}

func main() {
    x := value(3)
    y := x.cube()

    fmt.Println("Cube of", x, "is", y) 
}
```

```
Cube of 3 is 27
```

## Methods with Pointer Receiver

You can create a method that can have pointer receivers. This approach reflects the changes done in the method in the caller.

### Example

```go
package main
import "fmt"

type student struct {
    grade string
}


func (s *student) updateGrade(newGrade string) {
    s.grade = newGrade
}

func main() {
    s := student{grade: "B"}
    
    fmt.Println("Before:", s.grade)
    
    
    s.updateGrade("A")
    
    fmt.Println("After:", s.grade)
}
```

```
Before: B
After: A
```
