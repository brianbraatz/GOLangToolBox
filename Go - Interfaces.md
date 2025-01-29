---
Description: Go - Interfaces
Notes: Go programming provides another data type called interfaces which represents a set of method signatures. The struct data type implements these interfaces to have method definitions for the method signature of the interfaces.
author: 
Url: https://www.tutorialspoint.com/go/go_interfaces.htm
Created: "2025-01-29  02:37:53"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go - Interfaces

source: https://www.tutorialspoint.com/go/go_interfaces.htm

> ## Excerpt
> Go programming provides another data type called interfaces which represents a set of method signatures. The struct data type implements these interfaces to have method definitions for the method signature of the interfaces.

---
___

___

Go programming provides another data type called **interfaces** which represents a set of method signatures. The struct data type implements these interfaces to have method definitions for the method signature of the interfaces.

## Syntax

```
/* define an interface */
type interface_name interface {
   method_name1 [return_type]
   method_name2 [return_type]
   method_name3 [return_type]
   ...
   method_namen [return_type]
}

/* define a struct */
type struct_name struct {
   /* variables */
}

/* implement interface methods*/
func (struct_name_variable struct_name) method_name1() [return_type] {
   /* method implementation */
}
...
func (struct_name_variable struct_name) method_namen() [return_type] {
   /* method implementation */
}
```

## Example

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>(</span><span>"fmt"</span><span> </span><span>"math"</span><span>)</span><span>

</span><span>/* define an interface */</span><span>
type </span><span>Shape</span><span> </span><span>interface</span><span> </span><span>{</span><span>
   area</span><span>()</span><span> float64
</span><span>}</span><span>

</span><span>/* define a circle */</span><span>
type </span><span>Circle</span><span> </span><span>struct</span><span> </span><span>{</span><span>
   x</span><span>,</span><span>y</span><span>,</span><span>radius float64
</span><span>}</span><span>

</span><span>/* define a rectangle */</span><span>
type </span><span>Rectangle</span><span> </span><span>struct</span><span> </span><span>{</span><span>
   width</span><span>,</span><span> height float64
</span><span>}</span><span>

</span><span>/* define a method for circle (implementation of Shape.area())*/</span><span>
func</span><span>(</span><span>circle </span><span>Circle</span><span>)</span><span> area</span><span>()</span><span> float64 </span><span>{</span><span>
   </span><span>return</span><span> math</span><span>.</span><span>Pi</span><span> </span><span>*</span><span> circle</span><span>.</span><span>radius </span><span>*</span><span> circle</span><span>.</span><span>radius
</span><span>}</span><span>

</span><span>/* define a method for rectangle (implementation of Shape.area())*/</span><span>
func</span><span>(</span><span>rect </span><span>Rectangle</span><span>)</span><span> area</span><span>()</span><span> float64 </span><span>{</span><span>
   </span><span>return</span><span> rect</span><span>.</span><span>width </span><span>*</span><span> rect</span><span>.</span><span>height
</span><span>}</span><span>

</span><span>/* define a method for shape */</span><span>
func getArea</span><span>(</span><span>shape </span><span>Shape</span><span>)</span><span> float64 </span><span>{</span><span>
   </span><span>return</span><span> shape</span><span>.</span><span>area</span><span>()</span><span>
</span><span>}</span><span>

func main</span><span>()</span><span> </span><span>{</span><span>
   circle </span><span>:=</span><span> </span><span>Circle</span><span>{</span><span>x</span><span>:</span><span>0</span><span>,</span><span>y</span><span>:</span><span>0</span><span>,</span><span>radius</span><span>:</span><span>5</span><span>}</span><span>
   rectangle </span><span>:=</span><span> </span><span>Rectangle</span><span> </span><span>{</span><span>width</span><span>:</span><span>10</span><span>,</span><span> height</span><span>:</span><span>5</span><span>}</span><span>
   
   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"Circle area: %f\n"</span><span>,</span><span>getArea</span><span>(</span><span>circle</span><span>))</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"Rectangle area: %f\n"</span><span>,</span><span>getArea</span><span>(</span><span>rectangle</span><span>))</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
Circle area: 78.539816
Rectangle area: 50.000000
```
