---
Description: Go - Nested for Loops
Notes: Go programming language allows to use one loop inside another loop. The following section shows a few examples to illustrate the concept ?
author: 
Url: https://www.tutorialspoint.com/go/go_nested_loops.htm
Created: "2025-01-29  02:35:03"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go - Nested for Loops

source: https://www.tutorialspoint.com/go/go_nested_loops.htm

> ## Excerpt
> Go programming language allows to use one loop inside another loop. The following section shows a few examples to illustrate the concept ?

---
___

___

Go programming language allows to use one loop inside another loop. The following section shows a few examples to illustrate the concept −

## Syntax

The syntax for a **nested for loop** statement in Go is as follows −

```go
for [condition |  ( init; condition; increment ) | Range] {
   for [condition |  ( init; condition; increment ) | Range] {
      statement(s);
   }
   statement(s);
}
```

The following program uses a nested for loop to find the prime numbers from 2 to 100 −

```go
package main

import "fmt"

func main() {
   
   var i, j int

   for i = 2; i < 100; i++ {
      for j = 2; j <= (i/j); j++ {
         if(i%j==0) {
            break; 
         }
      }
      if(j > (i/j)) {
         fmt.Printf("%d is prime\n", i);
      }
   }  
}
```

When the above code is compiled and executed, it produces the following result −

```
2 is prime
3 is prime
5 is prime
7 is prime
11 is prime
13 is prime
17 is prime
19 is prime
23 is prime
29 is prime
31 is prime
37 is prime
41 is prime
43 is prime
47 is prime
53 is prime
59 is prime
61 is prime
67 is prime
71 is prime
73 is prime
79 is prime
83 is prime
89 is prime
97 is prime
```
