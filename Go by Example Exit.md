---
Description: Go by Example: Exit
Notes: Use os.Exit to immediately exit with a given
status.
author: 
Url: https://gobyexample.com/exit
Created: "2025-01-29  02:46:58"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Exit

source: https://gobyexample.com/exit

> ## Excerpt
> Use os.Exit to immediately exit with a given
status.

---
<table><tbody><tr><td><p>Use <code>os.Exit</code> to immediately exit with a given status.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/b9aYzlENkb__R"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"os"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p><code>defer</code>s will <em>not</em> be run when using <code>os.Exit</code>, so this <code>fmt.Println</code> will never be called.</p></td><td><pre><code><span><span>    <span>defer</span> <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"!"</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Exit with status 3.</p></td><td><pre><code><span><span>    <span>os</span><span>.</span><span>Exit</span><span>(</span><span>3</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td><p>Note that unlike e.g. C, Go does not use an integer return value from <code>main</code> to indicate exit status. If you’d like to exit with a non-zero status you should use <code>os.Exit</code>.</p></td><td></td></tr></tbody></table>

<table><tbody><tr><td><p>If you run <code>exit.go</code> using <code>go run</code>, the exit will be picked up by <code>go</code> and printed.</p></td><td><pre><code><span><span><span>$</span> go run exit.go
</span></span><span><span><span>exit status 3</span></span></span></code></pre></td></tr><tr><td><p>By building and executing a binary you can see the status in the terminal.</p></td><td><pre><code><span><span><span>$</span> go build exit.go
</span></span><span><span><span>$</span> ./exit
</span></span><span><span><span>$</span> echo $?
</span></span><span><span><span>3</span></span></span></code></pre></td></tr><tr><td><p>Note that the <code>!</code> from our program never got printed.</p></td><td></td></tr></tbody></table>
