---
Description: Go - The Switch Statement
Notes: Go - The Switch Statement - A switch statement allows a variable to be tested for equality against a list of values. Each value is called a case, and the variable being switched on is checked for each switch case.
author: 
Url: https://www.tutorialspoint.com/go/go_switch_statement.htm
Created: "2025-01-29  02:34:38"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go - The Switch Statement

source: https://www.tutorialspoint.com/go/go_switch_statement.htm

> ## Excerpt
> Go - The Switch Statement - A switch statement allows a variable to be tested for equality against a list of values. Each value is called a case, and the variable being switched on is checked for each switch case.

---
___

___

## Switch Statement

A **switch** statement allows a variable to be tested for equality against a list of values. Each value is called a case, and the variable being switched on is checked for each **switch case**.

In Go programming, switch statements are of two types −

-   **Expression Switch** − In expression switch, a case contains expressions, which is compared against the value of the switch expression.
    
-   **Type Switch** − In type switch, a case contain type which is compared against the type of a specially annotated switch expression.
    

### Flow Diagram

![switch statement in Go](https://www.tutorialspoint.com/go/images/switch_statement.jpg)

Now, let's understand the types of switch statements in detail.

## Expression Switch Statement

An **expression switch statement** in Go language checks a given value with the multiple case values and executes the associated code block for the first matched case.

### Syntax

The syntax for **expression switch** statement in Go programming language is as follows −

```go
switch(boolean-expression or integral type){
   case boolean-expression or integral type :
      statement(s);      
   case boolean-expression or integral type :
      statement(s); 
   
   
   default : 
      statement(s);
}
```

The following rules apply to a **expression switch** statement −

-   The **expression** used in a **switch** statement must have an integral or boolean expression, or be of a class type in which the class has a single conversion function to an integral or boolean value. If the expression is not passed then the default value is true.
-   You can have any number of case statements within a switch. Each case is followed by the value to be compared to and a colon.
-   The **constant-expression** for a case must be the same data type as the variable in the switch, and it must be a constant or a literal.
-   When the variable being switched on is equal to a case, the statements following that case will execute. No **break** is needed in the case statement.
-   A **switch** statement can have an optional **default** case, which must appear at the end of the switch. The default case can be used for performing a task when none of the cases is true. No **break** is needed in the default case.

### Example

Here is an example of expression switch statement:

```go
package main

import "fmt"

func main() {
   
   var grade string = "B"
   var marks int = 90

   switch marks {
      case 90: grade = "A"
      case 80: grade = "B"
      case 50,60,70 : grade = "C"
      default: grade = "D"  
   }
   switch {
      case grade == "A" :
         fmt.Printf("Excellent!\n" )     
      case grade == "B", grade == "C" :
         fmt.Printf("Well done\n" )      
      case grade == "D" :
         fmt.Printf("You passed\n" )      
      case grade == "F":
         fmt.Printf("Better try again\n" )
      default:
         fmt.Printf("Invalid grade\n" );
   }
   fmt.Printf("Your grade is  %s\n", grade );      
}
```

When the above code is compiled and executed, it produces the following result −

```
Excellent!
Your grade is  A
```

[

Explore our **latest online courses** and learn new skills at your own pace. Enroll and become a certified expert to boost your career.

](https://www.tutorialspoint.com/latest/courses?utm_source=tutorialspoint&utm_medium=tutorials_3p&utm_campaign=internal)

## Type Switch Statement

A **type switch statement** in Go language checks the type of an interface value and executes the associated code block for the first matched case.

### Syntax

The syntax for a **type switch** statement in Go programming is as follows −

```go
switch x.(type){
   case type:
      statement(s);      
   case type:
      statement(s); 
   
   default: 
      statement(s);
}
```

The following rules apply to a **type switch** statement −

-   The **expression** used in a **switch** statement must have an variable of interface{} type.
-   You can have any number of case statements within a switch. Each case is followed by the value to be compared to and a colon.
-   The type for a case must be the same data type as the variable in the switch, and it must be a valid data type.
-   When the variable being switched on is equal to a case, the statements following that case will execute. No break is needed in the case statement.
-   A switch statement can have an optional default case, which must appear at the end of the switch. The default case can be used for performing a task when none of the cases is true. No break is needed in the default case.

### Example

Here is an example of expression switch statement:

```go
package main

import "fmt"

func main() {
   var x interface{}
     
   switch i := x.(type) {
      case nil:  
         fmt.Printf("type of x :%T",i)                
      case int:  
         fmt.Printf("x is int")                       
      case float64:
         fmt.Printf("x is float64")           
      case func(int) float64:
         fmt.Printf("x is func(int)")                      
      case bool, string:
         fmt.Printf("x is bool or string")       
      default:
         fmt.Printf("don't know the type")     
   }   
}
```

When the above code is compiled and executed, it produces the following result −

```
type of x :&lt;nil&gt;
```
