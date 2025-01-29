---
Description: Go by Example: Channel Synchronization
Notes: We can use channels to synchronize execution
across goroutines. Here’s an example of using a
blocking receive to wait for a goroutine to finish.
When waiting for multiple goroutines to finish,
you may prefer to use a WaitGroup.
author: 
Url: https://gobyexample.com/channel-synchronization
Created: "2025-01-29  02:44:52"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Channel Synchronization

source: https://gobyexample.com/channel-synchronization

> ## Excerpt
> We can use channels to synchronize execution
across goroutines. Here’s an example of using a
blocking receive to wait for a goroutine to finish.
When waiting for multiple goroutines to finish,
you may prefer to use a WaitGroup.

---
<table><tbody><tr><td><p>We can use channels to synchronize execution across goroutines. Here’s an example of using a blocking receive to wait for a goroutine to finish. When waiting for multiple goroutines to finish, you may prefer to use a <a href="https://gobyexample.com/waitgroups">WaitGroup</a>.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/Nw-1DzIGk5f"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"time"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td><p>This is the function we’ll run in a goroutine. The <code>done</code> channel will be used to notify another goroutine that this function’s work is done.</p></td><td><pre><code><span><span><span>func</span> <span>worker</span><span>(</span><span>done</span> <span>chan</span> <span>bool</span><span>)</span> <span>{</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Print</span><span>(</span><span>"working..."</span><span>)</span>
</span></span><span><span>    <span>time</span><span>.</span><span>Sleep</span><span>(</span><span>time</span><span>.</span><span>Second</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"done"</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Send a value to notify that we’re done.</p></td><td><pre><code><span><span>    <span>done</span> <span>&lt;-</span> <span>true</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>Start a worker goroutine, giving it the channel to notify on.</p></td><td><pre><code><span><span>    <span>done</span> <span>:=</span> <span>make</span><span>(</span><span>chan</span> <span>bool</span><span>,</span> <span>1</span><span>)</span>
</span></span><span><span>    <span>go</span> <span>worker</span><span>(</span><span>done</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Block until we receive a notification from the worker on the channel.</p></td><td><pre><code><span><span>    <span>&lt;-</span><span>done</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go run channel-synchronization.go      
</span></span><span><span><span>working...done                  </span></span></span></code></pre></td></tr><tr><td><p>If you removed the <code>&lt;- done</code> line from this program, the program would exit before the <code>worker</code> even started.</p></td><td></td></tr></tbody></table>

Next example: [Channel Directions](https://gobyexample.com/channel-directions).
