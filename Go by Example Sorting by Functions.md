---
Description: Go by Example: Sorting by Functions
Notes: Sometimes we’ll want to sort a collection by something
other than its natural order. For example, suppose we
wanted to sort strings by their length instead of
alphabetically. Here’s an example of custom sorts
in Go.
author: 
Url: https://gobyexample.com/sorting-by-functions
Created: "2025-01-29  02:45:42"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Sorting by Functions

source: https://gobyexample.com/sorting-by-functions

> ## Excerpt
> Sometimes we’ll want to sort a collection by something
other than its natural order. For example, suppose we
wanted to sort strings by their length instead of
alphabetically. Here’s an example of custom sorts
in Go.

---
<table><tbody><tr><td><p>Sometimes we’ll want to sort a collection by something other than its natural order. For example, suppose we wanted to sort strings by their length instead of alphabetically. Here’s an example of custom sorts in Go.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/3EaTknAZHMu"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"cmp"</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"slices"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span>
</span></span><span><span>    <span>fruits</span> <span>:=</span> <span>[]</span><span>string</span><span>{</span><span>"peach"</span><span>,</span> <span>"banana"</span><span>,</span> <span>"kiwi"</span><span>}</span></span></span></code></pre></td></tr><tr><td><p>We implement a comparison function for string lengths. <code>cmp.Compare</code> is helpful for this.</p></td><td><pre><code><span><span>    <span>lenCmp</span> <span>:=</span> <span>func</span><span>(</span><span>a</span><span>,</span> <span>b</span> <span>string</span><span>)</span> <span>int</span> <span>{</span>
</span></span><span><span>        <span>return</span> <span>cmp</span><span>.</span><span>Compare</span><span>(</span><span>len</span><span>(</span><span>a</span><span>),</span> <span>len</span><span>(</span><span>b</span><span>))</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td><p>Now we can call <code>slices.SortFunc</code> with this custom comparison function to sort <code>fruits</code> by name length.</p></td><td><pre><code><span><span>    <span>slices</span><span>.</span><span>SortFunc</span><span>(</span><span>fruits</span><span>,</span> <span>lenCmp</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>fruits</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>We can use the same technique to sort a slice of values that aren’t built-in types.</p></td><td><pre><code><span><span>    <span>type</span> <span>Person</span> <span>struct</span> <span>{</span>
</span></span><span><span>        <span>name</span> <span>string</span>
</span></span><span><span>        <span>age</span>  <span>int</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span>    <span>people</span> <span>:=</span> <span>[]</span><span>Person</span><span>{</span>
</span></span><span><span>        <span>Person</span><span>{</span><span>name</span><span>:</span> <span>"Jax"</span><span>,</span> <span>age</span><span>:</span> <span>37</span><span>},</span>
</span></span><span><span>        <span>Person</span><span>{</span><span>name</span><span>:</span> <span>"TJ"</span><span>,</span> <span>age</span><span>:</span> <span>25</span><span>},</span>
</span></span><span><span>        <span>Person</span><span>{</span><span>name</span><span>:</span> <span>"Alex"</span><span>,</span> <span>age</span><span>:</span> <span>72</span><span>},</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td><p>Sort <code>people</code> by age using <code>slices.SortFunc</code>.</p><p>Note: if the <code>Person</code> struct is large, you may want the slice to contain <code>*Person</code> instead and adjust the sorting function accordingly. If in doubt, <a href="https://gobyexample.com/testing-and-benchmarking">benchmark</a>!</p></td><td><pre><code><span><span>    <span>slices</span><span>.</span><span>SortFunc</span><span>(</span><span>people</span><span>,</span>
</span></span><span><span>        <span>func</span><span>(</span><span>a</span><span>,</span> <span>b</span> <span>Person</span><span>)</span> <span>int</span> <span>{</span>
</span></span><span><span>            <span>return</span> <span>cmp</span><span>.</span><span>Compare</span><span>(</span><span>a</span><span>.</span><span>age</span><span>,</span> <span>b</span><span>.</span><span>age</span><span>)</span>
</span></span><span><span>        <span>})</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>people</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go run sorting-by-functions.go 
</span></span><span><span><span>[kiwi peach banana]
</span></span></span><span><span><span>[{TJ 25} {Jax 37} {Alex 72}]</span></span></span></code></pre></td></tr></tbody></table>

Next example: [Panic](https://gobyexample.com/panic).
