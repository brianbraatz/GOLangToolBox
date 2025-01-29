---
Description: Go - The continue Statement
Notes: The continue statement in Go programming language works somewhat like a break statement. Instead of forcing termination, a continue statement forces the next iteration of the loop to take place, skipping any code in between.
author: 
Url: https://www.tutorialspoint.com/go/go_continue_statement.htm
Created: "2025-01-29  02:35:23"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go - The continue Statement

source: https://www.tutorialspoint.com/go/go_continue_statement.htm

> ## Excerpt
> The continue statement in Go programming language works somewhat like a break statement. Instead of forcing termination, a continue statement forces the next iteration of the loop to take place, skipping any code in between.

---
___

___

The **continue** statement in Go programming language works somewhat like a **break** statement. Instead of forcing termination, a **continue** statement forces the next iteration of the loop to take place, skipping any code in between.

In case of the **for** loop, **continue** statement causes the conditional test and increment portions of the loop to execute.

## Syntax

The syntax for a **continue** statement in Go is as follows −

```go
continue;
```

![Go continue statement](https://www.tutorialspoint.com/go/images/go_continue_statement.jpg)

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
      if a == 15 {
         
         a = a + 1;
         continue;
      }
      fmt.Printf("value of a: %d\n", a);
      a++;     
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
