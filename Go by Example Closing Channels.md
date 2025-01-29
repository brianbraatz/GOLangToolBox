---
Description: Go by Example: Closing Channels
Notes: Closing a channel indicates that no more values
will be sent on it. This can be useful to communicate
completion to the channel’s receivers.
author: 
Url: https://gobyexample.com/closing-channels
Created: "2025-01-29  02:45:08"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Closing Channels

source: https://gobyexample.com/closing-channels

> ## Excerpt
> Closing a channel indicates that no more values
will be sent on it. This can be useful to communicate
completion to the channel’s receivers.

---
<table><tbody><tr><td><p><em>Closing</em> a channel indicates that no more values will be sent on it. This can be useful to communicate completion to the channel’s receivers.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/yZijZHYe22y"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>"fmt"</span></span></span></code></pre></td></tr><tr><td><p>In this example we’ll use a <code>jobs</code> channel to communicate work to be done from the <code>main()</code> goroutine to a worker goroutine. When we have no more jobs for the worker we’ll <code>close</code> the <code>jobs</code> channel.</p></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span>
</span></span><span><span>    <span>jobs</span> <span>:=</span> <span>make</span><span>(</span><span>chan</span> <span>int</span><span>,</span> <span>5</span><span>)</span>
</span></span><span><span>    <span>done</span> <span>:=</span> <span>make</span><span>(</span><span>chan</span> <span>bool</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Here’s the worker goroutine. It repeatedly receives from <code>jobs</code> with <code>j, more := &lt;-jobs</code>. In this special 2-value form of receive, the <code>more</code> value will be <code>false</code> if <code>jobs</code> has been <code>close</code>d and all values in the channel have already been received. We use this to notify on <code>done</code> when we’ve worked all our jobs.</p></td><td><pre><code><span><span>    <span>go</span> <span>func</span><span>()</span> <span>{</span>
</span></span><span><span>        <span>for</span> <span>{</span>
</span></span><span><span>            <span>j</span><span>,</span> <span>more</span> <span>:=</span> <span>&lt;-</span><span>jobs</span>
</span></span><span><span>            <span>if</span> <span>more</span> <span>{</span>
</span></span><span><span>                <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"received job"</span><span>,</span> <span>j</span><span>)</span>
</span></span><span><span>            <span>}</span> <span>else</span> <span>{</span>
</span></span><span><span>                <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"received all jobs"</span><span>)</span>
</span></span><span><span>                <span>done</span> <span>&lt;-</span> <span>true</span>
</span></span><span><span>                <span>return</span>
</span></span><span><span>            <span>}</span>
</span></span><span><span>        <span>}</span>
</span></span><span><span>    <span>}()</span></span></span></code></pre></td></tr><tr><td><p>This sends 3 jobs to the worker over the <code>jobs</code> channel, then closes it.</p></td><td><pre><code><span><span>    <span>for</span> <span>j</span> <span>:=</span> <span>1</span><span>;</span> <span>j</span> <span>&lt;=</span> <span>3</span><span>;</span> <span>j</span><span>++</span> <span>{</span>
</span></span><span><span>        <span>jobs</span> <span>&lt;-</span> <span>j</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"sent job"</span><span>,</span> <span>j</span><span>)</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span>    <span>close</span><span>(</span><span>jobs</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"sent all jobs"</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>We await the worker using the <a href="https://gobyexample.com/channel-synchronization">synchronization</a> approach we saw earlier.</p></td><td><pre><code><span><span>    <span>&lt;-</span><span>done</span></span></span></code></pre></td></tr><tr><td><p>Reading from a closed channel succeeds immediately, returning the zero value of the underlying type. The optional second return value is <code>true</code> if the value received was delivered by a successful send operation to the channel, or <code>false</code> if it was a zero value generated because the channel is closed and empty.</p></td><td><pre><code><span><span>    <span>_</span><span>,</span> <span>ok</span> <span>:=</span> <span>&lt;-</span><span>jobs</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"received more jobs:"</span><span>,</span> <span>ok</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go run closing-channels.go 
</span></span><span><span><span>sent job 1
</span></span></span><span><span><span>received job 1
</span></span></span><span><span><span>sent job 2
</span></span></span><span><span><span>received job 2
</span></span></span><span><span><span>sent job 3
</span></span></span><span><span><span>received job 3
</span></span></span><span><span><span>sent all jobs
</span></span></span><span><span><span>received all jobs
</span></span></span><span><span><span>received more jobs: false</span></span></span></code></pre></td></tr><tr><td><p>The idea of closed channels leads naturally to our next example: <code>range</code> over channels.</p></td><td></td></tr></tbody></table>

Next example: [Range over Channels](https://gobyexample.com/range-over-channels).
