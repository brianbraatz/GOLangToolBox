---
Description: Go by Example: Constants
Notes: Go supports constants of character, string, boolean,
and numeric values.
author: 
Url: https://gobyexample.com/constants
Created: "2025-01-29  02:42:04"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Constants

source: https://gobyexample.com/constants

> ## Excerpt
> Go supports constants of character, string, boolean,
and numeric values.

---
<table><tbody><tr><td><p>Go supports <em>constants</em> of character, string, boolean, and numeric values.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/Vw-pXSfo9_b"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"math"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td><p><code>const</code> declares a constant value.</p></td><td><pre><code><span><span><span>const</span> <span>s</span> <span>string</span> <span>=</span> <span>"constant"</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>s</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>A <code>const</code> statement can appear anywhere a <code>var</code> statement can.</p></td><td><pre><code><span><span>    <span>const</span> <span>n</span> <span>=</span> <span>500000000</span></span></span></code></pre></td></tr><tr><td><p>Constant expressions perform arithmetic with arbitrary precision.</p></td><td><pre><code><span><span>    <span>const</span> <span>d</span> <span>=</span> <span>3e20</span> <span>/</span> <span>n</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>d</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>A numeric constant has no type until it’s given one, such as by an explicit conversion.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>int64</span><span>(</span><span>d</span><span>))</span></span></span></code></pre></td></tr><tr><td><p>A number can be given a type by using it in a context that requires one, such as a variable assignment or function call. For example, here <code>math.Sin</code> expects a <code>float64</code>.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>math</span><span>.</span><span>Sin</span><span>(</span><span>n</span><span>))</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go run constant.go 
</span></span><span><span><span>constant
</span></span></span><span><span><span>6e+11
</span></span></span><span><span><span>600000000000
</span></span></span><span><span><span>-0.28470407323754404</span></span></span></code></pre></td></tr></tbody></table>

Next example: [For](https://gobyexample.com/for).
