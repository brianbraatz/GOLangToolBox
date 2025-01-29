---
Description: Go by Example: Pointers
Notes: Go supports pointers,
allowing you to pass references to values and records
within your program.
author: 
Url: https://gobyexample.com/pointers
Created: "2025-01-29  02:43:02"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Pointers

source: https://gobyexample.com/pointers

> ## Excerpt
> Go supports pointers,
allowing you to pass references to values and records
within your program.

---
<table><tbody><tr><td><p>Go supports <em><a href="https://en.wikipedia.org/wiki/Pointer_(computer_programming)">pointers</a></em>, allowing you to pass references to values and records within your program.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/OlWCLpxAyBz"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>"fmt"</span></span></span></code></pre></td></tr><tr><td><p>We’ll show how pointers work in contrast to values with 2 functions: <code>zeroval</code> and <code>zeroptr</code>. <code>zeroval</code> has an <code>int</code> parameter, so arguments will be passed to it by value. <code>zeroval</code> will get a copy of <code>ival</code> distinct from the one in the calling function.</p></td><td><pre><code><span><span><span>func</span> <span>zeroval</span><span>(</span><span>ival</span> <span>int</span><span>)</span> <span>{</span>
</span></span><span><span>    <span>ival</span> <span>=</span> <span>0</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td><p><code>zeroptr</code> in contrast has an <code>*int</code> parameter, meaning that it takes an <code>int</code> pointer. The <code>*iptr</code> code in the function body then <em>dereferences</em> the pointer from its memory address to the current value at that address. Assigning a value to a dereferenced pointer changes the value at the referenced address.</p></td><td><pre><code><span><span><span>func</span> <span>zeroptr</span><span>(</span><span>iptr</span> <span>*</span><span>int</span><span>)</span> <span>{</span>
</span></span><span><span>    <span>*</span><span>iptr</span> <span>=</span> <span>0</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span>
</span></span><span><span>    <span>i</span> <span>:=</span> <span>1</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"initial:"</span><span>,</span> <span>i</span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span>    <span>zeroval</span><span>(</span><span>i</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"zeroval:"</span><span>,</span> <span>i</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>The <code>&amp;i</code> syntax gives the memory address of <code>i</code>, i.e. a pointer to <code>i</code>.</p></td><td><pre><code><span><span>    <span>zeroptr</span><span>(</span><span>&amp;</span><span>i</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"zeroptr:"</span><span>,</span> <span>i</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Pointers can be printed too.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"pointer:"</span><span>,</span> <span>&amp;</span><span>i</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td><p><code>zeroval</code> doesn’t change the <code>i</code> in <code>main</code>, but <code>zeroptr</code> does because it has a reference to the memory address for that variable.</p></td><td><pre><code><span><span><span>$</span> go run pointers.go
</span></span><span><span><span>initial: 1
</span></span></span><span><span><span>zeroval: 1
</span></span></span><span><span><span>zeroptr: 0
</span></span></span><span><span><span>pointer: 0x42131100</span></span></span></code></pre></td></tr></tbody></table>

Next example: [Strings and Runes](https://gobyexample.com/strings-and-runes).
