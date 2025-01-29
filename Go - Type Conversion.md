---
Description: Go - Type Conversion
Notes: Go - Type Conversion - Type conversion is a way to convert a variable from one data type to another data type. For example, if you want to store a long value into a simple integer then you can type cast long to int. You can convert values from one type to another using the cast operator. Its syntax is as follows ?
author: 
Url: https://www.tutorialspoint.com/go/go_type_casting.htm
Created: "2025-01-29  02:37:46"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go - Type Conversion

source: https://www.tutorialspoint.com/go/go_type_casting.htm

> ## Excerpt
> Go - Type Conversion - Type conversion is a way to convert a variable from one data type to another data type. For example, if you want to store a long value into a simple integer then you can type cast long to int. You can convert values from one type to another using the cast operator. Its syntax is as follows ?

---
___

___

Type conversion is a way to convert a variable from one data type to another data type. For example, if you want to store a long value into a simple integer then you can type cast long to int. You can convert values from one type to another using the **cast operator**. Its syntax is as follows −

```
type_name(expression)
```

## Example

Consider the following example where the cast operator causes the division of one integer variable by another to be performed as a floating number operation.

[Live Demo](http://tpcg.io/VuxSeO)

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

func main</span><span>()</span><span> </span><span>{</span><span>
   </span><span>var</span><span> sum </span><span>int</span><span> </span><span>=</span><span> </span><span>17</span><span>
   </span><span>var</span><span> count </span><span>int</span><span> </span><span>=</span><span> </span><span>5</span><span>
   </span><span>var</span><span> mean float32
   
   mean </span><span>=</span><span> float32</span><span>(</span><span>sum</span><span>)/</span><span>float32</span><span>(</span><span>count</span><span>)</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"Value of mean : %f\n"</span><span>,</span><span>mean</span><span>)</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
Value of mean : 3.400000
```
