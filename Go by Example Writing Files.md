---
Description: Go by Example: Writing Files
Notes: Writing files in Go follows similar patterns to the
ones we saw earlier for reading.
author: 
Url: https://gobyexample.com/writing-files
Created: "2025-01-29  02:47:57"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Writing Files

source: https://gobyexample.com/writing-files

> ## Excerpt
> Writing files in Go follows similar patterns to the
ones we saw earlier for reading.

---
<table><tbody><tr><td><p>Writing files in Go follows similar patterns to the ones we saw earlier for reading.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/Y12O-L_zFS1"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"bufio"</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"os"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>check</span><span>(</span><span>e</span> <span>error</span><span>)</span> <span>{</span>
</span></span><span><span>    <span>if</span> <span>e</span> <span>!=</span> <span>nil</span> <span>{</span>
</span></span><span><span>        <span>panic</span><span>(</span><span>e</span><span>)</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>To start, here’s how to dump a string (or just bytes) into a file.</p></td><td><pre><code><span><span>    <span>d1</span> <span>:=</span> <span>[]</span><span>byte</span><span>(</span><span>"hello\ngo\n"</span><span>)</span>
</span></span><span><span>    <span>err</span> <span>:=</span> <span>os</span><span>.</span><span>WriteFile</span><span>(</span><span>"/tmp/dat1"</span><span>,</span> <span>d1</span><span>,</span> <span>0644</span><span>)</span>
</span></span><span><span>    <span>check</span><span>(</span><span>err</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>For more granular writes, open a file for writing.</p></td><td><pre><code><span><span>    <span>f</span><span>,</span> <span>err</span> <span>:=</span> <span>os</span><span>.</span><span>Create</span><span>(</span><span>"/tmp/dat2"</span><span>)</span>
</span></span><span><span>    <span>check</span><span>(</span><span>err</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>It’s idiomatic to defer a <code>Close</code> immediately after opening a file.</p></td><td><pre><code><span><span>    <span>defer</span> <span>f</span><span>.</span><span>Close</span><span>()</span></span></span></code></pre></td></tr><tr><td><p>You can <code>Write</code> byte slices as you’d expect.</p></td><td><pre><code><span><span>    <span>d2</span> <span>:=</span> <span>[]</span><span>byte</span><span>{</span><span>115</span><span>,</span> <span>111</span><span>,</span> <span>109</span><span>,</span> <span>101</span><span>,</span> <span>10</span><span>}</span>
</span></span><span><span>    <span>n2</span><span>,</span> <span>err</span> <span>:=</span> <span>f</span><span>.</span><span>Write</span><span>(</span><span>d2</span><span>)</span>
</span></span><span><span>    <span>check</span><span>(</span><span>err</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Printf</span><span>(</span><span>"wrote %d bytes\n"</span><span>,</span> <span>n2</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>A <code>WriteString</code> is also available.</p></td><td><pre><code><span><span>    <span>n3</span><span>,</span> <span>err</span> <span>:=</span> <span>f</span><span>.</span><span>WriteString</span><span>(</span><span>"writes\n"</span><span>)</span>
</span></span><span><span>    <span>check</span><span>(</span><span>err</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Printf</span><span>(</span><span>"wrote %d bytes\n"</span><span>,</span> <span>n3</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Issue a <code>Sync</code> to flush writes to stable storage.</p></td><td><pre><code><span><span>    <span>f</span><span>.</span><span>Sync</span><span>()</span></span></span></code></pre></td></tr><tr><td><p><code>bufio</code> provides buffered writers in addition to the buffered readers we saw earlier.</p></td><td><pre><code><span><span>    <span>w</span> <span>:=</span> <span>bufio</span><span>.</span><span>NewWriter</span><span>(</span><span>f</span><span>)</span>
</span></span><span><span>    <span>n4</span><span>,</span> <span>err</span> <span>:=</span> <span>w</span><span>.</span><span>WriteString</span><span>(</span><span>"buffered\n"</span><span>)</span>
</span></span><span><span>    <span>check</span><span>(</span><span>err</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Printf</span><span>(</span><span>"wrote %d bytes\n"</span><span>,</span> <span>n4</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Use <code>Flush</code> to ensure all buffered operations have been applied to the underlying writer.</p></td><td><pre><code><span><span>    <span>w</span><span>.</span><span>Flush</span><span>()</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td><p>Try running the file-writing code.</p></td><td><pre><code><span><span><span>$</span> go run writing-files.go 
</span></span><span><span><span>wrote 5 bytes
</span></span></span><span><span><span>wrote 7 bytes
</span></span></span><span><span><span>wrote 9 bytes</span></span></span></code></pre></td></tr><tr><td><p>Then check the contents of the written files.</p></td><td><pre><code><span><span><span>$</span> cat /tmp/dat1
</span></span><span><span><span>hello
</span></span></span><span><span><span>go
</span></span></span><span><span><span></span><span>$</span> cat /tmp/dat2
</span></span><span><span><span>some
</span></span></span><span><span><span>writes
</span></span></span><span><span><span>buffered</span></span></span></code></pre></td></tr><tr><td><p>Next we’ll look at applying some of the file I/O ideas we’ve just seen to the <code>stdin</code> and <code>stdout</code> streams.</p></td><td></td></tr></tbody></table>

Next example: [Line Filters](https://gobyexample.com/line-filters).
