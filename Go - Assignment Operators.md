---
Description: Go - Assignment Operators
Notes: Go - Assignment Operators - The following table lists all the assignment operators supported by Go language ?
author: 
Url: https://www.tutorialspoint.com/go/go_assignment_operators.htm
Created: "2025-01-29  02:33:12"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go - Assignment Operators

source: https://www.tutorialspoint.com/go/go_assignment_operators.htm

> ## Excerpt
> Go - Assignment Operators - The following table lists all the assignment operators supported by Go language ?

---
___

___

The following table lists all the assignment operators supported by Go language −

| Operator | Description | Example |
| --- | --- | --- |
| \= | Simple assignment operator, Assigns values from right side operands to left side operand | C = A + B will assign value of A + B into C |
| += | Add AND assignment operator, It adds right operand to the left operand and assign the result to left operand | C += A is equivalent to C = C + A |
| \-= | Subtract AND assignment operator, It subtracts right operand from the left operand and assign the result to left operand | C -= A is equivalent to C = C - A |
| \*= | Multiply AND assignment operator, It multiplies right operand with the left operand and assign the result to left operand | C \*= A is equivalent to C = C \* A |
| /= | Divide AND assignment operator, It divides left operand with the right operand and assign the result to left operand | C /= A is equivalent to C = C / A |
| %= | Modulus AND assignment operator, It takes modulus using two operands and assign the result to left operand | C %= A is equivalent to C = C % A |
| <<= | Left shift AND assignment operator | C <<= 2 is same as C = C << 2 |
| \>>= | Right shift AND assignment operator | C >>= 2 is same as C = C >> 2 |
| &= | Bitwise AND assignment operator | C &= 2 is same as C = C & 2 |
| ^= | bitwise exclusive OR and assignment operator | C ^= 2 is same as C = C ^ 2 |
| |= | bitwise inclusive OR and assignment operator | C |= 2 is same as C = C | 2 |

## Example

Try the following example to understand all the assignment operators available in Go programming language −

```go
package main

import "fmt"

func main() {
   var a int = 21
   var c int

   c =  a
   fmt.Printf("Line 1 - =  Operator Example, Value of c = %d\n", c )

   c +=  a
   fmt.Printf("Line 2 - += Operator Example, Value of c = %d\n", c )

   c -=  a
   fmt.Printf("Line 3 - -= Operator Example, Value of c = %d\n", c )

   c *=  a
   fmt.Printf("Line 4 - *= Operator Example, Value of c = %d\n", c )

   c /=  a
   fmt.Printf("Line 5 - /= Operator Example, Value of c = %d\n", c )

   c  = 200; 

   c <<=  2
   fmt.Printf("Line 6 - <<= Operator Example, Value of c = %d\n", c )

   c >>=  2
   fmt.Printf("Line 7 - >>= Operator Example, Value of c = %d\n", c )

   c &=  2
   fmt.Printf("Line 8 - &= Operator Example, Value of c = %d\n", c )

   c ^=  2
   fmt.Printf("Line 9 - ^= Operator Example, Value of c = %d\n", c )

   c |=  2
   fmt.Printf("Line 10 - |= Operator Example, Value of c = %d\n", c )
}
```

When you compile and execute the above program it produces the following result −

```
Line 1 - =  Operator Example, Value of c = 21
Line 2 - += Operator Example, Value of c = 42
Line 3 - -= Operator Example, Value of c = 21
Line 4 - *= Operator Example, Value of c = 441
Line 5 - /= Operator Example, Value of c = 21
Line 6 - &lt;&lt;= Operator Example, Value of c = 800
Line 7 - &gt;&gt;= Operator Example, Value of c = 200
Line 8 - &amp;= Operator Example, Value of c = 0
Line 9 - ^= Operator Example, Value of c = 2
Line 10 - |= Operator Example, Value of c = 2
```
