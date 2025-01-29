---
Description: Go - Error Handling
Notes: Go - Error Handling - Go programming provides a pretty simple error handling framework with inbuilt error interface type of the following declaration ?
author: 
Url: https://www.tutorialspoint.com/go/go_error_handling.htm
Created: "2025-01-29  02:37:59"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go - Error Handling

source: https://www.tutorialspoint.com/go/go_error_handling.htm

> ## Excerpt
> Go - Error Handling - Go programming provides a pretty simple error handling framework with inbuilt error interface type of the following declaration ?

---
___

___

Go programming provides a pretty simple error handling framework with inbuilt error interface type of the following declaration −

```
type error interface {
   Error() string
}
```

Functions normally return error as last return value. Use **errors.New** to construct a basic error message as following −

```
<span>func </span><span>Sqrt</span><span>(</span><span>value</span><span> float64</span><span>)(</span><span>float64</span><span>,</span><span> error</span><span>)</span><span> </span><span>{</span><span>
   </span><span>if</span><span>(</span><span>value</span><span> </span><span>&lt;</span><span> </span><span>0</span><span>){</span><span>
      </span><span>return</span><span> </span><span>0</span><span>,</span><span> errors</span><span>.</span><span>New</span><span>(</span><span>"Math: negative number passed to Sqrt"</span><span>)</span><span>
   </span><span>}</span><span>
   </span><span>return</span><span> math</span><span>.</span><span>Sqrt</span><span>(</span><span>value</span><span>),</span><span> </span><span>nil</span><span>
</span><span>}</span>
```

Use return value and error message.

```
<span>result</span><span>,</span><span> err</span><span>:=</span><span> </span><span>Sqrt</span><span>(-</span><span>1</span><span>)</span><span>

</span><span>if</span><span> err </span><span>!=</span><span> </span><span>nil</span><span> </span><span>{</span><span>
   fmt</span><span>.</span><span>Println</span><span>(</span><span>err</span><span>)</span><span>
</span><span>}</span>
```

## Example

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"errors"</span><span>
</span><span>import</span><span> </span><span>"fmt"</span><span>
</span><span>import</span><span> </span><span>"math"</span><span>

func </span><span>Sqrt</span><span>(</span><span>value</span><span> float64</span><span>)(</span><span>float64</span><span>,</span><span> error</span><span>)</span><span> </span><span>{</span><span>
   </span><span>if</span><span>(</span><span>value</span><span> </span><span>&lt;</span><span> </span><span>0</span><span>){</span><span>
      </span><span>return</span><span> </span><span>0</span><span>,</span><span> errors</span><span>.</span><span>New</span><span>(</span><span>"Math: negative number passed to Sqrt"</span><span>)</span><span>
   </span><span>}</span><span>
   </span><span>return</span><span> math</span><span>.</span><span>Sqrt</span><span>(</span><span>value</span><span>),</span><span> </span><span>nil</span><span>
</span><span>}</span><span>
func main</span><span>()</span><span> </span><span>{</span><span>
   result</span><span>,</span><span> err</span><span>:=</span><span> </span><span>Sqrt</span><span>(-</span><span>1</span><span>)</span><span>

   </span><span>if</span><span> err </span><span>!=</span><span> </span><span>nil</span><span> </span><span>{</span><span>
      fmt</span><span>.</span><span>Println</span><span>(</span><span>err</span><span>)</span><span>
   </span><span>}</span><span> </span><span>else</span><span> </span><span>{</span><span>
      fmt</span><span>.</span><span>Println</span><span>(</span><span>result</span><span>)</span><span>
   </span><span>}</span><span>
   
   result</span><span>,</span><span> err </span><span>=</span><span> </span><span>Sqrt</span><span>(</span><span>9</span><span>)</span><span>

   </span><span>if</span><span> err </span><span>!=</span><span> </span><span>nil</span><span> </span><span>{</span><span>
      fmt</span><span>.</span><span>Println</span><span>(</span><span>err</span><span>)</span><span>
   </span><span>}</span><span> </span><span>else</span><span> </span><span>{</span><span>
      fmt</span><span>.</span><span>Println</span><span>(</span><span>result</span><span>)</span><span>
   </span><span>}</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
Math: negative number passed to Sqrt
3
```
