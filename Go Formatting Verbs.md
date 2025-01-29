---
Description: Go Formatting Verbs
Notes: W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.
author: 
Url: https://www.w3schools.com/go/go_formatting_verbs.php
Created: "2025-01-29  02:27:07"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go Formatting Verbs

source: https://www.w3schools.com/go/go_formatting_verbs.php

> ## Excerpt
> W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.

---
## Go Formatting Verbs

___

## Formatting Verbs for Printf()

Go offers several formatting verbs that can be used with the `Printf()` function.

___

## General Formatting Verbs

The following verbs can be used with all data types:

| Verb | Description |
| --- | --- |
| %v | Prints the value in the default format |
| %#v | Prints the value in Go-syntax format |
| %T | Prints the type of the value |
| %% | Prints the % sign |

### Example

package main  
import ("fmt")

func main() {  
  var i = 15.5  
  var txt = "Hello World!"

  fmt.Printf("%v\\n", i)  
  fmt.Printf("%#v\\n", i)  
  fmt.Printf("%v%%\\n", i)  
  fmt.Printf("%T\\n", i)

  fmt.Printf("%v\\n", txt)  
  fmt.Printf("%#v\\n", txt)  
  fmt.Printf("%T\\n", txt)  
}

Result:

`15.5   15.5   15.5%   float64   Hello World!   "Hello World!"   string`

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_formatting1)

___

## Integer Formatting Verbs

The following verbs can be used with the integer data type:

| Verb | Description |
| --- | --- |
| %b | Base 2 |
| %d | Base 10 |
| %+d | Base 10 and always show sign |
| %o | Base 8 |
| %O | Base 8, with leading 0o |
| %x | Base 16, lowercase |
| %X | Base 16, uppercase |
| %#x | Base 16, with leading 0x |
| %4d | Pad with spaces (width 4, right justified) |
| %-4d | Pad with spaces (width 4, left justified) |
| %04d | Pad with zeroes (width 4 |

### Example

package main  
import ("fmt")  
  
func main() {  
  var i = 15  
   
  fmt.Printf("%b\\n", i)  
  fmt.Printf("%d\\n", i)  
  fmt.Printf("%+d\\n", i)  
  fmt.Printf("%o\\n", i)  
  fmt.Printf("%O\\n", i)  
  fmt.Printf("%x\\n", i)  
  fmt.Printf("%X\\n", i)  
  fmt.Printf("%#x\\n", i)  
  fmt.Printf("%4d\\n", i)  
  fmt.Printf("%-4d\\n", i)  
  fmt.Printf("%04d\\n", i)  
}

Result:

`1111   15   +15   17   0o17   f   F   0xf     15   15   0015`

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_formatting3)

___

___

## String Formatting Verbs

The following verbs can be used with the string data type:

| Verb | Description |
| --- | --- |
| %s | Prints the value as plain string |
| %q | Prints the value as a double-quoted string |
| %8s | Prints the value as plain string (width 8, right justified) |
| %-8s | Prints the value as plain string (width 8, left justified) |
| %x | Prints the value as hex dump of byte values |
| % x | Prints the value as hex dump with spaces |

### Example

package main  
import ("fmt")

func main() {  
  var txt = "Hello"  
   
  fmt.Printf("%s\\n", txt)  
  fmt.Printf("%q\\n", txt)  
  fmt.Printf("%8s\\n", txt)  
  fmt.Printf("%-8s\\n", txt)  
  fmt.Printf("%x\\n", txt)  
  fmt.Printf("% x\\n", txt)  
}

Result:

`Hello   "Hello"      Hello   Hello   48656c6c6f   48 65 6c 6c 6f`

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_formatting5)

___

## Boolean Formatting Verbs

The following verb can be used with the boolean data type:

| Verb | Description |
| --- | --- |
| %t | Value of the boolean operator in true or false format (same as using %v) |

### Example

package main  
import ("fmt")

func main() {  
  var i = true  
  var j = false

  fmt.Printf("%t\\n", i)  
  fmt.Printf("%t\\n", j)  
}

Result:

`true   false`

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_formatting2)

___

## Float Formatting Verbs

The following verbs can be used with the float data type:

| Verb | Description |
| --- | --- |
| %e | Scientific notation with 'e' as exponent |
| %f | Decimal point, no exponent |
| %.2f | Default width, precision 2 |
| %6.2f | Width 6, precision 2 |
| %g | Exponent as needed, only necessary digits |

### Example

package main  
import ("fmt")

func main() {  
  var i = 3.141  
  
  fmt.Printf("%e\\n", i)  
  fmt.Printf("%f\\n", i)  
  fmt.Printf("%.2f\\n", i)  
  fmt.Printf("%6.2f\\n", i)  
  fmt.Printf("%g\\n", i)  
}

Result:

`3.141000e+00   3.141000   3.14     3.14   3.141`

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_formatting4)

  

Track your progress - it's free!

   [![Get Certified](https://www.w3schools.com/images/img_fa_up_300.png)](https://campus.w3schools.com/products/w3schools-full-access-course)
