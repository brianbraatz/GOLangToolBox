---
Description: Go by Example: Timeouts
Notes: Timeouts are important for programs that connect to
external resources or that otherwise need to bound
execution time. Implementing timeouts in Go is easy and
elegant thanks to channels and select.
author: 
Url: https://gobyexample.com/timeouts
Created: "2025-01-29  02:45:02"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Timeouts

source: https://gobyexample.com/timeouts

> ## Excerpt
> Timeouts are important for programs that connect to
external resources or that otherwise need to bound
execution time. Implementing timeouts in Go is easy and
elegant thanks to channels and select.

---
<table><tbody><tr><td><p><em>Timeouts</em> are important for programs that connect to external resources or that otherwise need to bound execution time. Implementing timeouts in Go is easy and elegant thanks to channels and <code>select</code>.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/gyr0NbVKBVf"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"time"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>For our example, suppose we’re executing an external call that returns its result on a channel <code>c1</code> after 2s. Note that the channel is buffered, so the send in the goroutine is nonblocking. This is a common pattern to prevent goroutine leaks in case the channel is never read.</p></td><td><pre><code><span><span>    <span>c1</span> <span>:=</span> <span>make</span><span>(</span><span>chan</span> <span>string</span><span>,</span> <span>1</span><span>)</span>
</span></span><span><span>    <span>go</span> <span>func</span><span>()</span> <span>{</span>
</span></span><span><span>        <span>time</span><span>.</span><span>Sleep</span><span>(</span><span>2</span> <span>*</span> <span>time</span><span>.</span><span>Second</span><span>)</span>
</span></span><span><span>        <span>c1</span> <span>&lt;-</span> <span>"result 1"</span>
</span></span><span><span>    <span>}()</span></span></span></code></pre></td></tr><tr><td><p>Here’s the <code>select</code> implementing a timeout. <code>res := &lt;-c1</code> awaits the result and <code>&lt;-time.After</code> awaits a value to be sent after the timeout of 1s. Since <code>select</code> proceeds with the first receive that’s ready, we’ll take the timeout case if the operation takes more than the allowed 1s.</p></td><td><pre><code><span><span>    <span>select</span> <span>{</span>
</span></span><span><span>    <span>case</span> <span>res</span> <span>:=</span> <span>&lt;-</span><span>c1</span><span>:</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>res</span><span>)</span>
</span></span><span><span>    <span>case</span> <span>&lt;-</span><span>time</span><span>.</span><span>After</span><span>(</span><span>1</span> <span>*</span> <span>time</span><span>.</span><span>Second</span><span>):</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"timeout 1"</span><span>)</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td><p>If we allow a longer timeout of 3s, then the receive from <code>c2</code> will succeed and we’ll print the result.</p></td><td><pre><code><span><span>    <span>c2</span> <span>:=</span> <span>make</span><span>(</span><span>chan</span> <span>string</span><span>,</span> <span>1</span><span>)</span>
</span></span><span><span>    <span>go</span> <span>func</span><span>()</span> <span>{</span>
</span></span><span><span>        <span>time</span><span>.</span><span>Sleep</span><span>(</span><span>2</span> <span>*</span> <span>time</span><span>.</span><span>Second</span><span>)</span>
</span></span><span><span>        <span>c2</span> <span>&lt;-</span> <span>"result 2"</span>
</span></span><span><span>    <span>}()</span>
</span></span><span><span>    <span>select</span> <span>{</span>
</span></span><span><span>    <span>case</span> <span>res</span> <span>:=</span> <span>&lt;-</span><span>c2</span><span>:</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>res</span><span>)</span>
</span></span><span><span>    <span>case</span> <span>&lt;-</span><span>time</span><span>.</span><span>After</span><span>(</span><span>3</span> <span>*</span> <span>time</span><span>.</span><span>Second</span><span>):</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"timeout 2"</span><span>)</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td><p>Running this program shows the first operation timing out and the second succeeding.</p></td><td><pre><code><span><span><span>$</span> go run timeouts.go 
</span></span><span><span><span>timeout 1
</span></span></span><span><span><span>result 2</span></span></span></code></pre></td></tr></tbody></table>

Next example: [Non-Blocking Channel Operations](https://gobyexample.com/non-blocking-channel-operations).
