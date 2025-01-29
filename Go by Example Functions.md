---
Description: Go by Example: Functions
Notes: Functions are central in Go. We’ll learn about
functions with a few different examples.
author: 
Url: https://gobyexample.com/functions
Created: "2025-01-29  02:42:27"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Functions

source: https://gobyexample.com/functions

> ## Excerpt
> Functions are central in Go. We’ll learn about
functions with a few different examples.

---
<table><tbody><tr><td><p><em>Functions</em> are central in Go. We’ll learn about functions with a few different examples.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/-o49-dQfGbK"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>"fmt"</span></span></span></code></pre></td></tr><tr><td><p>Here’s a function that takes two <code>int</code>s and returns their sum as an <code>int</code>.</p></td><td><pre><code><span><span><span>func</span> <span>plus</span><span>(</span><span>a</span> <span>int</span><span>,</span> <span>b</span> <span>int</span><span>)</span> <span>int</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>Go requires explicit returns, i.e. it won’t automatically return the value of the last expression.</p></td><td><pre><code><span><span>    <span>return</span> <span>a</span> <span>+</span> <span>b</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td><p>When you have multiple consecutive parameters of the same type, you may omit the type name for the like-typed parameters up to the final parameter that declares the type.</p></td><td><pre><code><span><span><span>func</span> <span>plusPlus</span><span>(</span><span>a</span><span>,</span> <span>b</span><span>,</span> <span>c</span> <span>int</span><span>)</span> <span>int</span> <span>{</span>
</span></span><span><span>    <span>return</span> <span>a</span> <span>+</span> <span>b</span> <span>+</span> <span>c</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>Call a function just as you’d expect, with <code>name(args)</code>.</p></td><td><pre><code><span><span>    <span>res</span> <span>:=</span> <span>plus</span><span>(</span><span>1</span><span>,</span> <span>2</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"1+2 ="</span><span>,</span> <span>res</span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span>    <span>res</span> <span>=</span> <span>plusPlus</span><span>(</span><span>1</span><span>,</span> <span>2</span><span>,</span> <span>3</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"1+2+3 ="</span><span>,</span> <span>res</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go run functions.go 
</span></span><span><span><span>1+2 = 3
</span></span></span><span><span><span>1+2+3 = 6</span></span></span></code></pre></td></tr><tr><td><p>There are several other features to Go functions. One is multiple return values, which we’ll look at next.</p></td><td></td></tr></tbody></table>

Next example: [Multiple Return Values](https://gobyexample.com/multiple-return-values).
