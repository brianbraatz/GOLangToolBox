---
Description: Go by Example: Enums
Notes: Enumerated types (enums) are a special case of
sum types.
An enum is a type that has a fixed number of possible
values, each with a distinct name. Go doesn’t have an
enum type as a distinct language feature, but enums
are simple to implement using existing language idioms.
author: 
Url: https://gobyexample.com/enums
Created: "2025-01-29  02:44:23"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Enums

source: https://gobyexample.com/enums

> ## Excerpt
> Enumerated types (enums) are a special case of
sum types.
An enum is a type that has a fixed number of possible
values, each with a distinct name. Go doesn’t have an
enum type as a distinct language feature, but enums
are simple to implement using existing language idioms.

---
<table><tbody><tr><td><p><em>Enumerated types</em> (enums) are a special case of <a href="https://en.wikipedia.org/wiki/Algebraic_data_type">sum types</a>. An enum is a type that has a fixed number of possible values, each with a distinct name. Go doesn’t have an enum type as a distinct language feature, but enums are simple to implement using existing language idioms.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/prQMptP_p1s"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>"fmt"</span></span></span></code></pre></td></tr><tr><td><p>Our enum type <code>ServerState</code> has an underlying <code>int</code> type.</p></td><td><pre><code><span><span><span>type</span> <span>ServerState</span> <span>int</span></span></span></code></pre></td></tr><tr><td><p>The possible values for <code>ServerState</code> are defined as constants. The special keyword <a href="https://go.dev/ref/spec#Iota">iota</a> generates successive constant values automatically; in this case 0, 1, 2 and so on.</p></td><td><pre><code><span><span><span>const</span> <span>(</span>
</span></span><span><span>    <span>StateIdle</span> <span>ServerState</span> <span>=</span> <span>iota</span>
</span></span><span><span>    <span>StateConnected</span>
</span></span><span><span>    <span>StateError</span>
</span></span><span><span>    <span>StateRetrying</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td><p>By implementing the <a href="https://pkg.go.dev/fmt#Stringer">fmt.Stringer</a> interface, values of <code>ServerState</code> can be printed out or converted to strings.</p><p>This can get cumbersome if there are many possible values. In such cases the <a href="https://pkg.go.dev/golang.org/x/tools/cmd/stringer">stringer tool</a> can be used in conjunction with <code>go:generate</code> to automate the process. See <a href="https://eli.thegreenplace.net/2021/a-comprehensive-guide-to-go-generate">this post</a> for a longer explanation.</p></td><td><pre><code><span><span><span>var</span> <span>stateName</span> <span>=</span> <span>map</span><span>[</span><span>ServerState</span><span>]</span><span>string</span><span>{</span>
</span></span><span><span>    <span>StateIdle</span><span>:</span>      <span>"idle"</span><span>,</span>
</span></span><span><span>    <span>StateConnected</span><span>:</span> <span>"connected"</span><span>,</span>
</span></span><span><span>    <span>StateError</span><span>:</span>     <span>"error"</span><span>,</span>
</span></span><span><span>    <span>StateRetrying</span><span>:</span>  <span>"retrying"</span><span>,</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>(</span><span>ss</span> <span>ServerState</span><span>)</span> <span>String</span><span>()</span> <span>string</span> <span>{</span>
</span></span><span><span>    <span>return</span> <span>stateName</span><span>[</span><span>ss</span><span>]</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td><p>If we have a value of type <code>int</code>, we cannot pass it to <code>transition</code> - the compiler will complain about type mismatch. This provides some degree of compile-time type safety for enums.</p></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span>
</span></span><span><span>    <span>ns</span> <span>:=</span> <span>transition</span><span>(</span><span>StateIdle</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>ns</span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span>    <span>ns2</span> <span>:=</span> <span>transition</span><span>(</span><span>ns</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>ns2</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td><p>transition emulates a state transition for a server; it takes the existing state and returns a new state.</p></td><td><pre><code><span><span><span>func</span> <span>transition</span><span>(</span><span>s</span> <span>ServerState</span><span>)</span> <span>ServerState</span> <span>{</span>
</span></span><span><span>    <span>switch</span> <span>s</span> <span>{</span>
</span></span><span><span>    <span>case</span> <span>StateIdle</span><span>:</span>
</span></span><span><span>        <span>return</span> <span>StateConnected</span>
</span></span><span><span>    <span>case</span> <span>StateConnected</span><span>,</span> <span>StateRetrying</span><span>:</span></span></span></code></pre></td></tr><tr><td><p>Suppose we check some predicates here to determine the next state…</p></td><td><pre><code><span><span>        <span>return</span> <span>StateIdle</span>
</span></span><span><span>    <span>case</span> <span>StateError</span><span>:</span>
</span></span><span><span>        <span>return</span> <span>StateError</span>
</span></span><span><span>    <span>default</span><span>:</span>
</span></span><span><span>        <span>panic</span><span>(</span><span>fmt</span><span>.</span><span>Errorf</span><span>(</span><span>"unknown state: %s"</span><span>,</span> <span>s</span><span>))</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go run enums.go
</span></span><span><span><span>connected
</span></span></span><span><span><span>idle</span></span></span></code></pre></td></tr></tbody></table>

Next example: [Struct Embedding](https://gobyexample.com/struct-embedding).
