---
Description: Go by Example: If/Else
Notes: Branching with if and else in Go is
straight-forward.
author: 
Url: https://gobyexample.com/if-else
Created: "2025-01-29  02:42:11"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: If/Else

source: https://gobyexample.com/if-else

> ## Excerpt
> Branching with if and else in Go is
straight-forward.

---
<table><tbody><tr><td><p>Branching with <code>if</code> and <code>else</code> in Go is straight-forward.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/RKgKzCe7qcF"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>"fmt"</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>Here’s a basic example.</p></td><td><pre><code><span><span>    <span>if</span> <span>7</span><span>%</span><span>2</span> <span>==</span> <span>0</span> <span>{</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"7 is even"</span><span>)</span>
</span></span><span><span>    <span>}</span> <span>else</span> <span>{</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"7 is odd"</span><span>)</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td><p>You can have an <code>if</code> statement without an else.</p></td><td><pre><code><span><span>    <span>if</span> <span>8</span><span>%</span><span>4</span> <span>==</span> <span>0</span> <span>{</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"8 is divisible by 4"</span><span>)</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td><p>Logical operators like <code>&amp;&amp;</code> and <code>||</code> are often useful in conditions.</p></td><td><pre><code><span><span>    <span>if</span> <span>8</span><span>%</span><span>2</span> <span>==</span> <span>0</span> <span>||</span> <span>7</span><span>%</span><span>2</span> <span>==</span> <span>0</span> <span>{</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"either 8 or 7 are even"</span><span>)</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td><p>A statement can precede conditionals; any variables declared in this statement are available in the current and all subsequent branches.</p></td><td><pre><code><span><span>    <span>if</span> <span>num</span> <span>:=</span> <span>9</span><span>;</span> <span>num</span> <span>&lt;</span> <span>0</span> <span>{</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>num</span><span>,</span> <span>"is negative"</span><span>)</span>
</span></span><span><span>    <span>}</span> <span>else</span> <span>if</span> <span>num</span> <span>&lt;</span> <span>10</span> <span>{</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>num</span><span>,</span> <span>"has 1 digit"</span><span>)</span>
</span></span><span><span>    <span>}</span> <span>else</span> <span>{</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>num</span><span>,</span> <span>"has multiple digits"</span><span>)</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td><p>Note that you don’t need parentheses around conditions in Go, but that the braces are required.</p></td><td></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go run if-else.go
</span></span><span><span><span>7 is odd
</span></span></span><span><span><span>8 is divisible by 4
</span></span></span><span><span><span>either 8 or 7 are even
</span></span></span><span><span><span>9 has 1 digit</span></span></span></code></pre></td></tr><tr><td><p>There is no <a href="https://en.wikipedia.org/wiki/%3F:">ternary if</a> in Go, so you’ll need to use a full <code>if</code> statement even for basic conditions.</p></td><td></td></tr></tbody></table>

Next example: [Switch](https://gobyexample.com/switch).
