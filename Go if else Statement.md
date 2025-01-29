---
Description: Go if else Statement
Notes: Go if else Statement - Go if-else statement is a conditional statement having two code blocks and executes them based on whether a condition is true or false. In an if-else statement, the if statement is followed by an else statement.
author: 
Url: https://www.tutorialspoint.com/go/go_if_else_statement.htm
Created: "2025-01-29  02:34:21"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go if else Statement

source: https://www.tutorialspoint.com/go/go_if_else_statement.htm

> ## Excerpt
> Go if else Statement - Go if-else statement is a conditional statement having two code blocks and executes them based on whether a condition is true or false. In an if-else statement, the if statement is followed by an else statement.

---
___

___

## The if else Statement

**Go if-else statement** is a [conditional statement](https://www.tutorialspoint.com/go/go_decision_making.htm) having two code blocks and executes them based on whether a condition is true or false. In an if-else statement, the **if** statement is followed by an **else** statement.

### Syntax

The syntax of an **if...else** statement in Go programming language is −

```go
if(boolean_expression) {
   
} else {
   
}
```

### Flow Diagram

![Go if...else statement](https://www.tutorialspoint.com/go/images/if_else_statement.jpg)

### Example

```go
package main

import "fmt"

func main() {
   
   var a int = 100;
 
   
   if( a < 20 ) {
      
      fmt.Printf("a is less than 20\n" );
   } else {
      
      fmt.Printf("a is not less than 20\n" );
   }
   fmt.Printf("value of a is : %d\n", a);
}
```

When the above code is compiled and executed, it produces the following result −

```
a is not less than 20;
value of a is : 100
```

## The else if else Statement

An **if** statement can be followed by an optional **else if...else** statement, which is very useful to test various conditions using single if...else if statement.

When using if , else if , else statements there are few points to keep in mind −

-   An if can have zero or one else's and it must come after any else if's.
    
-   An if can have zero to many else if's and they must come before the else.
    
-   Once an else if succeeds, none of the remaining else if's or else's will be tested.
    

### Syntax

The syntax of an **if...else if...else** statement in Go programming language is −

```go
if(boolean_expression 1) {
   
} else if( boolean_expression 2) {
   
} else if( boolean_expression 3) {
   
} else {
   
}
```

```go
package main

import "fmt"

func main() {
   
   var a int = 100
 
   
   if( a == 10 ) {
      
      fmt.Printf("Value of a is 10\n" )
   } else if( a == 20 ) {
      
      fmt.Printf("Value of a is 20\n" )
   } else if( a == 30 ) {
      
      fmt.Printf("Value of a is 30\n" )
   } else {
      
      fmt.Printf("None of the values is matching\n" )
   }
   fmt.Printf("Exact value of a is: %d\n", a )
}
```

When the above code is compiled and executed, it produces the following result −

```
None of the values is matching
Exact value of a is: 100
```
