---
Description: Go by Example: Channel Directions
Notes: When using channels as function parameters, you can
specify if a channel is meant to only send or receive
values. This specificity increases the type-safety of
the program.
author: 
Url: https://gobyexample.com/channel-directions
Created: "2025-01-29  02:44:55"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Channel Directions

source: https://gobyexample.com/channel-directions

> ## Excerpt
> When using channels as function parameters, you can
specify if a channel is meant to only send or receive
values. This specificity increases the type-safety of
the program.

---
<table><tbody><tr><td><p>When using channels as function parameters, you can specify if a channel is meant to only send or receive values. This specificity increases the type-safety of the program.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/mjNJDHwUH4R"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>"fmt"</span></span></span></code></pre></td></tr><tr><td><p>This <code>ping</code> function only accepts a channel for sending values. It would be a compile-time error to try to receive on this channel.</p></td><td><pre><code><span><span><span>func</span> <span>ping</span><span>(</span><span>pings</span> <span>chan</span><span>&lt;-</span> <span>string</span><span>,</span> <span>msg</span> <span>string</span><span>)</span> <span>{</span>
</span></span><span><span>    <span>pings</span> <span>&lt;-</span> <span>msg</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td><p>The <code>pong</code> function accepts one channel for receives (<code>pings</code>) and a second for sends (<code>pongs</code>).</p></td><td><pre><code><span><span><span>func</span> <span>pong</span><span>(</span><span>pings</span> <span>&lt;-</span><span>chan</span> <span>string</span><span>,</span> <span>pongs</span> <span>chan</span><span>&lt;-</span> <span>string</span><span>)</span> <span>{</span>
</span></span><span><span>    <span>msg</span> <span>:=</span> <span>&lt;-</span><span>pings</span>
</span></span><span><span>    <span>pongs</span> <span>&lt;-</span> <span>msg</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span>
</span></span><span><span>    <span>pings</span> <span>:=</span> <span>make</span><span>(</span><span>chan</span> <span>string</span><span>,</span> <span>1</span><span>)</span>
</span></span><span><span>    <span>pongs</span> <span>:=</span> <span>make</span><span>(</span><span>chan</span> <span>string</span><span>,</span> <span>1</span><span>)</span>
</span></span><span><span>    <span>ping</span><span>(</span><span>pings</span><span>,</span> <span>"passed message"</span><span>)</span>
</span></span><span><span>    <span>pong</span><span>(</span><span>pings</span><span>,</span> <span>pongs</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>&lt;-</span><span>pongs</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go run channel-directions.go
</span></span><span><span><span>passed message</span></span></span></code></pre></td></tr></tbody></table>

Next example: [Select](https://gobyexample.com/select).
