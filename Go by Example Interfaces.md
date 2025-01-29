---
Description: Go by Example: Interfaces
Notes: Interfaces are named collections of method
signatures.
author: 
Url: https://gobyexample.com/interfaces
Created: "2025-01-29  02:44:20"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Interfaces

source: https://gobyexample.com/interfaces

> ## Excerpt
> Interfaces are named collections of method
signatures.

---
<table><tbody><tr><td><p><em>Interfaces</em> are named collections of method signatures.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/xAAbgd7GOKD"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"math"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Here’s a basic interface for geometric shapes.</p></td><td><pre><code><span><span><span>type</span> <span>geometry</span> <span>interface</span> <span>{</span>
</span></span><span><span>    <span>area</span><span>()</span> <span>float64</span>
</span></span><span><span>    <span>perim</span><span>()</span> <span>float64</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td><p>For our example we’ll implement this interface on <code>rect</code> and <code>circle</code> types.</p></td><td><pre><code><span><span><span>type</span> <span>rect</span> <span>struct</span> <span>{</span>
</span></span><span><span>    <span>width</span><span>,</span> <span>height</span> <span>float64</span>
</span></span><span><span><span>}</span>
</span></span><span><span><span>type</span> <span>circle</span> <span>struct</span> <span>{</span>
</span></span><span><span>    <span>radius</span> <span>float64</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td><p>To implement an interface in Go, we just need to implement all the methods in the interface. Here we implement <code>geometry</code> on <code>rect</code>s.</p></td><td><pre><code><span><span><span>func</span> <span>(</span><span>r</span> <span>rect</span><span>)</span> <span>area</span><span>()</span> <span>float64</span> <span>{</span>
</span></span><span><span>    <span>return</span> <span>r</span><span>.</span><span>width</span> <span>*</span> <span>r</span><span>.</span><span>height</span>
</span></span><span><span><span>}</span>
</span></span><span><span><span>func</span> <span>(</span><span>r</span> <span>rect</span><span>)</span> <span>perim</span><span>()</span> <span>float64</span> <span>{</span>
</span></span><span><span>    <span>return</span> <span>2</span><span>*</span><span>r</span><span>.</span><span>width</span> <span>+</span> <span>2</span><span>*</span><span>r</span><span>.</span><span>height</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td><p>The implementation for <code>circle</code>s.</p></td><td><pre><code><span><span><span>func</span> <span>(</span><span>c</span> <span>circle</span><span>)</span> <span>area</span><span>()</span> <span>float64</span> <span>{</span>
</span></span><span><span>    <span>return</span> <span>math</span><span>.</span><span>Pi</span> <span>*</span> <span>c</span><span>.</span><span>radius</span> <span>*</span> <span>c</span><span>.</span><span>radius</span>
</span></span><span><span><span>}</span>
</span></span><span><span><span>func</span> <span>(</span><span>c</span> <span>circle</span><span>)</span> <span>perim</span><span>()</span> <span>float64</span> <span>{</span>
</span></span><span><span>    <span>return</span> <span>2</span> <span>*</span> <span>math</span><span>.</span><span>Pi</span> <span>*</span> <span>c</span><span>.</span><span>radius</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td><p>If a variable has an interface type, then we can call methods that are in the named interface. Here’s a generic <code>measure</code> function taking advantage of this to work on any <code>geometry</code>.</p></td><td><pre><code><span><span><span>func</span> <span>measure</span><span>(</span><span>g</span> <span>geometry</span><span>)</span> <span>{</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>g</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>g</span><span>.</span><span>area</span><span>())</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>g</span><span>.</span><span>perim</span><span>())</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td><p>Sometimes it’s useful to know the runtime type of an interface value. One option is using a <em>type assertion</em> as shown here; another is a <a href="https://gobyexample.com/switch">type <code>switch</code></a>.</p></td><td><pre><code><span><span><span>func</span> <span>detectCircle</span><span>(</span><span>g</span> <span>geometry</span><span>)</span> <span>{</span>
</span></span><span><span>    <span>if</span> <span>c</span><span>,</span> <span>ok</span> <span>:=</span> <span>g</span><span>.(</span><span>circle</span><span>);</span> <span>ok</span> <span>{</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"circle with radius"</span><span>,</span> <span>c</span><span>.</span><span>radius</span><span>)</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span>
</span></span><span><span>    <span>r</span> <span>:=</span> <span>rect</span><span>{</span><span>width</span><span>:</span> <span>3</span><span>,</span> <span>height</span><span>:</span> <span>4</span><span>}</span>
</span></span><span><span>    <span>c</span> <span>:=</span> <span>circle</span><span>{</span><span>radius</span><span>:</span> <span>5</span><span>}</span></span></span></code></pre></td></tr><tr><td><p>The <code>circle</code> and <code>rect</code> struct types both implement the <code>geometry</code> interface so we can use instances of these structs as arguments to <code>measure</code>.</p></td><td><pre><code><span><span>    <span>measure</span><span>(</span><span>r</span><span>)</span>
</span></span><span><span>    <span>measure</span><span>(</span><span>c</span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span>    <span>detectCircle</span><span>(</span><span>r</span><span>)</span>
</span></span><span><span>    <span>detectCircle</span><span>(</span><span>c</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go run interfaces.go
</span></span><span><span><span>{3 4}
</span></span></span><span><span><span>12
</span></span></span><span><span><span>14
</span></span></span><span><span><span>{5}
</span></span></span><span><span><span>78.53981633974483
</span></span></span><span><span><span>31.41592653589793
</span></span></span><span><span><span>circle with radius 5</span></span></span></code></pre></td></tr><tr><td><p>To understand how Go’s interfaces work under the hood, check out this <a href="https://research.swtch.com/interfaces">blog post</a>.</p></td><td></td></tr></tbody></table>

Next example: [Enums](https://gobyexample.com/enums).
