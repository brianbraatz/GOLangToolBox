---
Description: Go by Example: HTTP Client
Notes: The Go standard library comes with excellent support
for HTTP clients and servers in the net/http
package. In this example we’ll use it to issue simple
HTTP requests.
author: 
Url: https://gobyexample.com/http-client
Created: "2025-01-29  02:48:34"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: HTTP Client

source: https://gobyexample.com/http-client

> ## Excerpt
> The Go standard library comes with excellent support
for HTTP clients and servers in the net/http
package. In this example we’ll use it to issue simple
HTTP requests.

---
<table><tbody><tr><td><p>The Go standard library comes with excellent support for HTTP clients and servers in the <code>net/http</code> package. In this example we’ll use it to issue simple HTTP requests.</p></td><td><a href="https://go.dev/play/p/vFW_el7oHMk"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"bufio"</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"net/http"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>Issue an HTTP GET request to a server. <code>http.Get</code> is a convenient shortcut around creating an <code>http.Client</code> object and calling its <code>Get</code> method; it uses the <code>http.DefaultClient</code> object which has useful default settings.</p></td><td><pre><code><span><span>    <span>resp</span><span>,</span> <span>err</span> <span>:=</span> <span>http</span><span>.</span><span>Get</span><span>(</span><span>"https://gobyexample.com"</span><span>)</span>
</span></span><span><span>    <span>if</span> <span>err</span> <span>!=</span> <span>nil</span> <span>{</span>
</span></span><span><span>        <span>panic</span><span>(</span><span>err</span><span>)</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span>    <span>defer</span> <span>resp</span><span>.</span><span>Body</span><span>.</span><span>Close</span><span>()</span></span></span></code></pre></td></tr><tr><td><p>Print the HTTP response status.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"Response status:"</span><span>,</span> <span>resp</span><span>.</span><span>Status</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Print the first 5 lines of the response body.</p></td><td><pre><code><span><span>    <span>scanner</span> <span>:=</span> <span>bufio</span><span>.</span><span>NewScanner</span><span>(</span><span>resp</span><span>.</span><span>Body</span><span>)</span>
</span></span><span><span>    <span>for</span> <span>i</span> <span>:=</span> <span>0</span><span>;</span> <span>scanner</span><span>.</span><span>Scan</span><span>()</span> <span>&amp;&amp;</span> <span>i</span> <span>&lt;</span> <span>5</span><span>;</span> <span>i</span><span>++</span> <span>{</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>scanner</span><span>.</span><span>Text</span><span>())</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span>    <span>if</span> <span>err</span> <span>:=</span> <span>scanner</span><span>.</span><span>Err</span><span>();</span> <span>err</span> <span>!=</span> <span>nil</span> <span>{</span>
</span></span><span><span>        <span>panic</span><span>(</span><span>err</span><span>)</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go run http-clients.go
</span></span><span><span><span>Response status: 200 OK
</span></span></span><span><span><span>&lt;!DOCTYPE html&gt;
</span></span></span><span><span><span>&lt;html&gt;
</span></span></span><span><span><span>  &lt;head&gt;
</span></span></span><span><span><span>    &lt;meta charset="utf-8"&gt;
</span></span></span><span><span><span>    &lt;title&gt;Go by Example&lt;/title&gt;</span></span></span></code></pre></td></tr></tbody></table>

Next example: [HTTP Server](https://gobyexample.com/http-server).
