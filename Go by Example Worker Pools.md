---
Description: Go by Example: Worker Pools
Notes: In this example we’ll look at how to implement
a worker pool using goroutines and channels.
author: 
Url: https://gobyexample.com/worker-pools
Created: "2025-01-29  02:45:20"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Worker Pools

source: https://gobyexample.com/worker-pools

> ## Excerpt
> In this example we’ll look at how to implement
a worker pool using goroutines and channels.

---
<table><tbody><tr><td><p>In this example we’ll look at how to implement a <em>worker pool</em> using goroutines and channels.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/hiSJJsYZJKL"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"time"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Here’s the worker, of which we’ll run several concurrent instances. These workers will receive work on the <code>jobs</code> channel and send the corresponding results on <code>results</code>. We’ll sleep a second per job to simulate an expensive task.</p></td><td><pre><code><span><span><span>func</span> <span>worker</span><span>(</span><span>id</span> <span>int</span><span>,</span> <span>jobs</span> <span>&lt;-</span><span>chan</span> <span>int</span><span>,</span> <span>results</span> <span>chan</span><span>&lt;-</span> <span>int</span><span>)</span> <span>{</span>
</span></span><span><span>    <span>for</span> <span>j</span> <span>:=</span> <span>range</span> <span>jobs</span> <span>{</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"worker"</span><span>,</span> <span>id</span><span>,</span> <span>"started  job"</span><span>,</span> <span>j</span><span>)</span>
</span></span><span><span>        <span>time</span><span>.</span><span>Sleep</span><span>(</span><span>time</span><span>.</span><span>Second</span><span>)</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"worker"</span><span>,</span> <span>id</span><span>,</span> <span>"finished job"</span><span>,</span> <span>j</span><span>)</span>
</span></span><span><span>        <span>results</span> <span>&lt;-</span> <span>j</span> <span>*</span> <span>2</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>In order to use our pool of workers we need to send them work and collect their results. We make 2 channels for this.</p></td><td><pre><code><span><span>    <span>const</span> <span>numJobs</span> <span>=</span> <span>5</span>
</span></span><span><span>    <span>jobs</span> <span>:=</span> <span>make</span><span>(</span><span>chan</span> <span>int</span><span>,</span> <span>numJobs</span><span>)</span>
</span></span><span><span>    <span>results</span> <span>:=</span> <span>make</span><span>(</span><span>chan</span> <span>int</span><span>,</span> <span>numJobs</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>This starts up 3 workers, initially blocked because there are no jobs yet.</p></td><td><pre><code><span><span>    <span>for</span> <span>w</span> <span>:=</span> <span>1</span><span>;</span> <span>w</span> <span>&lt;=</span> <span>3</span><span>;</span> <span>w</span><span>++</span> <span>{</span>
</span></span><span><span>        <span>go</span> <span>worker</span><span>(</span><span>w</span><span>,</span> <span>jobs</span><span>,</span> <span>results</span><span>)</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td><p>Here we send 5 <code>jobs</code> and then <code>close</code> that channel to indicate that’s all the work we have.</p></td><td><pre><code><span><span>    <span>for</span> <span>j</span> <span>:=</span> <span>1</span><span>;</span> <span>j</span> <span>&lt;=</span> <span>numJobs</span><span>;</span> <span>j</span><span>++</span> <span>{</span>
</span></span><span><span>        <span>jobs</span> <span>&lt;-</span> <span>j</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span>    <span>close</span><span>(</span><span>jobs</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Finally we collect all the results of the work. This also ensures that the worker goroutines have finished. An alternative way to wait for multiple goroutines is to use a <a href="https://gobyexample.com/waitgroups">WaitGroup</a>.</p></td><td><pre><code><span><span>    <span>for</span> <span>a</span> <span>:=</span> <span>1</span><span>;</span> <span>a</span> <span>&lt;=</span> <span>numJobs</span><span>;</span> <span>a</span><span>++</span> <span>{</span>
</span></span><span><span>        <span>&lt;-</span><span>results</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td><p>Our running program shows the 5 jobs being executed by various workers. The program only takes about 2 seconds despite doing about 5 seconds of total work because there are 3 workers operating concurrently.</p></td><td><pre><code><span><span><span>$</span> time go run worker-pools.go 
</span></span><span><span><span>worker 1 started  job 1
</span></span></span><span><span><span>worker 2 started  job 2
</span></span></span><span><span><span>worker 3 started  job 3
</span></span></span><span><span><span>worker 1 finished job 1
</span></span></span><span><span><span>worker 1 started  job 4
</span></span></span><span><span><span>worker 2 finished job 2
</span></span></span><span><span><span>worker 2 started  job 5
</span></span></span><span><span><span>worker 3 finished job 3
</span></span></span><span><span><span>worker 1 finished job 4
</span></span></span><span><span><span>worker 2 finished job 5</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>real    0m2.358s</span></span></span></code></pre></td></tr></tbody></table>

Next example: [WaitGroups](https://gobyexample.com/waitgroups).
