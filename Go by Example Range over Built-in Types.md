---
Description: Go by Example: Range over Built-in Types
Notes: range iterates over elements in a variety of
built-in data structures. Let’s see how to
use range with some of the data structures
we’ve already learned.
author: 
Url: https://gobyexample.com/range-over-built-in-types
Created: "2025-01-29  02:42:58"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Range over Built-in Types

source: https://gobyexample.com/range-over-built-in-types

> ## Excerpt
> range iterates over elements in a variety of
built-in data structures. Let’s see how to
use range with some of the data structures
we’ve already learned.

---
<table><tbody><tr><td><p><em>range</em> iterates over elements in a variety of built-in data structures. Let’s see how to use <code>range</code> with some of the data structures we’ve already learned.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/S171w0PjgsD"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>"fmt"</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>Here we use <code>range</code> to sum the numbers in a slice. Arrays work like this too.</p></td><td><pre><code><span><span>    <span>nums</span> <span>:=</span> <span>[]</span><span>int</span><span>{</span><span>2</span><span>,</span> <span>3</span><span>,</span> <span>4</span><span>}</span>
</span></span><span><span>    <span>sum</span> <span>:=</span> <span>0</span>
</span></span><span><span>    <span>for</span> <span>_</span><span>,</span> <span>num</span> <span>:=</span> <span>range</span> <span>nums</span> <span>{</span>
</span></span><span><span>        <span>sum</span> <span>+=</span> <span>num</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"sum:"</span><span>,</span> <span>sum</span><span>)</span></span></span></code></pre></td></tr><tr><td><p><code>range</code> on arrays and slices provides both the index and value for each entry. Above we didn’t need the index, so we ignored it with the blank identifier <code>_</code>. Sometimes we actually want the indexes though.</p></td><td><pre><code><span><span>    <span>for</span> <span>i</span><span>,</span> <span>num</span> <span>:=</span> <span>range</span> <span>nums</span> <span>{</span>
</span></span><span><span>        <span>if</span> <span>num</span> <span>==</span> <span>3</span> <span>{</span>
</span></span><span><span>            <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"index:"</span><span>,</span> <span>i</span><span>)</span>
</span></span><span><span>        <span>}</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td><p><code>range</code> on map iterates over key/value pairs.</p></td><td><pre><code><span><span>    <span>kvs</span> <span>:=</span> <span>map</span><span>[</span><span>string</span><span>]</span><span>string</span><span>{</span><span>"a"</span><span>:</span> <span>"apple"</span><span>,</span> <span>"b"</span><span>:</span> <span>"banana"</span><span>}</span>
</span></span><span><span>    <span>for</span> <span>k</span><span>,</span> <span>v</span> <span>:=</span> <span>range</span> <span>kvs</span> <span>{</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Printf</span><span>(</span><span>"%s -&gt; %s\n"</span><span>,</span> <span>k</span><span>,</span> <span>v</span><span>)</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td><p><code>range</code> can also iterate over just the keys of a map.</p></td><td><pre><code><span><span>    <span>for</span> <span>k</span> <span>:=</span> <span>range</span> <span>kvs</span> <span>{</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"key:"</span><span>,</span> <span>k</span><span>)</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td><p><code>range</code> on strings iterates over Unicode code points. The first value is the starting byte index of the <code>rune</code> and the second the <code>rune</code> itself. See <a href="https://gobyexample.com/strings-and-runes">Strings and Runes</a> for more details.</p></td><td><pre><code><span><span>    <span>for</span> <span>i</span><span>,</span> <span>c</span> <span>:=</span> <span>range</span> <span>"go"</span> <span>{</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>i</span><span>,</span> <span>c</span><span>)</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go run range-over-built-in-types.go
</span></span><span><span><span>sum: 9
</span></span></span><span><span><span>index: 1
</span></span></span><span><span><span>a -&gt; apple
</span></span></span><span><span><span>b -&gt; banana
</span></span></span><span><span><span>key: a
</span></span></span><span><span><span>key: b
</span></span></span><span><span><span>0 103
</span></span></span><span><span><span>1 111</span></span></span></code></pre></td></tr></tbody></table>

Next example: [Pointers](https://gobyexample.com/pointers).
