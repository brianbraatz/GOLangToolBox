---
Description: Go Recursion Functions
Notes: W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.
author: 
Url: https://www.w3schools.com/go/go_function_recursion.php
Created: "2025-01-29  02:30:21"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go Recursion Functions

source: https://www.w3schools.com/go/go_function_recursion.php

> ## Excerpt
> W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.

---
## Go Recursion Functions

___

## Recursion Functions

Go accepts recursion functions. A function is recursive if it calls itself and reaches a stop condition.

In the following example, `testcount()` is a function that calls itself. We use the `x` variable as the data, which increments with 1 (`x + 1`) every time we recurse. The recursion ends when the `x` variable equals to 11 (`x == 11`). 

### Example

package main  
import ("fmt")  
  
func testcount(x int) int {  
  if x == 11 {  
    return 0  
  }  
  fmt.Println(x)  
  return testcount(x \+ 1)  
}

func main(){  
  testcount(1)  
}

Result:

`1   2   3   4   5   6   7   8   9   10`

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_func10_1)

Recursion is a common mathematical and programming concept. This has the benefit of meaning that you can loop through data to reach a result.

The developer should be careful with recursion functions as it can be quite easy to slip into writing a function which never terminates, or one that uses excess amounts of memory or processor power. However, when written correctly recursion can be a very efficient and mathematically-elegant approach to programming.

In the following example, `factorial_recursion()` is a function that calls itself. We use the `x` variable as the data, which decrements (-1) every time we recurse. The recursion ends when the condition is not greater than 0 (i.e. when it is 0).

### Example

package main  
import ("fmt")

func factorial\_recursion(x float64) (y float64) {  
  if x > 0 {  
     y = x \* factorial\_recursion(x-1)  
  } else {  
     y = 1  
  }  
  return  
}

func main() {  
  fmt.Println(factorial\_recursion(4))  
}

Result:

`24   `

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_func10)

To a new developer it can take some time to work out how exactly this works, best way to find out is by testing and modifying it.

  

Track your progress - it's free!

   [![Get Certified](https://www.w3schools.com/images/img_course_up_300.png)](https://campus.w3schools.com/collections/course-catalog)
