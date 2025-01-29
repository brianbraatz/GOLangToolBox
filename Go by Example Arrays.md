---
Description: Go by Example: Arrays
Notes: In Go, an array is a numbered sequence of elements of a
specific length. In typical Go code, slices are
much more common; arrays are useful in some special
scenarios.
author: 
Url: https://gobyexample.com/arrays
Created: "2025-01-29  02:42:18"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Arrays

source: https://gobyexample.com/arrays

> ## Excerpt
> In Go, an array is a numbered sequence of elements of a
specific length. In typical Go code, slices are
much more common; arrays are useful in some special
scenarios.

---
<table><tbody><tr><td><p>In Go, an <em>array</em> is a numbered sequence of elements of a specific length. In typical Go code, <a href="https://gobyexample.com/slices">slices</a> are much more common; arrays are useful in some special scenarios.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/zVIFeNnUdwv"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>"fmt"</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>Here we create an array <code>a</code> that will hold exactly 5 <code>int</code>s. The type of elements and length are both part of the array’s type. By default an array is zero-valued, which for <code>int</code>s means <code>0</code>s.</p></td><td><pre><code><span><span>    <span>var</span> <span>a</span> <span>[</span><span>5</span><span>]</span><span>int</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"emp:"</span><span>,</span> <span>a</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>We can set a value at an index using the <code>array[index] = value</code> syntax, and get a value with <code>array[index]</code>.</p></td><td><pre><code><span><span>    <span>a</span><span>[</span><span>4</span><span>]</span> <span>=</span> <span>100</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"set:"</span><span>,</span> <span>a</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"get:"</span><span>,</span> <span>a</span><span>[</span><span>4</span><span>])</span></span></span></code></pre></td></tr><tr><td><p>The builtin <code>len</code> returns the length of an array.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"len:"</span><span>,</span> <span>len</span><span>(</span><span>a</span><span>))</span></span></span></code></pre></td></tr><tr><td><p>Use this syntax to declare and initialize an array in one line.</p></td><td><pre><code><span><span>    <span>b</span> <span>:=</span> <span>[</span><span>5</span><span>]</span><span>int</span><span>{</span><span>1</span><span>,</span> <span>2</span><span>,</span> <span>3</span><span>,</span> <span>4</span><span>,</span> <span>5</span><span>}</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"dcl:"</span><span>,</span> <span>b</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>You can also have the compiler count the number of elements for you with <code>...</code></p></td><td><pre><code><span><span>    <span>b</span> <span>=</span> <span>[</span><span>...</span><span>]</span><span>int</span><span>{</span><span>1</span><span>,</span> <span>2</span><span>,</span> <span>3</span><span>,</span> <span>4</span><span>,</span> <span>5</span><span>}</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"dcl:"</span><span>,</span> <span>b</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>If you specify the index with <code>:</code>, the elements in between will be zeroed.</p></td><td><pre><code><span><span>    <span>b</span> <span>=</span> <span>[</span><span>...</span><span>]</span><span>int</span><span>{</span><span>100</span><span>,</span> <span>3</span><span>:</span> <span>400</span><span>,</span> <span>500</span><span>}</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"idx:"</span><span>,</span> <span>b</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Array types are one-dimensional, but you can compose types to build multi-dimensional data structures.</p></td><td><pre><code><span><span>    <span>var</span> <span>twoD</span> <span>[</span><span>2</span><span>][</span><span>3</span><span>]</span><span>int</span>
</span></span><span><span>    <span>for</span> <span>i</span> <span>:=</span> <span>0</span><span>;</span> <span>i</span> <span>&lt;</span> <span>2</span><span>;</span> <span>i</span><span>++</span> <span>{</span>
</span></span><span><span>        <span>for</span> <span>j</span> <span>:=</span> <span>0</span><span>;</span> <span>j</span> <span>&lt;</span> <span>3</span><span>;</span> <span>j</span><span>++</span> <span>{</span>
</span></span><span><span>            <span>twoD</span><span>[</span><span>i</span><span>][</span><span>j</span><span>]</span> <span>=</span> <span>i</span> <span>+</span> <span>j</span>
</span></span><span><span>        <span>}</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"2d: "</span><span>,</span> <span>twoD</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>You can create and initialize multi-dimensional arrays at once too.</p></td><td><pre><code><span><span>    <span>twoD</span> <span>=</span> <span>[</span><span>2</span><span>][</span><span>3</span><span>]</span><span>int</span><span>{</span>
</span></span><span><span>        <span>{</span><span>1</span><span>,</span> <span>2</span><span>,</span> <span>3</span><span>},</span>
</span></span><span><span>        <span>{</span><span>1</span><span>,</span> <span>2</span><span>,</span> <span>3</span><span>},</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"2d: "</span><span>,</span> <span>twoD</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td><p>Note that arrays appear in the form <code>[v1 v2 v3 ...]</code> when printed with <code>fmt.Println</code>.</p></td><td><pre><code><span><span><span>$</span> go run arrays.go
</span></span><span><span><span>emp: [0 0 0 0 0]
</span></span></span><span><span><span>set: [0 0 0 0 100]
</span></span></span><span><span><span>get: 100
</span></span></span><span><span><span>len: 5
</span></span></span><span><span><span>dcl: [1 2 3 4 5]
</span></span></span><span><span><span>dcl: [1 2 3 4 5]
</span></span></span><span><span><span>idx: [100 0 0 400 500]
</span></span></span><span><span><span>2d:  [[0 1 2] [1 2 3]]
</span></span></span><span><span><span>2d:  [[1 2 3] [1 2 3]]</span></span></span></code></pre></td></tr></tbody></table>

Next example: [Slices](https://gobyexample.com/slices).
