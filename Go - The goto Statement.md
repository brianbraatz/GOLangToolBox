---
Description: Go - The goto Statement
Notes: A goto statement in Go programming language provides an unconditional jump from the goto to a labeled statement in the same function.
author: 
Url: https://www.tutorialspoint.com/go/go_goto_statement.htm
Created: "2025-01-29  02:35:32"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go - The goto Statement

source: https://www.tutorialspoint.com/go/go_goto_statement.htm

> ## Excerpt
> A goto statement in Go programming language provides an unconditional jump from the goto to a labeled statement in the same function.

---
___

___

A **goto** statement in Go programming language provides an unconditional jump from the goto to a labeled statement in the same function.

**Note** − Use of **goto** statement is highly discouraged in any programming language because it becomes difficult to trace the control flow of a program, making the program difficult to understand and hard to modify. Any program that uses a goto can be rewritten using some other construct.

## Syntax

The syntax for a **goto** statement in Go is as follows −

```go
goto label;
..
.
label: statement;
```

## Flow Diagram

![Go goto statement](https://www.tutorialspoint.com/go/images/go_goto_statement.jpg)

[

Explore our **latest online courses** and learn new skills at your own pace. Enroll and become a certified expert to boost your career.

](https://www.tutorialspoint.com/latest/courses?utm_source=tutorialspoint&utm_medium=tutorials_3p&utm_campaign=internal)

## Example

```go
package main

import "fmt"

func main() {
   
   var a int = 10

   
   LOOP: for a < 20 {
      if a == 15 {
         
         a = a + 1
         goto LOOP
      }
      fmt.Printf("value of a: %d\n", a)
      a++     
   }  
}
```

When the above code is compiled and executed, it produces the following result −

```
value of a: 10
value of a: 11
value of a: 12
value of a: 13
value of a: 14
value of a: 16
value of a: 17
value of a: 18
value of a: 19
```
