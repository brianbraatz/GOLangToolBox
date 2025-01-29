---
Description: Go by Example: Atomic Counters
Notes: The primary mechanism for managing state in Go is
communication over channels. We saw this for example
with worker pools. There are a few other
options for managing state though. Here we’ll
look at using the sync/atomic package for atomic
counters accessed by multiple goroutines.
author: 
Url: https://gobyexample.com/atomic-counters
Created: "2025-01-29  02:45:29"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Atomic Counters

source: https://gobyexample.com/atomic-counters

> ## Excerpt
> The primary mechanism for managing state in Go is
communication over channels. We saw this for example
with worker pools. There are a few other
options for managing state though. Here we’ll
look at using the sync/atomic package for atomic
counters accessed by multiple goroutines.

---
<table><tbody><tr><td><p>The primary mechanism for managing state in Go is communication over channels. We saw this for example with <a href="https://gobyexample.com/worker-pools">worker pools</a>. There are a few other options for managing state though. Here we’ll look at using the <code>sync/atomic</code> package for <em>atomic counters</em> accessed by multiple goroutines.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/HWE6h4-y-Fw"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"sync"</span>
</span></span><span><span>    <span>"sync/atomic"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>We’ll use an atomic integer type to represent our (always-positive) counter.</p></td><td><pre><code><span><span>    <span>var</span> <span>ops</span> <span>atomic</span><span>.</span><span>Uint64</span></span></span></code></pre></td></tr><tr><td><p>A WaitGroup will help us wait for all goroutines to finish their work.</p></td><td><pre><code><span><span>    <span>var</span> <span>wg</span> <span>sync</span><span>.</span><span>WaitGroup</span></span></span></code></pre></td></tr><tr><td><p>We’ll start 50 goroutines that each increment the counter exactly 1000 times.</p></td><td><pre><code><span><span>    <span>for</span> <span>i</span> <span>:=</span> <span>0</span><span>;</span> <span>i</span> <span>&lt;</span> <span>50</span><span>;</span> <span>i</span><span>++</span> <span>{</span>
</span></span><span><span>        <span>wg</span><span>.</span><span>Add</span><span>(</span><span>1</span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span>        <span>go</span> <span>func</span><span>()</span> <span>{</span>
</span></span><span><span>            <span>for</span> <span>c</span> <span>:=</span> <span>0</span><span>;</span> <span>c</span> <span>&lt;</span> <span>1000</span><span>;</span> <span>c</span><span>++</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>To atomically increment the counter we use <code>Add</code>.</p></td><td><pre><code><span><span>                <span>ops</span><span>.</span><span>Add</span><span>(</span><span>1</span><span>)</span>
</span></span><span><span>            <span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span>            <span>wg</span><span>.</span><span>Done</span><span>()</span>
</span></span><span><span>        <span>}()</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td><p>Wait until all the goroutines are done.</p></td><td><pre><code><span><span>    <span>wg</span><span>.</span><span>Wait</span><span>()</span></span></span></code></pre></td></tr><tr><td><p>Here no goroutines are writing to ‘ops’, but using <code>Load</code> it’s safe to atomically read a value even while other goroutines are (atomically) updating it.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"ops:"</span><span>,</span> <span>ops</span><span>.</span><span>Load</span><span>())</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td><p>We expect to get exactly 50,000 operations. Had we used a non-atomic integer and incremented it with <code>ops++</code>, we’d likely get a different number, changing between runs, because the goroutines would interfere with each other. Moreover, we’d get data race failures when running with the <code>-race</code> flag.</p></td><td><pre><code><span><span><span>$</span> go run atomic-counters.go
</span></span><span><span><span>ops: 50000</span></span></span></code></pre></td></tr><tr><td><p>Next we’ll look at mutexes, another tool for managing state.</p></td><td></td></tr></tbody></table>

Next example: [Mutexes](https://gobyexample.com/mutexes).
