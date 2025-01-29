---
Description: Go - for Loop
Notes: Go - for Loop - A for loop is a repetition control structure. It allows you to write a loop that needs to execute a specific number of times.
author: 
Url: https://www.tutorialspoint.com/go/go_for_loop.htm
Created: "2025-01-29  02:34:56"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go - for Loop

source: https://www.tutorialspoint.com/go/go_for_loop.htm

> ## Excerpt
> Go - for Loop - A for loop is a repetition control structure. It allows you to write a loop that needs to execute a specific number of times.

---
___

___

A **for** loop is a repetition control structure. It allows you to write a loop that needs to execute a specific number of times.

## for Loop Syntax

The syntax of **for** loop in Go programming language is −

```
for [condition |  ( init; condition; increment ) | Range] {
   statement(s);
}
```

## Working of for Loop in Go

The flow of control (working flow) in a **for** loop is a follows −

-   If a **condition** is available, then for loop executes as long as condition is true.
    
-   If a **for** clause that is **( init; condition; increment )** is present then −
    
    -   The **init** step is executed first, and only once. This step allows you to declare and initialize any loop control variables. You are not required to put a statement here, as long as a semicolon appears.
        
    -   Next, the **condition** is evaluated. If it is true, the body of the loop is executed. If it is false, the body of the loop does not execute and the flow of control jumps to the next statement just after the **for** loop.
        
    -   After the body of the for loop executes, the flow of control jumps back up to the **increment** statement. This statement allows you to update any loop control variables. This statement can be left blank, as long as a semicolon appears after the condition.
        
    -   The condition is now evaluated again. If it is true, the loop executes and the process repeats itself (body of loop, then increment step, and then again the condition). After the condition becomes false, the for loop terminates.
        
-   If **range** is available, then the for loop executes for each item in the range.
    

[

Explore our **latest online courses** and learn new skills at your own pace. Enroll and become a certified expert to boost your career.

](https://www.tutorialspoint.com/latest/courses?utm_source=tutorialspoint&utm_medium=tutorials_3p&utm_campaign=internal)

## Flow Diagram of for Loop

![for loop in Go](https://www.tutorialspoint.com/go/images/go_for_loop.jpg)

## For Loop Example

The following example demonstrates the use of a for loop to print numbers from 1 to 10:

```go
package main
import "fmt"

func main() {
    
    for i := 1; i <= 10; i++ {
        fmt.Println(i)
    }
}
```

When you compile and execute the above program, it produces the following result −

```
1
2
3
4
5
6
7
8
9
10
```

## Multiple For Loops

The multiple for loops can also be used in a program section or in a function scope.

### Example

The following example demonstrates how you can use multiple for loops in a program:

```go
package main

import "fmt"

func main() {
   var b int = 15
   var a int
   numbers := [6]int{1, 2, 3, 5} 

   
   for a := 0; a < 10; a++ {
      fmt.Printf("value of a: %d\n", a)
   }
   for a < b {
      a++
      fmt.Printf("value of a: %d\n", a)
   }
   for i,x:= range numbers {
      fmt.Printf("value of x = %d at %d\n", x,i)
   }   
}
```

When the above code is compiled and executed, it produces the following result −

```
value of a: 0
value of a: 1
value of a: 2
value of a: 3
value of a: 4
value of a: 5
value of a: 6
value of a: 7
value of a: 8
value of a: 9
value of a: 1
value of a: 2
value of a: 3
value of a: 4
value of a: 5
value of a: 6
value of a: 7
value of a: 8
value of a: 9
value of a: 10
value of a: 11
value of a: 12
value of a: 13
value of a: 14
value of a: 15
value of x = 1 at 0
value of x = 2 at 1
value of x = 3 at 2
value of x = 5 at 3
value of x = 0 at 4
value of x = 0 at 5
```

## For Loop with String

For the string manipulation, you can use the for loop. The for loop with a string is useful to iterate over the characters of the string.

### Example

In this example, we are accessing the characters of the string using the for loop:

```go
package main
import "fmt"

func main() {
    str := "TutorialsPoint"

    
    fmt.Println("Characters of the string with their index:")
    for i := 0; i < len(str); i++ {
        fmt.Printf("[%2d]: %c\n", i, str[i])
    }
}
```

When the above code is compiled and executed, it produces the following result −

```
Characters of the string with their index:
[ 0]: T
[ 1]: u
[ 2]: t
[ 3]: o
[ 4]: r
[ 5]: i
[ 6]: a
[ 7]: l
[ 8]: s
[ 9]: P
[10]: o
[11]: i
[12]: n
[13]: t
```

## For Loop as an Infinite Loop

You can use the for loop as an infinite loop by omitting the condition; keep the content part in the loop's body that you want to execute infinitely.

### Example

The following example demonstrates the use of a for loop as an infinite loop:

```go
package main
import "fmt"

func main() {
    for {
        fmt.Println("Hello, World!")
    }
}
```

```
Hello, World!
Hello, World!
Hello, World!
Hello, World!
...
...
...
```

## Nested For Loop

Go language allows nesting of a for loop where you can use one or more for loops inside a loop.

**Read More:** [Go Nested For Loop](https://www.tutorialspoint.com/go/go_nested_loops.htm)

### Example

The following example prints a star pattern using the nested for loop:

```go
package main
import "fmt"

func main() {
    
    for i := 1; i <= 5; i++ {
        
        for j := 1; j <= i; j++ {
            fmt.Print("*")
        }
        fmt.Println() 
    }
}
```

When you compile and execute the above program, it produces the following result −

```
*
**
***
****
*****
```
