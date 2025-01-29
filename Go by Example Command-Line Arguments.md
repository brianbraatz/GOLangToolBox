---
Description: Go by Example: Command-Line Arguments
Notes: Command-line arguments
are a common way to parameterize execution of programs.
For example, go run hello.go uses run and
hello.go arguments to the go program.
author: 
Url: https://gobyexample.com/command-line-arguments
Created: "2025-01-29  02:48:17"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Command-Line Arguments

source: https://gobyexample.com/command-line-arguments

> ## Excerpt
> Command-line arguments
are a common way to parameterize execution of programs.
For example, go run hello.go uses run and
hello.go arguments to the go program.

---
<table><tbody><tr><td><p><a href="https://en.wikipedia.org/wiki/Command-line_interface#Arguments"><em>Command-line arguments</em></a> are a common way to parameterize execution of programs. For example, <code>go run hello.go</code> uses <code>run</code> and <code>hello.go</code> arguments to the <code>go</code> program.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/UYCEvh9d2Zb"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"os"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p><code>os.Args</code> provides access to raw command-line arguments. Note that the first value in this slice is the path to the program, and <code>os.Args[1:]</code> holds the arguments to the program.</p></td><td><pre><code><span><span>    <span>argsWithProg</span> <span>:=</span> <span>os</span><span>.</span><span>Args</span>
</span></span><span><span>    <span>argsWithoutProg</span> <span>:=</span> <span>os</span><span>.</span><span>Args</span><span>[</span><span>1</span><span>:]</span></span></span></code></pre></td></tr><tr><td><p>You can get individual args with normal indexing.</p></td><td><pre><code><span><span>    <span>arg</span> <span>:=</span> <span>os</span><span>.</span><span>Args</span><span>[</span><span>3</span><span>]</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>argsWithProg</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>argsWithoutProg</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>arg</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td><p>To experiment with command-line arguments it’s best to build a binary with <code>go build</code> first.</p></td><td><pre><code><span><span><span>$</span> go build command-line-arguments.go
</span></span><span><span><span>$</span> ./command-line-arguments a b c d
</span></span><span><span><span>[./command-line-arguments a b c d]       
</span></span></span><span><span><span>[a b c d]
</span></span></span><span><span><span>c</span></span></span></code></pre></td></tr><tr><td><p>Next we’ll look at more advanced command-line processing with flags.</p></td><td></td></tr></tbody></table>

Next example: [Command-Line Flags](https://gobyexample.com/command-line-flags).
