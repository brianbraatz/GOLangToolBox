---
Description: Go - Miscellaneous Operators
Notes: Go - Miscellaneous Operators - There are a few other important operators supported by Go Language including sizeof and ?:.
author: 
Url: https://www.tutorialspoint.com/go/go_misc_operator.htm
Created: "2025-01-29  02:33:48"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go - Miscellaneous Operators

source: https://www.tutorialspoint.com/go/go_misc_operator.htm

> ## Excerpt
> Go - Miscellaneous Operators - There are a few other important operators supported by Go Language including sizeof and ?:.

---
___

___

There are a few other important operators supported by Go Language including **sizeof** and **?:.**

| Operator | Description | Example |
| --- | --- | --- |
| & | Returns the address of a variable. | &a; provides actual address of the variable. |
| \* | Pointer to a variable. | \*a; provides pointer to a variable. |

## Example

Try following example to understand all the miscellaneous operators available in Go programming language −

```go
package main

import "fmt"

func main() {
   var a int = 4
   var b int32
   var c float32
   var ptr *int

   
   fmt.Printf("Line 1 - Type of variable a = %T\n", a );
   fmt.Printf("Line 2 - Type of variable b = %T\n", b );
   fmt.Printf("Line 3 - Type of variable c= %T\n", c );

   
   ptr = &a
   fmt.Printf("value of a is  %d\n", a);
   fmt.Printf("*ptr is %d.\n", *ptr);
}
```

When you compile and execute the above program it produces the following result −

```
Line 1 - Type of variable a = int
Line 2 - Type of variable b = int32
Line 3 - Type of variable c= float32
value of a is  4
*ptr is 4.
```
