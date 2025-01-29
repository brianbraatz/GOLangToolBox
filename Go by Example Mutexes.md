---
Description: Go by Example: Mutexes
Notes: In the previous example we saw how to manage simple
counter state using atomic operations.
For more complex state we can use a mutex
to safely access data across multiple goroutines.
author: 
Url: https://gobyexample.com/mutexes
Created: "2025-01-29  02:45:32"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Mutexes

source: https://gobyexample.com/mutexes

> ## Excerpt
> In the previous example we saw how to manage simple
counter state using atomic operations.
For more complex state we can use a mutex
to safely access data across multiple goroutines.

---
<table><tbody><tr><td><p>In the previous example we saw how to manage simple counter state using <a href="https://gobyexample.com/atomic-counters">atomic operations</a>. For more complex state we can use a <a href="https://en.wikipedia.org/wiki/Mutual_exclusion"><em>mutex</em></a> to safely access data across multiple goroutines.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/JU735qy2UmB"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"sync"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Container holds a map of counters; since we want to update it concurrently from multiple goroutines, we add a <code>Mutex</code> to synchronize access. Note that mutexes must not be copied, so if this <code>struct</code> is passed around, it should be done by pointer.</p></td><td><pre><code><span><span><span>type</span> <span>Container</span> <span>struct</span> <span>{</span>
</span></span><span><span>    <span>mu</span>       <span>sync</span><span>.</span><span>Mutex</span>
</span></span><span><span>    <span>counters</span> <span>map</span><span>[</span><span>string</span><span>]</span><span>int</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td><p>Lock the mutex before accessing <code>counters</code>; unlock it at the end of the function using a <a href="https://gobyexample.com/defer">defer</a> statement.</p></td><td><pre><code><span><span><span>func</span> <span>(</span><span>c</span> <span>*</span><span>Container</span><span>)</span> <span>inc</span><span>(</span><span>name</span> <span>string</span><span>)</span> <span>{</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span>    <span>c</span><span>.</span><span>mu</span><span>.</span><span>Lock</span><span>()</span>
</span></span><span><span>    <span>defer</span> <span>c</span><span>.</span><span>mu</span><span>.</span><span>Unlock</span><span>()</span>
</span></span><span><span>    <span>c</span><span>.</span><span>counters</span><span>[</span><span>name</span><span>]</span><span>++</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td><p>Note that the zero value of a mutex is usable as-is, so no initialization is required here.</p></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span>
</span></span><span><span>    <span>c</span> <span>:=</span> <span>Container</span><span>{</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span>        <span>counters</span><span>:</span> <span>map</span><span>[</span><span>string</span><span>]</span><span>int</span><span>{</span><span>"a"</span><span>:</span> <span>0</span><span>,</span> <span>"b"</span><span>:</span> <span>0</span><span>},</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span>    <span>var</span> <span>wg</span> <span>sync</span><span>.</span><span>WaitGroup</span></span></span></code></pre></td></tr><tr><td><p>This function increments a named counter in a loop.</p></td><td><pre><code><span><span>    <span>doIncrement</span> <span>:=</span> <span>func</span><span>(</span><span>name</span> <span>string</span><span>,</span> <span>n</span> <span>int</span><span>)</span> <span>{</span>
</span></span><span><span>        <span>for</span> <span>i</span> <span>:=</span> <span>0</span><span>;</span> <span>i</span> <span>&lt;</span> <span>n</span><span>;</span> <span>i</span><span>++</span> <span>{</span>
</span></span><span><span>            <span>c</span><span>.</span><span>inc</span><span>(</span><span>name</span><span>)</span>
</span></span><span><span>        <span>}</span>
</span></span><span><span>        <span>wg</span><span>.</span><span>Done</span><span>()</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td><p>Run several goroutines concurrently; note that they all access the same <code>Container</code>, and two of them access the same counter.</p></td><td><pre><code><span><span>    <span>wg</span><span>.</span><span>Add</span><span>(</span><span>3</span><span>)</span>
</span></span><span><span>    <span>go</span> <span>doIncrement</span><span>(</span><span>"a"</span><span>,</span> <span>10000</span><span>)</span>
</span></span><span><span>    <span>go</span> <span>doIncrement</span><span>(</span><span>"a"</span><span>,</span> <span>10000</span><span>)</span>
</span></span><span><span>    <span>go</span> <span>doIncrement</span><span>(</span><span>"b"</span><span>,</span> <span>10000</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Wait for the goroutines to finish</p></td><td><pre><code><span><span>    <span>wg</span><span>.</span><span>Wait</span><span>()</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>c</span><span>.</span><span>counters</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td><p>Running the program shows that the counters updated as expected.</p></td><td><pre><code><span><span><span>$</span> go run mutexes.go
</span></span><span><span><span>map[a:20000 b:10000]</span></span></span></code></pre></td></tr><tr><td><p>Next we’ll look at implementing this same state management task using only goroutines and channels.</p></td><td></td></tr></tbody></table>

Next example: [Stateful Goroutines](https://gobyexample.com/stateful-goroutines).
