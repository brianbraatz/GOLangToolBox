---
Description: Go For Loops
Notes: W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.
author: 
Url: https://www.w3schools.com/go/go_loops.php
Created: "2025-01-29  02:29:56"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go For Loops

source: https://www.w3schools.com/go/go_loops.php

> ## Excerpt
> W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.

---
## Go For Loops

___

The `for` loop loops through a block of code a specified number of times.

The `for` loop is the only loop available in Go.

___

## Go for Loop

Loops are handy if you want to run the same code over and over again, each time with a different value.

Each execution of a loop is called an **iteration**.

The `for` loop can take up to three statements:

### Syntax

for _statement1; statement2; statement3_ {  }

**_statement1_** Initializes the loop counter value.

**_statement2_** Evaluated for each loop iteration. If it evaluates to TRUE, the loop continues. If it evaluates to FALSE, the loop ends.

**_statement3_** Increases the loop counter value.

**Note:** These statements don't need to be present as loops arguments. However, they need to be present in the code in some form.

___

## for Loop Examples

### Example 1

This example will print the numbers from 0 to 4:  

package main  
import ("fmt")  
  
func main() {  
  for i:=0; i < 5; i++ {  
    fmt.Println(i)  
  }  
}

Result:

`0   1   2   3   4   `

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_for1)

#### Example 1 explained

-   i:=0; - Initialize the loop counter (i), and set the start value to 0
-   i < 5; - Continue the loop as long as i is less than 5
-   i++ - Increase the loop counter value by 1 for each iteration

### Example 2

This example counts to 100 by tens: 

package main  
import ("fmt")  
  
func main() {  
  for i:=0; i <= 100; i+=10 {  
    fmt.Println(i)  
  }  
}

Result:

`0   10   20   30   40   50   60   70   80   90   100   `

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_for5)

#### Example 2 explained

-   i:=0; - Initialize the loop counter (i), and set the start value to 0
-   i <= 100; - Continue the loop as long as i is less than or equal to 100
-   i+=10 - Increase the loop counter value by 10 for each iteration

___

___

## The continue Statement

The `continue` statement is used to skip one or more iterations in the loop. It then continues with the next iteration in the loop.

### Example

This example skips the value of 3:

package main  
import ("fmt")  
  
func main() {  
  for i:=0; i < 5; i++ {  
    if i == 3 {  
      continue  
    }  
   fmt.Println(i)  
  }  
}  

Result:

`0   1   2   4   `

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_for2)

___

## The break Statement

The `break` statement is used to break/terminate the loop execution.

### Example

This example breaks out of the loop when i is equal to 3:

package main  
import ("fmt")  
  
func main() {  
  for i:=0; i < 5; i++ {  
    if i == 3 {  
      break  
    }  
   fmt.Println(i)  
  }  
}  

Result:

`0   1   2   `

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_for3)

**Note:** `continue` and `break` are usually used with **conditions**.

___

## Nested Loops

It is possible to place a loop inside another loop.

Here, the "inner loop" will be executed one time for each iteration of the "outer loop":

### Example

package main  
import ("fmt")  
  
func main() {  
  adj := \[2\]string{"big", "tasty"}  
  fruits := \[3\]string{"apple", "orange", "banana"}  
  for i:=0; i < len(adj); i++ {  
    for j:=0; j < len(fruits); j++ {  
      fmt.Println(adj\[i\],fruits\[j\])  
    }  
  }  
}

Result:

`big apple   big orange   big banana   tasty apple   tasty orange   tasty banana   `

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_for4)

___

## The Range Keyword

The `range` keyword is used to more easily iterate through the elements of an array, slice or map. It returns both the index and the value.

The `range` keyword is used like this:

### Syntax

for _index, value :=_ range _array_|_slice_|_map_ {  }

### Example

This example uses `range` to iterate over an array and print both the indexes and the values at each (`idx` stores the index, `val` stores the value):

package main  
import ("fmt")  
  
func main() {  
  fruits := \[3\]string{"apple", "orange", "banana"}  
  for idx, val := range fruits {  
     fmt.Printf("%v\\t%v\\n", idx, val)  
  }  
}

Result:

`0      apple   1      orange   2      banana   `

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_for6)

**Tip:** To only show the value or the index, you can omit the other output using an underscore (`_`).

### Example

Here, we want to omit the indexes (`idx` stores the index, `val` stores the value):

package main  
import ("fmt")  
  
func main() {  
  fruits := \[3\]string{"apple", "orange", "banana"}  
  for \_, val := range fruits {  
     fmt.Printf("%v\\n", val)  
  }  
}

Result:

`apple   orange   banana   `

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_for7)

### Example

Here, we want to omit the values (`idx` stores the index, `val` stores the value):

package main  
import ("fmt")  
  
func main() {  
  fruits := \[3\]string{"apple", "orange", "banana"}

  for idx, \_ := range fruits {  
     fmt.Printf("%v\\n", idx)  
  }  
}

Result:

`0   1   2   `

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_for8)

___

## Go Exercises

  

Track your progress - it's free!

   [![Get Certified](https://www.w3schools.com/images/img_fa_up_300.png)](https://campus.w3schools.com/products/w3schools-full-access-course)
