---
Description: Go by Example: Methods
Notes: Go supports methods defined on struct types.
author: 
Url: https://gobyexample.com/methods
Created: "2025-01-29  02:44:16"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Methods

source: https://gobyexample.com/methods

> ## Excerpt
> Go supports methods defined on struct types.

---
<table><tbody><tr><td><p>Go supports <em>methods</em> defined on struct types.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/4wmDCAydC1e"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>"fmt"</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>type</span> <span>rect</span> <span>struct</span> <span>{</span>
</span></span><span><span>    <span>width</span><span>,</span> <span>height</span> <span>int</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td><p>This <code>area</code> method has a <em>receiver type</em> of <code>*rect</code>.</p></td><td><pre><code><span><span><span>func</span> <span>(</span><span>r</span> <span>*</span><span>rect</span><span>)</span> <span>area</span><span>()</span> <span>int</span> <span>{</span>
</span></span><span><span>    <span>return</span> <span>r</span><span>.</span><span>width</span> <span>*</span> <span>r</span><span>.</span><span>height</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td><p>Methods can be defined for either pointer or value receiver types. Here’s an example of a value receiver.</p></td><td><pre><code><span><span><span>func</span> <span>(</span><span>r</span> <span>rect</span><span>)</span> <span>perim</span><span>()</span> <span>int</span> <span>{</span>
</span></span><span><span>    <span>return</span> <span>2</span><span>*</span><span>r</span><span>.</span><span>width</span> <span>+</span> <span>2</span><span>*</span><span>r</span><span>.</span><span>height</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span>
</span></span><span><span>    <span>r</span> <span>:=</span> <span>rect</span><span>{</span><span>width</span><span>:</span> <span>10</span><span>,</span> <span>height</span><span>:</span> <span>5</span><span>}</span></span></span></code></pre></td></tr><tr><td><p>Here we call the 2 methods defined for our struct.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"area: "</span><span>,</span> <span>r</span><span>.</span><span>area</span><span>())</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"perim:"</span><span>,</span> <span>r</span><span>.</span><span>perim</span><span>())</span></span></span></code></pre></td></tr><tr><td><p>Go automatically handles conversion between values and pointers for method calls. You may want to use a pointer receiver type to avoid copying on method calls or to allow the method to mutate the receiving struct.</p></td><td><pre><code><span><span>    <span>rp</span> <span>:=</span> <span>&amp;</span><span>r</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"area: "</span><span>,</span> <span>rp</span><span>.</span><span>area</span><span>())</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"perim:"</span><span>,</span> <span>rp</span><span>.</span><span>perim</span><span>())</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go run methods.go 
</span></span><span><span><span>area:  50
</span></span></span><span><span><span>perim: 30
</span></span></span><span><span><span>area:  50
</span></span></span><span><span><span>perim: 30</span></span></span></code></pre></td></tr><tr><td><p>Next we’ll look at Go’s mechanism for grouping and naming related sets of methods: interfaces.</p></td><td></td></tr></tbody></table>

Next example: [Interfaces](https://gobyexample.com/interfaces).
