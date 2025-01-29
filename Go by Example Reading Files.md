---
Description: Go by Example: Reading Files
Notes: Reading and writing files are basic tasks needed for
many Go programs. First we’ll look at some examples of
reading files.
author: 
Url: https://gobyexample.com/reading-files
Created: "2025-01-29  02:47:54"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Reading Files

source: https://gobyexample.com/reading-files

> ## Excerpt
> Reading and writing files are basic tasks needed for
many Go programs. First we’ll look at some examples of
reading files.

---
<table><tbody><tr><td><p>Reading and writing files are basic tasks needed for many Go programs. First we’ll look at some examples of reading files.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/SKTzfpnV0To"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"bufio"</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"io"</span>
</span></span><span><span>    <span>"os"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Reading files requires checking most calls for errors. This helper will streamline our error checks below.</p></td><td><pre><code><span><span><span>func</span> <span>check</span><span>(</span><span>e</span> <span>error</span><span>)</span> <span>{</span>
</span></span><span><span>    <span>if</span> <span>e</span> <span>!=</span> <span>nil</span> <span>{</span>
</span></span><span><span>        <span>panic</span><span>(</span><span>e</span><span>)</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>Perhaps the most basic file reading task is slurping a file’s entire contents into memory.</p></td><td><pre><code><span><span>    <span>dat</span><span>,</span> <span>err</span> <span>:=</span> <span>os</span><span>.</span><span>ReadFile</span><span>(</span><span>"/tmp/dat"</span><span>)</span>
</span></span><span><span>    <span>check</span><span>(</span><span>err</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Print</span><span>(</span><span>string</span><span>(</span><span>dat</span><span>))</span></span></span></code></pre></td></tr><tr><td><p>You’ll often want more control over how and what parts of a file are read. For these tasks, start by <code>Open</code>ing a file to obtain an <code>os.File</code> value.</p></td><td><pre><code><span><span>    <span>f</span><span>,</span> <span>err</span> <span>:=</span> <span>os</span><span>.</span><span>Open</span><span>(</span><span>"/tmp/dat"</span><span>)</span>
</span></span><span><span>    <span>check</span><span>(</span><span>err</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Read some bytes from the beginning of the file. Allow up to 5 to be read but also note how many actually were read.</p></td><td><pre><code><span><span>    <span>b1</span> <span>:=</span> <span>make</span><span>([]</span><span>byte</span><span>,</span> <span>5</span><span>)</span>
</span></span><span><span>    <span>n1</span><span>,</span> <span>err</span> <span>:=</span> <span>f</span><span>.</span><span>Read</span><span>(</span><span>b1</span><span>)</span>
</span></span><span><span>    <span>check</span><span>(</span><span>err</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Printf</span><span>(</span><span>"%d bytes: %s\n"</span><span>,</span> <span>n1</span><span>,</span> <span>string</span><span>(</span><span>b1</span><span>[:</span><span>n1</span><span>]))</span></span></span></code></pre></td></tr><tr><td><p>You can also <code>Seek</code> to a known location in the file and <code>Read</code> from there.</p></td><td><pre><code><span><span>    <span>o2</span><span>,</span> <span>err</span> <span>:=</span> <span>f</span><span>.</span><span>Seek</span><span>(</span><span>6</span><span>,</span> <span>io</span><span>.</span><span>SeekStart</span><span>)</span>
</span></span><span><span>    <span>check</span><span>(</span><span>err</span><span>)</span>
</span></span><span><span>    <span>b2</span> <span>:=</span> <span>make</span><span>([]</span><span>byte</span><span>,</span> <span>2</span><span>)</span>
</span></span><span><span>    <span>n2</span><span>,</span> <span>err</span> <span>:=</span> <span>f</span><span>.</span><span>Read</span><span>(</span><span>b2</span><span>)</span>
</span></span><span><span>    <span>check</span><span>(</span><span>err</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Printf</span><span>(</span><span>"%d bytes @ %d: "</span><span>,</span> <span>n2</span><span>,</span> <span>o2</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Printf</span><span>(</span><span>"%v\n"</span><span>,</span> <span>string</span><span>(</span><span>b2</span><span>[:</span><span>n2</span><span>]))</span></span></span></code></pre></td></tr><tr><td><p>Other methods of seeking are relative to the current cursor position,</p></td><td><pre><code><span><span>    <span>_</span><span>,</span> <span>err</span> <span>=</span> <span>f</span><span>.</span><span>Seek</span><span>(</span><span>2</span><span>,</span> <span>io</span><span>.</span><span>SeekCurrent</span><span>)</span>
</span></span><span><span>    <span>check</span><span>(</span><span>err</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>and relative to the end of the file.</p></td><td><pre><code><span><span>    <span>_</span><span>,</span> <span>err</span> <span>=</span> <span>f</span><span>.</span><span>Seek</span><span>(</span><span>-</span><span>4</span><span>,</span> <span>io</span><span>.</span><span>SeekEnd</span><span>)</span>
</span></span><span><span>    <span>check</span><span>(</span><span>err</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>The <code>io</code> package provides some functions that may be helpful for file reading. For example, reads like the ones above can be more robustly implemented with <code>ReadAtLeast</code>.</p></td><td><pre><code><span><span>    <span>o3</span><span>,</span> <span>err</span> <span>:=</span> <span>f</span><span>.</span><span>Seek</span><span>(</span><span>6</span><span>,</span> <span>io</span><span>.</span><span>SeekStart</span><span>)</span>
</span></span><span><span>    <span>check</span><span>(</span><span>err</span><span>)</span>
</span></span><span><span>    <span>b3</span> <span>:=</span> <span>make</span><span>([]</span><span>byte</span><span>,</span> <span>2</span><span>)</span>
</span></span><span><span>    <span>n3</span><span>,</span> <span>err</span> <span>:=</span> <span>io</span><span>.</span><span>ReadAtLeast</span><span>(</span><span>f</span><span>,</span> <span>b3</span><span>,</span> <span>2</span><span>)</span>
</span></span><span><span>    <span>check</span><span>(</span><span>err</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Printf</span><span>(</span><span>"%d bytes @ %d: %s\n"</span><span>,</span> <span>n3</span><span>,</span> <span>o3</span><span>,</span> <span>string</span><span>(</span><span>b3</span><span>))</span></span></span></code></pre></td></tr><tr><td><p>There is no built-in rewind, but <code>Seek(0, io.SeekStart)</code> accomplishes this.</p></td><td><pre><code><span><span>    <span>_</span><span>,</span> <span>err</span> <span>=</span> <span>f</span><span>.</span><span>Seek</span><span>(</span><span>0</span><span>,</span> <span>io</span><span>.</span><span>SeekStart</span><span>)</span>
</span></span><span><span>    <span>check</span><span>(</span><span>err</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>The <code>bufio</code> package implements a buffered reader that may be useful both for its efficiency with many small reads and because of the additional reading methods it provides.</p></td><td><pre><code><span><span>    <span>r4</span> <span>:=</span> <span>bufio</span><span>.</span><span>NewReader</span><span>(</span><span>f</span><span>)</span>
</span></span><span><span>    <span>b4</span><span>,</span> <span>err</span> <span>:=</span> <span>r4</span><span>.</span><span>Peek</span><span>(</span><span>5</span><span>)</span>
</span></span><span><span>    <span>check</span><span>(</span><span>err</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Printf</span><span>(</span><span>"5 bytes: %s\n"</span><span>,</span> <span>string</span><span>(</span><span>b4</span><span>))</span></span></span></code></pre></td></tr><tr><td><p>Close the file when you’re done (usually this would be scheduled immediately after <code>Open</code>ing with <code>defer</code>).</p></td><td><pre><code><span><span>    <span>f</span><span>.</span><span>Close</span><span>()</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> echo "hello" &gt; /tmp/dat
</span></span><span><span><span>$</span> echo "go" &gt;&gt;   /tmp/dat
</span></span><span><span><span>$</span> go run reading-files.go
</span></span><span><span><span>hello
</span></span></span><span><span><span>go
</span></span></span><span><span><span>5 bytes: hello
</span></span></span><span><span><span>2 bytes @ 6: go
</span></span></span><span><span><span>2 bytes @ 6: go
</span></span></span><span><span><span>5 bytes: hello</span></span></span></code></pre></td></tr><tr><td><p>Next we’ll look at writing files.</p></td><td></td></tr></tbody></table>

Next example: [Writing Files](https://gobyexample.com/writing-files).
