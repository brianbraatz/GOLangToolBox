---
Description: Go by Example: Non-Blocking Channel Operations
Notes: Basic sends and receives on channels are blocking.
However, we can use select with a default clause to
implement non-blocking sends, receives, and even
non-blocking multi-way selects.
author: 
Url: https://gobyexample.com/non-blocking-channel-operations
Created: "2025-01-29  02:45:05"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Non-Blocking Channel Operations

source: https://gobyexample.com/non-blocking-channel-operations

> ## Excerpt
> Basic sends and receives on channels are blocking.
However, we can use select with a default clause to
implement non-blocking sends, receives, and even
non-blocking multi-way selects.

---
<table><tbody><tr><td><p>Basic sends and receives on channels are blocking. However, we can use <code>select</code> with a <code>default</code> clause to implement <em>non-blocking</em> sends, receives, and even non-blocking multi-way <code>select</code>s.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/TFv6-7OVNVq"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>"fmt"</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span>
</span></span><span><span>    <span>messages</span> <span>:=</span> <span>make</span><span>(</span><span>chan</span> <span>string</span><span>)</span>
</span></span><span><span>    <span>signals</span> <span>:=</span> <span>make</span><span>(</span><span>chan</span> <span>bool</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Here’s a non-blocking receive. If a value is available on <code>messages</code> then <code>select</code> will take the <code>&lt;-messages</code> <code>case</code> with that value. If not it will immediately take the <code>default</code> case.</p></td><td><pre><code><span><span>    <span>select</span> <span>{</span>
</span></span><span><span>    <span>case</span> <span>msg</span> <span>:=</span> <span>&lt;-</span><span>messages</span><span>:</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"received message"</span><span>,</span> <span>msg</span><span>)</span>
</span></span><span><span>    <span>default</span><span>:</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"no message received"</span><span>)</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td><p>A non-blocking send works similarly. Here <code>msg</code> cannot be sent to the <code>messages</code> channel, because the channel has no buffer and there is no receiver. Therefore the <code>default</code> case is selected.</p></td><td><pre><code><span><span>    <span>msg</span> <span>:=</span> <span>"hi"</span>
</span></span><span><span>    <span>select</span> <span>{</span>
</span></span><span><span>    <span>case</span> <span>messages</span> <span>&lt;-</span> <span>msg</span><span>:</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"sent message"</span><span>,</span> <span>msg</span><span>)</span>
</span></span><span><span>    <span>default</span><span>:</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"no message sent"</span><span>)</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td><p>We can use multiple <code>case</code>s above the <code>default</code> clause to implement a multi-way non-blocking select. Here we attempt non-blocking receives on both <code>messages</code> and <code>signals</code>.</p></td><td><pre><code><span><span>    <span>select</span> <span>{</span>
</span></span><span><span>    <span>case</span> <span>msg</span> <span>:=</span> <span>&lt;-</span><span>messages</span><span>:</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"received message"</span><span>,</span> <span>msg</span><span>)</span>
</span></span><span><span>    <span>case</span> <span>sig</span> <span>:=</span> <span>&lt;-</span><span>signals</span><span>:</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"received signal"</span><span>,</span> <span>sig</span><span>)</span>
</span></span><span><span>    <span>default</span><span>:</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"no activity"</span><span>)</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go run non-blocking-channel-operations.go 
</span></span><span><span><span>no message received
</span></span></span><span><span><span>no message sent
</span></span></span><span><span><span>no activity</span></span></span></code></pre></td></tr></tbody></table>

Next example: [Closing Channels](https://gobyexample.com/closing-channels).
