---
Description: Go - The Select Statement
Notes: Go select statement is useful to handle multiple channel operations and selects the ready channel against multiple channels.
author: 
Url: https://www.tutorialspoint.com/go/go_select_statement.htm
Created: "2025-01-29  02:34:45"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go - The Select Statement

source: https://www.tutorialspoint.com/go/go_select_statement.htm

> ## Excerpt
> Go select statement is useful to handle multiple channel operations and selects the ready channel against multiple channels.

---
___

___

Go select statement is useful to handle multiple channel operations and selects the ready channel against multiple channels.

## The Select Statement

When you are working with multiple channels in Go language, the **select statement** waits on multiple channel operations and executes the code block for the channel that is ready.

### Syntax

The syntax for a **select** statement in Go programming language is as follows −

```
select {
   case communication clause  :
      statement(s);      
   case communication clause  :
      statement(s); 
   /* you can have any number of case statements */
   default : /* Optional */
      statement(s);
}
```

## Rules for Using a Select Statement in Go

The following rules apply to a **select** statement −

-   You can have any number of case statements within a select. Each case is followed by the value to be compared to and a colon.
-   The **type** for a case must be the a communication channel operation.
-   When the channel operation occured the statements following that case will execute. No **break** is needed in the case statement.
-   A **select** statement can have an optional **default** case, which must appear at the end of the select. The default case can be used for performing a task when none of the cases is true. No **break** is needed in the default case.

[

Explore our **latest online courses** and learn new skills at your own pace. Enroll and become a certified expert to boost your career.

](https://www.tutorialspoint.com/latest/courses?utm_source=tutorialspoint&utm_medium=tutorials_3p&utm_campaign=internal)

## Example of Select Statement

The following example demonstrates how you can use the select statement to handle multiple channels:

```go
package main

import "fmt"

func main() {
   var c1, c2, c3 chan int
   var i1, i2 int
   select {
      case i1 = <-c1:
         fmt.Printf("received ", i1, " from c1\n")
      case c2 <- i2:
         fmt.Printf("sent ", i2, " to c2\n")
      case i3, ok := (<-c3):  
         if ok {
            fmt.Printf("received ", i3, " from c3\n")
         } else {
            fmt.Printf("c3 is closed\n")
         }
      default:
         fmt.Printf("no communication\n")
   }    
}   
```

When the above code is compiled and executed, it produces the following result −

```
no communication
```

## Nested select Statement

A nested select statement allows you to use one or more select statements inside a select statement.

### Example

The following is an example of a nested select statement in Go language:

```go
package main

import (
"fmt"
"time"
)

func main() {

ch1 := make(chan string)
ch2 := make(chan int)


go func() {
time.Sleep(1 * time.Second)
ch1 <- "I am in channel 1"
}()


go func() {
time.Sleep(3 * time.Second)
ch2 <- 10
}()


select {
case ch_data1 := <-ch1:
fmt.Println("Received from channel1:", ch_data1)
select {
case ch_data2 := <-ch2:
fmt.Println("Received from channel2:", ch_data2)
default:
fmt.Println("No data in channel2 yet")
}
case ch_data2 := <-ch2:
fmt.Println("Received from channel2:", ch_data2)
default:
fmt.Println("No messages received yet from any channel")
}
}
```

When the above code is compiled and executed, it produces the following result −

```
No messages received yet from any channel
```
