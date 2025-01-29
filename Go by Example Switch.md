---
Description: Go by Example: Switch
Notes: Switch statements express conditionals across many
branches.
author: 
Url: https://gobyexample.com/switch
Created: "2025-01-29  02:42:14"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Switch

source: https://gobyexample.com/switch

> ## Excerpt
> Switch statements express conditionals across many
branches.

---
<table><tbody><tr><td><p><em>Switch statements</em> express conditionals across many branches.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/qVDqWoUQ6AI"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"time"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>Here’s a basic <code>switch</code>.</p></td><td><pre><code><span><span>    <span>i</span> <span>:=</span> <span>2</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Print</span><span>(</span><span>"Write "</span><span>,</span> <span>i</span><span>,</span> <span>" as "</span><span>)</span>
</span></span><span><span>    <span>switch</span> <span>i</span> <span>{</span>
</span></span><span><span>    <span>case</span> <span>1</span><span>:</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"one"</span><span>)</span>
</span></span><span><span>    <span>case</span> <span>2</span><span>:</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"two"</span><span>)</span>
</span></span><span><span>    <span>case</span> <span>3</span><span>:</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"three"</span><span>)</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td><p>You can use commas to separate multiple expressions in the same <code>case</code> statement. We use the optional <code>default</code> case in this example as well.</p></td><td><pre><code><span><span>    <span>switch</span> <span>time</span><span>.</span><span>Now</span><span>().</span><span>Weekday</span><span>()</span> <span>{</span>
</span></span><span><span>    <span>case</span> <span>time</span><span>.</span><span>Saturday</span><span>,</span> <span>time</span><span>.</span><span>Sunday</span><span>:</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"It's the weekend"</span><span>)</span>
</span></span><span><span>    <span>default</span><span>:</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"It's a weekday"</span><span>)</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td><p><code>switch</code> without an expression is an alternate way to express if/else logic. Here we also show how the <code>case</code> expressions can be non-constants.</p></td><td><pre><code><span><span>    <span>t</span> <span>:=</span> <span>time</span><span>.</span><span>Now</span><span>()</span>
</span></span><span><span>    <span>switch</span> <span>{</span>
</span></span><span><span>    <span>case</span> <span>t</span><span>.</span><span>Hour</span><span>()</span> <span>&lt;</span> <span>12</span><span>:</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"It's before noon"</span><span>)</span>
</span></span><span><span>    <span>default</span><span>:</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"It's after noon"</span><span>)</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td><p>A type <code>switch</code> compares types instead of values. You can use this to discover the type of an interface value. In this example, the variable <code>t</code> will have the type corresponding to its clause.</p></td><td><pre><code><span><span>    <span>whatAmI</span> <span>:=</span> <span>func</span><span>(</span><span>i</span> <span>interface</span><span>{})</span> <span>{</span>
</span></span><span><span>        <span>switch</span> <span>t</span> <span>:=</span> <span>i</span><span>.(</span><span>type</span><span>)</span> <span>{</span>
</span></span><span><span>        <span>case</span> <span>bool</span><span>:</span>
</span></span><span><span>            <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"I'm a bool"</span><span>)</span>
</span></span><span><span>        <span>case</span> <span>int</span><span>:</span>
</span></span><span><span>            <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"I'm an int"</span><span>)</span>
</span></span><span><span>        <span>default</span><span>:</span>
</span></span><span><span>            <span>fmt</span><span>.</span><span>Printf</span><span>(</span><span>"Don't know type %T\n"</span><span>,</span> <span>t</span><span>)</span>
</span></span><span><span>        <span>}</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span>    <span>whatAmI</span><span>(</span><span>true</span><span>)</span>
</span></span><span><span>    <span>whatAmI</span><span>(</span><span>1</span><span>)</span>
</span></span><span><span>    <span>whatAmI</span><span>(</span><span>"hey"</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go run switch.go 
</span></span><span><span><span>Write 2 as two
</span></span></span><span><span><span>It's a weekday
</span></span></span><span><span><span>It's after noon
</span></span></span><span><span><span>I'm a bool
</span></span></span><span><span><span>I'm an int
</span></span></span><span><span><span>Don't know type string</span></span></span></code></pre></td></tr></tbody></table>

Next example: [Arrays](https://gobyexample.com/arrays).
