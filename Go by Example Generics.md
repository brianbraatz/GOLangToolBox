---
Description: Go by Example: Generics
Notes: Starting with version 1.18, Go has added support for
generics, also known as type parameters.
author: 
Url: https://gobyexample.com/generics
Created: "2025-01-29  02:44:29"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Generics

source: https://gobyexample.com/generics

> ## Excerpt
> Starting with version 1.18, Go has added support for
generics, also known as type parameters.

---
<table><tbody><tr><td><p>Starting with version 1.18, Go has added support for <em>generics</em>, also known as <em>type parameters</em>.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/7v7vElzhAeO"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>"fmt"</span></span></span></code></pre></td></tr><tr><td><p>As an example of a generic function, <code>SlicesIndex</code> takes a slice of any <code>comparable</code> type and an element of that type and returns the index of the first occurrence of v in s, or -1 if not present. The <code>comparable</code> constraint means that we can compare values of this type with the <code>==</code> and <code>!=</code> operators. For a more thorough explanation of this type signature, see <a href="https://go.dev/blog/deconstructing-type-parameters">this blog post</a>. Note that this function exists in the standard library as <a href="https://pkg.go.dev/slices#Index">slices.Index</a>.</p></td><td><pre><code><span><span><span>func</span> <span>SlicesIndex</span><span>[</span><span>S</span> <span>~</span><span>[]</span><span>E</span><span>,</span> <span>E</span> <span>comparable</span><span>](</span><span>s</span> <span>S</span><span>,</span> <span>v</span> <span>E</span><span>)</span> <span>int</span> <span>{</span>
</span></span><span><span>    <span>for</span> <span>i</span> <span>:=</span> <span>range</span> <span>s</span> <span>{</span>
</span></span><span><span>        <span>if</span> <span>v</span> <span>==</span> <span>s</span><span>[</span><span>i</span><span>]</span> <span>{</span>
</span></span><span><span>            <span>return</span> <span>i</span>
</span></span><span><span>        <span>}</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span>    <span>return</span> <span>-</span><span>1</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td><p>As an example of a generic type, <code>List</code> is a singly-linked list with values of any type.</p></td><td><pre><code><span><span><span>type</span> <span>List</span><span>[</span><span>T</span> <span>any</span><span>]</span> <span>struct</span> <span>{</span>
</span></span><span><span>    <span>head</span><span>,</span> <span>tail</span> <span>*</span><span>element</span><span>[</span><span>T</span><span>]</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>type</span> <span>element</span><span>[</span><span>T</span> <span>any</span><span>]</span> <span>struct</span> <span>{</span>
</span></span><span><span>    <span>next</span> <span>*</span><span>element</span><span>[</span><span>T</span><span>]</span>
</span></span><span><span>    <span>val</span>  <span>T</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td><p>We can define methods on generic types just like we do on regular types, but we have to keep the type parameters in place. The type is <code>List[T]</code>, not <code>List</code>.</p></td><td><pre><code><span><span><span>func</span> <span>(</span><span>lst</span> <span>*</span><span>List</span><span>[</span><span>T</span><span>])</span> <span>Push</span><span>(</span><span>v</span> <span>T</span><span>)</span> <span>{</span>
</span></span><span><span>    <span>if</span> <span>lst</span><span>.</span><span>tail</span> <span>==</span> <span>nil</span> <span>{</span>
</span></span><span><span>        <span>lst</span><span>.</span><span>head</span> <span>=</span> <span>&amp;</span><span>element</span><span>[</span><span>T</span><span>]{</span><span>val</span><span>:</span> <span>v</span><span>}</span>
</span></span><span><span>        <span>lst</span><span>.</span><span>tail</span> <span>=</span> <span>lst</span><span>.</span><span>head</span>
</span></span><span><span>    <span>}</span> <span>else</span> <span>{</span>
</span></span><span><span>        <span>lst</span><span>.</span><span>tail</span><span>.</span><span>next</span> <span>=</span> <span>&amp;</span><span>element</span><span>[</span><span>T</span><span>]{</span><span>val</span><span>:</span> <span>v</span><span>}</span>
</span></span><span><span>        <span>lst</span><span>.</span><span>tail</span> <span>=</span> <span>lst</span><span>.</span><span>tail</span><span>.</span><span>next</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td><p>AllElements returns all the List elements as a slice. In the next example we’ll see a more idiomatic way of iterating over all elements of custom types.</p></td><td><pre><code><span><span><span>func</span> <span>(</span><span>lst</span> <span>*</span><span>List</span><span>[</span><span>T</span><span>])</span> <span>AllElements</span><span>()</span> <span>[]</span><span>T</span> <span>{</span>
</span></span><span><span>    <span>var</span> <span>elems</span> <span>[]</span><span>T</span>
</span></span><span><span>    <span>for</span> <span>e</span> <span>:=</span> <span>lst</span><span>.</span><span>head</span><span>;</span> <span>e</span> <span>!=</span> <span>nil</span><span>;</span> <span>e</span> <span>=</span> <span>e</span><span>.</span><span>next</span> <span>{</span>
</span></span><span><span>        <span>elems</span> <span>=</span> <span>append</span><span>(</span><span>elems</span><span>,</span> <span>e</span><span>.</span><span>val</span><span>)</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span>    <span>return</span> <span>elems</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span>
</span></span><span><span>    <span>var</span> <span>s</span> <span>=</span> <span>[]</span><span>string</span><span>{</span><span>"foo"</span><span>,</span> <span>"bar"</span><span>,</span> <span>"zoo"</span><span>}</span></span></span></code></pre></td></tr><tr><td><p>When invoking generic functions, we can often rely on <em>type inference</em>. Note that we don’t have to specify the types for <code>S</code> and <code>E</code> when calling <code>SlicesIndex</code> - the compiler infers them automatically.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"index of zoo:"</span><span>,</span> <span>SlicesIndex</span><span>(</span><span>s</span><span>,</span> <span>"zoo"</span><span>))</span></span></span></code></pre></td></tr><tr><td><p>… though we could also specify them explicitly.</p></td><td><pre><code><span><span>    <span>_</span> <span>=</span> <span>SlicesIndex</span><span>[[]</span><span>string</span><span>,</span> <span>string</span><span>](</span><span>s</span><span>,</span> <span>"zoo"</span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span>    <span>lst</span> <span>:=</span> <span>List</span><span>[</span><span>int</span><span>]{}</span>
</span></span><span><span>    <span>lst</span><span>.</span><span>Push</span><span>(</span><span>10</span><span>)</span>
</span></span><span><span>    <span>lst</span><span>.</span><span>Push</span><span>(</span><span>13</span><span>)</span>
</span></span><span><span>    <span>lst</span><span>.</span><span>Push</span><span>(</span><span>23</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"list:"</span><span>,</span> <span>lst</span><span>.</span><span>AllElements</span><span>())</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go run generics.go
</span></span><span><span><span>index of zoo: 2
</span></span></span><span><span><span>list: [10 13 23]</span></span></span></code></pre></td></tr></tbody></table>

Next example: [Range over Iterators](https://gobyexample.com/range-over-iterators).
