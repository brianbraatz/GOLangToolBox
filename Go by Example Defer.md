---
Description: Go by Example: Defer
Notes: Defer is used to ensure that a function call is
performed later in a program’s execution, usually for
purposes of cleanup. defer is often used where e.g.
ensure and finally would be used in other languages.
author: 
Url: https://gobyexample.com/defer
Created: "2025-01-29  02:47:02"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Defer

source: https://gobyexample.com/defer

> ## Excerpt
> Defer is used to ensure that a function call is
performed later in a program’s execution, usually for
purposes of cleanup. defer is often used where e.g.
ensure and finally would be used in other languages.

---
<table><tbody><tr><td><p><em>Defer</em> is used to ensure that a function call is performed later in a program’s execution, usually for purposes of cleanup. <code>defer</code> is often used where e.g. <code>ensure</code> and <code>finally</code> would be used in other languages.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/nhAzhDn_jga"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"os"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Suppose we wanted to create a file, write to it, and then close when we’re done. Here’s how we could do that with <code>defer</code>.</p></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>Immediately after getting a file object with <code>createFile</code>, we defer the closing of that file with <code>closeFile</code>. This will be executed at the end of the enclosing function (<code>main</code>), after <code>writeFile</code> has finished.</p></td><td><pre><code><span><span>    <span>f</span> <span>:=</span> <span>createFile</span><span>(</span><span>"/tmp/defer.txt"</span><span>)</span>
</span></span><span><span>    <span>defer</span> <span>closeFile</span><span>(</span><span>f</span><span>)</span>
</span></span><span><span>    <span>writeFile</span><span>(</span><span>f</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>createFile</span><span>(</span><span>p</span> <span>string</span><span>)</span> <span>*</span><span>os</span><span>.</span><span>File</span> <span>{</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"creating"</span><span>)</span>
</span></span><span><span>    <span>f</span><span>,</span> <span>err</span> <span>:=</span> <span>os</span><span>.</span><span>Create</span><span>(</span><span>p</span><span>)</span>
</span></span><span><span>    <span>if</span> <span>err</span> <span>!=</span> <span>nil</span> <span>{</span>
</span></span><span><span>        <span>panic</span><span>(</span><span>err</span><span>)</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span>    <span>return</span> <span>f</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>writeFile</span><span>(</span><span>f</span> <span>*</span><span>os</span><span>.</span><span>File</span><span>)</span> <span>{</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"writing"</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Fprintln</span><span>(</span><span>f</span><span>,</span> <span>"data"</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td><p>It’s important to check for errors when closing a file, even in a deferred function.</p></td><td><pre><code><span><span><span>func</span> <span>closeFile</span><span>(</span><span>f</span> <span>*</span><span>os</span><span>.</span><span>File</span><span>)</span> <span>{</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"closing"</span><span>)</span>
</span></span><span><span>    <span>err</span> <span>:=</span> <span>f</span><span>.</span><span>Close</span><span>()</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span>    <span>if</span> <span>err</span> <span>!=</span> <span>nil</span> <span>{</span>
</span></span><span><span>        <span>panic</span><span>(</span><span>err</span><span>)</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td><p>Running the program confirms that the file is closed after being written.</p></td><td><pre><code><span><span><span>$</span> go run defer.go
</span></span><span><span><span>creating
</span></span></span><span><span><span>writing
</span></span></span><span><span><span>closing</span></span></span></code></pre></td></tr></tbody></table>

Next example: [Recover](https://gobyexample.com/recover).
