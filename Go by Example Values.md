---
Description: Go by Example: Values
Notes: Go has various value types including strings,
integers, floats, booleans, etc. Here are a few
basic examples.
author: 
Url: https://gobyexample.com/values
Created: "2025-01-29  02:41:57"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Values

source: https://gobyexample.com/values

> ## Excerpt
> Go has various value types including strings,
integers, floats, booleans, etc. Here are a few
basic examples.

---
<table><tbody><tr><td><p>Go has various value types including strings, integers, floats, booleans, etc. Here are a few basic examples.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/YnVS3LZr8pk"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>"fmt"</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>Strings, which can be added together with <code>+</code>.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"go"</span> <span>+</span> <span>"lang"</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Integers and floats.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"1+1 ="</span><span>,</span> <span>1</span><span>+</span><span>1</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"7.0/3.0 ="</span><span>,</span> <span>7.0</span><span>/</span><span>3.0</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Booleans, with boolean operators as you’d expect.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>true</span> <span>&amp;&amp;</span> <span>false</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>true</span> <span>||</span> <span>false</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(!</span><span>true</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go run values.go
</span></span><span><span><span>golang
</span></span></span><span><span><span>1+1 = 2
</span></span></span><span><span><span>7.0/3.0 = 2.3333333333333335
</span></span></span><span><span><span>false
</span></span></span><span><span><span>true
</span></span></span><span><span><span>false</span></span></span></code></pre></td></tr></tbody></table>

Next example: [Variables](https://gobyexample.com/variables).
