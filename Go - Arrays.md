---
Description: Go - Arrays
Notes: Go - Arrays - Go programming language provides a data structure called the array, which can store a fixed-size sequential collection of elements of the same type. An array is used to store a collection of data, but it is often more useful to think of an array as a collection of variables of the same type.
author: 
Url: https://www.tutorialspoint.com/go/go_arrays.htm
Created: "2025-01-29  02:36:40"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go - Arrays

source: https://www.tutorialspoint.com/go/go_arrays.htm

> ## Excerpt
> Go - Arrays - Go programming language provides a data structure called the array, which can store a fixed-size sequential collection of elements of the same type. An array is used to store a collection of data, but it is often more useful to think of an array as a collection of variables of the same type.

---
___

___

Go programming language provides a data structure called **the array**, which can store a fixed-size sequential collection of elements of the same type. An array is used to store a collection of data, but it is often more useful to think of an array as a collection of variables of the same type.

Instead of declaring individual variables, such as number0, number1, ..., and number99, you declare one array variable such as numbers and use numbers\[0\], numbers\[1\], and ..., numbers\[99\] to represent individual variables. A specific element in an array is accessed by an index.

All arrays consist of contiguous memory locations. The lowest address corresponds to the first element and the highest address to the last element.

![Arrays in Go](https://www.tutorialspoint.com/go/images/arrays.jpg)

## Declaring Arrays

To declare an array in Go, a programmer specifies the type of the elements and the number of elements required by an array as follows −

```
var variable_name [SIZE] variable_type
```

This is called a _single-dimensional_ array. The **arraySize** must be an integer constant greater than zero and **type** can be any valid Go data type. For example, to declare a 10-element array called **balance** of type float32, use this statement −

```
var balance [10] float32
```

Here, **balance** is a variable array that can hold up to 10 float numbers.

## Initializing Arrays

You can initialize array in Go either one by one or using a single statement as follows −

```
var balance = [5]float32{1000.0, 2.0, 3.4, 7.0, 50.0}
```

The number of values between braces { } can not be larger than the number of elements that we declare for the array between square brackets \[ \].

If you omit the size of the array, an array just big enough to hold the initialization is created. Therefore, if you write −

```
var balance = []float32{1000.0, 2.0, 3.4, 7.0, 50.0}
```

You will create exactly the same array as you did in the previous example. Following is an example to assign a single element of the array −

```
balance[4] = 50.0
```

The above statement assigns element number 5<sup>th</sup> in the array with a value of 50.0. All arrays have 0 as the index of their first element which is also called base index and last index of an array will be total size of the array minus 1. Following is the pictorial representation of the same array we discussed above −

![Array Presentation](https://www.tutorialspoint.com/go/images/array_presentation.jpg)

[

Explore our **latest online courses** and learn new skills at your own pace. Enroll and become a certified expert to boost your career.

](https://www.tutorialspoint.com/latest/courses?utm_source=tutorialspoint&utm_medium=tutorials_3p&utm_campaign=internal)

## Accessing Array Elements

An element is accessed by indexing the array name. This is done by placing the index of the element within square brackets after the name of the array. For example −

```
float32 salary = balance[9]
```

The above statement will take 10<sup>th</sup> element from the array and assign the value to salary variable. Following is an example which will use all the above mentioned three concepts viz. declaration, assignment and accessing arrays −

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

func main</span><span>()</span><span> </span><span>{</span><span>
   </span><span>var</span><span> n </span><span>[</span><span>10</span><span>]</span><span>int</span><span> </span><span>/* n is an array of 10 integers */</span><span>
   </span><span>var</span><span> i</span><span>,</span><span>j </span><span>int</span><span>

   </span><span>/* initialize elements of array n to 0 */</span><span>         
   </span><span>for</span><span> i </span><span>=</span><span> </span><span>0</span><span>;</span><span> i </span><span>&lt;</span><span> </span><span>10</span><span>;</span><span> i</span><span>++</span><span> </span><span>{</span><span>
      n</span><span>[</span><span>i</span><span>]</span><span> </span><span>=</span><span> i </span><span>+</span><span> </span><span>100</span><span> </span><span>/* set element at location i to i + 100 */</span><span>
   </span><span>}</span><span>
   
   </span><span>/* output each array element's value */</span><span>
   </span><span>for</span><span> j </span><span>=</span><span> </span><span>0</span><span>;</span><span> j </span><span>&lt;</span><span> </span><span>10</span><span>;</span><span> j</span><span>++</span><span> </span><span>{</span><span>
      fmt</span><span>.</span><span>Printf</span><span>(</span><span>"Element[%d] = %d\n"</span><span>,</span><span> j</span><span>,</span><span> n</span><span>[</span><span>j</span><span>]</span><span> </span><span>)</span><span>
   </span><span>}</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
Element[0] = 100
Element[1] = 101
Element[2] = 102
Element[3] = 103
Element[4] = 104
Element[5] = 105
Element[6] = 106
Element[7] = 107
Element[8] = 108
Element[9] = 109
```

## Go Arrays in Detail

There are important concepts related to array which should be clear to a Go programmer −

| Sr.No | Concept & Description |
| --- | --- |
| 1 | [Multi-dimensional arrays](https://www.tutorialspoint.com/go/go_multi_dimensional_arrays.htm "Multi-dimensional arrays in Go")
Go supports multidimensional arrays. The simplest form of a multidimensional array is the two-dimensional array.

 |
| 2 | [Passing arrays to functions](https://www.tutorialspoint.com/go/go_passing_arrays_to_functions.htm "Passing arrays to functions as arguments in Go")

You can pass to the function a pointer to an array by specifying the array's name without an index.

 |
