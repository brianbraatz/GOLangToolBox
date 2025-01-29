---
Description: Go by Example: Channels
Notes: Channels are the pipes that connect concurrent
goroutines. You can send values into channels from one
goroutine and receive those values into another
goroutine.
author: 
Url: https://gobyexample.com/channels
Created: "2025-01-29  02:44:44"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Channels

source: https://gobyexample.com/channels

> ## Excerpt
> Channels are the pipes that connect concurrent
goroutines. You can send values into channels from one
goroutine and receive those values into another
goroutine.

---
<table><tbody><tr><td><p><em>Channels</em> are the pipes that connect concurrent goroutines. You can send values into channels from one goroutine and receive those values into another goroutine.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/MaLY7AiAkHM"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>"fmt"</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>Create a new channel with <code>make(chan val-type)</code>. Channels are typed by the values they convey.</p></td><td><pre><code><span><span>    <span>messages</span> <span>:=</span> <span>make</span><span>(</span><span>chan</span> <span>string</span><span>)</span></span></span></code></pre></td></tr><tr><td><p><em>Send</em> a value into a channel using the <code>channel &lt;-</code> syntax. Here we send <code>"ping"</code> to the <code>messages</code> channel we made above, from a new goroutine.</p></td><td><pre><code><span><span>    <span>go</span> <span>func</span><span>()</span> <span>{</span> <span>messages</span> <span>&lt;-</span> <span>"ping"</span> <span>}()</span></span></span></code></pre></td></tr><tr><td><p>The <code>&lt;-channel</code> syntax <em>receives</em> a value from the channel. Here we’ll receive the <code>"ping"</code> message we sent above and print it out.</p></td><td><pre><code><span><span>    <span>msg</span> <span>:=</span> <span>&lt;-</span><span>messages</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>msg</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td><p>When we run the program the <code>"ping"</code> message is successfully passed from one goroutine to another via our channel.</p></td><td><pre><code><span><span><span>$</span> go run channels.go 
</span></span><span><span><span>ping</span></span></span></code></pre></td></tr><tr><td><p>By default sends and receives block until both the sender and receiver are ready. This property allowed us to wait at the end of our program for the <code>"ping"</code> message without having to use any other synchronization.</p></td><td></td></tr></tbody></table>

Next example: [Channel Buffering](https://gobyexample.com/channel-buffering).
