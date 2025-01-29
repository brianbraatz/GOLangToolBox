---
Description: Go by Example: Channel Buffering
Notes: By default channels are unbuffered, meaning that they
will only accept sends (chan <-) if there is a
corresponding receive (<- chan) ready to receive the
sent value. Buffered channels accept a limited
number of  values without a corresponding receiver for
those values.
author: 
Url: https://gobyexample.com/channel-buffering
Created: "2025-01-29  02:44:47"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Channel Buffering

source: https://gobyexample.com/channel-buffering

> ## Excerpt
> By default channels are unbuffered, meaning that they
will only accept sends (chan <-) if there is a
corresponding receive (<- chan) ready to receive the
sent value. Buffered channels accept a limited
number of  values without a corresponding receiver for
those values.

---
<table><tbody><tr><td><p>By default channels are <em>unbuffered</em>, meaning that they will only accept sends (<code>chan &lt;-</code>) if there is a corresponding receive (<code>&lt;- chan</code>) ready to receive the sent value. <em>Buffered channels</em> accept a limited number of values without a corresponding receiver for those values.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/3BRCdRnRszb"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>"fmt"</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>Here we <code>make</code> a channel of strings buffering up to 2 values.</p></td><td><pre><code><span><span>    <span>messages</span> <span>:=</span> <span>make</span><span>(</span><span>chan</span> <span>string</span><span>,</span> <span>2</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Because this channel is buffered, we can send these values into the channel without a corresponding concurrent receive.</p></td><td><pre><code><span><span>    <span>messages</span> <span>&lt;-</span> <span>"buffered"</span>
</span></span><span><span>    <span>messages</span> <span>&lt;-</span> <span>"channel"</span></span></span></code></pre></td></tr><tr><td><p>Later we can receive these two values as usual.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>&lt;-</span><span>messages</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>&lt;-</span><span>messages</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go run channel-buffering.go 
</span></span><span><span><span>buffered
</span></span></span><span><span><span>channel</span></span></span></code></pre></td></tr></tbody></table>

Next example: [Channel Synchronization](https://gobyexample.com/channel-synchronization).
