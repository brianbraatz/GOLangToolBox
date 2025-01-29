---
Description: Go by Example: Variables
Notes: In Go, variables are explicitly declared and used by
the compiler to e.g. check type-correctness of function
calls.
author: 
Url: https://gobyexample.com/variables
Created: "2025-01-29  02:42:00"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Variables

source: https://gobyexample.com/variables

> ## Excerpt
> In Go, variables are explicitly declared and used by
the compiler to e.g. check type-correctness of function
calls.

---
<table><tbody><tr><td><p>In Go, <em>variables</em> are explicitly declared and used by the compiler to e.g. check type-correctness of function calls.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/N5rWndIliJW"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>"fmt"</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p><code>var</code> declares 1 or more variables.</p></td><td><pre><code><span><span>    <span>var</span> <span>a</span> <span>=</span> <span>"initial"</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>a</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>You can declare multiple variables at once.</p></td><td><pre><code><span><span>    <span>var</span> <span>b</span><span>,</span> <span>c</span> <span>int</span> <span>=</span> <span>1</span><span>,</span> <span>2</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>b</span><span>,</span> <span>c</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Go will infer the type of initialized variables.</p></td><td><pre><code><span><span>    <span>var</span> <span>d</span> <span>=</span> <span>true</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>d</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Variables declared without a corresponding initialization are <em>zero-valued</em>. For example, the zero value for an <code>int</code> is <code>0</code>.</p></td><td><pre><code><span><span>    <span>var</span> <span>e</span> <span>int</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>e</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>The <code>:=</code> syntax is shorthand for declaring and initializing a variable, e.g. for <code>var f string = "apple"</code> in this case. This syntax is only available inside functions.</p></td><td><pre><code><span><span>    <span>f</span> <span>:=</span> <span>"apple"</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>f</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go run variables.go
</span></span><span><span><span>initial
</span></span></span><span><span><span>1 2
</span></span></span><span><span><span>true
</span></span></span><span><span><span>0
</span></span></span><span><span><span>apple</span></span></span></code></pre></td></tr></tbody></table>

Next example: [Constants](https://gobyexample.com/constants).
