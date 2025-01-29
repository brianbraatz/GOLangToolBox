---
Description: Go - break statement
Notes: The break statement in Go programming language has the following two usages ?
author: 
Url: https://www.tutorialspoint.com/go/go_break_statement.htm
Created: "2025-01-29  02:35:15"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go - break statement

source: https://www.tutorialspoint.com/go/go_break_statement.htm

> ## Excerpt
> The break statement in Go programming language has the following two usages ?

---
___

___

The **break** statement in Go programming language has the following two usages −

-   When a **break** statement is encountered inside a loop, the loop is immediately terminated and the program control resumes at the next statement following the loop.
    
-   It can be used to terminate a case in a **switch** statement.
    

If you are using nested loops, the break statement will stop the execution of the innermost loop and start executing the next line of code after the block.

## Syntax

The syntax for a **break** statement in Go is as follows −

```go
break;
```

![Go break statement](https://www.tutorialspoint.com/go/images/go_break_statement.jpg)

[

Explore our **latest online courses** and learn new skills at your own pace. Enroll and become a certified expert to boost your career.

](https://www.tutorialspoint.com/latest/courses?utm_source=tutorialspoint&utm_medium=tutorials_3p&utm_campaign=internal)

## Example

```go
package main

import "fmt"

func main() {
   
   var a int = 10

   
   for a < 20 {
      fmt.Printf("value of a: %d\n", a);
      a++;
      if a > 15 {
         
         break;
      }
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
value of a: 15
```
