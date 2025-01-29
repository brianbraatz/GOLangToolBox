---
Description: Go by Example: Random Numbers
Notes: Go’s math/rand/v2 package provides
pseudorandom number
generation.
author: 
Url: https://gobyexample.com/random-numbers
Created: "2025-01-29  02:47:41"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Random Numbers

source: https://gobyexample.com/random-numbers

> ## Excerpt
> Go’s math/rand/v2 package provides
pseudorandom number
generation.

---
<table><tbody><tr><td><p>Go’s <code>math/rand/v2</code> package provides <a href="https://en.wikipedia.org/wiki/Pseudorandom_number_generator">pseudorandom number</a> generation.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/TkgmNAl8euK"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"math/rand/v2"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>For example, <code>rand.IntN</code> returns a random <code>int</code> n, <code>0 &lt;= n &lt; 100</code>.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Print</span><span>(</span><span>rand</span><span>.</span><span>IntN</span><span>(</span><span>100</span><span>),</span> <span>","</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Print</span><span>(</span><span>rand</span><span>.</span><span>IntN</span><span>(</span><span>100</span><span>))</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>()</span></span></span></code></pre></td></tr><tr><td><p><code>rand.Float64</code> returns a <code>float64</code> <code>f</code>, <code>0.0 &lt;= f &lt; 1.0</code>.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>rand</span><span>.</span><span>Float64</span><span>())</span></span></span></code></pre></td></tr><tr><td><p>This can be used to generate random floats in other ranges, for example <code>5.0 &lt;= f' &lt; 10.0</code>.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Print</span><span>((</span><span>rand</span><span>.</span><span>Float64</span><span>()</span><span>*</span><span>5</span><span>)</span><span>+</span><span>5</span><span>,</span> <span>","</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Print</span><span>((</span><span>rand</span><span>.</span><span>Float64</span><span>()</span> <span>*</span> <span>5</span><span>)</span> <span>+</span> <span>5</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>()</span></span></span></code></pre></td></tr><tr><td><p>If you want a known seed, create a new <code>rand.Source</code> and pass it into the <code>New</code> constructor. <code>NewPCG</code> creates a new <a href="https://en.wikipedia.org/wiki/Permuted_congruential_generator">PCG</a> source that requires a seed of two <code>uint64</code> numbers.</p></td><td><pre><code><span><span>    <span>s2</span> <span>:=</span> <span>rand</span><span>.</span><span>NewPCG</span><span>(</span><span>42</span><span>,</span> <span>1024</span><span>)</span>
</span></span><span><span>    <span>r2</span> <span>:=</span> <span>rand</span><span>.</span><span>New</span><span>(</span><span>s2</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Print</span><span>(</span><span>r2</span><span>.</span><span>IntN</span><span>(</span><span>100</span><span>),</span> <span>","</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Print</span><span>(</span><span>r2</span><span>.</span><span>IntN</span><span>(</span><span>100</span><span>))</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>()</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span>    <span>s3</span> <span>:=</span> <span>rand</span><span>.</span><span>NewPCG</span><span>(</span><span>42</span><span>,</span> <span>1024</span><span>)</span>
</span></span><span><span>    <span>r3</span> <span>:=</span> <span>rand</span><span>.</span><span>New</span><span>(</span><span>s3</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Print</span><span>(</span><span>r3</span><span>.</span><span>IntN</span><span>(</span><span>100</span><span>),</span> <span>","</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Print</span><span>(</span><span>r3</span><span>.</span><span>IntN</span><span>(</span><span>100</span><span>))</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>()</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td><p>Some of the generated numbers may be different when you run the sample.</p></td><td><pre><code><span><span><span>$</span> go run random-numbers.go
</span></span><span><span><span>68,56
</span></span></span><span><span><span>0.8090228139659177
</span></span></span><span><span><span>5.840125017402497,6.937056298890035
</span></span></span><span><span><span>94,49
</span></span></span><span><span><span>94,49</span></span></span></code></pre></td></tr><tr><td><p>See the <a href="https://pkg.go.dev/math/rand/v2"><code>math/rand/v2</code></a> package docs for references on other random quantities that Go can provide.</p></td><td></td></tr></tbody></table>

Next example: [Number Parsing](https://gobyexample.com/number-parsing).
