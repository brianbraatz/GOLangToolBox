---
Description: Go Float Data Types
Notes: W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.
author: 
Url: https://www.w3schools.com/go/go_float_data_type.php
Created: "2025-01-29  02:27:50"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go Float Data Types

source: https://www.w3schools.com/go/go_float_data_type.php

> ## Excerpt
> W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.

---
## Go Float Data Types

___

## Go Float Data Types

The float data types are used to store positive and negative numbers with a decimal point, like 35.3, -2.34, or 3597.34987.

The float data type has two keywords:

| Type | Size | Range |
| --- | --- | --- |
| `float32` | 32 bits | \-3.4e+38 to 3.4e+38. |
| `float64` | 64 bits | \-1.7e+308 to +1.7e+308. |

**Tip:** The default type for float is `float64`. If you do not specify a type, the type will be `float64`.

___

## The float32 Keyword

### Example

This example shows how to declare some variables of type `float32`:

package main  
import ("fmt")  
  
func main() {  
  var x float32 = 123.78  
  var y float32 = 3.4e+38  
  fmt.Printf("Type: %T, value: %v\\n", x, x)  
  fmt.Printf("Type: %T, value: %v", y, y)  
}

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_data_types_float1)

___

## The float64 Keyword

The `float64` data type can store a larger set of numbers than `float32`.

### Example

This example shows how to declare a variable of type `float64`:

package main  
import ("fmt")  
  
func main() {  
  var x float64 = 1.7e+308  
  fmt.Printf("Type: %T, value: %v", x, x)  
}

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_data_types_float2)

___

## Which Float Type to Use?

The type of float to choose, depends on the value the variable has to store.

### Example

This example will result in an error because 3.4e+39 is out of range for float32:

package main  
import ("fmt")  
  
func main() {  
  var x float32= 3.4e+39  
  fmt.Println(x)  
}

Result:

`./prog.go:5:7: constant 3.4e+39 overflows float32`

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_data_types_float3)

  

Track your progress - it's free!
