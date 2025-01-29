---
Description: Go by Example: Context
Notes: In the previous example we looked at setting up a simple
HTTP server. HTTP servers are useful for
demonstrating the usage of context.Context for
controlling cancellation. A Context carries deadlines,
cancellation signals, and other request-scoped values
across API boundaries and goroutines.
author: 
Url: https://gobyexample.com/context
Created: "2025-01-29  02:48:40"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Context

source: https://gobyexample.com/context

> ## Excerpt
> In the previous example we looked at setting up a simple
HTTP server. HTTP servers are useful for
demonstrating the usage of context.Context for
controlling cancellation. A Context carries deadlines,
cancellation signals, and other request-scoped values
across API boundaries and goroutines.

---
<table><tbody><tr><td><p>In the previous example we looked at setting up a simple <a href="https://gobyexample.com/http-servers">HTTP server</a>. HTTP servers are useful for demonstrating the usage of <code>context.Context</code> for controlling cancellation. A <code>Context</code> carries deadlines, cancellation signals, and other request-scoped values across API boundaries and goroutines.</p></td><td><a href="https://go.dev/play/p/0_bu1o8rIBO"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"net/http"</span>
</span></span><span><span>    <span>"time"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>hello</span><span>(</span><span>w</span> <span>http</span><span>.</span><span>ResponseWriter</span><span>,</span> <span>req</span> <span>*</span><span>http</span><span>.</span><span>Request</span><span>)</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>A <code>context.Context</code> is created for each request by the <code>net/http</code> machinery, and is available with the <code>Context()</code> method.</p></td><td><pre><code><span><span>    <span>ctx</span> <span>:=</span> <span>req</span><span>.</span><span>Context</span><span>()</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"server: hello handler started"</span><span>)</span>
</span></span><span><span>    <span>defer</span> <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"server: hello handler ended"</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Wait for a few seconds before sending a reply to the client. This could simulate some work the server is doing. While working, keep an eye on the context’s <code>Done()</code> channel for a signal that we should cancel the work and return as soon as possible.</p></td><td><pre><code><span><span>    <span>select</span> <span>{</span>
</span></span><span><span>    <span>case</span> <span>&lt;-</span><span>time</span><span>.</span><span>After</span><span>(</span><span>10</span> <span>*</span> <span>time</span><span>.</span><span>Second</span><span>):</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Fprintf</span><span>(</span><span>w</span><span>,</span> <span>"hello\n"</span><span>)</span>
</span></span><span><span>    <span>case</span> <span>&lt;-</span><span>ctx</span><span>.</span><span>Done</span><span>():</span></span></span></code></pre></td></tr><tr><td><p>The context’s <code>Err()</code> method returns an error that explains why the <code>Done()</code> channel was closed.</p></td><td><pre><code><span><span>        <span>err</span> <span>:=</span> <span>ctx</span><span>.</span><span>Err</span><span>()</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"server:"</span><span>,</span> <span>err</span><span>)</span>
</span></span><span><span>        <span>internalError</span> <span>:=</span> <span>http</span><span>.</span><span>StatusInternalServerError</span>
</span></span><span><span>        <span>http</span><span>.</span><span>Error</span><span>(</span><span>w</span><span>,</span> <span>err</span><span>.</span><span>Error</span><span>(),</span> <span>internalError</span><span>)</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>As before, we register our handler on the “/hello” route, and start serving.</p></td><td><pre><code><span><span>    <span>http</span><span>.</span><span>HandleFunc</span><span>(</span><span>"/hello"</span><span>,</span> <span>hello</span><span>)</span>
</span></span><span><span>    <span>http</span><span>.</span><span>ListenAndServe</span><span>(</span><span>":8090"</span><span>,</span> <span>nil</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td><p>Run the server in the background.</p></td><td><pre><code><span><span><span>$</span> go run context.go &amp;</span></span></code></pre></td></tr><tr><td><p>Simulate a client request to <code>/hello</code>, hitting Ctrl+C shortly after starting to signal cancellation.</p></td><td><pre><code><span><span><span>$</span> curl localhost:8090/hello
</span></span><span><span><span>server: hello handler started
</span></span></span><span><span><span>^C
</span></span></span><span><span><span>server: context canceled
</span></span></span><span><span><span>server: hello handler ended</span></span></span></code></pre></td></tr></tbody></table>

Next example: [Spawning Processes](https://gobyexample.com/spawning-processes).
