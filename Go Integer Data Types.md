---
Description: Go Integer Data Types
Notes: W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.
author: 
Url: https://www.w3schools.com/go/go_integer_data_type.php
Created: "2025-01-29  02:27:36"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go Integer Data Types

source: https://www.w3schools.com/go/go_integer_data_type.php

> ## Excerpt
> W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.

---
## Go Integer Data Types

___

## Go Integer Data Types

Integer data types are used to store a whole number without decimals, like 35, -50, or 1345000.

The integer data type has two categories:

-   **Signed integers** - can store both positive and negative values
-   **Unsigned integers** - can only store non-negative values

**Tip:** The default type for integer is `int`. If you do not specify a type, the type will be `int`.

___

## Signed Integers

Signed integers, declared with one of the `int` keywords, can store both positive and negative values:

### Example

package main  
import ("fmt")

func main() {  
  var x int = 500  
  var y int = -4500  
  fmt.Printf("Type: %T, value: %v", x, x)  
  fmt.Printf("Type: %T, value: %v", y, y)  
}

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_data_types_integer2)

Go has five keywords/types of signed integers:

| Type | Size | Range |
| --- | --- | --- |
| `int` | Depends on platform:  
32 bits in 32 bit systems and  
64 bit in 64 bit systems | \-2147483648 to 2147483647 in 32 bit systems and  
\-9223372036854775808 to 9223372036854775807 in 64 bit systems |
| `int8` | 8 bits/1 byte | \-128 to 127 |
| `int16` | 16 bits/2 byte | \-32768 to 32767 |
| `int32` | 32 bits/4 byte | \-2147483648 to 2147483647 |
| `int64` | 64 bits/8 byte | \-9223372036854775808 to 9223372036854775807 |

___

___

## Unsigned Integers

Unsigned integers, declared with one of the `uint` keywords, can only store non-negative values:

### Example

package main  
import ("fmt")

func main() {  
  var x uint = 500  
  var y uint = 4500  
  fmt.Printf("Type: %T, value: %v", x, x)  
  fmt.Printf("Type: %T, value: %v", y, y)  
}  

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_data_types_integer1)

Go has five keywords/types of unsigned integers:

| Type | Size | Range |
| --- | --- | --- |
| `uint` | Depends on platform:  
32 bits in 32 bit systems and  
64 bit in 64 bit systems | 0 to 4294967295 in 32 bit systems and  
0 to 18446744073709551615 in 64 bit systems |
| `uint8` | 8 bits/1 byte | 0 to 255 |
| `uint16` | 16 bits/2 byte | 0 to 65535 |
| `uint32` | 32 bits/4 byte | 0 to 4294967295 |
| `uint64` | 64 bits/8 byte | 0 to 18446744073709551615 |

___

## Which Integer Type to Use?

The type of integer to choose, depends on the value the variable has to store.

### Example

This example will result in an error because 1000 is out of range for int8 (which is from -128 to 127):

package main  
import ("fmt")  
  
func main() {  
  var x int8 = 1000  
  fmt.Printf("Type: %T, value: %v", x, x)  
}

Result:

`./prog.go:5:7: constant 1000 overflows int8`

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_data_types_integer3)

  

Track your progress - it's free!

   [![Get Certified](https://www.w3schools.com/images/img_academy_up_300.png)](https://www.w3schools.com/academy/index.php)
