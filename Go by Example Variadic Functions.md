---
Description: Go by Example: Variadic Functions
Notes: Variadic functions
can be called with any number of trailing arguments.
For example, fmt.Println is a common variadic
function.
author: 
Url: https://gobyexample.com/variadic-functions
Created: "2025-01-29  02:42:34"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Variadic Functions

source: https://gobyexample.com/variadic-functions

> ## Excerpt
> Variadic functions
can be called with any number of trailing arguments.
For example, fmt.Println is a common variadic
function.

---
<table><tbody><tr><td><p><a href="https://en.wikipedia.org/wiki/Variadic_function"><em>Variadic functions</em></a> can be called with any number of trailing arguments. For example, <code>fmt.Println</code> is a common variadic function.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/glNdE8aKPNq"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>"fmt"</span></span></span></code></pre></td></tr><tr><td><p>Here’s a function that will take an arbitrary number of <code>int</code>s as arguments.</p></td><td><pre><code><span><span><span>func</span> <span>sum</span><span>(</span><span>nums</span> <span>...</span><span>int</span><span>)</span> <span>{</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Print</span><span>(</span><span>nums</span><span>,</span> <span>" "</span><span>)</span>
</span></span><span><span>    <span>total</span> <span>:=</span> <span>0</span></span></span></code></pre></td></tr><tr><td><p>Within the function, the type of <code>nums</code> is equivalent to <code>[]int</code>. We can call <code>len(nums)</code>, iterate over it with <code>range</code>, etc.</p></td><td><pre><code><span><span>    <span>for</span> <span>_</span><span>,</span> <span>num</span> <span>:=</span> <span>range</span> <span>nums</span> <span>{</span>
</span></span><span><span>        <span>total</span> <span>+=</span> <span>num</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>total</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>Variadic functions can be called in the usual way with individual arguments.</p></td><td><pre><code><span><span>    <span>sum</span><span>(</span><span>1</span><span>,</span> <span>2</span><span>)</span>
</span></span><span><span>    <span>sum</span><span>(</span><span>1</span><span>,</span> <span>2</span><span>,</span> <span>3</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>If you already have multiple args in a slice, apply them to a variadic function using <code>func(slice...)</code> like this.</p></td><td><pre><code><span><span>    <span>nums</span> <span>:=</span> <span>[]</span><span>int</span><span>{</span><span>1</span><span>,</span> <span>2</span><span>,</span> <span>3</span><span>,</span> <span>4</span><span>}</span>
</span></span><span><span>    <span>sum</span><span>(</span><span>nums</span><span>...</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go run variadic-functions.go 
</span></span><span><span><span>[1 2] 3
</span></span></span><span><span><span>[1 2 3] 6
</span></span></span><span><span><span>[1 2 3 4] 10</span></span></span></code></pre></td></tr><tr><td><p>Another key aspect of functions in Go is their ability to form closures, which we’ll look at next.</p></td><td></td></tr></tbody></table>

Next example: [Closures](https://gobyexample.com/closures).
