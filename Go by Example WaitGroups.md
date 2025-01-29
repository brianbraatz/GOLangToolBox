---
Description: Go by Example: WaitGroups
Notes: To wait for multiple goroutines to finish, we can
use a wait group.
author: 
Url: https://gobyexample.com/waitgroups
Created: "2025-01-29  02:45:23"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: WaitGroups

source: https://gobyexample.com/waitgroups

> ## Excerpt
> To wait for multiple goroutines to finish, we can
use a wait group.

---
<table><tbody><tr><td><p>To wait for multiple goroutines to finish, we can use a <em>wait group</em>.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/fC_Chrkb5uA"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"sync"</span>
</span></span><span><span>    <span>"time"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td><p>This is the function we’ll run in every goroutine.</p></td><td><pre><code><span><span><span>func</span> <span>worker</span><span>(</span><span>id</span> <span>int</span><span>)</span> <span>{</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Printf</span><span>(</span><span>"Worker %d starting\n"</span><span>,</span> <span>id</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Sleep to simulate an expensive task.</p></td><td><pre><code><span><span>    <span>time</span><span>.</span><span>Sleep</span><span>(</span><span>time</span><span>.</span><span>Second</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Printf</span><span>(</span><span>"Worker %d done\n"</span><span>,</span> <span>id</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>This WaitGroup is used to wait for all the goroutines launched here to finish. Note: if a WaitGroup is explicitly passed into functions, it should be done <em>by pointer</em>.</p></td><td><pre><code><span><span>    <span>var</span> <span>wg</span> <span>sync</span><span>.</span><span>WaitGroup</span></span></span></code></pre></td></tr><tr><td><p>Launch several goroutines and increment the WaitGroup counter for each.</p></td><td><pre><code><span><span>    <span>for</span> <span>i</span> <span>:=</span> <span>1</span><span>;</span> <span>i</span> <span>&lt;=</span> <span>5</span><span>;</span> <span>i</span><span>++</span> <span>{</span>
</span></span><span><span>        <span>wg</span><span>.</span><span>Add</span><span>(</span><span>1</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Wrap the worker call in a closure that makes sure to tell the WaitGroup that this worker is done. This way the worker itself does not have to be aware of the concurrency primitives involved in its execution.</p></td><td><pre><code><span><span>        <span>go</span> <span>func</span><span>()</span> <span>{</span>
</span></span><span><span>            <span>defer</span> <span>wg</span><span>.</span><span>Done</span><span>()</span>
</span></span><span><span>            <span>worker</span><span>(</span><span>i</span><span>)</span>
</span></span><span><span>        <span>}()</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td><p>Block until the WaitGroup counter goes back to 0; all the workers notified they’re done.</p></td><td><pre><code><span><span>    <span>wg</span><span>.</span><span>Wait</span><span>()</span></span></span></code></pre></td></tr><tr><td><p>Note that this approach has no straightforward way to propagate errors from workers. For more advanced use cases, consider using the <a href="https://pkg.go.dev/golang.org/x/sync/errgroup">errgroup package</a>.</p></td><td><pre><code><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go run waitgroups.go
</span></span><span><span><span>Worker 5 starting
</span></span></span><span><span><span>Worker 3 starting
</span></span></span><span><span><span>Worker 4 starting
</span></span></span><span><span><span>Worker 1 starting
</span></span></span><span><span><span>Worker 2 starting
</span></span></span><span><span><span>Worker 4 done
</span></span></span><span><span><span>Worker 1 done
</span></span></span><span><span><span>Worker 2 done
</span></span></span><span><span><span>Worker 5 done
</span></span></span><span><span><span>Worker 3 done</span></span></span></code></pre></td></tr><tr><td><p>The order of workers starting up and finishing is likely to be different for each invocation.</p></td><td></td></tr></tbody></table>

Next example: [Rate Limiting](https://gobyexample.com/rate-limiting).
