---
Description: Go by Example: Goroutines
Notes: A goroutine is a lightweight thread of execution.
author: 
Url: https://gobyexample.com/goroutines
Created: "2025-01-29  02:44:41"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Goroutines

source: https://gobyexample.com/goroutines

> ## Excerpt
> A goroutine is a lightweight thread of execution.

---
<table><tbody><tr><td><p>A <em>goroutine</em> is a lightweight thread of execution.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/I7scqRijEJt"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"time"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>f</span><span>(</span><span>from</span> <span>string</span><span>)</span> <span>{</span>
</span></span><span><span>    <span>for</span> <span>i</span> <span>:=</span> <span>0</span><span>;</span> <span>i</span> <span>&lt;</span> <span>3</span><span>;</span> <span>i</span><span>++</span> <span>{</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>from</span><span>,</span> <span>":"</span><span>,</span> <span>i</span><span>)</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>Suppose we have a function call <code>f(s)</code>. Here’s how we’d call that in the usual way, running it synchronously.</p></td><td><pre><code><span><span>    <span>f</span><span>(</span><span>"direct"</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>To invoke this function in a goroutine, use <code>go f(s)</code>. This new goroutine will execute concurrently with the calling one.</p></td><td><pre><code><span><span>    <span>go</span> <span>f</span><span>(</span><span>"goroutine"</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>You can also start a goroutine for an anonymous function call.</p></td><td><pre><code><span><span>    <span>go</span> <span>func</span><span>(</span><span>msg</span> <span>string</span><span>)</span> <span>{</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>msg</span><span>)</span>
</span></span><span><span>    <span>}(</span><span>"going"</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Our two function calls are running asynchronously in separate goroutines now. Wait for them to finish (for a more robust approach, use a <a href="https://gobyexample.com/waitgroups">WaitGroup</a>).</p></td><td><pre><code><span><span>    <span>time</span><span>.</span><span>Sleep</span><span>(</span><span>time</span><span>.</span><span>Second</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"done"</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td><p>When we run this program, we see the output of the blocking call first, then the output of the two goroutines. The goroutines’ output may be interleaved, because goroutines are being run concurrently by the Go runtime.</p></td><td><pre><code><span><span><span>$</span> go run goroutines.go
</span></span><span><span><span>direct : 0
</span></span></span><span><span><span>direct : 1
</span></span></span><span><span><span>direct : 2
</span></span></span><span><span><span>goroutine : 0
</span></span></span><span><span><span>going
</span></span></span><span><span><span>goroutine : 1
</span></span></span><span><span><span>goroutine : 2
</span></span></span><span><span><span>done</span></span></span></code></pre></td></tr><tr><td><p>Next we’ll look at a complement to goroutines in concurrent Go programs: channels.</p></td><td></td></tr></tbody></table>

Next example: [Channels](https://gobyexample.com/channels).
