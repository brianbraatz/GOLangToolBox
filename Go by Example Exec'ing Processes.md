---
Description: Go by Example: Exec'ing Processes
Notes: In the previous example we looked at
spawning external processes. We
do this when we need an external process accessible to
a running Go process. Sometimes we just want to
completely replace the current Go process with another
(perhaps non-Go) one. To do this we’ll use Go’s
implementation of the classic
exec
function.
author: 
Url: https://gobyexample.com/execing-processes
Created: "2025-01-29  02:48:46"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Exec'ing Processes

source: https://gobyexample.com/execing-processes

> ## Excerpt
> In the previous example we looked at
spawning external processes. We
do this when we need an external process accessible to
a running Go process. Sometimes we just want to
completely replace the current Go process with another
(perhaps non-Go) one. To do this we’ll use Go’s
implementation of the classic
exec
function.

---
<table><tbody><tr><td><p>In the previous example we looked at <a href="https://gobyexample.com/spawning-processes">spawning external processes</a>. We do this when we need an external process accessible to a running Go process. Sometimes we just want to completely replace the current Go process with another (perhaps non-Go) one. To do this we’ll use Go’s implementation of the classic <a href="https://en.wikipedia.org/wiki/Exec_(operating_system)"><code>exec</code></a> function.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/s9qg7olf1dM"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"os"</span>
</span></span><span><span>    <span>"os/exec"</span>
</span></span><span><span>    <span>"syscall"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>For our example we’ll exec <code>ls</code>. Go requires an absolute path to the binary we want to execute, so we’ll use <code>exec.LookPath</code> to find it (probably <code>/bin/ls</code>).</p></td><td><pre><code><span><span>    <span>binary</span><span>,</span> <span>lookErr</span> <span>:=</span> <span>exec</span><span>.</span><span>LookPath</span><span>(</span><span>"ls"</span><span>)</span>
</span></span><span><span>    <span>if</span> <span>lookErr</span> <span>!=</span> <span>nil</span> <span>{</span>
</span></span><span><span>        <span>panic</span><span>(</span><span>lookErr</span><span>)</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td><p><code>Exec</code> requires arguments in slice form (as opposed to one big string). We’ll give <code>ls</code> a few common arguments. Note that the first argument should be the program name.</p></td><td><pre><code><span><span>    <span>args</span> <span>:=</span> <span>[]</span><span>string</span><span>{</span><span>"ls"</span><span>,</span> <span>"-a"</span><span>,</span> <span>"-l"</span><span>,</span> <span>"-h"</span><span>}</span></span></span></code></pre></td></tr><tr><td><p><code>Exec</code> also needs a set of <a href="https://gobyexample.com/environment-variables">environment variables</a> to use. Here we just provide our current environment.</p></td><td><pre><code><span><span>    <span>env</span> <span>:=</span> <span>os</span><span>.</span><span>Environ</span><span>()</span></span></span></code></pre></td></tr><tr><td><p>Here’s the actual <code>syscall.Exec</code> call. If this call is successful, the execution of our process will end here and be replaced by the <code>/bin/ls -a -l -h</code> process. If there is an error we’ll get a return value.</p></td><td><pre><code><span><span>    <span>execErr</span> <span>:=</span> <span>syscall</span><span>.</span><span>Exec</span><span>(</span><span>binary</span><span>,</span> <span>args</span><span>,</span> <span>env</span><span>)</span>
</span></span><span><span>    <span>if</span> <span>execErr</span> <span>!=</span> <span>nil</span> <span>{</span>
</span></span><span><span>        <span>panic</span><span>(</span><span>execErr</span><span>)</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td><p>When we run our program it is replaced by <code>ls</code>.</p></td><td><pre><code><span><span><span>$</span> go run execing-processes.go
</span></span><span><span><span>total 16
</span></span></span><span><span><span>drwxr-xr-x  4 mark 136B Oct 3 16:29 .
</span></span></span><span><span><span>drwxr-xr-x 91 mark 3.0K Oct 3 12:50 ..
</span></span></span><span><span><span>-rw-r--r--  1 mark 1.3K Oct 3 16:28 execing-processes.go</span></span></span></code></pre></td></tr><tr><td><p>Note that Go does not offer a classic Unix <code>fork</code> function. Usually this isn’t an issue though, since starting goroutines, spawning processes, and exec’ing processes covers most use cases for <code>fork</code>.</p></td><td></td></tr></tbody></table>

Next example: [Signals](https://gobyexample.com/signals).
