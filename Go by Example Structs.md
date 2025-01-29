---
Description: Go by Example: Structs
Notes: Go’s structs are typed collections of fields.
They’re useful for grouping data together to form
records.
author: 
Url: https://gobyexample.com/structs
Created: "2025-01-29  02:44:13"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Structs

source: https://gobyexample.com/structs

> ## Excerpt
> Go’s structs are typed collections of fields.
They’re useful for grouping data together to form
records.

---
<table><tbody><tr><td><p>Go’s <em>structs</em> are typed collections of fields. They’re useful for grouping data together to form records.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/56SPo-L2nMN"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>"fmt"</span></span></span></code></pre></td></tr><tr><td><p>This <code>person</code> struct type has <code>name</code> and <code>age</code> fields.</p></td><td><pre><code><span><span><span>type</span> <span>person</span> <span>struct</span> <span>{</span>
</span></span><span><span>    <span>name</span> <span>string</span>
</span></span><span><span>    <span>age</span>  <span>int</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td><p><code>newPerson</code> constructs a new person struct with the given name.</p></td><td><pre><code><span><span><span>func</span> <span>newPerson</span><span>(</span><span>name</span> <span>string</span><span>)</span> <span>*</span><span>person</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>Go is a garbage collected language; you can safely return a pointer to a local variable - it will only be cleaned up by the garbage collector when there are no active references to it.</p></td><td><pre><code><span><span>    <span>p</span> <span>:=</span> <span>person</span><span>{</span><span>name</span><span>:</span> <span>name</span><span>}</span>
</span></span><span><span>    <span>p</span><span>.</span><span>age</span> <span>=</span> <span>42</span>
</span></span><span><span>    <span>return</span> <span>&amp;</span><span>p</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>This syntax creates a new struct.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>person</span><span>{</span><span>"Bob"</span><span>,</span> <span>20</span><span>})</span></span></span></code></pre></td></tr><tr><td><p>You can name the fields when initializing a struct.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>person</span><span>{</span><span>name</span><span>:</span> <span>"Alice"</span><span>,</span> <span>age</span><span>:</span> <span>30</span><span>})</span></span></span></code></pre></td></tr><tr><td><p>Omitted fields will be zero-valued.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>person</span><span>{</span><span>name</span><span>:</span> <span>"Fred"</span><span>})</span></span></span></code></pre></td></tr><tr><td><p>An <code>&amp;</code> prefix yields a pointer to the struct.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>&amp;</span><span>person</span><span>{</span><span>name</span><span>:</span> <span>"Ann"</span><span>,</span> <span>age</span><span>:</span> <span>40</span><span>})</span></span></span></code></pre></td></tr><tr><td><p>It’s idiomatic to encapsulate new struct creation in constructor functions</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>newPerson</span><span>(</span><span>"Jon"</span><span>))</span></span></span></code></pre></td></tr><tr><td><p>Access struct fields with a dot.</p></td><td><pre><code><span><span>    <span>s</span> <span>:=</span> <span>person</span><span>{</span><span>name</span><span>:</span> <span>"Sean"</span><span>,</span> <span>age</span><span>:</span> <span>50</span><span>}</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>s</span><span>.</span><span>name</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>You can also use dots with struct pointers - the pointers are automatically dereferenced.</p></td><td><pre><code><span><span>    <span>sp</span> <span>:=</span> <span>&amp;</span><span>s</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>sp</span><span>.</span><span>age</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Structs are mutable.</p></td><td><pre><code><span><span>    <span>sp</span><span>.</span><span>age</span> <span>=</span> <span>51</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>sp</span><span>.</span><span>age</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>If a struct type is only used for a single value, we don’t have to give it a name. The value can have an anonymous struct type. This technique is commonly used for <a href="https://gobyexample.com/testing-and-benchmarking">table-driven tests</a>.</p></td><td><pre><code><span><span>    <span>dog</span> <span>:=</span> <span>struct</span> <span>{</span>
</span></span><span><span>        <span>name</span>   <span>string</span>
</span></span><span><span>        <span>isGood</span> <span>bool</span>
</span></span><span><span>    <span>}{</span>
</span></span><span><span>        <span>"Rex"</span><span>,</span>
</span></span><span><span>        <span>true</span><span>,</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>dog</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go run structs.go
</span></span><span><span><span>{Bob 20}
</span></span></span><span><span><span>{Alice 30}
</span></span></span><span><span><span>{Fred 0}
</span></span></span><span><span><span>&amp;{Ann 40}
</span></span></span><span><span><span>&amp;{Jon 42}
</span></span></span><span><span><span>Sean
</span></span></span><span><span><span>50
</span></span></span><span><span><span>51
</span></span></span><span><span><span>{Rex true}</span></span></span></code></pre></td></tr></tbody></table>

Next example: [Methods](https://gobyexample.com/methods).
