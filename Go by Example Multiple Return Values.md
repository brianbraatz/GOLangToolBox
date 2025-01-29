---
Description: Go by Example: Multiple Return Values
Notes: Go has built-in support for multiple return values.
This feature is used often in idiomatic Go, for example
to return both result and error values from a function.
author: 
Url: https://gobyexample.com/multiple-return-values
Created: "2025-01-29  02:42:31"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Multiple Return Values

source: https://gobyexample.com/multiple-return-values

> ## Excerpt
> Go has built-in support for multiple return values.
This feature is used often in idiomatic Go, for example
to return both result and error values from a function.

---
<table><tbody><tr><td><p>Go has built-in support for <em>multiple return values</em>. This feature is used often in idiomatic Go, for example to return both result and error values from a function.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/vZdUvLB1WbK"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>"fmt"</span></span></span></code></pre></td></tr><tr><td><p>The <code>(int, int)</code> in this function signature shows that the function returns 2 <code>int</code>s.</p></td><td><pre><code><span><span><span>func</span> <span>vals</span><span>()</span> <span>(</span><span>int</span><span>,</span> <span>int</span><span>)</span> <span>{</span>
</span></span><span><span>    <span>return</span> <span>3</span><span>,</span> <span>7</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>Here we use the 2 different return values from the call with <em>multiple assignment</em>.</p></td><td><pre><code><span><span>    <span>a</span><span>,</span> <span>b</span> <span>:=</span> <span>vals</span><span>()</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>a</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>b</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>If you only want a subset of the returned values, use the blank identifier <code>_</code>.</p></td><td><pre><code><span><span>    <span>_</span><span>,</span> <span>c</span> <span>:=</span> <span>vals</span><span>()</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>c</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go run multiple-return-values.go
</span></span><span><span><span>3
</span></span></span><span><span><span>7
</span></span></span><span><span><span>7</span></span></span></code></pre></td></tr><tr><td><p>Accepting a variable number of arguments is another nice feature of Go functions; we’ll look at this next.</p></td><td></td></tr></tbody></table>

Next example: [Variadic Functions](https://gobyexample.com/variadic-functions).
