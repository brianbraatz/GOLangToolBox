---
Description: Go by Example: Custom Errors
Notes: It’s possible to use custom types as errors by
implementing the Error() method on them. Here’s a
variant on the example above that uses a custom type
to explicitly represent an argument error.
author: 
Url: https://gobyexample.com/custom-errors
Created: "2025-01-29  02:44:38"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Custom Errors

source: https://gobyexample.com/custom-errors

> ## Excerpt
> It’s possible to use custom types as errors by
implementing the Error() method on them. Here’s a
variant on the example above that uses a custom type
to explicitly represent an argument error.

---
<table><tbody><tr><td><p>It’s possible to use custom types as <code>error</code>s by implementing the <code>Error()</code> method on them. Here’s a variant on the example above that uses a custom type to explicitly represent an argument error.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/qKKTjmc6SuB"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"errors"</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td><p>A custom error type usually has the suffix “Error”.</p></td><td><pre><code><span><span><span>type</span> <span>argError</span> <span>struct</span> <span>{</span>
</span></span><span><span>    <span>arg</span>     <span>int</span>
</span></span><span><span>    <span>message</span> <span>string</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td><p>Adding this <code>Error</code> method makes <code>argError</code> implement the <code>error</code> interface.</p></td><td><pre><code><span><span><span>func</span> <span>(</span><span>e</span> <span>*</span><span>argError</span><span>)</span> <span>Error</span><span>()</span> <span>string</span> <span>{</span>
</span></span><span><span>    <span>return</span> <span>fmt</span><span>.</span><span>Sprintf</span><span>(</span><span>"%d - %s"</span><span>,</span> <span>e</span><span>.</span><span>arg</span><span>,</span> <span>e</span><span>.</span><span>message</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>f</span><span>(</span><span>arg</span> <span>int</span><span>)</span> <span>(</span><span>int</span><span>,</span> <span>error</span><span>)</span> <span>{</span>
</span></span><span><span>    <span>if</span> <span>arg</span> <span>==</span> <span>42</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>Return our custom error.</p></td><td><pre><code><span><span>        <span>return</span> <span>-</span><span>1</span><span>,</span> <span>&amp;</span><span>argError</span><span>{</span><span>arg</span><span>,</span> <span>"can't work with it"</span><span>}</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span>    <span>return</span> <span>arg</span> <span>+</span> <span>3</span><span>,</span> <span>nil</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p><code>errors.As</code> is a more advanced version of <code>errors.Is</code>. It checks that a given error (or any error in its chain) matches a specific error type and converts to a value of that type, returning <code>true</code>. If there’s no match, it returns <code>false</code>.</p></td><td><pre><code><span><span>    <span>_</span><span>,</span> <span>err</span> <span>:=</span> <span>f</span><span>(</span><span>42</span><span>)</span>
</span></span><span><span>    <span>var</span> <span>ae</span> <span>*</span><span>argError</span>
</span></span><span><span>    <span>if</span> <span>errors</span><span>.</span><span>As</span><span>(</span><span>err</span><span>,</span> <span>&amp;</span><span>ae</span><span>)</span> <span>{</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>ae</span><span>.</span><span>arg</span><span>)</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>ae</span><span>.</span><span>message</span><span>)</span>
</span></span><span><span>    <span>}</span> <span>else</span> <span>{</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"err doesn't match argError"</span><span>)</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go run custom-errors.go
</span></span><span><span><span>42
</span></span></span><span><span><span>can't work with it</span></span></span></code></pre></td></tr></tbody></table>

Next example: [Goroutines](https://gobyexample.com/goroutines).
