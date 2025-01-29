---
Description: Go by Example: Line Filters
Notes: A line filter is a common type of program that reads
input on stdin, processes it, and then prints some
derived result to stdout. grep and sed are common
line filters.
author: 
Url: https://gobyexample.com/line-filters
Created: "2025-01-29  02:48:00"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Line Filters

source: https://gobyexample.com/line-filters

> ## Excerpt
> A line filter is a common type of program that reads
input on stdin, processes it, and then prints some
derived result to stdout. grep and sed are common
line filters.

---
<table><tbody><tr><td><p>A <em>line filter</em> is a common type of program that reads input on stdin, processes it, and then prints some derived result to stdout. <code>grep</code> and <code>sed</code> are common line filters.</p></td><td></td></tr><tr><td><p>Here’s an example line filter in Go that writes a capitalized version of all input text. You can use this pattern to write your own Go line filters.</p></td><td><a href="https://go.dev/play/p/kNcupWRsYPP"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"bufio"</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"os"</span>
</span></span><span><span>    <span>"strings"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>Wrapping the unbuffered <code>os.Stdin</code> with a buffered scanner gives us a convenient <code>Scan</code> method that advances the scanner to the next token; which is the next line in the default scanner.</p></td><td><pre><code><span><span>    <span>scanner</span> <span>:=</span> <span>bufio</span><span>.</span><span>NewScanner</span><span>(</span><span>os</span><span>.</span><span>Stdin</span><span>)</span></span></span></code></pre></td></tr><tr><td><p><code>Text</code> returns the current token, here the next line, from the input.</p></td><td><pre><code><span><span>    <span>for</span> <span>scanner</span><span>.</span><span>Scan</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span>        <span>ucl</span> <span>:=</span> <span>strings</span><span>.</span><span>ToUpper</span><span>(</span><span>scanner</span><span>.</span><span>Text</span><span>())</span></span></span></code></pre></td></tr><tr><td><p>Write out the uppercased line.</p></td><td><pre><code><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>ucl</span><span>)</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td><p>Check for errors during <code>Scan</code>. End of file is expected and not reported by <code>Scan</code> as an error.</p></td><td><pre><code><span><span>    <span>if</span> <span>err</span> <span>:=</span> <span>scanner</span><span>.</span><span>Err</span><span>();</span> <span>err</span> <span>!=</span> <span>nil</span> <span>{</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Fprintln</span><span>(</span><span>os</span><span>.</span><span>Stderr</span><span>,</span> <span>"error:"</span><span>,</span> <span>err</span><span>)</span>
</span></span><span><span>        <span>os</span><span>.</span><span>Exit</span><span>(</span><span>1</span><span>)</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td><p>To try out our line filter, first make a file with a few lowercase lines.</p></td><td><pre><code><span><span><span>$</span> echo 'hello'   &gt; /tmp/lines
</span></span><span><span><span>$</span> echo 'filter' &gt;&gt; /tmp/lines</span></span></code></pre></td></tr><tr><td><p>Then use the line filter to get uppercase lines.</p></td><td><pre><code><span><span><span>$</span> cat /tmp/lines | go run line-filters.go
</span></span><span><span><span>HELLO
</span></span></span><span><span><span>FILTER</span></span></span></code></pre></td></tr></tbody></table>

Next example: [File Paths](https://gobyexample.com/file-paths).
