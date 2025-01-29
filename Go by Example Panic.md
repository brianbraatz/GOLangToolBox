---
Description: Go by Example: Panic
Notes: A panic typically means something went unexpectedly
wrong. Mostly we use it to fail fast on errors that
shouldn’t occur during normal operation, or that we
aren’t prepared to handle gracefully.
author: 
Url: https://gobyexample.com/panic
Created: "2025-01-29  02:45:45"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Panic

source: https://gobyexample.com/panic

> ## Excerpt
> A panic typically means something went unexpectedly
wrong. Mostly we use it to fail fast on errors that
shouldn’t occur during normal operation, or that we
aren’t prepared to handle gracefully.

---
<table><tbody><tr><td><p>A <code>panic</code> typically means something went unexpectedly wrong. Mostly we use it to fail fast on errors that shouldn’t occur during normal operation, or that we aren’t prepared to handle gracefully.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/9-2vCvRuhmE"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>"os"</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>We’ll use panic throughout this site to check for unexpected errors. This is the only program on the site designed to panic.</p></td><td><pre><code><span><span>    <span>panic</span><span>(</span><span>"a problem"</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>A common use of panic is to abort if a function returns an error value that we don’t know how to (or want to) handle. Here’s an example of <code>panic</code>king if we get an unexpected error when creating a new file.</p></td><td><pre><code><span><span>    <span>_</span><span>,</span> <span>err</span> <span>:=</span> <span>os</span><span>.</span><span>Create</span><span>(</span><span>"/tmp/file"</span><span>)</span>
</span></span><span><span>    <span>if</span> <span>err</span> <span>!=</span> <span>nil</span> <span>{</span>
</span></span><span><span>        <span>panic</span><span>(</span><span>err</span><span>)</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td><p>Running this program will cause it to panic, print an error message and goroutine traces, and exit with a non-zero status.</p></td><td></td></tr><tr><td><p>When first panic in <code>main</code> fires, the program exits without reaching the rest of the code. If you’d like to see the program try to create a temp file, comment the first panic out.</p></td><td><pre><code><span><span><span>$</span> go run panic.go
</span></span><span><span><span>panic: a problem</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>goroutine 1 [running]:
</span></span></span><span><span><span>main.main()
</span></span></span><span><span><span>    /.../panic.go:12 +0x47
</span></span></span><span><span><span>...
</span></span></span><span><span><span>exit status 2</span></span></span></code></pre></td></tr><tr><td><p>Note that unlike some languages which use exceptions for handling of many errors, in Go it is idiomatic to use error-indicating return values wherever possible.</p></td><td></td></tr></tbody></table>

Next example: [Defer](https://gobyexample.com/defer).
