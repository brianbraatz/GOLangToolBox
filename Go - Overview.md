---
Description: Go - Overview
Notes: Go - Overview - Go is a general-purpose language designed with systems programming in mind. It was initially developed at Google in the year 2007 by Robert Griesemer, Rob Pike, and Ken Thompson. It is strongly and statically typed, provides inbuilt support for garbage collection, and supports concurrent programming
author: 
Url: https://www.tutorialspoint.com/go/go_overview.htm
Created: "2025-01-29  02:31:57"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go - Overview

source: https://www.tutorialspoint.com/go/go_overview.htm

> ## Excerpt
> Go - Overview - Go is a general-purpose language designed with systems programming in mind. It was initially developed at Google in the year 2007 by Robert Griesemer, Rob Pike, and Ken Thompson. It is strongly and statically typed, provides inbuilt support for garbage collection, and supports concurrent programming

---
___

___

## What is Go Language?

Go is a general-purpose language designed with systems programming in mind. It was initially developed at Google in the year 2007 by Robert Griesemer, Rob Pike, and Ken Thompson. It is strongly and statically typed, provides inbuilt support for garbage collection, and supports concurrent programming.

Programs are constructed using packages, for efficient management of dependencies. Go programming implementations use a traditional compile and link model to generate executable binaries. The Go programming language was announced in November 2009 and is used in some of the Google's production systems.

## Features of Go Programming

The most important features of Go programming are listed below −

-   Support for environment adopting patterns similar to dynamic languages. For example, type inference (x := 0 is valid declaration of a variable x of type int)
    
-   Compilation time is fast.
    
-   Inbuilt concurrency support: lightweight processes (via go routines), channels, select statement.
    
-   Go programs are simple, concise, and safe.
    
-   Support for Interfaces and Type embedding.
    
-   Production of statically linked native binaries without external dependencies.
    

[

Explore our **latest online courses** and learn new skills at your own pace. Enroll and become a certified expert to boost your career.

](https://www.tutorialspoint.com/latest/courses?utm_source=tutorialspoint&utm_medium=tutorials_3p&utm_campaign=internal)

## Features Excluded Intentionally

To keep the language simple and concise, the following features commonly available in other similar languages are omitted in Go −

-   Support for type inheritance
    
-   Support for method or operator overloading
    
-   Support for circular dependencies among packages
    
-   Support for pointer arithmetic
    
-   Support for assertions
    
-   Support for generic programming
    

## Go Programs

A Go program can vary in length from 3 lines to millions of lines and it should be written into one or more text files with the extension ".go". For example, hello.go.

You can use "vi", "vim" or any other text editor to write your Go program into a file.

## First Program in Go Language

Here is a simple first program (printing "Hello, World!") in Go language:

```go
package main

import "fmt"

func main() {
    fmt.Println("Hello, World!")
}
```
