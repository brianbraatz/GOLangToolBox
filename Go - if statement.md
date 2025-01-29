---
Description: Go - if statement
Notes: Go - if statement - Go if statement consists of a boolean expression followed by one or more statements. It checks whether the given Boolean expression is true or not. If it is true, the associate statements execute.
author: 
Url: https://www.tutorialspoint.com/go/go_if_statement.htm
Created: "2025-01-29  02:34:12"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go - if statement

source: https://www.tutorialspoint.com/go/go_if_statement.htm

> ## Excerpt
> Go - if statement - Go if statement consists of a boolean expression followed by one or more statements. It checks whether the given Boolean expression is true or not. If it is true, the associate statements execute.

---
___

___

## The if Statement

**Go if statement** consists of a boolean expression followed by one or more statements. It checks whether the given Boolean expression is true or not. If it is true, the associate statements execute.

## Syntax

The syntax of an **if** statement in Go programming language is −

```go
if(boolean_expression) {
   
}
```

[

Explore our **latest online courses** and learn new skills at your own pace. Enroll and become a certified expert to boost your career.

](https://www.tutorialspoint.com/latest/courses?utm_source=tutorialspoint&utm_medium=tutorials_3p&utm_campaign=internal)

## Flow Diagram

![Go if statement](https://www.tutorialspoint.com/go/images/if_statement.jpg "Go if statement")

## Example

This example demonstrates how to use an if statement in Go to check a condition and execute a block of code when the condition is true.

```go
package main

import "fmt"

func main() {
   
   var a int = 10
 
   
   if( a < 20 ) {
      
      fmt.Printf("a is less than 20\n" )
   }
   fmt.Printf("value of a is : %d\n", a)
}
```

When the above code is compiled and executed, it produces the following result −

```
a is less than 20;
value of a is : 10
```

## Example

In the following example, we are checking if a number is positive, negative, or zero using only if statements:

```go
package main

import "fmt"

func main() {
    var num int
    
    num = -10

    if num > 0 {
        fmt.Println("The number is positive.")
    }
    if num < 0 {
        fmt.Println("The number is negative.")
    }
    if num == 0 {
        fmt.Println("The number is zero.")
    }
}
```

When the above code is compiled and executed, it produces the following result −

```
The number is negative.
```
