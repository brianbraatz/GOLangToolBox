---
Description: Go - Operators Precedence
Notes: Operator precedence determines the grouping of terms in an expression. This affects how an expression is evaluated. Certain operators have higher precedence than others; for example, the multiplication operator has higher precedence than the addition operator.
author: 
Url: https://www.tutorialspoint.com/go/go_operators_precedence.htm
Created: "2025-01-29  02:33:56"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go - Operators Precedence

source: https://www.tutorialspoint.com/go/go_operators_precedence.htm

> ## Excerpt
> Operator precedence determines the grouping of terms in an expression. This affects how an expression is evaluated. Certain operators have higher precedence than others; for example, the multiplication operator has higher precedence than the addition operator.

---
___

___

Operator precedence determines the grouping of terms in an expression. This affects how an expression is evaluated. Certain operators have higher precedence than others; for example, the multiplication operator has higher precedence than the addition operator.

For example x = 7 + 3 \* 2; here, x is assigned 13, not 20 because operator \* has higher precedence than +, so it first gets multiplied with 3\*2 and then adds into 7.

Here, operators with the highest precedence appear at the top of the table, those with the lowest appear at the bottom. Within an expression, higher precedence operators will be evaluated first.

| Category | Operator | Associativity |
| --- | --- | --- |
| Postfix | () \[\] -> . ++ - - | Left to right |
| Unary | \+ - ! ~ ++ - - (type)\* & sizeof | Right to left |
| Multiplicative | \* / % | Left to right |
| Additive | \+ - | Left to right |
| Shift | << >> | Left to right |
| Relational | < <= > >= | Left to right |
| Equality | \== != | Left to right |
| Bitwise AND | & | Left to right |
| Bitwise XOR | ^ | Left to right |
| Bitwise OR | | | Left to right |
| Logical AND | && | Left to right |
| Logical OR | || | Left to right |
| Assignment | \= += -= \*= /= %=>>= <<= &= ^= |= | Right to left |
| Comma | , | Left to right |

## Example

Try the following example to understand the operator precedence available in Go programming language −

```go
package main

import "fmt"

func main() {
   var a int = 20
   var b int = 10
   var c int = 15
   var d int = 5
   var e int;

   e = (a + b) * c / d;      
   fmt.Printf("Value of (a + b) * c / d is : %d\n",  e );

   e = ((a + b) * c) / d;    
   fmt.Printf("Value of ((a + b) * c) / d is  : %d\n" ,  e );

   e = (a + b) * (c / d);   
   fmt.Printf("Value of (a + b) * (c / d) is  : %d\n",  e );

   e = a + (b * c) / d;     
   fmt.Printf("Value of a + (b * c) / d is  : %d\n" ,  e );  
}
```

When you compile and execute the above program it produces the following result −

```
Value of (a + b) * c / d is : 90
Value of ((a + b) * c) / d is  : 90
Value of (a + b) * (c / d) is  : 90
Value of a + (b * c) / d is  : 50
```
