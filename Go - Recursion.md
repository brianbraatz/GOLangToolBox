---
Description: Go - Recursion
Notes: Go - Recursion - Recursion is the process of repeating items in a self-similar way. The same concept applies in programming languages as well. If a program allows to call a function inside the same function, then it is called a recursive function call. Take a look at the following example ?
author: 
Url: https://www.tutorialspoint.com/go/go_recursion.htm
Created: "2025-01-29  02:37:27"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go - Recursion

source: https://www.tutorialspoint.com/go/go_recursion.htm

> ## Excerpt
> Go - Recursion - Recursion is the process of repeating items in a self-similar way. The same concept applies in programming languages as well. If a program allows to call a function inside the same function, then it is called a recursive function call. Take a look at the following example ?

---
___

___

Recursion is the process of repeating items in a self-similar way. The same concept applies in programming languages as well. If a program allows to call a function inside the same function, then it is called a recursive function call. Take a look at the following example −

```
<span>func recursion</span><span>()</span><span> </span><span>{</span><span>
   recursion</span><span>()</span><span> </span><span>/* function calls itself */</span><span>
</span><span>}</span><span>
func main</span><span>()</span><span> </span><span>{</span><span>
   recursion</span><span>()</span><span>
</span><span>}</span>
```

The Go programming language supports recursion. That is, it allows a function to call itself. But while using recursion, programmers need to be careful to define an exit condition from the function, otherwise it will go on to become an infinite loop.

## Examples of Recursion in Go

Recursive functions are very useful to solve many mathematical problems such as calculating factorial of a number, generating a Fibonacci series, etc.

### Example 1: Calculating Factorial Using Recursion in Go

The following example calculates the factorial of a given number using a recursive function −

[Live Demo](http://tpcg.io/5WHOT5)

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

func factorial</span><span>(</span><span>i </span><span>int</span><span>)</span><span>int</span><span> </span><span>{</span><span>
   </span><span>if</span><span>(</span><span>i </span><span>&lt;=</span><span> </span><span>1</span><span>)</span><span> </span><span>{</span><span>
      </span><span>return</span><span> </span><span>1</span><span>
   </span><span>}</span><span>
   </span><span>return</span><span> i </span><span>*</span><span> factorial</span><span>(</span><span>i </span><span>-</span><span> </span><span>1</span><span>)</span><span>
</span><span>}</span><span>
func main</span><span>()</span><span> </span><span>{</span><span> 
   </span><span>var</span><span> i </span><span>int</span><span> </span><span>=</span><span> </span><span>15</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span>"Factorial of %d is %d"</span><span>,</span><span> i</span><span>,</span><span> factorial</span><span>(</span><span>i</span><span>))</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
Factorial of 15 is 1307674368000
```

## Example 2: Fibonacci Series Using Recursion in Go

The following example shows how to generate a Fibonacci series of a given number using a recursive function −

[Live Demo](http://tpcg.io/6oOFE0)

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

func fibonaci</span><span>(</span><span>i </span><span>int</span><span>)</span><span> </span><span>(</span><span>ret </span><span>int</span><span>)</span><span> </span><span>{</span><span>
   </span><span>if</span><span> i </span><span>==</span><span> </span><span>0</span><span> </span><span>{</span><span>
      </span><span>return</span><span> </span><span>0</span><span>
   </span><span>}</span><span>
   </span><span>if</span><span> i </span><span>==</span><span> </span><span>1</span><span> </span><span>{</span><span>
      </span><span>return</span><span> </span><span>1</span><span>
   </span><span>}</span><span>
   </span><span>return</span><span> fibonaci</span><span>(</span><span>i</span><span>-</span><span>1</span><span>)</span><span> </span><span>+</span><span> fibonaci</span><span>(</span><span>i</span><span>-</span><span>2</span><span>)</span><span>
</span><span>}</span><span>
func main</span><span>()</span><span> </span><span>{</span><span>
   </span><span>var</span><span> i </span><span>int</span><span>
   </span><span>for</span><span> i </span><span>=</span><span> </span><span>0</span><span>;</span><span> i </span><span>&lt;</span><span> </span><span>10</span><span>;</span><span> i</span><span>++</span><span> </span><span>{</span><span>
      fmt</span><span>.</span><span>Printf</span><span>(</span><span>"%d "</span><span>,</span><span> fibonaci</span><span>(</span><span>i</span><span>))</span><span>
   </span><span>}</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
0 1 1 2 3 5 8 13 21 34 
```
