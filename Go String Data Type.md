---
Description: Go String Data Type
Notes: W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.
author: 
Url: https://www.w3schools.com/go/go_string_data_type.php
Created: "2025-01-29  02:27:59"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go String Data Type

source: https://www.w3schools.com/go/go_string_data_type.php

> ## Excerpt
> W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.

---
## Go String Data Type

___

## String Data Type

The `string` data type is used to store a sequence of characters (text). String values must be surrounded by double quotes:

### Example

package main  
import ("fmt")  
  
func main() {  
  var txt1 string = "Hello!"  
  var txt2 string  
  txt3 := "World 1"  
  
  fmt.Printf("Type: %T, value: %v\\n", txt1, txt1)  
  fmt.Printf("Type: %T, value: %v\\n", txt2, txt2)  
  fmt.Printf("Type: %T, value: %v\\n", txt3, txt3)  
}

Result:

`Type: string, value: Hello!   Type: string, value:   Type: string, value: World 1   `

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_data_types_string1)

  

Track your progress - it's free!
