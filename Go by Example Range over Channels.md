---
Description: Go by Example: Range over Channels
Notes: In a previous example we saw how for and
range provide iteration over basic data structures.
We can also use this syntax to iterate over
values received from a channel.
author: 
Url: https://gobyexample.com/range-over-channels
Created: "2025-01-29  02:45:12"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Range over Channels

source: https://gobyexample.com/range-over-channels

> ## Excerpt
> In a previous example we saw how for and
range provide iteration over basic data structures.
We can also use this syntax to iterate over
values received from a channel.

---
<table><tbody><tr><td><p>In a <a href="https://gobyexample.com/range-over-built-in-types">previous</a> example we saw how <code>for</code> and <code>range</code> provide iteration over basic data structures. We can also use this syntax to iterate over values received from a channel.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/8vAhX6eX1wy"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>"fmt"</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>We’ll iterate over 2 values in the <code>queue</code> channel.</p></td><td><pre><code><span><span>    <span>queue</span> <span>:=</span> <span>make</span><span>(</span><span>chan</span> <span>string</span><span>,</span> <span>2</span><span>)</span>
</span></span><span><span>    <span>queue</span> <span>&lt;-</span> <span>"one"</span>
</span></span><span><span>    <span>queue</span> <span>&lt;-</span> <span>"two"</span>
</span></span><span><span>    <span>close</span><span>(</span><span>queue</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>This <code>range</code> iterates over each element as it’s received from <code>queue</code>. Because we <code>close</code>d the channel above, the iteration terminates after receiving the 2 elements.</p></td><td><pre><code><span><span>    <span>for</span> <span>elem</span> <span>:=</span> <span>range</span> <span>queue</span> <span>{</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>elem</span><span>)</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go run range-over-channels.go
</span></span><span><span><span>one
</span></span></span><span><span><span>two</span></span></span></code></pre></td></tr><tr><td><p>This example also showed that it’s possible to close a non-empty channel but still have the remaining values be received.</p></td><td></td></tr></tbody></table>

Next example: [Timers](https://gobyexample.com/timers).
