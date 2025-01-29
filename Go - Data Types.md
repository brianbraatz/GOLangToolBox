---
Description: Go - Data Types
Notes: In the Go programming language, data types refer to an extensive system used for declaring variables or functions of different types. The type of a variable determines how much space it occupies in storage and how the bit pattern stored is interpreted.
author: 
Url: https://www.tutorialspoint.com/go/go_data_types.htm
Created: "2025-01-29  02:32:23"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go - Data Types

source: https://www.tutorialspoint.com/go/go_data_types.htm

> ## Excerpt
> In the Go programming language, data types refer to an extensive system used for declaring variables or functions of different types. The type of a variable determines how much space it occupies in storage and how the bit pattern stored is interpreted.

---
___

___

In the Go programming language, **data types** refer to an extensive system used for declaring [variables](https://www.tutorialspoint.com/go/go_variables.htm) or [functions](https://www.tutorialspoint.com/go/go_functions.htm) of different types. The type of a variable determines how much space it occupies in storage and how the bit pattern stored is interpreted.

## Types of Go Data Types

The types in Go can be classified as follows −

| Sr.No. | Types and Description |
| --- | --- |
| 1 | 
**Boolean types**

They are boolean types and consists of the two predefined constants: (a) true (b) false

 |
| 2 | 

**Numeric types**

They are again arithmetic types and they represents a) integer types or b) floating point values throughout the program.

 |
| 3 | 

**String types**

A string type represents the set of string values. Its value is a sequence of bytes. Strings are immutable types that is once created, it is not possible to change the contents of a string. The predeclared string type is string.

 |
| 4 | 

**Derived types**

They include (a) Pointer types, (b) Array types, (c) Structure types, (d) Union types and (e) Function types f) Slice types g) Interface types h) Map types i) Channel Types

 |

Array types and structure types are collectively referred to as **aggregate types**. The type of a function specifies the set of all functions with the same parameter and result types. We will discuss the basic types in the following section, whereas other types will be covered in the upcoming chapters.

## Boolean Types

In Go, `bool` is the single type representing Boolean values. It is widely used in logical and conditional operations. It can accept only two values which are "`true`" or "`false`".

| Sr.No. | Types and Description |
| --- | --- |
| 1 | 
**bool**

The only Boolean type in Go, which can hold one of two values: `true` or `false`.

 |

### Example

The following is an example of how the bool type is used in Go:

```go
package main

import "fmt"

func main() {
    
    var var1 bool = true
    var var2 bool = false

    
    fmt.Println("var1:", var1)
    fmt.Println("var2:", var2)

    
    if var1 {
        fmt.Println("It's true.")
    } else {
        fmt.Println("It's false")
    }
}
```

#### Output

```
var1: true
var2: false
It's true.
```

[

Explore our **latest online courses** and learn new skills at your own pace. Enroll and become a certified expert to boost your career.

](https://www.tutorialspoint.com/latest/courses?utm_source=tutorialspoint&utm_medium=tutorials_3p&utm_campaign=internal)

## Integer Types

The predefined architecture-independent integer types are −

| Sr.No. | Types and Description |
| --- | --- |
| 1 | 
**uint8**

Unsigned 8-bit integers (0 to 255)

 |
| 2 | 

**uint16**

Unsigned 16-bit integers (0 to 65535)

 |
| 3 | 

**uint32**

Unsigned 32-bit integers (0 to 4294967295)

 |
| 4 | 

**uint64**

Unsigned 64-bit integers (0 to 18446744073709551615)

 |
| 5 | 

**int8**

Signed 8-bit integers (-128 to 127)

 |
| 6 | 

**int16**

Signed 16-bit integers (-32768 to 32767)

 |
| 7 | 

**int32**

Signed 32-bit integers (-2147483648 to 2147483647)

 |
| 8 | 

**int64**

Signed 64-bit integers (-9223372036854775808 to 9223372036854775807)

 |

### Example

The following is an example of how the integer types are used in Go:

```go
package main

import "fmt"

func main() {
    
    var u8 uint8 = 255
    var u16 uint16 = 65535

    
    var i8 int8 = -128
    var i16 int16 = 32767

    
    fmt.Println("Unsigned 8-bit integer (uint8):", u8)
    fmt.Println("Unsigned 16-bit integer (uint16):", u16)
    fmt.Println("Signed 8-bit integer (int8):", i8)
    fmt.Println("Signed 16-bit integer (int16):", i16)
}
```

#### Output

```
Unsigned 8-bit integer (uint8): 255
Unsigned 16-bit integer (uint16): 65535
Signed 8-bit integer (int8): -128
Signed 16-bit integer (int16): 32767
```

## Floating Types

The predefined architecture-independent float types are −

| Sr.No. | Types and Description |
| --- | --- |
| 1 | 
**float32**

IEEE-754 32-bit floating-point numbers

 |
| 2 | 

**float64**

IEEE-754 64-bit floating-point numbers

 |
| 3 | 

**complex64**

Complex numbers with float32 real and imaginary parts

 |
| 4 | 

**complex128**

Complex numbers with float64 real and imaginary parts

 |

The value of an n-bit integer is n bits and is represented using two's complement arithmetic operations.

### Example

The following is an example of how the float types are used in Go:

```go
package main

import "fmt"

func main() {
    var pi float32 = 3.14159
    var e float64 = 2.718281828459045

    var firstComplexNumber complex64 = complex(1.0, 2.0)
    var secondComplexNumber complex128 = complex(3.0, 4.0)

    
    fmt.Println("Value of pi (float32):", pi)
    fmt.Println("Value of e (float64):", e)
    fmt.Println("First complex number (complex64):", firstComplexNumber)
    fmt.Println("Second complex number (complex128):", secondComplexNumber)

    
    fmt.Println("Real part of first complex number:", real(firstComplexNumber))
    fmt.Println("Imaginary part of first complex number:", imag(firstComplexNumber))

    fmt.Println("Real part of second complex number:", real(secondComplexNumber))
    fmt.Println("Imaginary part of second complex number:", imag(secondComplexNumber))
}
```

#### Output

```
Value of pi (float32): 3.14159
Value of e (float64): 2.718281828459045
First complex number (complex64): (1+2i)
Second complex number (complex128): (3+4i)
Real part of first complex number: 1
Imaginary part of first complex number: 2
Real part of second complex number: 3
Imaginary part of second complex number: 4
```

## Other Numeric Types

There is also a set of numeric types with implementation-specific sizes −

| Sr.No. | Types and Description |
| --- | --- |
| 1 | 
**byte**

same as uint8

 |
| 2 | 

**rune**

same as int32

 |
| 3 | 

**uint**

32 or 64 bits

 |
| 4 | 

**int**

same size as uint

 |
| 5 | 

**uintptr**

an unsigned integer to store the uninterpreted bits of a pointer value

 |

## Derived Types

In Go language, the derived data types are based on other types. They can be created with the help of other data types.

### 1\. Pointer Types

The pointer data type stores the memory address of another variable.

Here is an example of pointer type:

```go
package main

import "fmt"

func main() {
var x int = 42
var ptr *int = &x
fmt.Println(*ptr)
}
```

The output will be:

```
42
```

### 2\. Array Types

The array data type is a fixed-size sequence of elements of the same type. It is used to store multiple values of the same data type in a variable.

Here is an example of array type:

```go
package main

import "fmt"

func main() {
var arr [3]int = [3]int{10, 22, 31}
fmt.Println(arr)
}
```

The output will be:

```
[10 22 31]
```

### 3\. Structure Types

The structure (struct) data type is a collection of fields, each with a name and a type. The structure type allows you to store different types of values.

Here is an example of structure type:

```go
package main

import "fmt"

func main() {
   type Student struct {
      Name string
      Age  int
   }
   var std Student = Student{"Prakash Joshi", 30}
   fmt.Println(std)
}
```

The output will be:

```
{Prakash Joshi 30}
```

### 4\. Union Types

Go language does not provide the support of unions, but unions can be used as `interface{}` to hold any type of value.

Here is an example:

```go
package main

import "fmt"

func main() {
   var u interface {} = "Prakash Joshi"
   fmt.Println(u)
   u = 30
   fmt.Println(u)
   u = "Teja"
   fmt.Println(u)
}
```

The output will be:

```
Prakash Joshi
30
Teja
```

### 5\. Function Types

The function is used for organizing and structuring the code, allowing grouping of the related code together in purpose to make it reusable and easy to maintain.

Here is an example:

```go
package main

import "fmt"

func main() {
    var AddTwoNums = func(a, b int) int { 
        return a + b 
    }
    
    
    fmt.Println(AddTwoNums(10, 20))  
}
```

The output will be:

```
30
```

### 6\. Slice Types

In Go language, the slice type is a dynamically sized and flexible view of an array.

Here is an example:

```go
package main

import "fmt"

func main() {
    var arr []int = []int{11, 22, 33, 44}
    fmt.Println(arr) 
}
```

The output will be:

```
[11 22 33 44]
```

### 7\. Map Types

The map data type is an unordered collection of key-value pairs.

Here is an example to demonstrate how you can use the map data type in Go:

```go
package main

import "fmt"

func main() {
    
    
    var countryCodes = map[string]string{
        "USA":    "+1",
        "India":  "+91",
        "China":  "+86",
        "Brazil": "+55",
        "UK":     "+44",
    }

    
    fmt.Println(countryCodes)

    
    fmt.Println("Country code for India:", countryCodes["India"])
}
```

The output will be:

```
map[Brazil:+55 China:+86 India:+91 UK:+44 USA:+1]
Country code for India: +91
```

### 8\. Channel Types

The channels are useful when you are working with goroutines; these types are used for communication between goroutines.

Here is an example to demonstrate how you can use the channels in Go:

```go
package main

import "fmt"

func main() {
    ch := make(chan int)
    go func() { ch <- 42 }()
    fmt.Println(<-ch)  
}
```

The output will be:

```
42
```
