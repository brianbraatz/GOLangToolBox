---
Description: Go - Logical Operators
Notes: The following table lists all the logical operators supported by Go language. Assume variable A holds 1 and variable B holds 0, then ?
author: 
Url: https://www.tutorialspoint.com/go/go_logical_operators.htm
Created: "2025-01-29  02:33:26"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go - Logical Operators

source: https://www.tutorialspoint.com/go/go_logical_operators.htm

> ## Excerpt
> The following table lists all the logical operators supported by Go language. Assume variable A holds 1 and variable B holds 0, then ?

---
___

___

The following table lists all the logical operators supported by Go language. Assume variable **A** holds 1 and variable **B** holds 0, then −

| Operator | Description | Example |
| --- | --- | --- |
| && | Called Logical AND operator. If both the operands are non-zero, then condition becomes true. | (A && B) is false. |
| || | Called Logical OR Operator. If any of the two operands is non-zero, then condition becomes true. | (A || B) is true. |
| ! | Called Logical NOT Operator. Use to reverses the logical state of its operand. If a condition is true then Logical NOT operator will make false. | !(A && B) is true. |

The following table shows all the logical operators supported by Go language. Assume variable **A** holds true and variable **B** holds false, then −

| Operator | Description | Example |
| --- | --- | --- |
| && | Called Logical AND operator. If both the operands are false, then the condition becomes false. | (A && B) is false. |
| || | Called Logical OR Operator. If any of the two operands is true, then the condition becomes true. | (A || B) is true. |
| ! | Called Logical NOT Operator. Use to reverses the logical state of its operand. If a condition is true, then Logical NOT operator will make it false. | !(A && B) is true. |

## Example

Try the following example to understand all the logical operators available in Go programming language −

```go
package main

import "fmt"

func main() {
   var a bool = true
   var b bool = false
   if ( a && b ) {
      fmt.Printf("Line 1 - Condition is true\n" )
   }
   if ( a || b ) {
      fmt.Printf("Line 2 - Condition is true\n" )
   }
   
   
   a = false
   b = true
   if ( a && b ) {
      fmt.Printf("Line 3 - Condition is true\n" )
   } else {
      fmt.Printf("Line 3 - Condition is not true\n" )
   }
   if ( !(a && b) ) {
      fmt.Printf("Line 4 - Condition is true\n" )
   }
}
```

When you compile and execute the above program it produces the following result −

```
Line 2 - Condition is true
Line 3 - Condition is not true
Line 4 - Condition is true
```
