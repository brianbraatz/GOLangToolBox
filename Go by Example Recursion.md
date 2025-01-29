---
Description: Go by Example: Recursion
Notes: Go supports
recursive functions.
Here’s a classic example.
author: 
Url: https://gobyexample.com/recursion
Created: "2025-01-29  02:42:50"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Recursion

source: https://gobyexample.com/recursion

> ## Excerpt
> Go supports
recursive functions.
Here’s a classic example.

---
<table><tbody><tr><td><p>Go supports <a href="https://en.wikipedia.org/wiki/Recursion_(computer_science)"><em>recursive functions</em></a>. Here’s a classic example.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/k4IRATLn9cE"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>"fmt"</span></span></span></code></pre></td></tr><tr><td><p>This <code>fact</code> function calls itself until it reaches the base case of <code>fact(0)</code>.</p></td><td><pre><code><span><span><span>func</span> <span>fact</span><span>(</span><span>n</span> <span>int</span><span>)</span> <span>int</span> <span>{</span>
</span></span><span><span>    <span>if</span> <span>n</span> <span>==</span> <span>0</span> <span>{</span>
</span></span><span><span>        <span>return</span> <span>1</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span>    <span>return</span> <span>n</span> <span>*</span> <span>fact</span><span>(</span><span>n</span><span>-</span><span>1</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>fact</span><span>(</span><span>7</span><span>))</span></span></span></code></pre></td></tr><tr><td><p>Anonymous functions can also be recursive, but this requires explicitly declaring a variable with <code>var</code> to store the function before it’s defined.</p></td><td><pre><code><span><span>    <span>var</span> <span>fib</span> <span>func</span><span>(</span><span>n</span> <span>int</span><span>)</span> <span>int</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span>    <span>fib</span> <span>=</span> <span>func</span><span>(</span><span>n</span> <span>int</span><span>)</span> <span>int</span> <span>{</span>
</span></span><span><span>        <span>if</span> <span>n</span> <span>&lt;</span> <span>2</span> <span>{</span>
</span></span><span><span>            <span>return</span> <span>n</span>
</span></span><span><span>        <span>}</span></span></span></code></pre></td></tr><tr><td><p>Since <code>fib</code> was previously declared in <code>main</code>, Go knows which function to call with <code>fib</code> here.</p></td><td><pre><code><span><span>        <span>return</span> <span>fib</span><span>(</span><span>n</span><span>-</span><span>1</span><span>)</span> <span>+</span> <span>fib</span><span>(</span><span>n</span><span>-</span><span>2</span><span>)</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>fib</span><span>(</span><span>7</span><span>))</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go run recursion.go 
</span></span><span><span><span>5040
</span></span></span><span><span><span>13</span></span></span></code></pre></td></tr></tbody></table>

Next example: [Range over Built-in Types](https://gobyexample.com/range-over-built-in-types).
