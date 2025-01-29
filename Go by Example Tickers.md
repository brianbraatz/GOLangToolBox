---
Description: Go by Example: Tickers
Notes: Timers are for when you want to do
something once in the future - tickers are for when
you want to do something repeatedly at regular
intervals. Here’s an example of a ticker that ticks
periodically until we stop it.
author: 
Url: https://gobyexample.com/tickers
Created: "2025-01-29  02:45:18"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Tickers

source: https://gobyexample.com/tickers

> ## Excerpt
> Timers are for when you want to do
something once in the future - tickers are for when
you want to do something repeatedly at regular
intervals. Here’s an example of a ticker that ticks
periodically until we stop it.

---
<table><tbody><tr><td><p><a href="https://gobyexample.com/timers">Timers</a> are for when you want to do something once in the future - <em>tickers</em> are for when you want to do something repeatedly at regular intervals. Here’s an example of a ticker that ticks periodically until we stop it.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/gs6zoJP-Pl9"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"time"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>Tickers use a similar mechanism to timers: a channel that is sent values. Here we’ll use the <code>select</code> builtin on the channel to await the values as they arrive every 500ms.</p></td><td><pre><code><span><span>    <span>ticker</span> <span>:=</span> <span>time</span><span>.</span><span>NewTicker</span><span>(</span><span>500</span> <span>*</span> <span>time</span><span>.</span><span>Millisecond</span><span>)</span>
</span></span><span><span>    <span>done</span> <span>:=</span> <span>make</span><span>(</span><span>chan</span> <span>bool</span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span>    <span>go</span> <span>func</span><span>()</span> <span>{</span>
</span></span><span><span>        <span>for</span> <span>{</span>
</span></span><span><span>            <span>select</span> <span>{</span>
</span></span><span><span>            <span>case</span> <span>&lt;-</span><span>done</span><span>:</span>
</span></span><span><span>                <span>return</span>
</span></span><span><span>            <span>case</span> <span>t</span> <span>:=</span> <span>&lt;-</span><span>ticker</span><span>.</span><span>C</span><span>:</span>
</span></span><span><span>                <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"Tick at"</span><span>,</span> <span>t</span><span>)</span>
</span></span><span><span>            <span>}</span>
</span></span><span><span>        <span>}</span>
</span></span><span><span>    <span>}()</span></span></span></code></pre></td></tr><tr><td><p>Tickers can be stopped like timers. Once a ticker is stopped it won’t receive any more values on its channel. We’ll stop ours after 1600ms.</p></td><td><pre><code><span><span>    <span>time</span><span>.</span><span>Sleep</span><span>(</span><span>1600</span> <span>*</span> <span>time</span><span>.</span><span>Millisecond</span><span>)</span>
</span></span><span><span>    <span>ticker</span><span>.</span><span>Stop</span><span>()</span>
</span></span><span><span>    <span>done</span> <span>&lt;-</span> <span>true</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"Ticker stopped"</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td><p>When we run this program the ticker should tick 3 times before we stop it.</p></td><td><pre><code><span><span><span>$</span> go run tickers.go
</span></span><span><span><span>Tick at 2012-09-23 11:29:56.487625 -0700 PDT
</span></span></span><span><span><span>Tick at 2012-09-23 11:29:56.988063 -0700 PDT
</span></span></span><span><span><span>Tick at 2012-09-23 11:29:57.488076 -0700 PDT
</span></span></span><span><span><span>Ticker stopped</span></span></span></code></pre></td></tr></tbody></table>

Next example: [Worker Pools](https://gobyexample.com/worker-pools).
