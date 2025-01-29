---
Description: Go by Example: Hello World
Notes: Our first program will print the classic “hello world”
message. Here’s the full source code.
author: 
Url: https://gobyexample.com/hello-world
Created: "2025-01-29  02:41:53"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Hello World

source: https://gobyexample.com/hello-world

> ## Excerpt
> Our first program will print the classic “hello world”
message. Here’s the full source code.

---
<table><tbody><tr><td><p>Our first program will print the classic “hello world” message. Here’s the full source code.</p></td><td><a href="https://go.dev/play/p/NeviD0awXjt"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>"fmt"</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"hello world"</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td><p>To run the program, put the code in <code>hello-world.go</code> and use <code>go run</code>.</p></td><td><pre><code><span><span><span>$</span> go run hello-world.go
</span></span><span><span><span>hello world</span></span></span></code></pre></td></tr><tr><td><p>Sometimes we’ll want to build our programs into binaries. We can do this using <code>go build</code>.</p></td><td><pre><code><span><span><span>$</span> go build hello-world.go
</span></span><span><span><span>$</span> ls
</span></span><span><span><span>hello-world    hello-world.go</span></span></span></code></pre></td></tr><tr><td><p>We can then execute the built binary directly.</p></td><td><pre><code><span><span><span>$</span> ./hello-world
</span></span><span><span><span>hello world</span></span></span></code></pre></td></tr><tr><td><p>Now that we can run and build basic Go programs, let’s learn more about the language.</p></td><td></td></tr></tbody></table>

Next example: [Values](https://gobyexample.com/values).
