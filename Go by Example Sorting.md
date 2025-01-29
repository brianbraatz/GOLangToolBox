---
Description: Go by Example: Sorting
Notes: Go’s slices package implements sorting for builtins
and user-defined types. We’ll look at sorting for
builtins first.
author: 
Url: https://gobyexample.com/sorting
Created: "2025-01-29  02:45:38"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Sorting

source: https://gobyexample.com/sorting

> ## Excerpt
> Go’s slices package implements sorting for builtins
and user-defined types. We’ll look at sorting for
builtins first.

---
<table><tbody><tr><td><p>Go’s <code>slices</code> package implements sorting for builtins and user-defined types. We’ll look at sorting for builtins first.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/X7iJcIua02T"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"slices"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>Sorting functions are generic, and work for any <em>ordered</em> built-in type. For a list of ordered types, see <a href="https://pkg.go.dev/cmp#Ordered">cmp.Ordered</a>.</p></td><td><pre><code><span><span>    <span>strs</span> <span>:=</span> <span>[]</span><span>string</span><span>{</span><span>"c"</span><span>,</span> <span>"a"</span><span>,</span> <span>"b"</span><span>}</span>
</span></span><span><span>    <span>slices</span><span>.</span><span>Sort</span><span>(</span><span>strs</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"Strings:"</span><span>,</span> <span>strs</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>An example of sorting <code>int</code>s.</p></td><td><pre><code><span><span>    <span>ints</span> <span>:=</span> <span>[]</span><span>int</span><span>{</span><span>7</span><span>,</span> <span>2</span><span>,</span> <span>4</span><span>}</span>
</span></span><span><span>    <span>slices</span><span>.</span><span>Sort</span><span>(</span><span>ints</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"Ints:   "</span><span>,</span> <span>ints</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>We can also use the <code>slices</code> package to check if a slice is already in sorted order.</p></td><td><pre><code><span><span>    <span>s</span> <span>:=</span> <span>slices</span><span>.</span><span>IsSorted</span><span>(</span><span>ints</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"Sorted: "</span><span>,</span> <span>s</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go run sorting.go
</span></span><span><span><span>Strings: [a b c]
</span></span></span><span><span><span>Ints:    [2 4 7]
</span></span></span><span><span><span>Sorted:  true</span></span></span></code></pre></td></tr></tbody></table>

Next example: [Sorting by Functions](https://gobyexample.com/sorting-by-functions).
