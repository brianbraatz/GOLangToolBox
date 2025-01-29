---
Description: Go by Example: Embed Directive
Notes: //go:embed is a compiler
directive that
allows programs to include arbitrary files and folders in the Go binary at
build time. Read more about the embed directive
here.
author: 
Url: https://gobyexample.com/embed-directive
Created: "2025-01-29  02:48:11"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Embed Directive

source: https://gobyexample.com/embed-directive

> ## Excerpt
> //go:embed is a compiler
directive that
allows programs to include arbitrary files and folders in the Go binary at
build time. Read more about the embed directive
here.

---
<table><tbody><tr><td><p><code>//go:embed</code> is a <a href="https://pkg.go.dev/cmd/compile#hdr-Compiler_Directives">compiler directive</a> that allows programs to include arbitrary files and folders in the Go binary at build time. Read more about the embed directive <a href="https://pkg.go.dev/embed">here</a>.</p></td><td><a href="https://go.dev/play/p/6m2ll-D52BB"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td><p>Import the <code>embed</code> package; if you don’t use any exported identifiers from this package, you can do a blank import with <code>_ "embed"</code>.</p></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"embed"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td><p><code>embed</code> directives accept paths relative to the directory containing the Go source file. This directive embeds the contents of the file into the <code>string</code> variable immediately following it.</p></td><td><pre><code><span><span><span>//go:embed folder/single_file.txt
</span></span></span><span><span><span></span><span>var</span> <span>fileString</span> <span>string</span></span></span></code></pre></td></tr><tr><td><p>Or embed the contents of the file into a <code>[]byte</code>.</p></td><td><pre><code><span><span><span>//go:embed folder/single_file.txt
</span></span></span><span><span><span></span><span>var</span> <span>fileByte</span> <span>[]</span><span>byte</span></span></span></code></pre></td></tr><tr><td><p>We can also embed multiple files or even folders with wildcards. This uses a variable of the <a href="https://pkg.go.dev/embed#FS">embed.FS type</a>, which implements a simple virtual file system.</p></td><td><pre><code><span><span><span>//go:embed folder/single_file.txt
</span></span></span><span><span><span>//go:embed folder/*.hash
</span></span></span><span><span><span></span><span>var</span> <span>folder</span> <span>embed</span><span>.</span><span>FS</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>Print out the contents of <code>single_file.txt</code>.</p></td><td><pre><code><span><span>    <span>print</span><span>(</span><span>fileString</span><span>)</span>
</span></span><span><span>    <span>print</span><span>(</span><span>string</span><span>(</span><span>fileByte</span><span>))</span></span></span></code></pre></td></tr><tr><td><p>Retrieve some files from the embedded folder.</p></td><td><pre><code><span><span>    <span>content1</span><span>,</span> <span>_</span> <span>:=</span> <span>folder</span><span>.</span><span>ReadFile</span><span>(</span><span>"folder/file1.hash"</span><span>)</span>
</span></span><span><span>    <span>print</span><span>(</span><span>string</span><span>(</span><span>content1</span><span>))</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span>    <span>content2</span><span>,</span> <span>_</span> <span>:=</span> <span>folder</span><span>.</span><span>ReadFile</span><span>(</span><span>"folder/file2.hash"</span><span>)</span>
</span></span><span><span>    <span>print</span><span>(</span><span>string</span><span>(</span><span>content2</span><span>))</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td><p>Use these commands to run the example. (Note: due to limitation on go playground, this example can only be run on your local machine.)</p></td><td><pre><code><span><span><span>$</span> mkdir -p folder
</span></span><span><span><span>$</span> echo "hello go" &gt; folder/single_file.txt
</span></span><span><span><span>$</span> echo "123" &gt; folder/file1.hash
</span></span><span><span><span>$</span> echo "456" &gt; folder/file2.hash</span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>$</span> go run embed-directive.go
</span></span><span><span><span>hello go
</span></span></span><span><span><span>hello go
</span></span></span><span><span><span>123
</span></span></span><span><span><span>456</span></span></span></code></pre></td></tr></tbody></table>

Next example: [Testing and Benchmarking](https://gobyexample.com/testing-and-benchmarking).
