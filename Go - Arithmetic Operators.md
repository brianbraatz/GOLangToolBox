---
Description: Go - Arithmetic Operators
Notes: Following table shows all the arithmetic operators supported by Go language. Assume variable A holds 10 and variable B holds 20, then:
author: 
Url: https://www.tutorialspoint.com/go/go_arithmetic_operators.htm
Created: "2025-01-29  02:33:06"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go - Arithmetic Operators

source: https://www.tutorialspoint.com/go/go_arithmetic_operators.htm

> ## Excerpt
> Following table shows all the arithmetic operators supported by Go language. Assume variable A holds 10 and variable B holds 20, then:

---
___

___

Following table shows all the arithmetic operators supported by Go language. Assume variable **A** holds 10 and variable **B** holds 20, then:

| Operator | Description | Example |
| --- | --- | --- |
| + | Adds two operands | A + B gives 30 |
| \- | Subtracts second operand from the first | A - B gives -10 |
| \* | Multiplies both operands | A \* B gives 200 |
| / | Divides the numerator by the denominator. | B / A gives 2 |
| % | Modulus operator; gives the remainder after an integer division. | B % A gives 0 |
| ++ | Increment operator. It increases the integer value by one. | A++ gives 11 |
| \-- | Decrement operator. It decreases the integer value by one. | A-- gives 9 |

## Example

Try the following example to understand all the arithmetic operators available in Go programming language −

```go
package main

import "fmt"

func main() {

   var a int = 21
   var b int = 10
   var c int

   c = a + b
   fmt.Printf("Line 1 - Value of c is %d\n", c )
   
   c = a - b
   fmt.Printf("Line 2 - Value of c is %d\n", c )
   
   c = a * b
   fmt.Printf("Line 3 - Value of c is %d\n", c )
   
   c = a / b
   fmt.Printf("Line 4 - Value of c is %d\n", c )
   
   c = a % b
   fmt.Printf("Line 5 - Value of c is %d\n", c )
   
   a++
   fmt.Printf("Line 6 - Value of a is %d\n", a )
   
   a--
   fmt.Printf("Line 7 - Value of a is %d\n", a )
}
```

When you compile and execute the above program, it produces the following result −

```
Line 1 - Value of c is 31
Line 2 - Value of c is 11
Line 3 - Value of c is 210
Line 4 - Value of c is 2
Line 5 - Value of c is 1
Line 6 - Value of a is 22
Line 7 - Value of a is 21
```
