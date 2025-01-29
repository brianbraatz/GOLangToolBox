---
Description: Go by Example: Closures
Notes: Go supports anonymous functions,
which can form closures.
Anonymous functions are useful when you want to define
a function inline without having to name it.
author: 
Url: https://gobyexample.com/closures
Created: "2025-01-29  02:42:46"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Closures

source: https://gobyexample.com/closures

> ## Excerpt
> Go supports anonymous functions,
which can form closures.
Anonymous functions are useful when you want to define
a function inline without having to name it.

---
<table><tbody><tr><td><p>Go supports <a href="https://en.wikipedia.org/wiki/Anonymous_function"><em>anonymous functions</em></a>, which can form <a href="https://en.wikipedia.org/wiki/Closure_(computer_science)"><em>closures</em></a>. Anonymous functions are useful when you want to define a function inline without having to name it.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/NpgpzS8ZG8y"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>"fmt"</span></span></span></code></pre></td></tr><tr><td><p>This function <code>intSeq</code> returns another function, which we define anonymously in the body of <code>intSeq</code>. The returned function <em>closes over</em> the variable <code>i</code> to form a closure.</p></td><td><pre><code><span><span><span>func</span> <span>intSeq</span><span>()</span> <span>func</span><span>()</span> <span>int</span> <span>{</span>
</span></span><span><span>    <span>i</span> <span>:=</span> <span>0</span>
</span></span><span><span>    <span>return</span> <span>func</span><span>()</span> <span>int</span> <span>{</span>
</span></span><span><span>        <span>i</span><span>++</span>
</span></span><span><span>        <span>return</span> <span>i</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>We call <code>intSeq</code>, assigning the result (a function) to <code>nextInt</code>. This function value captures its own <code>i</code> value, which will be updated each time we call <code>nextInt</code>.</p></td><td><pre><code><span><span>    <span>nextInt</span> <span>:=</span> <span>intSeq</span><span>()</span></span></span></code></pre></td></tr><tr><td><p>See the effect of the closure by calling <code>nextInt</code> a few times.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>nextInt</span><span>())</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>nextInt</span><span>())</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>nextInt</span><span>())</span></span></span></code></pre></td></tr><tr><td><p>To confirm that the state is unique to that particular function, create and test a new one.</p></td><td><pre><code><span><span>    <span>newInts</span> <span>:=</span> <span>intSeq</span><span>()</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>newInts</span><span>())</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go run closures.go
</span></span><span><span><span>1
</span></span></span><span><span><span>2
</span></span></span><span><span><span>3
</span></span></span><span><span><span>1</span></span></span></code></pre></td></tr><tr><td><p>The last feature of functions we’ll look at for now is recursion.</p></td><td></td></tr></tbody></table>

Next example: [Recursion](https://gobyexample.com/recursion).
