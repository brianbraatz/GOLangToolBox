---
Description: Go by Example: Rate Limiting
Notes: Rate limiting
is an important mechanism for controlling resource
utilization and maintaining quality of service. Go
elegantly supports rate limiting with goroutines,
channels, and tickers.
author: 
Url: https://gobyexample.com/rate-limiting
Created: "2025-01-29  02:45:26"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Rate Limiting

source: https://gobyexample.com/rate-limiting

> ## Excerpt
> Rate limiting
is an important mechanism for controlling resource
utilization and maintaining quality of service. Go
elegantly supports rate limiting with goroutines,
channels, and tickers.

---
<table><tbody><tr><td><p><a href="https://en.wikipedia.org/wiki/Rate_limiting"><em>Rate limiting</em></a> is an important mechanism for controlling resource utilization and maintaining quality of service. Go elegantly supports rate limiting with goroutines, channels, and <a href="https://gobyexample.com/tickers">tickers</a>.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/lqf7pC2FUeT"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"time"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>First we’ll look at basic rate limiting. Suppose we want to limit our handling of incoming requests. We’ll serve these requests off a channel of the same name.</p></td><td><pre><code><span><span>    <span>requests</span> <span>:=</span> <span>make</span><span>(</span><span>chan</span> <span>int</span><span>,</span> <span>5</span><span>)</span>
</span></span><span><span>    <span>for</span> <span>i</span> <span>:=</span> <span>1</span><span>;</span> <span>i</span> <span>&lt;=</span> <span>5</span><span>;</span> <span>i</span><span>++</span> <span>{</span>
</span></span><span><span>        <span>requests</span> <span>&lt;-</span> <span>i</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span>    <span>close</span><span>(</span><span>requests</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>This <code>limiter</code> channel will receive a value every 200 milliseconds. This is the regulator in our rate limiting scheme.</p></td><td><pre><code><span><span>    <span>limiter</span> <span>:=</span> <span>time</span><span>.</span><span>Tick</span><span>(</span><span>200</span> <span>*</span> <span>time</span><span>.</span><span>Millisecond</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>By blocking on a receive from the <code>limiter</code> channel before serving each request, we limit ourselves to 1 request every 200 milliseconds.</p></td><td><pre><code><span><span>    <span>for</span> <span>req</span> <span>:=</span> <span>range</span> <span>requests</span> <span>{</span>
</span></span><span><span>        <span>&lt;-</span><span>limiter</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"request"</span><span>,</span> <span>req</span><span>,</span> <span>time</span><span>.</span><span>Now</span><span>())</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td><p>We may want to allow short bursts of requests in our rate limiting scheme while preserving the overall rate limit. We can accomplish this by buffering our limiter channel. This <code>burstyLimiter</code> channel will allow bursts of up to 3 events.</p></td><td><pre><code><span><span>    <span>burstyLimiter</span> <span>:=</span> <span>make</span><span>(</span><span>chan</span> <span>time</span><span>.</span><span>Time</span><span>,</span> <span>3</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Fill up the channel to represent allowed bursting.</p></td><td><pre><code><span><span>    <span>for</span> <span>i</span> <span>:=</span> <span>0</span><span>;</span> <span>i</span> <span>&lt;</span> <span>3</span><span>;</span> <span>i</span><span>++</span> <span>{</span>
</span></span><span><span>        <span>burstyLimiter</span> <span>&lt;-</span> <span>time</span><span>.</span><span>Now</span><span>()</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td><p>Every 200 milliseconds we’ll try to add a new value to <code>burstyLimiter</code>, up to its limit of 3.</p></td><td><pre><code><span><span>    <span>go</span> <span>func</span><span>()</span> <span>{</span>
</span></span><span><span>        <span>for</span> <span>t</span> <span>:=</span> <span>range</span> <span>time</span><span>.</span><span>Tick</span><span>(</span><span>200</span> <span>*</span> <span>time</span><span>.</span><span>Millisecond</span><span>)</span> <span>{</span>
</span></span><span><span>            <span>burstyLimiter</span> <span>&lt;-</span> <span>t</span>
</span></span><span><span>        <span>}</span>
</span></span><span><span>    <span>}()</span></span></span></code></pre></td></tr><tr><td><p>Now simulate 5 more incoming requests. The first 3 of these will benefit from the burst capability of <code>burstyLimiter</code>.</p></td><td><pre><code><span><span>    <span>burstyRequests</span> <span>:=</span> <span>make</span><span>(</span><span>chan</span> <span>int</span><span>,</span> <span>5</span><span>)</span>
</span></span><span><span>    <span>for</span> <span>i</span> <span>:=</span> <span>1</span><span>;</span> <span>i</span> <span>&lt;=</span> <span>5</span><span>;</span> <span>i</span><span>++</span> <span>{</span>
</span></span><span><span>        <span>burstyRequests</span> <span>&lt;-</span> <span>i</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span>    <span>close</span><span>(</span><span>burstyRequests</span><span>)</span>
</span></span><span><span>    <span>for</span> <span>req</span> <span>:=</span> <span>range</span> <span>burstyRequests</span> <span>{</span>
</span></span><span><span>        <span>&lt;-</span><span>burstyLimiter</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"request"</span><span>,</span> <span>req</span><span>,</span> <span>time</span><span>.</span><span>Now</span><span>())</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td><p>Running our program we see the first batch of requests handled once every ~200 milliseconds as desired.</p></td><td><pre><code><span><span><span>$</span> go run rate-limiting.go
</span></span><span><span><span>request 1 2012-10-19 00:38:18.687438 +0000 UTC
</span></span></span><span><span><span>request 2 2012-10-19 00:38:18.887471 +0000 UTC
</span></span></span><span><span><span>request 3 2012-10-19 00:38:19.087238 +0000 UTC
</span></span></span><span><span><span>request 4 2012-10-19 00:38:19.287338 +0000 UTC
</span></span></span><span><span><span>request 5 2012-10-19 00:38:19.487331 +0000 UTC</span></span></span></code></pre></td></tr><tr><td><p>For the second batch of requests we serve the first 3 immediately because of the burstable rate limiting, then serve the remaining 2 with ~200ms delays each.</p></td><td><pre><code><span><span><span>request 1 2012-10-19 00:38:20.487578 +0000 UTC
</span></span></span><span><span><span>request 2 2012-10-19 00:38:20.487645 +0000 UTC
</span></span></span><span><span><span>request 3 2012-10-19 00:38:20.487676 +0000 UTC
</span></span></span><span><span><span>request 4 2012-10-19 00:38:20.687483 +0000 UTC
</span></span></span><span><span><span>request 5 2012-10-19 00:38:20.887542 +0000 UTC</span></span></span></code></pre></td></tr></tbody></table>

Next example: [Atomic Counters](https://gobyexample.com/atomic-counters).
