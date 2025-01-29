---
Description: Go by Example: Epoch
Notes: A common requirement in programs is getting the number
of seconds, milliseconds, or nanoseconds since the
Unix epoch.
Here’s how to do it in Go.
author: 
Url: https://gobyexample.com/epoch
Created: "2025-01-29  02:47:35"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Epoch

source: https://gobyexample.com/epoch

> ## Excerpt
> A common requirement in programs is getting the number
of seconds, milliseconds, or nanoseconds since the
Unix epoch.
Here’s how to do it in Go.

---
<table><tbody><tr><td><p>A common requirement in programs is getting the number of seconds, milliseconds, or nanoseconds since the <a href="https://en.wikipedia.org/wiki/Unix_time">Unix epoch</a>. Here’s how to do it in Go.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/lRmD1EWHHPz"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"time"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>Use <code>time.Now</code> with <code>Unix</code>, <code>UnixMilli</code> or <code>UnixNano</code> to get elapsed time since the Unix epoch in seconds, milliseconds or nanoseconds, respectively.</p></td><td><pre><code><span><span>    <span>now</span> <span>:=</span> <span>time</span><span>.</span><span>Now</span><span>()</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>now</span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>now</span><span>.</span><span>Unix</span><span>())</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>now</span><span>.</span><span>UnixMilli</span><span>())</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>now</span><span>.</span><span>UnixNano</span><span>())</span></span></span></code></pre></td></tr><tr><td><p>You can also convert integer seconds or nanoseconds since the epoch into the corresponding <code>time</code>.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>time</span><span>.</span><span>Unix</span><span>(</span><span>now</span><span>.</span><span>Unix</span><span>(),</span> <span>0</span><span>))</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>time</span><span>.</span><span>Unix</span><span>(</span><span>0</span><span>,</span> <span>now</span><span>.</span><span>UnixNano</span><span>()))</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go run epoch.go 
</span></span><span><span><span>2012-10-31 16:13:58.292387 +0000 UTC
</span></span></span><span><span><span>1351700038
</span></span></span><span><span><span>1351700038292
</span></span></span><span><span><span>1351700038292387000
</span></span></span><span><span><span>2012-10-31 16:13:58 +0000 UTC
</span></span></span><span><span><span>2012-10-31 16:13:58.292387 +0000 UTC</span></span></span></code></pre></td></tr><tr><td><p>Next we’ll look at another time-related task: time parsing and formatting.</p></td><td></td></tr></tbody></table>

Next example: [Time Formatting / Parsing](https://gobyexample.com/time-formatting-parsing).
