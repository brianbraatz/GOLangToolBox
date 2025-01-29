---
Description: Go by Example: URL Parsing
Notes: URLs provide a uniform way to locate resources.
Here’s how to parse URLs in Go.
author: 
Url: https://gobyexample.com/url-parsing
Created: "2025-01-29  02:47:46"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: URL Parsing

source: https://gobyexample.com/url-parsing

> ## Excerpt
> URLs provide a uniform way to locate resources.
Here’s how to parse URLs in Go.

---
<table><tbody><tr><td><p>URLs provide a <a href="https://adam.herokuapp.com/past/2010/3/30/urls_are_the_uniform_way_to_locate_resources/">uniform way to locate resources</a>. Here’s how to parse URLs in Go.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/fHTQn9X7l1B"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"net"</span>
</span></span><span><span>    <span>"net/url"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>We’ll parse this example URL, which includes a scheme, authentication info, host, port, path, query params, and query fragment.</p></td><td><pre><code><span><span>    <span>s</span> <span>:=</span> <span>"postgres://user:pass@host.com:5432/path?k=v#f"</span></span></span></code></pre></td></tr><tr><td><p>Parse the URL and ensure there are no errors.</p></td><td><pre><code><span><span>    <span>u</span><span>,</span> <span>err</span> <span>:=</span> <span>url</span><span>.</span><span>Parse</span><span>(</span><span>s</span><span>)</span>
</span></span><span><span>    <span>if</span> <span>err</span> <span>!=</span> <span>nil</span> <span>{</span>
</span></span><span><span>        <span>panic</span><span>(</span><span>err</span><span>)</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td><p>Accessing the scheme is straightforward.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>u</span><span>.</span><span>Scheme</span><span>)</span></span></span></code></pre></td></tr><tr><td><p><code>User</code> contains all authentication info; call <code>Username</code> and <code>Password</code> on this for individual values.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>u</span><span>.</span><span>User</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>u</span><span>.</span><span>User</span><span>.</span><span>Username</span><span>())</span>
</span></span><span><span>    <span>p</span><span>,</span> <span>_</span> <span>:=</span> <span>u</span><span>.</span><span>User</span><span>.</span><span>Password</span><span>()</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>p</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>The <code>Host</code> contains both the hostname and the port, if present. Use <code>SplitHostPort</code> to extract them.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>u</span><span>.</span><span>Host</span><span>)</span>
</span></span><span><span>    <span>host</span><span>,</span> <span>port</span><span>,</span> <span>_</span> <span>:=</span> <span>net</span><span>.</span><span>SplitHostPort</span><span>(</span><span>u</span><span>.</span><span>Host</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>host</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>port</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Here we extract the <code>path</code> and the fragment after the <code>#</code>.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>u</span><span>.</span><span>Path</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>u</span><span>.</span><span>Fragment</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>To get query params in a string of <code>k=v</code> format, use <code>RawQuery</code>. You can also parse query params into a map. The parsed query param maps are from strings to slices of strings, so index into <code>[0]</code> if you only want the first value.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>u</span><span>.</span><span>RawQuery</span><span>)</span>
</span></span><span><span>    <span>m</span><span>,</span> <span>_</span> <span>:=</span> <span>url</span><span>.</span><span>ParseQuery</span><span>(</span><span>u</span><span>.</span><span>RawQuery</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>m</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>m</span><span>[</span><span>"k"</span><span>][</span><span>0</span><span>])</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td><p>Running our URL parsing program shows all the different pieces that we extracted.</p></td><td><pre><code><span><span><span>$</span> go run url-parsing.go 
</span></span><span><span><span>postgres
</span></span></span><span><span><span>user:pass
</span></span></span><span><span><span>user
</span></span></span><span><span><span>pass
</span></span></span><span><span><span>host.com:5432
</span></span></span><span><span><span>host.com
</span></span></span><span><span><span>5432
</span></span></span><span><span><span>/path
</span></span></span><span><span><span>f
</span></span></span><span><span><span>k=v
</span></span></span><span><span><span>map[k:[v]]
</span></span></span><span><span><span>v</span></span></span></code></pre></td></tr></tbody></table>

Next example: [SHA256 Hashes](https://gobyexample.com/sha256-hashes).
