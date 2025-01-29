---
Description: Go - Scope Rules
Notes: Go - Scope Rules - A scope in any programming is a region of the program where a defined variable can exist and beyond that the variable cannot be accessed. There are three places where variables can be declared in Go programming language ?
author: 
Url: https://www.tutorialspoint.com/go/go_scope_rules.htm
Created: "2025-01-29  02:36:21"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go - Scope Rules

source: https://www.tutorialspoint.com/go/go_scope_rules.htm

> ## Excerpt
> Go - Scope Rules - A scope in any programming is a region of the program where a defined variable can exist and beyond that the variable cannot be accessed. There are three places where variables can be declared in Go programming language ?

---
___

___

A scope in any programming is a region of the program where a defined variable can exist and beyond that the variable cannot be accessed. There are three places where variables can be declared in Go programming language −

-   Inside a function or a block (**local** variables)
    
-   Outside of all functions (**global** variables)
    
-   In the definition of function parameters (**formal** parameters)
    

Let us find out what are **local** and **global** variables and what are **formal** parameters.

## Local Variables

[Variables](https://www.tutorialspoint.com/go/go_variables.htm) that are declared inside a function or a block are called local variables. They can be used only by statements that are inside that function or block of code. Local variables are not known to functions outside their own.

### Example

The following example uses local variables. Here all the variables a, b, and c are local to the main() function.

```go
package main

import "fmt"

func main() {
   
   var a, b, c int 

   
   a = 10
   b = 20
   c = a + b

   fmt.Printf ("value of a = %d, b = %d and c = %d\n", a, b, c)
}
```

When the above code is compiled and executed, it produces the following result −

```
value of a = 10, b = 20 and c = 30
```

## Global Variables

Global variables are defined outside of a function, usually on top of the program. Global variables hold their value throughout the lifetime of the program and they can be accessed inside any of the [functions](https://www.tutorialspoint.com/go/go_functions.htm) defined for the program.

A global variable can be accessed by any function. That is, a global variable is available for use throughout the program after its declaration.

### Example

The following example uses both global and local variables −

```go
package main

import "fmt"
 

var g int
 
func main() {
   
   var a, b int

   
   a = 10
   b = 20
   g = a + b

   fmt.Printf("value of a = %d, b = %d and g = %d\n", a, b, g)
}
```

When the above code is compiled and executed, it produces the following result −

```
value of a = 10, b = 20 and g = 30
```

A program can have the same name for local and global variables but the value of the local variable inside a function takes preference. For example −

### Example

```go
package main

import "fmt"
 

var g int = 20
 
func main() {
   
   var g int = 10
 
   fmt.Printf ("value of g = %d\n",  g)
}
```

When the above code is compiled and executed, it produces the following result −

```
value of g = 10
```

[

Explore our **latest online courses** and learn new skills at your own pace. Enroll and become a certified expert to boost your career.

](https://www.tutorialspoint.com/latest/courses?utm_source=tutorialspoint&utm_medium=tutorials_3p&utm_campaign=internal)

## Formal Parameters

Formal parameters are treated as local variables with-in that function and they take preference over the global variables. For example −

### Example

```go
package main

import "fmt"
 

var a int = 20;
 
func main() {
   
   var a int = 10
   var b int = 20
   var c int = 0

   fmt.Printf("value of a in main() = %d\n",  a);
   c = sum( a, b);
   fmt.Printf("value of c in main() = %d\n",  c);
}

func sum(a, b int) int {
   fmt.Printf("value of a in sum() = %d\n",  a);
   fmt.Printf("value of b in sum() = %d\n",  b);

   return a + b;
}
```

When the above code is compiled and executed, it produces the following result −

```
value of a in main() = 10
value of a in sum() = 10
value of b in sum() = 20
value of c in main() = 30
```

## Initializing Local and Global Variables

Local and global variables are initialized to their default value, which is 0; while pointers are initialized to nil.

| Data Type | Initial Default Value |
| --- | --- |
| int | 0 |
| float32 | 0 |
| pointer | nil |
