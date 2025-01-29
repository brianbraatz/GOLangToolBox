---
Description: Golang Cheatsheet
Notes: Golang Cheatsheet - This is the Golang cheatsheet, which provides everything from basic to advanced concepts to help you grow as a programmer. By learning this cheatsheet, students and developers can prepare for interviews. Go through the cheatsheet to learn the concepts of Golang programming.
author: 
Url: https://www.tutorialspoint.com/go/go_cheatsheet.htm
Created: "2025-01-29  02:38:38"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Golang Cheatsheet

source: https://www.tutorialspoint.com/go/go_cheatsheet.htm

> ## Excerpt
> Golang Cheatsheet - This is the Golang cheatsheet, which provides everything from basic to advanced concepts to help you grow as a programmer. By learning this cheatsheet, students and developers can prepare for interviews. Go through the cheatsheet to learn the concepts of Golang programming.

---
___

___

This is the **Golang cheatsheet**, which provides everything from basic to advanced concepts to help you grow as a programmer. By learning this cheatsheet, students and developers can prepare for interviews. Go through the cheatsheet to learn the concepts of [**Golang programming**](https://www.tutorialspoint.com/go/index.htm).

### Table of Content

1.  **Basics Overview of Golang**

-   [Syntax](https://www.tutorialspoint.com/go/go_cheatsheet.htm#syntax)
-   [Data Types](https://www.tutorialspoint.com/go/go_cheatsheet.htm#data_types)
-   [Variables](https://www.tutorialspoint.com/go/go_cheatsheet.htm#variables)
-   [Constants](https://www.tutorialspoint.com/go/go_cheatsheet.htm#constants)
-   [Comments](https://www.tutorialspoint.com/go/go_cheatsheet.htm#comments)

3.  **Control Structures in Golang**

-   [If Statements](https://www.tutorialspoint.com/go/go_cheatsheet.htm#if_statements)
-   [If-Else Statement](https://www.tutorialspoint.com/go/go_cheatsheet.htm#if_else_statements)
-   [Nested-If Statement](https://www.tutorialspoint.com/go/go_cheatsheet.htm#nested_if_statements)
-   [Switch Statements](https://www.tutorialspoint.com/go/go_cheatsheet.htm#switch_statements)
-   [For Loops](https://www.tutorialspoint.com/go/go_cheatsheet.htm#for_loops)
-   [Range](https://www.tutorialspoint.com/go/go_cheatsheet.htm#range)
-   [Slice](https://www.tutorialspoint.com/go/go_cheatsheet.htm#slice)
-   [Maps](https://www.tutorialspoint.com/go/go_cheatsheet.htm#maps)

5.  **Pointer in Golang**

-   [Pointer](https://www.tutorialspoint.com/go/go_cheatsheet.htm#pointer)

7.  **Golang Operators**

-   [Arithmetic Operators](https://www.tutorialspoint.com/go/go_cheatsheet.htm#arithmetic_operators)
-   [Relational Operators](https://www.tutorialspoint.com/go/go_cheatsheet.htm#relational_operators)
-   [Logical Operators](https://www.tutorialspoint.com/go/go_cheatsheet.htm#logical_operators)
-   [Bitwise Operators](https://www.tutorialspoint.com/go/go_cheatsheet.htm#bitwise_operators)
-   [Assignment Operators](https://www.tutorialspoint.com/go/go_cheatsheet.htm#assignment_operators)
-   [Miscellaneous Operators](https://www.tutorialspoint.com/go/go_cheatsheet.htm#miscellaneous_operators)

9.  **Control Flow Statement in Golang**

-   [break statement](https://www.tutorialspoint.com/go/go_cheatsheet.htm#break_statement)
-   [continue statement](https://www.tutorialspoint.com/go/go_cheatsheet.htm#continue_statement)
-   [goto statement](https://www.tutorialspoint.com/go/go_cheatsheet.htm#goto_statement)

11.  **Golang Functions**

-   [Function Declaration](https://www.tutorialspoint.com/go/go_cheatsheet.htm#function_declaration)
-   [Return Values](https://www.tutorialspoint.com/go/go_cheatsheet.htm#return_values)
-   [Variadic Functions](https://www.tutorialspoint.com/go/go_cheatsheet.htm#variadic_functions)
-   [Anonymous Functions](https://www.tutorialspoint.com/go/go_cheatsheet.htm#anonymous_functions)

13.  **Structure and Interfaces in Golang**

-   [type\_and\_struct](https://www.tutorialspoint.com/go/go_cheatsheet.htm#type_and_struct)
-   [Interfaces](https://www.tutorialspoint.com/go/go_cheatsheet.htm#interfaces)
-   [Type Assertion](https://www.tutorialspoint.com/go/go_cheatsheet.htm#type_assertion)

15.  **Golang Concurrency**

-   [Goroutines](https://www.tutorialspoint.com/go/go_cheatsheet.htm#goroutines)
-   [Channels](https://www.tutorialspoint.com/go/go_cheatsheet.htm#channels)
-   [Select Statement](https://www.tutorialspoint.com/go/go_cheatsheet.htm#select_statement)

17.  **Error Handling in Golang**

-   [Error Types](https://www.tutorialspoint.com/go/go_cheatsheet.htm#error_types)
-   [Panic and Recover](https://www.tutorialspoint.com/go/go_cheatsheet.htm#panic_recover)

19.  **Golang Packages**

-   [Importing Packages](https://www.tutorialspoint.com/go/go_cheatsheet.htm#importing_packages)
-   [Creating Packages](https://www.tutorialspoint.com/go/go_cheatsheet.htm#creating_packages)

21.  **File Handling in Golang**

-   [Reading Files](https://www.tutorialspoint.com/go/go_cheatsheet.htm#reading_files)
-   [Writing Files](https://www.tutorialspoint.com/go/go_cheatsheet.htm#writing_files)

23.  **Testing in Golang**

-   [Writing Tests](https://www.tutorialspoint.com/go/go_cheatsheet.htm#writing_tests)
-   [Running Tests](https://www.tutorialspoint.com/go/go_cheatsheet.htm#running_tests)

25.  **Common Libraries in Golang**

-   [Standard Library Overview](https://www.tutorialspoint.com/go/go_cheatsheet.htm#standard_library)

## 1\. Basics Overview of Golang

In the basics of Golang, we will learn about the fundamental topics:

### i. Syntax

**[Golang syntax](https://www.tutorialspoint.com/go/go_basic_syntax.htm)** is very simple to use. Here is an example to display "Welcome to Tutorialspoint" in Golang.

```go
package main
import "fmt"
func main() {
   fmt.Println("Welcome to Tutorialspoint")
}
```

### ii. Data Types

The **[data types](https://www.tutorialspoint.com/go/go_data_types.htm)** are used to declare the variables or functions of different types. Following is the table that helps you to get the understanding of various data types in golang −

| Integer | Floating-point | Complex number | Strings | Boolean |
| --- | --- | --- | --- | --- |
| int, int8, int16, int32, int64 | float32, float64 | complex64, complex128 | string | bool |

```go
package main
import "fmt"

func main() {
   var m int = 100
   var n float64 = 99.5
   var x bool = true
   var y string = "Tutorialspoint"
   fmt.Println(m)
   fmt.Println(n)
   fmt.Println(x)
   fmt.Println(y)
}
```

### iii. Variables

**[Variables](https://www.tutorialspoint.com/go/go_variables.htm)** are used to store the data values. The basic syntax of a variable in golang −

```
var variable_name type = value
```

**Note**: The symbol "**:=**" is used to declare the short variable declaration.

```go
package main
import "fmt"

func main() {
   var id int = 30
   name := "John"
   fmt.Println("ID:", name)
   fmt.Println("Address:", id)
}
```

### iv. Constants

**[Constants](https://www.tutorialspoint.com/go/go_constants.htm)** of Golang, use the keyword **consts**. This cannot be change after being set.

```go
package main
import "fmt"

func main() {
   const PI float64 = 3.14159
   fmt.Println("Value of PI:", PI)
}
```

**Comments** in Golang are written in two ways − single-line comment (**//**) and multi-line comments (**/\* ... \*/**).

```go
package main
import "fmt"

func main() {
   
}
```

The control structure is a block of code that determines the flow of execution in a program based on conditions and loops.

### i. If Statements

The **[if statement](https://www.tutorialspoint.com/go/go_if_statement.htm)** specifies the block of code if a condition is true.

```go
package main
import "fmt"

func main() {

var n int = 800
if n < 5000 {
   fmt.Printf("n is less than 5000\n")
}
fmt.Printf("Value of n is : %d\n", n)
}
```

### ii. If-Else Statement

The **[if-else statement](https://www.tutorialspoint.com/go/go_if_else_statement.htm)** specifies the code block if the condition is **false**.

```go
package main
import "fmt"

func main() {
   num := 0

   
    if num > 0 {
       fmt.Println("The given number is positive.")
    } else if num < 0 {
       fmt.Println("The given number is negative.")
    } else {
       fmt.Println("The given number is zero.")
    }
}
```

### iii. Nested-If Statement

The **[nested-if statement](https://www.tutorialspoint.com/go/go_nested_if_statements.htm)** is defined using an if statement inside another if statement.

```go
package main
import "fmt"

func main() {
   number := 8

   
   if number > 0 {
       fmt.Println("The number is positive.")
       if number%2 == 0 {
           fmt.Println("The number is even.")
       } else {
           fmt.Println("The number is odd.")
       }
   } else {
       fmt.Println("The number is zero or negative.")
   }
}
```

### iv. Switch Statements

The **[switch statement](https://www.tutorialspoint.com/go/go_switch_statement.htm)** is used to execute one block of code when the case matches.

```go
package main
import "fmt"

func main() {
    day := 4

   
   switch day {
   case 1:
      fmt.Println("Monday")
   case 2:
      fmt.Println("Tuesday")
   case 3:
      fmt.Println("Wednesday")
   case 4:
      fmt.Println("Thursday")
   case 5:
      fmt.Println("Friday")
   case 6:
      fmt.Println("Saturday")
   case 7:
      fmt.Println("Sunday")
   default:
      fmt.Println("Invalid day")
   }
}
```

### v. For Loops

A **[for loop](https://www.tutorialspoint.com/go/go_for_loop.htm)** is defined by the repetition of a control structure.

```go
package main
import "fmt"

func main() {
   
   for i := 1; i <= 5; i++ {
       fmt.Println(i)
   }
}
```

### vi. Range

In Golang, **[range](https://www.tutorialspoint.com/go/go_range.htm)** is a keyword that is used for the iteration of various data structures such as arrays, slices, strings, maps, and channels.

```go
package main
import "fmt"

func main() {
   num := []int{10, 20, 30, 40, 50}

   
   for idx, val := range num {
       fmt.Println("Index:", idx, "Value:", val)
   }
}
```

### vii. Slice

A **[slice](https://www.tutorialspoint.com/go/go_slice.htm)** of Go defines the variable-length sequence that stores the elements of the same type.

```go
package main
import "fmt"
 
func main() {
   arr := []int{1, 2, 3, 4, 5, 6, 7, 8}
   slice := arr[3:5]
 
   fmt.Println("Array: ", arr)
   fmt.Println("Slice: ", slice)
}
```

### viii. Maps

**[Maps](https://www.tutorialspoint.com/go/go_maps.htm)** are used to store data in key:value pairs.

```go
package main
import ("fmt")

func main() {
   var X = map[string]string{"Stree 2 ": " 15 AUG 2024", "Pushpa 2 ": " 5 DEC 2024", "Mufasa ": " 20 DEC 2024"}
   Y := map[string]int{"A": 1, "B": 2, "C": 3, "D": 4}

   fmt.Printf("I.\t%v\n", X)
   fmt.Printf("II.\t%v\n", Y)
}
```

[

Explore our **latest online courses** and learn new skills at your own pace. Enroll and become a certified expert to boost your career.

](https://www.tutorialspoint.com/latest/courses?utm_source=tutorialspoint&utm_medium=tutorials_3p&utm_campaign=internal)

## 3\. Pointer in Golang

In Golang, a **[pointer](https://www.tutorialspoint.com/go/go_pointers.htm)** refers to a specified memory location of the value.

### i. Pointer

This is the basic program of pointer in Golang.

```go
package main
import "fmt"

func main() {
   var n int = 58  
   
   var ptr *int  
   
   ptr = &n              

   fmt.Println("Value of num:", n)   
   fmt.Println("Address of num:", &n) 
   fmt.Println("Pointer (address) stored in ptr:", ptr)
   fmt.Println("Value at ptr (dereferencing):", *ptr) 
}
```

## Golang Operators

The **operators** of Golang allows user to perform different types of operation which is listed below −

-   **[Arithmetic Operators](https://www.tutorialspoint.com/go/go_arithmetic_operators.htm)**: These operators are used to perform basic mathematical operations such as addition (**+**), subtraction (**\-**), multiplication (**\***), division (**/**), and modulus (**%**).
-   **[Relational Operators](https://www.tutorialspoint.com/go/go_relational_operators.htm)**: Relational operators compare two values and return a boolean result (**true** or **false**). Common operators include **<**, **<=**, **\>**, **\>=**, **\==**, and **!=**.
-   **[Logical Operators](https://www.tutorialspoint.com/go/go_logical_operators.htm)**: These operators are used to perform logical operations. They include AND (**&&**), OR (**||**), and NOT (**!**).
-   **[Bitwise Operators](https://www.tutorialspoint.com/go/go_bitwise_operators.htm)**: Bitwise operators perform operations on binary representations of numbers. They include AND (**&**), OR (**|**), XOR (**^**), left shift (**<<**), and right shift (**\>>**).
-   **[Assignment Operators](https://www.tutorialspoint.com/go/go_assignment_operators.htm)**: These operators assign values to variables. In Golang, the common assignment operator is **\=**. Additionally, shorthand operators like **+=**, **\-=**, and **\*=** are also available.
-   **[Miscellaneous Operators](https://www.tutorialspoint.com/go/go_misc_operator.htm)**: These include operators like the increment (**++**) and decrement (**\--**) operators.

## 5\. Control Flow Statement in Golang

The control flow statement determines the order in which instructions are executed in a program.

### i. break statement

The **[break statement](https://www.tutorialspoint.com/go/go_break_statement.htm)** stops executing the loops.

```go
package main
import "fmt"

func main() {
   fmt.Println("Illustration of break statement:")
   for i := 1; i <= 4; i++ {
       if i == 2 {
           break  
       }
       fmt.Println(i)
   }
}
```

### ii. continue statement

The **[continue statement](https://www.tutorialspoint.com/go/go_continue_statement.htm)** skips the current iteration in the loop.

```go
package main
import "fmt"

func main() {
   fmt.Println("Illustration of continue statement:")
   for i := 1; i <= 6; i++ {
       if i == 3 {
           continue  
       }
       fmt.Println(i)
   }
}
```

### iii. goto statement

The **[goto statement](https://www.tutorialspoint.com/go/go_goto_statement.htm)** jumps to a specified label in code.

```go
package main
import "fmt"

func main() {
   
   var a int = 10

   
   LOOP: for a < 20 {
      if a == 15 {
         
         a = a + 1
         goto LOOP
      }
      fmt.Printf("value of a: %d\n", a)
      a++     
   }  
}
```

## 6\. Golang Functions

The **[Golang function](https://www.tutorialspoint.com/go/go_functions.htm)** is reusable code that can be used for specific tasks.

### i. Function Declaration

To declare a function in golang, use **func** keyword −

```go
func FunctionName() {
  
}
```

A **function** that can return any number of values is known as return values.

```go
package main
import "fmt"


func sum(a, b int) int {
   return a + b
}

func main() {
   
   result := sum(3, 4)
   fmt.Println("Sum:", result)
}
```

### iii. Variadic Functions

A **variadic function** in Golang allows the user to pass n numbers as arguments. The ellipsis is denoted by three dots (...).

```go
package main
import "fmt"


func sum(nums ...int) int {
   total := 0
   for _, n := range nums {
       total += n
   }
   return total
}

func main() {
   fmt.Println("Sum of 1, 2, 3, 7, 1:", sum(1, 2, 3, 7, 1))
   fmt.Println("Sum of 6, 5:", sum(6, 5))
}
```

### iv. Anonymous Functions

This type of function doesn't have a name.

```go
package main
import "fmt"

func main() {
    
    func() {
        fmt.Println("Welcome to Tutorialspoint!")
    }()
}
```

## 7\. Structure and Interfaces in Golang

**[Structure](https://www.tutorialspoint.com/go/go_structures.htm)** defines the collection of members of different data types. This stores all the data into a single variable. This type of function doesn't have a name.

### i. type and struct

To declare a structure, use the keyword struct and type −

```go
type struct_name struct {
  member_1 string
  member_2 int
  member_3 string
  member_4  int
}
```

Here is the basics of **interfaces** in golang language −

```go
type InterfaceName interface {
    Method_1() returnType
    Method_2() returnType
}
```

Type assertion is used to check whether an interface holds a specific type and extract the value of that type.

```go
package main
import "fmt"

func main() {
   var i interface{} = "Tutorialspoint"
   
   t := i.(string)
   fmt.Println(t)
   
   t, p := i.(string)
   fmt.Println(t, p)
   
   f, p := i.(float64)
   fmt.Println(f, p)
   
   f = i.(float64) 
   fmt.Println(f)
}
```

## 8\. Golang Concurrency

Concurrency in Golang refers to the ability of handling multiple tasks. This can be achieved using goroutines, channels, and the select statement.

### i. Goroutines

**Goroutines** in Golang are independent functions that run concurrently. It means handling multiple tasks within a single program.

```go
package main
import "fmt"

func display(str string) {
   for i := 0; i < 4; i++ {
       fmt.Println(str)
   }
}

func main() {
   
   go display("Hello, Goroutine!")  
   display("Hello, Main!")
}
```

### ii. Channels

A **channel** is a medium that allows one goroutine to communicate with another goroutine.

```go
package main 
import "fmt"
  
func main() { 
  
   
   var channel_1 chan int
   fmt.Println("Value of the channel: ", channel_1) 
   fmt.Printf("Type of the channel_1: %T ", channel_1) 
   
   
   channel_2 := make(chan int) 
   fmt.Println("\nValue of the channel1: ", channel_2) 
   fmt.Printf("Type of the channel_2: %T ", channel_2) 
} 
```

### iii. Select Statement

In Golang, the **[select statement](https://www.tutorialspoint.com/go/go_select_statement.htm)** is used to handle multiple communications, like sending and receiving values.

```go
select {
    case value := <- channel1:
        
    case channel2 <- value:
        
    default:
        
}
```

**[Error handling](https://www.tutorialspoint.com/go/go_error_handling.htm)** defines the process of detecting the error during the program execution.

### i. Error Types

In Golang, errors are represented by the **error**. The following is a list of errors based on different scenarios −

-   **Built-in error type**: This is represented by errors.new function from the error package to build a simple error value.
-   **Formatted error**: This is represented by fmt.Errorf function that allows users to create errors with formatted messages.
-   **custom error**: This is implemented using the error() method.

```go

errors.New("division by zero is not allowed")


fmt.Errorf("...write something...", filename)


type error interface {
   error() string
}
```

In Golang, a **panic** is defined as a runtime error that stops the program execution unless it is recovered using recover. We can say this is used for programming bugs.

**a.** This is the basic example of panic.

```go
package main
import "fmt"

func main() {
   fmt.Println("The program starts...")
   
   panic("Something went wrong!") 
   fmt.Println("This will not be displayed")
}
```

**b.** This is the example of the recover() function that is used within the inside defer statement that catches and handles panics.

```go
package main
import "fmt"

func safeDivide(x, y int) {
   defer func() {
   if z := recover(); z != nil {
   fmt.Println("Recovered from panic:", z)
   }
   }()
   if y == 0 {
   panic("division by zero")
   }
   fmt.Println("Result:", x/y)
}
func main() {
   fmt.Println("Start program")
   safeDivide(100, 0)
   fmt.Println("End program")
}
```

## 10\. Golang Packages

In Golang, **packages** are collections of relatable source files that organise, modularise, and be reusable.

### i. Importing Packages

Golang is organised by packages, which allows users to modularise and reuse the code.

```go
package main
import (
   
   "fmt" 
   
   "math" 
)
func main() {
   fmt.Println("Square root of 100 is:", math.Sqrt(100))
}
```

### ii. Creating Packages

To create custom packages in Golang, follow the below steps −

-   **Step 1**: Create a folder for the package. For example − gopackage
-   **Step 2**: Write the code for the package. For example − mention the path "path/to/package".

```go
package main
import (
   "fmt"
   
   "path/to/mypackage" 
)
func main() {
   sum := mypackage.Add(2, 3)
   product := mypackage.Multiply(10, 5)

   fmt.Println("Sum of two numbers:", sum)
   fmt.Println("Product of two numbers:", product) 
}
```

**File handling** in Golang allows users to interact with data that is stored on the disk.

### i. Reading Files

To read the file, use the os and io/ioutil packages.

```go
package main
import (
   "fmt"
   "io/ioutil"
   "log"
)

func main() {
   
   data, err := ioutil.ReadFile("file.txt")
   if err != nil {
   log.Fatal(err)
   }
   
   fmt.Println(string(data))
}
```

While writing into a file, use the os.WriteFile(). Below is the basic example −

```go
package main
import (
   "log"
   "os"
)

func main() {
   
   data := []byte("Hello!\nWelcome to Tutorialspoint.")
   
   
   er := os.WriteFile("example_file.txt", data, 8649)
   if er != nil {
   log.Fatalf("Failed to write to file: %v", er)
   }
   log.Println("The written files is printed successfully!")
}
```

Golang **testing** package tests whether the program is being run or not.

### i. Writing Tests

The testing package of Golang is used for writing tests. Thus, this verifies the correctness of the code.

```go
package main

import "testing"


func add(a, b int) int {
    return a + b
}


func TestAdd(t *testing.T) {
    result := add(2, 3)
    if result != 5 {
        t.Errorf("Add(2, 3) = %d; want 5", result)
    }
}
```

### ii. Running Tests

To run the tests, use the following command −

```go
go test
```

**Golang libraries** are pre-written code modules that process everyday tasks.

### i. Standard Library Overview

Some of the common libraries that are mostly used in Golang programming −

| Golang Libraries | Description |
| --- | --- |
| import "fmt" | This provides formatting strings, reading input, and printing output. |
| import "os" | This provides a function to interact with the operating system. |
| import "json" | This provides functions for encoding and decoding JSON data. |
| import "error" | This provides a function to create and handle errors. |
| import "regexp" | This provides a function for compiling regular expressions. |
| import "io" | This provides basic input-output operations like reading and writing. |
| import "math" | This provides mathematical functions like trigonometric, exponential, and logarithmic operations. |
| import "strings" | This provides a string for manipulation and processing. |
