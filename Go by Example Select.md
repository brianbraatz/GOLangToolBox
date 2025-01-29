---
Description: Go by Example: Select
Notes: Go’s select lets you wait on multiple channel
operations. Combining goroutines and channels with
select is a powerful feature of Go.
author: 
Url: https://gobyexample.com/select
Created: "2025-01-29  02:44:58"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Select

source: https://gobyexample.com/select

> ## Excerpt
> Go’s select lets you wait on multiple channel
operations. Combining goroutines and channels with
select is a powerful feature of Go.

---
<table><tbody><tr><td><p>Go’s <em>select</em> lets you wait on multiple channel operations. Combining goroutines and channels with select is a powerful feature of Go.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/FzONhs4-tae"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"time"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>For our example we’ll select across two channels.</p></td><td><pre><code><span><span>    <span>c1</span> <span>:=</span> <span>make</span><span>(</span><span>chan</span> <span>string</span><span>)</span>
</span></span><span><span>    <span>c2</span> <span>:=</span> <span>make</span><span>(</span><span>chan</span> <span>string</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Each channel will receive a value after some amount of time, to simulate e.g. blocking RPC operations executing in concurrent goroutines.</p></td><td><pre><code><span><span>    <span>go</span> <span>func</span><span>()</span> <span>{</span>
</span></span><span><span>        <span>time</span><span>.</span><span>Sleep</span><span>(</span><span>1</span> <span>*</span> <span>time</span><span>.</span><span>Second</span><span>)</span>
</span></span><span><span>        <span>c1</span> <span>&lt;-</span> <span>"one"</span>
</span></span><span><span>    <span>}()</span>
</span></span><span><span>    <span>go</span> <span>func</span><span>()</span> <span>{</span>
</span></span><span><span>        <span>time</span><span>.</span><span>Sleep</span><span>(</span><span>2</span> <span>*</span> <span>time</span><span>.</span><span>Second</span><span>)</span>
</span></span><span><span>        <span>c2</span> <span>&lt;-</span> <span>"two"</span>
</span></span><span><span>    <span>}()</span></span></span></code></pre></td></tr><tr><td><p>We’ll use <code>select</code> to await both of these values simultaneously, printing each one as it arrives.</p></td><td><pre><code><span><span>    <span>for</span> <span>i</span> <span>:=</span> <span>0</span><span>;</span> <span>i</span> <span>&lt;</span> <span>2</span><span>;</span> <span>i</span><span>++</span> <span>{</span>
</span></span><span><span>        <span>select</span> <span>{</span>
</span></span><span><span>        <span>case</span> <span>msg1</span> <span>:=</span> <span>&lt;-</span><span>c1</span><span>:</span>
</span></span><span><span>            <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"received"</span><span>,</span> <span>msg1</span><span>)</span>
</span></span><span><span>        <span>case</span> <span>msg2</span> <span>:=</span> <span>&lt;-</span><span>c2</span><span>:</span>
</span></span><span><span>            <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"received"</span><span>,</span> <span>msg2</span><span>)</span>
</span></span><span><span>        <span>}</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td><p>We receive the values <code>"one"</code> and then <code>"two"</code> as expected.</p></td><td><pre><code><span><span><span>$</span> time go run select.go 
</span></span><span><span><span>received one
</span></span></span><span><span><span>received two</span></span></span></code></pre></td></tr><tr><td><p>Note that the total execution time is only ~2 seconds since both the 1 and 2 second <code>Sleeps</code> execute concurrently.</p></td><td><pre><code><span><span><span>real    0m2.245s</span></span></span></code></pre></td></tr></tbody></table>

Next example: [Timeouts](https://gobyexample.com/timeouts).
