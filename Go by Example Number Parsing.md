---
Description: Go by Example: Number Parsing
Notes: Parsing numbers from strings is a basic but common task
in many programs; here’s how to do it in Go.
author: 
Url: https://gobyexample.com/number-parsing
Created: "2025-01-29  02:47:43"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Number Parsing

source: https://gobyexample.com/number-parsing

> ## Excerpt
> Parsing numbers from strings is a basic but common task
in many programs; here’s how to do it in Go.

---
<table><tbody><tr><td><p>Parsing numbers from strings is a basic but common task in many programs; here’s how to do it in Go.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/ZAMEid6Fpmu"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td><p>The built-in package <code>strconv</code> provides the number parsing.</p></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"strconv"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>With <code>ParseFloat</code>, this <code>64</code> tells how many bits of precision to parse.</p></td><td><pre><code><span><span>    <span>f</span><span>,</span> <span>_</span> <span>:=</span> <span>strconv</span><span>.</span><span>ParseFloat</span><span>(</span><span>"1.234"</span><span>,</span> <span>64</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>f</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>For <code>ParseInt</code>, the <code>0</code> means infer the base from the string. <code>64</code> requires that the result fit in 64 bits.</p></td><td><pre><code><span><span>    <span>i</span><span>,</span> <span>_</span> <span>:=</span> <span>strconv</span><span>.</span><span>ParseInt</span><span>(</span><span>"123"</span><span>,</span> <span>0</span><span>,</span> <span>64</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>i</span><span>)</span></span></span></code></pre></td></tr><tr><td><p><code>ParseInt</code> will recognize hex-formatted numbers.</p></td><td><pre><code><span><span>    <span>d</span><span>,</span> <span>_</span> <span>:=</span> <span>strconv</span><span>.</span><span>ParseInt</span><span>(</span><span>"0x1c8"</span><span>,</span> <span>0</span><span>,</span> <span>64</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>d</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>A <code>ParseUint</code> is also available.</p></td><td><pre><code><span><span>    <span>u</span><span>,</span> <span>_</span> <span>:=</span> <span>strconv</span><span>.</span><span>ParseUint</span><span>(</span><span>"789"</span><span>,</span> <span>0</span><span>,</span> <span>64</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>u</span><span>)</span></span></span></code></pre></td></tr><tr><td><p><code>Atoi</code> is a convenience function for basic base-10 <code>int</code> parsing.</p></td><td><pre><code><span><span>    <span>k</span><span>,</span> <span>_</span> <span>:=</span> <span>strconv</span><span>.</span><span>Atoi</span><span>(</span><span>"135"</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>k</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Parse functions return an error on bad input.</p></td><td><pre><code><span><span>    <span>_</span><span>,</span> <span>e</span> <span>:=</span> <span>strconv</span><span>.</span><span>Atoi</span><span>(</span><span>"wat"</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>e</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go run number-parsing.go 
</span></span><span><span><span>1.234
</span></span></span><span><span><span>123
</span></span></span><span><span><span>456
</span></span></span><span><span><span>789
</span></span></span><span><span><span>135
</span></span></span><span><span><span>strconv.ParseInt: parsing "wat": invalid syntax</span></span></span></code></pre></td></tr><tr><td><p>Next we’ll look at another common parsing task: URLs.</p></td><td></td></tr></tbody></table>

Next example: [URL Parsing](https://gobyexample.com/url-parsing).
