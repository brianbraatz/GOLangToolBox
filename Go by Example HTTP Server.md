---
Description: Go by Example: HTTP Server
Notes: Writing a basic HTTP server is easy using the
net/http package.
author: 
Url: https://gobyexample.com/http-server
Created: "2025-01-29  02:48:37"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: HTTP Server

source: https://gobyexample.com/http-server

> ## Excerpt
> Writing a basic HTTP server is easy using the
net/http package.

---
<table><tbody><tr><td><p>Writing a basic HTTP server is easy using the <code>net/http</code> package.</p></td><td><a href="https://go.dev/play/p/s3xMMt9Ytry"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"net/http"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td><p>A fundamental concept in <code>net/http</code> servers is <em>handlers</em>. A handler is an object implementing the <code>http.Handler</code> interface. A common way to write a handler is by using the <code>http.HandlerFunc</code> adapter on functions with the appropriate signature.</p></td><td><pre><code><span><span><span>func</span> <span>hello</span><span>(</span><span>w</span> <span>http</span><span>.</span><span>ResponseWriter</span><span>,</span> <span>req</span> <span>*</span><span>http</span><span>.</span><span>Request</span><span>)</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>Functions serving as handlers take a <code>http.ResponseWriter</code> and a <code>http.Request</code> as arguments. The response writer is used to fill in the HTTP response. Here our simple response is just “hello\n”.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Fprintf</span><span>(</span><span>w</span><span>,</span> <span>"hello\n"</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>headers</span><span>(</span><span>w</span> <span>http</span><span>.</span><span>ResponseWriter</span><span>,</span> <span>req</span> <span>*</span><span>http</span><span>.</span><span>Request</span><span>)</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>This handler does something a little more sophisticated by reading all the HTTP request headers and echoing them into the response body.</p></td><td><pre><code><span><span>    <span>for</span> <span>name</span><span>,</span> <span>headers</span> <span>:=</span> <span>range</span> <span>req</span><span>.</span><span>Header</span> <span>{</span>
</span></span><span><span>        <span>for</span> <span>_</span><span>,</span> <span>h</span> <span>:=</span> <span>range</span> <span>headers</span> <span>{</span>
</span></span><span><span>            <span>fmt</span><span>.</span><span>Fprintf</span><span>(</span><span>w</span><span>,</span> <span>"%v: %v\n"</span><span>,</span> <span>name</span><span>,</span> <span>h</span><span>)</span>
</span></span><span><span>        <span>}</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>We register our handlers on server routes using the <code>http.HandleFunc</code> convenience function. It sets up the <em>default router</em> in the <code>net/http</code> package and takes a function as an argument.</p></td><td><pre><code><span><span>    <span>http</span><span>.</span><span>HandleFunc</span><span>(</span><span>"/hello"</span><span>,</span> <span>hello</span><span>)</span>
</span></span><span><span>    <span>http</span><span>.</span><span>HandleFunc</span><span>(</span><span>"/headers"</span><span>,</span> <span>headers</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Finally, we call the <code>ListenAndServe</code> with the port and a handler. <code>nil</code> tells it to use the default router we’ve just set up.</p></td><td><pre><code><span><span>    <span>http</span><span>.</span><span>ListenAndServe</span><span>(</span><span>":8090"</span><span>,</span> <span>nil</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td><p>Run the server in the background.</p></td><td><pre><code><span><span><span>$</span> go run http-server.go &amp;</span></span></code></pre></td></tr><tr><td><p>Access the <code>/hello</code> route.</p></td><td><pre><code><span><span><span>$</span> curl localhost:8090/hello
</span></span><span><span><span>hello</span></span></span></code></pre></td></tr></tbody></table>

Next example: [Context](https://gobyexample.com/context).
