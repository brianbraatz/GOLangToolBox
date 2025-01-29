---
Description: Go by Example: Struct Embedding
Notes: Go supports embedding of structs and interfaces
to express a more seamless composition of types.
This is not to be confused with //go:embed which is
a go directive introduced in Go version 1.16+ to embed
files and folders into the application binary.
author: 
Url: https://gobyexample.com/struct-embedding
Created: "2025-01-29  02:44:26"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Struct Embedding

source: https://gobyexample.com/struct-embedding

> ## Excerpt
> Go supports embedding of structs and interfaces
to express a more seamless composition of types.
This is not to be confused with //go:embed which is
a go directive introduced in Go version 1.16+ to embed
files and folders into the application binary.

---
<table><tbody><tr><td><p>Go supports <em>embedding</em> of structs and interfaces to express a more seamless <em>composition</em> of types. This is not to be confused with <a href="https://gobyexample.com/embed-directive"><code>//go:embed</code></a> which is a go directive introduced in Go version 1.16+ to embed files and folders into the application binary.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/-LOu1L0i2tR"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>"fmt"</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>type</span> <span>base</span> <span>struct</span> <span>{</span>
</span></span><span><span>    <span>num</span> <span>int</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>(</span><span>b</span> <span>base</span><span>)</span> <span>describe</span><span>()</span> <span>string</span> <span>{</span>
</span></span><span><span>    <span>return</span> <span>fmt</span><span>.</span><span>Sprintf</span><span>(</span><span>"base with num=%v"</span><span>,</span> <span>b</span><span>.</span><span>num</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td><p>A <code>container</code> <em>embeds</em> a <code>base</code>. An embedding looks like a field without a name.</p></td><td><pre><code><span><span><span>type</span> <span>container</span> <span>struct</span> <span>{</span>
</span></span><span><span>    <span>base</span>
</span></span><span><span>    <span>str</span> <span>string</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>When creating structs with literals, we have to initialize the embedding explicitly; here the embedded type serves as the field name.</p></td><td><pre><code><span><span>    <span>co</span> <span>:=</span> <span>container</span><span>{</span>
</span></span><span><span>        <span>base</span><span>:</span> <span>base</span><span>{</span>
</span></span><span><span>            <span>num</span><span>:</span> <span>1</span><span>,</span>
</span></span><span><span>        <span>},</span>
</span></span><span><span>        <span>str</span><span>:</span> <span>"some name"</span><span>,</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td><p>We can access the base’s fields directly on <code>co</code>, e.g. <code>co.num</code>.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Printf</span><span>(</span><span>"co={num: %v, str: %v}\n"</span><span>,</span> <span>co</span><span>.</span><span>num</span><span>,</span> <span>co</span><span>.</span><span>str</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Alternatively, we can spell out the full path using the embedded type name.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"also num:"</span><span>,</span> <span>co</span><span>.</span><span>base</span><span>.</span><span>num</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Since <code>container</code> embeds <code>base</code>, the methods of <code>base</code> also become methods of a <code>container</code>. Here we invoke a method that was embedded from <code>base</code> directly on <code>co</code>.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"describe:"</span><span>,</span> <span>co</span><span>.</span><span>describe</span><span>())</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span>    <span>type</span> <span>describer</span> <span>interface</span> <span>{</span>
</span></span><span><span>        <span>describe</span><span>()</span> <span>string</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td><p>Embedding structs with methods may be used to bestow interface implementations onto other structs. Here we see that a <code>container</code> now implements the <code>describer</code> interface because it embeds <code>base</code>.</p></td><td><pre><code><span><span>    <span>var</span> <span>d</span> <span>describer</span> <span>=</span> <span>co</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"describer:"</span><span>,</span> <span>d</span><span>.</span><span>describe</span><span>())</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go run struct-embedding.go
</span></span><span><span><span>co={num: 1, str: some name}
</span></span></span><span><span><span>also num: 1
</span></span></span><span><span><span>describe: base with num=1
</span></span></span><span><span><span>describer: base with num=1</span></span></span></code></pre></td></tr></tbody></table>

Next example: [Generics](https://gobyexample.com/generics).
