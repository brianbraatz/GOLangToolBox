---
Description: Go - Slices
Notes: Go - Slices - Go Slice is an abstraction over Go Array. Go Array allows you to define variables that can hold several data items of the same kind but it does not provide any inbuilt method to increase its size dynamically or get a sub-array of its own. Slices overcome this limitation. It provides many utility fun
author: 
Url: https://www.tutorialspoint.com/go/go_slice.htm
Created: "2025-01-29  02:37:08"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go - Slices

source: https://www.tutorialspoint.com/go/go_slice.htm

> ## Excerpt
> Go - Slices - Go Slice is an abstraction over Go Array. Go Array allows you to define variables that can hold several data items of the same kind but it does not provide any inbuilt method to increase its size dynamically or get a sub-array of its own. Slices overcome this limitation. It provides many utility fun

---
___

___

Go Slice is an abstraction over Go Array. Go Array allows you to define variables that can hold several data items of the same kind but it does not provide any inbuilt method to increase its size dynamically or get a sub-array of its own. Slices overcome this limitation. It provides many utility functions required on Array and is widely used in Go programming.

## Defining a slice

To define a slice, you can declare it as an array without specifying its size. Alternatively, you can use **make** function to create a slice.

```
var numbers []int /* a slice of unspecified size */
/* numbers == []int{0,0,0,0,0}*/
numbers = make([]int,5,5) /* a slice of length 5 and capacity 5*/
```

## len() and cap() functions

A slice is an abstraction over array. It actually uses arrays as an underlying structure. The **len()** function returns the elements presents in the slice where **cap()** function returns the capacity of the slice (i.e., how many elements it can be accommodate). The following example explains the usage of slice −

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

func main</span><span>()</span><span> </span><span>{</span><span>
   </span><span>var</span><span> numbers </span><span>=</span><span> make</span><span>([]</span><span>int</span><span>,</span><span>3</span><span>,</span><span>5</span><span>)</span><span>
   printSlice</span><span>(</span><span>numbers</span><span>)</span><span>
</span><span>}</span><span>
func printSlice</span><span>(</span><span>x </span><span>[]</span><span>int</span><span>){</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"len=%d cap=%d slice=%v\n"</span><span>,</span><span>len</span><span>(</span><span>x</span><span>),</span><span>cap</span><span>(</span><span>x</span><span>),</span><span>x</span><span>)</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
len = 3 cap = 5 slice = [0 0 0]
```

[

Explore our **latest online courses** and learn new skills at your own pace. Enroll and become a certified expert to boost your career.

](https://www.tutorialspoint.com/latest/courses?utm_source=tutorialspoint&utm_medium=tutorials_3p&utm_campaign=internal)

## Nil slice

If a slice is declared with no inputs, then by default, it is initialized as nil. Its length and capacity are zero. For example −

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

func main</span><span>()</span><span> </span><span>{</span><span>
   </span><span>var</span><span> numbers </span><span>[]</span><span>int</span><span>
   printSlice</span><span>(</span><span>numbers</span><span>)</span><span>
   
   </span><span>if</span><span>(</span><span>numbers </span><span>==</span><span> </span><span>nil</span><span>){</span><span>
      fmt</span><span>.</span><span>Printf</span><span>(</span><span>"slice is nil"</span><span>)</span><span>
   </span><span>}</span><span>
</span><span>}</span><span>
func printSlice</span><span>(</span><span>x </span><span>[]</span><span>int</span><span>){</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"len = %d cap = %d slice = %v\n"</span><span>,</span><span> len</span><span>(</span><span>x</span><span>),</span><span> cap</span><span>(</span><span>x</span><span>),</span><span>x</span><span>)</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
len = 0 cap = 0 slice = []
slice is nil
```

## Subslicing

Slice allows lower-bound and upper bound to be specified to get the subslice of it using**\[lower-bound:upper-bound\]**. For example −

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

func main</span><span>()</span><span> </span><span>{</span><span>
   </span><span>/* create a slice */</span><span>
   numbers </span><span>:=</span><span> </span><span>[]</span><span>int</span><span>{</span><span>0</span><span>,</span><span>1</span><span>,</span><span>2</span><span>,</span><span>3</span><span>,</span><span>4</span><span>,</span><span>5</span><span>,</span><span>6</span><span>,</span><span>7</span><span>,</span><span>8</span><span>}</span><span>   
   printSlice</span><span>(</span><span>numbers</span><span>)</span><span>
   
   </span><span>/* print the original slice */</span><span>
   fmt</span><span>.</span><span>Println</span><span>(</span><span>"numbers =="</span><span>,</span><span> numbers</span><span>)</span><span>
   
   </span><span>/* print the sub slice starting from index 1(included) to index 4(excluded)*/</span><span>
   fmt</span><span>.</span><span>Println</span><span>(</span><span>"numbers[1:4] =="</span><span>,</span><span> numbers</span><span>[</span><span>1</span><span>:</span><span>4</span><span>])</span><span>
   
   </span><span>/* missing lower bound implies 0*/</span><span>
   fmt</span><span>.</span><span>Println</span><span>(</span><span>"numbers[:3] =="</span><span>,</span><span> numbers</span><span>[:</span><span>3</span><span>])</span><span>
   
   </span><span>/* missing upper bound implies len(s)*/</span><span>
   fmt</span><span>.</span><span>Println</span><span>(</span><span>"numbers[4:] =="</span><span>,</span><span> numbers</span><span>[</span><span>4</span><span>:])</span><span>
   
   numbers1 </span><span>:=</span><span> make</span><span>([]</span><span>int</span><span>,</span><span>0</span><span>,</span><span>5</span><span>)</span><span>
   printSlice</span><span>(</span><span>numbers1</span><span>)</span><span>
   
   </span><span>/* print the sub slice starting from index 0(included) to index 2(excluded) */</span><span>
   number2 </span><span>:=</span><span> numbers</span><span>[:</span><span>2</span><span>]</span><span>
   printSlice</span><span>(</span><span>number2</span><span>)</span><span>
   
   </span><span>/* print the sub slice starting from index 2(included) to index 5(excluded) */</span><span>
   number3 </span><span>:=</span><span> numbers</span><span>[</span><span>2</span><span>:</span><span>5</span><span>]</span><span>
   printSlice</span><span>(</span><span>number3</span><span>)</span><span>
   
</span><span>}</span><span>
func printSlice</span><span>(</span><span>x </span><span>[]</span><span>int</span><span>){</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"len = %d cap = %d slice = %v\n"</span><span>,</span><span> len</span><span>(</span><span>x</span><span>),</span><span> cap</span><span>(</span><span>x</span><span>),</span><span>x</span><span>)</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
len = 9 cap = 9 slice = [0 1 2 3 4 5 6 7 8]
numbers == [0 1 2 3 4 5 6 7 8]
numbers[1:4] == [1 2 3]
numbers[:3] == [0 1 2]
numbers[4:] == [4 5 6 7 8]
len = 0 cap = 5 slice = []
len = 2 cap = 9  slice = [0 1]
len = 3 cap = 7 slice = [2 3 4]
```

## append() and copy() Functions

One can increase the capacity of a slice using the **append()** function. Using **copy()**function, the contents of a source slice are copied to a destination slice. For example −

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

func main</span><span>()</span><span> </span><span>{</span><span>
   </span><span>var</span><span> numbers </span><span>[]</span><span>int</span><span>
   printSlice</span><span>(</span><span>numbers</span><span>)</span><span>
   
   </span><span>/* append allows nil slice */</span><span>
   numbers </span><span>=</span><span> append</span><span>(</span><span>numbers</span><span>,</span><span> </span><span>0</span><span>)</span><span>
   printSlice</span><span>(</span><span>numbers</span><span>)</span><span>
   
   </span><span>/* add one element to slice*/</span><span>
   numbers </span><span>=</span><span> append</span><span>(</span><span>numbers</span><span>,</span><span> </span><span>1</span><span>)</span><span>
   printSlice</span><span>(</span><span>numbers</span><span>)</span><span>
   
   </span><span>/* add more than one element at a time*/</span><span>
   numbers </span><span>=</span><span> append</span><span>(</span><span>numbers</span><span>,</span><span> </span><span>2</span><span>,</span><span>3</span><span>,</span><span>4</span><span>)</span><span>
   printSlice</span><span>(</span><span>numbers</span><span>)</span><span>
   
   </span><span>/* create a slice numbers1 with double the capacity of earlier slice*/</span><span>
   numbers1 </span><span>:=</span><span> make</span><span>([]</span><span>int</span><span>,</span><span> len</span><span>(</span><span>numbers</span><span>),</span><span> </span><span>(</span><span>cap</span><span>(</span><span>numbers</span><span>))*</span><span>2</span><span>)</span><span>
   
   </span><span>/* copy content of numbers to numbers1 */</span><span>
   copy</span><span>(</span><span>numbers1</span><span>,</span><span>numbers</span><span>)</span><span>
   printSlice</span><span>(</span><span>numbers1</span><span>)</span><span>   
</span><span>}</span><span>
func printSlice</span><span>(</span><span>x </span><span>[]</span><span>int</span><span>){</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"len=%d cap=%d slice=%v\n"</span><span>,</span><span>len</span><span>(</span><span>x</span><span>),</span><span>cap</span><span>(</span><span>x</span><span>),</span><span>x</span><span>)</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
len = 0 cap = 0 slice = []
len = 1 cap = 2 slice = [0]
len = 2 cap = 2 slice = [0 1]
len = 5 cap = 8 slice = [0 1 2 3 4]
len = 5 cap = 16 slice = [0 1 2 3 4]
```
