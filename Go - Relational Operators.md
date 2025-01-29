---
Description: Go - Relational Operators
Notes: The following table lists all the relational operators supported by Go language. Assume variable A holds 10 and variable B holds 20, then ?
author: 
Url: https://www.tutorialspoint.com/go/go_relational_operators.htm
Created: "2025-01-29  02:33:19"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go - Relational Operators

source: https://www.tutorialspoint.com/go/go_relational_operators.htm

> ## Excerpt
> The following table lists all the relational operators supported by Go language. Assume variable A holds 10 and variable B holds 20, then ?

---
___

___

The following table lists all the relational operators supported by Go language. Assume variable **A** holds 10 and variable **B** holds 20, then −

| Operator | Description | Example |
| --- | --- | --- |
| \== | It checks if the values of two operands are equal or not; if yes, the condition becomes true. | (A == B) is not true. |
| != | It checks if the values of two operands are equal or not; if the values are not equal, then the condition becomes true. | (A != B) is true. |
| \> | It checks if the value of left operand is greater than the value of right operand; if yes, the condition becomes true. | (A > B) is not true. |
| < | It checks if the value of left operand is less than the value of the right operand; if yes, the condition becomes true. | (A < B) is true. |
| \>= | It checks if the value of the left operand is greater than or equal to the value of the right operand; if yes, the condition becomes true. | (A >= B) is not true. |
| <= | It checks if the value of left operand is less than or equal to the value of right operand; if yes, the condition becomes true. | (A <= B) is true. |

## Example

Try the following example to understand all the relational operators available in Go programming language −

```go
package main

import "fmt"

func main() {
   var a int = 21
   var b int = 10

   if( a == b ) {
      fmt.Printf("Line 1 - a is equal to b\n" )
   } else {
      fmt.Printf("Line 1 - a is not equal to b\n" )
   }
   if ( a < b ) {
      fmt.Printf("Line 2 - a is less than b\n" )
   } else {
      fmt.Printf("Line 2 - a is not less than b\n" )
   } 
   if ( a > b ) {
      fmt.Printf("Line 3 - a is greater than b\n" )
   } else {
      fmt.Printf("Line 3 - a is not greater than b\n" )
   }
   
   
   a = 5
   b = 20
   if ( a <= b ) {
      fmt.Printf("Line 4 - a is either less than or equal to  b\n" )
   }
   if ( b >= a ) {
      fmt.Printf("Line 5 - b is either greater than  or equal to b\n" )
   }
}
```

When you compile and execute the above program it produces the following result −

```
Line 1 - a is not equal to b
Line 2 - a is not less than b
Line 3 - a is greater than b
Line 4 - a is either less than or equal to  b
Line 5 - b is either greater than  or equal to b
```
