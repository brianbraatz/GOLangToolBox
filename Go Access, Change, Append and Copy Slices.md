---
Description: Go Access, Change, Append and Copy Slices
Notes: W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.
author: 
Url: https://www.w3schools.com/go/go_slices_modify.php
Created: "2025-01-29  02:28:19"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go Access, Change, Append and Copy Slices

source: https://www.w3schools.com/go/go_slices_modify.php

> ## Excerpt
> W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.

---
## Go Access, Change, Append and Copy Slices

___

## Access Elements of a Slice

You can access a specific slice element by referring to the index number.

In Go, indexes start at 0. That means that \[0\] is the first element, \[1\] is the second element, etc.

### Example

This example shows how to access the first and third elements in the prices slice:

package main  
import ("fmt")

func main() {  
  prices := \[\]int{10,20,30}  
  
  fmt.Println(prices\[0\])  
  fmt.Println(prices\[2\])  
}

Result:

`10   30`

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_slices4)

___

## Change Elements of a Slice

You can also change a specific slice element by referring to the index number.

### Example

This example shows how to change the third element in the prices slice:

package main  
import ("fmt")

func main() {  
  prices := \[\]int{10,20,30}  
  prices\[2\] = 50  
  fmt.Println(prices\[0\])  
  fmt.Println(prices\[2\])  
}

Result:

`10   50`

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_slices4_2)

___

## Append Elements To a Slice

You can append elements to the end of a slice using the `append()`function:

### Syntax

_slice\_name_ = append(_slice\_name_, _element1_, _element2_, ...)  

### Example

This example shows how to append elements to the end of a slice:

package main  
import ("fmt")

func main() {  
  myslice1 := \[\]int{1, 2, 3, 4, 5, 6}  
  fmt.Printf("myslice1 = %v\\n", myslice1)  
  fmt.Printf("length = %d\\n", len(myslice1))  
  fmt.Printf("capacity = %d\\n", cap(myslice1))

  myslice1 = append(myslice1, 20, 21)  
  fmt.Printf("myslice1 = %v\\n", myslice1)  
  fmt.Printf("length = %d\\n", len(myslice1))  
  fmt.Printf("capacity = %d\\n", cap(myslice1))  
}

Result:

`myslice1 = [1 2 3 4 5 6]   length = 6   capacity = 6   myslice1 = [1 2 3 4 5 6 20 21]   length = 8   capacity = 12`

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_slices5)

___

___

## Append One Slice To Another Slice

To append all the elements of one slice to another slice, use the `append()`function:

### Syntax

_slice3_ = append(_slice1_, _slice2_...)  

**Note:** The **'...'** after _slice2_ is **necessary** when appending the elements of one slice to another.

### Example

This example shows how to append one slice to another slice:

package main  
import ("fmt")

func main() {  
  myslice1 := \[\]int{1,2,3}  
  myslice2 := \[\]int{4,5,6}  
  myslice3 := append(myslice1, myslice2...)

  fmt.Printf("myslice3=%v\\n", myslice3)  
  fmt.Printf("length=%d\\n", len(myslice3))  
  fmt.Printf("capacity=%d\\n", cap(myslice3))  
}

Result:

`myslice3=[1 2 3 4 5 6]   length=6   capacity=6`

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_slices6)

___

## Change The Length of a Slice

Unlike arrays, it is possible to change the length of a slice.

### Example

This example shows how to change the length of a slice:

package main  
import ("fmt")

func main() {  
  arr1 := \[6\]int{9, 10, 11, 12, 13, 14}   myslice1 := arr1\[1:5\]   fmt.Printf("myslice1 = %v\\n", myslice1)  
  fmt.Printf("length = %d\\n", len(myslice1))  
  fmt.Printf("capacity = %d\\n", cap(myslice1))

  myslice1 = arr1\[1:3\]   fmt.Printf("myslice1 = %v\\n", myslice1)  
  fmt.Printf("length = %d\\n", len(myslice1))  
  fmt.Printf("capacity = %d\\n", cap(myslice1))

  myslice1 = append(myslice1, 20, 21, 22, 23)   fmt.Printf("myslice1 = %v\\n", myslice1)  
  fmt.Printf("length = %d\\n", len(myslice1))  
  fmt.Printf("capacity = %d\\n", cap(myslice1))  
}

Result:

`myslice1 = [10 11 12 13]   length = 4   capacity = 5   myslice1 = [10 11]   length = 2   capacity = 5   myslice1 = [10 11 20 21 22 23]   length = 6   capacity = 10`

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_slices7)

___

## Memory Efficiency

 When using slices, Go loads all the underlying elements into the memory.

If the array is large and you need only a few elements, it is better to copy those elements using the `copy()` function.

The `copy()` function creates a new underlying array with only the required elements for the slice. This will reduce the memory used for the program. 

The `copy()` function takes in two slices _dest_ and _src_, and copies data from _src_ to _dest_. It returns the number of elements copied.

### Example

This example shows how to use the `copy()` function:

package main  
import ("fmt")

func main() {  
  numbers := \[\]int{1,2,3,4,5,6,7,8,9,10,11,12,13,14,15}  
    fmt.Printf("numbers = %v\\n", numbers)  
  fmt.Printf("length = %d\\n", len(numbers))  
  fmt.Printf("capacity = %d\\n", cap(numbers))

    neededNumbers := numbers\[:len(numbers)-10\]  
  numbersCopy := make(\[\]int, len(neededNumbers))  
  copy(numbersCopy, neededNumbers)

  fmt.Printf("numbersCopy = %v\\n", numbersCopy)  
  fmt.Printf("length = %d\\n", len(numbersCopy))  
  fmt.Printf("capacity = %d\\n", cap(numbersCopy))  
}

Result:

`// Original slice   numbers = [1 2 3 4 5 6 7 8 9 10 11 12 13 14 15]   length = 15   capacity = 15   // New slice   numbersCopy = [1 2 3 4 5]   length = 5   capacity = 5`

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_slices8)

The capacity of the new slice is now less than the capacity of the original slice because the new underlying array is smaller.

  

Track your progress - it's free!
