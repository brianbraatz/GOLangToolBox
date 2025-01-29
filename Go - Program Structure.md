---
Description: Go - Program Structure
Notes: Before we study the basic building blocks of Go programming language, let us first discuss the bare minimum structure of Go programs so that we can take it as a reference in subsequent chapters.
author: 
Url: https://www.tutorialspoint.com/go/go_program_structure.htm
Created: "2025-01-29  02:32:10"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go - Program Structure

source: https://www.tutorialspoint.com/go/go_program_structure.htm

> ## Excerpt
> Before we study the basic building blocks of Go programming language, let us first discuss the bare minimum structure of Go programs so that we can take it as a reference in subsequent chapters.

---
___

___

Before we study the basic building blocks of Go programming language, let us first discuss the bare minimum structure of Go programs so that we can take it as a reference in subsequent chapters.

## Structure of a Go Program

A Go program basically consists of the following parts −

-   Package Declaration
-   Import Packages
-   Functions
-   Variables
-   Statements and Expressions
-   Comments

## Example: Hello World Program

Let us look at a simple code that would print the words "Hello World" −

### Code

```go
package main

import "fmt"

func main() {
   
   fmt.Println("Hello, World!")
}
```

[

Explore our **latest online courses** and learn new skills at your own pace. Enroll and become a certified expert to boost your career.

](https://www.tutorialspoint.com/latest/courses?utm_source=tutorialspoint&utm_medium=tutorials_3p&utm_campaign=internal)

## Explanation of Code Parts

Let us take a look at the various parts of the above program −

### 1\. Package Declaration

The first line of the program package main defines the package name in which this program should lie. It is a mandatory statement, as Go programs run in packages. The main package is the starting point to run the program. Each package has a path and name associated with it.

### 2\. Import Packages

The next line import "fmt" is a preprocessor command which tells the Go compiler to include the files lying in the package fmt.

### 3\. Main Function

The next line func main() is the main function where the program execution begins.

### 4\. Comments

The next line /\*...\*/ is ignored by the compiler and it is there to add comments in the program. Comments are also represented using // similar to Java or C++ comments.

### 5\. Print Statement

The next line fmt.Println(...) is another function available in Go which causes the message "Hello, World!" to be displayed on the screen. Here fmt package has exported Println method which is used to display the message on the screen.

Notice the capital P of Println method. In Go language, a name is exported if it starts with capital letter. Exported means the function or variable/constant is accessible to the importer of the respective package.

## Executing a Go Program

Let us discuss how to save the source code in a file, compile it, and finally execute the program. Please follow the steps given below −

-   Open a text editor and add the above-mentioned code.
-   Save the file as _hello.go_
-   Open the command prompt.
-   Go to the directory where you saved the file.
-   Type go run _hello.go_ and press enter to run your code.
-   If there are no errors in your code, then you will see _"Hello World!"_ printed on the screen.

```
$ go run hello.go
Hello, World!
```

Make sure the Go compiler is in your path and that you are running it in the directory containing the source file hello.go.
