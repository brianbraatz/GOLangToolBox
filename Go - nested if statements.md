---
Description: Go - nested if statements
Notes: It is always legal in Go programming to nest if-else statements, which means you can use one if or else if statement inside another if or else if statement(s).
author: 
Url: https://www.tutorialspoint.com/go/go_nested_if_statements.htm
Created: "2025-01-29  02:34:30"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go - nested if statements

source: https://www.tutorialspoint.com/go/go_nested_if_statements.htm

> ## Excerpt
> It is always legal in Go programming to nest if-else statements, which means you can use one if or else if statement inside another if or else if statement(s).

---
___

___

## Nested if Statement

It is always legal in Go programming to **nest** if-else statements, which means you can use one if or else if statement inside another if or else if statement(s).

## Syntax

The syntax for a **nested if** statement is as follows −

```
if( boolean_expression 1) {
   /* Executes when the boolean expression 1 is true */
   if(boolean_expression 2) {
      /* Executes when the boolean expression 2 is true */
   }
}
```

You can nest **else if...else** in the similar way as you have nested _if_ statement.

[

Explore our **latest online courses** and learn new skills at your own pace. Enroll and become a certified expert to boost your career.

](https://www.tutorialspoint.com/latest/courses?utm_source=tutorialspoint&utm_medium=tutorials_3p&utm_campaign=internal)

## Example of Nested if Statement

This example demonstrates nested if statements:

```go
package main

import "fmt"

func main() {
   
   var a int = 100
   var b int = 200
 
   
   if( a == 100 ) {
      
      if( b == 200 )  {
         
         fmt.Printf("Value of a is 100 and b is 200\n" );
      }
   }
   fmt.Printf("Exact value of a is : %d\n", a );
   fmt.Printf("Exact value of b is : %d\n", b );
}
```

When the above code is compiled and executed, it produces the following result −

```
Value of a is 100 and b is 200
Exact value of a is : 100
Exact value of b is : 200
```

## Nested if Statement with break

The `break` statement terminates the [loops](https://www.tutorialspoint.com/go/go_loops.htm), and it can be used inside a **nested if statement**, but a **nested if statement** should be used inside a loop.

### Example

This example demonstrates the use of a `break` statement within a nested if statement that is placed inside a [`for` loop](https://www.tutorialspoint.com/go/go_for_loop.htm).

In this example, there is an integer array, and we are checking even and odd numbers that are greater than 20 and breaking the loop if an even number is found that is greater than 20.

```go
package main
import "fmt"

func main() {
    
    arr := []int{10, 20, 55, 53, 75, 80}

    for _, num := range arr {
        if num > 20 {
            if num%2 == 0 {
                fmt.Println("Even number found, breaking loop.")
                break
            } else {
                fmt.Printf("Odd number > 20: %d\n", num)
            }
        }
    }

    fmt.Println("End of loop.")
}
```

When the above code is compiled and executed, it produces the following result −

```
Odd number &gt; 20: 55
Odd number &gt; 20: 53
Odd number &gt; 20: 75
Even number found, breaking loop.
End of loop.
```
