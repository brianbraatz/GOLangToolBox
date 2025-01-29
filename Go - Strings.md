---
Description: Go - Strings
Notes: Go - Strings - Strings, which are widely used in Go programming, are a readonly slice of bytes. In the Go programming language, strings are slices. The Go platform provides various libraries to manipulate strings.
author: 
Url: https://www.tutorialspoint.com/go/go_strings.htm
Created: "2025-01-29  02:36:34"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go - Strings

source: https://www.tutorialspoint.com/go/go_strings.htm

> ## Excerpt
> Go - Strings - Strings, which are widely used in Go programming, are a readonly slice of bytes. In the Go programming language, strings are slices. The Go platform provides various libraries to manipulate strings.

---
___

___

Strings, which are widely used in Go programming, are a readonly slice of bytes. In the Go programming language, strings are **slices**. The Go platform provides various libraries to manipulate strings.

-   unicode
-   regexp
-   strings

## Creating Strings

The most direct way to create a string is to write −

```go
var greeting = "Hello world!"
```

A string literal holds a valid UTF-8 sequences called runes. A String holds arbitrary bytes.

### Example

```go
package main

import "fmt"

func main() {
   var greeting =  "Hello world!"
   
   fmt.Printf("normal string: ")
   fmt.Printf("%s", greeting)
   fmt.Printf("\n")
   fmt.Printf("hex bytes: ")
   
   for i := 0; i < len(greeting); i++ {
       fmt.Printf("%x ", greeting[i])
   }
   
   fmt.Printf("\n")
   const sampleText = "\xbd\xb2\x3d\xbc\x20\xe2\x8c\x98" 
   
   
   fmt.Printf("quoted string: ")
   fmt.Printf("%+q", sampleText)
   fmt.Printf("\n")  
}
```

This would produce the following result −

```
normal string: Hello world!
hex bytes: 48 65 6c 6c 6f 20 77 6f 72 6c 64 21 
quoted string: "\xbd\xb2=\xbc \u2318"
```

**Note** − The string literal is immutable, so that once it is created a string literal cannot be changed.

## Finding String Length

The `len(str)` method returns the number of bytes contained in the string literal.

### Example

```go
package main

import "fmt"

func main() {
   var greeting =  "Hello world!"
   
   fmt.Printf("String Length is: ")
   fmt.Println(len(greeting))  
}
```

This would produce the following result −

```
String Length is : 12
```

[

Explore our **latest online courses** and learn new skills at your own pace. Enroll and become a certified expert to boost your career.

](https://www.tutorialspoint.com/latest/courses?utm_source=tutorialspoint&utm_medium=tutorials_3p&utm_campaign=internal)

## Concatenating Strings

The strings package includes a method **join** for concatenating multiple strings −

```go
strings.Join(sample, " ")
```

### Example

Let us look at the following example −

```go
package main

import ("fmt" "math" )"fmt" "strings")

func main() {
   greetings :=  []string{"Hello","world!"}   
   fmt.Println(strings.Join(greetings, " "))
}
```

This would produce the following result −

```
Hello world!
```

## Iterate Over String Characters

You can iterate through each character of a string using a [`for` loop](https://www.tutorialspoint.com/go/go_for_loop.htm) with the [`range` keyword](https://www.tutorialspoint.com/go/go_range.htm). By using this, you can access both the index and the character.

### Example

The following example demonstrates how you can iterate over the string characters:

```go
package main

import "fmt"

func main() {
    str := "TutorialsPoint"
    for index, char := range str {
        fmt.Printf("Index: %d, Character: %c\n", index, char)
    }
}
```

This would produce the following result −

```
Index: 0, Character: T
Index: 1, Character: u
Index: 2, Character: t
Index: 3, Character: o
Index: 4, Character: r
Index: 5, Character: i
Index: 6, Character: a
Index: 7, Character: l
Index: 8, Character: s
Index: 9, Character: P
Index: 10, Character: o
Index: 11, Character: i
Index: 12, Character: n
Index: 13, Character: t
```
