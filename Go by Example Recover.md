---
Description: Go by Example: Recover
Notes: Go makes it possible to recover from a panic, by
using the recover built-in function. A recover can
stop a panic from aborting the program and let it
continue with execution instead.
author: 
Url: https://gobyexample.com/recover
Created: "2025-01-29  02:47:05"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Recover

source: https://gobyexample.com/recover

> ## Excerpt
> Go makes it possible to recover from a panic, by
using the recover built-in function. A recover can
stop a panic from aborting the program and let it
continue with execution instead.

---
<table><tbody><tr><td><p>Go makes it possible to <em>recover</em> from a panic, by using the <code>recover</code> built-in function. A <code>recover</code> can stop a <code>panic</code> from aborting the program and let it continue with execution instead.</p></td><td></td></tr><tr><td><p>An example of where this can be useful: a server wouldn’t want to crash if one of the client connections exhibits a critical error. Instead, the server would want to close that connection and continue serving other clients. In fact, this is what Go’s <code>net/http</code> does by default for HTTP servers.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/Sk-SVdofEIZ"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>"fmt"</span></span></span></code></pre></td></tr><tr><td><p>This function panics.</p></td><td><pre><code><span><span><span>func</span> <span>mayPanic</span><span>()</span> <span>{</span>
</span></span><span><span>    <span>panic</span><span>(</span><span>"a problem"</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td><p><code>recover</code> must be called within a deferred function. When the enclosing function panics, the defer will activate and a <code>recover</code> call within it will catch the panic.</p></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>The return value of <code>recover</code> is the error raised in the call to <code>panic</code>.</p></td><td><pre><code><span><span>    <span>defer</span> <span>func</span><span>()</span> <span>{</span>
</span></span><span><span>        <span>if</span> <span>r</span> <span>:=</span> <span>recover</span><span>();</span> <span>r</span> <span>!=</span> <span>nil</span> <span>{</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span>            <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"Recovered. Error:\n"</span><span>,</span> <span>r</span><span>)</span>
</span></span><span><span>        <span>}</span>
</span></span><span><span>    <span>}()</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span>    <span>mayPanic</span><span>()</span></span></span></code></pre></td></tr><tr><td><p>This code will not run, because <code>mayPanic</code> panics. The execution of <code>main</code> stops at the point of the panic and resumes in the deferred closure.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"After mayPanic()"</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go run recover.go
</span></span><span><span><span>Recovered. Error:
</span></span></span><span><span><span> a problem</span></span></span></code></pre></td></tr></tbody></table>

Next example: [String Functions](https://gobyexample.com/string-functions).
