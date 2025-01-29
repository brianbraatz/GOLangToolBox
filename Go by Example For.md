---
Description: Go by Example: For
Notes: for is Go’s only looping construct. Here are
some basic types of for loops.
author: 
Url: https://gobyexample.com/for
Created: "2025-01-29  02:42:08"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: For

source: https://gobyexample.com/for

> ## Excerpt
> for is Go’s only looping construct. Here are
some basic types of for loops.

---
<table><tbody><tr><td><p><code>for</code> is Go’s only looping construct. Here are some basic types of <code>for</code> loops.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/_F2rYHNilKa"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>"fmt"</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>The most basic type, with a single condition.</p></td><td><pre><code><span><span>    <span>i</span> <span>:=</span> <span>1</span>
</span></span><span><span>    <span>for</span> <span>i</span> <span>&lt;=</span> <span>3</span> <span>{</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>i</span><span>)</span>
</span></span><span><span>        <span>i</span> <span>=</span> <span>i</span> <span>+</span> <span>1</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td><p>A classic initial/condition/after <code>for</code> loop.</p></td><td><pre><code><span><span>    <span>for</span> <span>j</span> <span>:=</span> <span>0</span><span>;</span> <span>j</span> <span>&lt;</span> <span>3</span><span>;</span> <span>j</span><span>++</span> <span>{</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>j</span><span>)</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td><p>Another way of accomplishing the basic “do this N times” iteration is <code>range</code> over an integer.</p></td><td><pre><code><span><span>    <span>for</span> <span>i</span> <span>:=</span> <span>range</span> <span>3</span> <span>{</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"range"</span><span>,</span> <span>i</span><span>)</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td><p><code>for</code> without a condition will loop repeatedly until you <code>break</code> out of the loop or <code>return</code> from the enclosing function.</p></td><td><pre><code><span><span>    <span>for</span> <span>{</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"loop"</span><span>)</span>
</span></span><span><span>        <span>break</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td><p>You can also <code>continue</code> to the next iteration of the loop.</p></td><td><pre><code><span><span>    <span>for</span> <span>n</span> <span>:=</span> <span>range</span> <span>6</span> <span>{</span>
</span></span><span><span>        <span>if</span> <span>n</span><span>%</span><span>2</span> <span>==</span> <span>0</span> <span>{</span>
</span></span><span><span>            <span>continue</span>
</span></span><span><span>        <span>}</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>n</span><span>)</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go run for.go
</span></span><span><span><span>1
</span></span></span><span><span><span>2
</span></span></span><span><span><span>3
</span></span></span><span><span><span>0
</span></span></span><span><span><span>1
</span></span></span><span><span><span>2
</span></span></span><span><span><span>range 0
</span></span></span><span><span><span>range 1
</span></span></span><span><span><span>range 2
</span></span></span><span><span><span>loop
</span></span></span><span><span><span>1
</span></span></span><span><span><span>3
</span></span></span><span><span><span>5</span></span></span></code></pre></td></tr><tr><td><p>We’ll see some other <code>for</code> forms later when we look at <code>range</code> statements, channels, and other data structures.</p></td><td></td></tr></tbody></table>

Next example: [If/Else](https://gobyexample.com/if-else).
