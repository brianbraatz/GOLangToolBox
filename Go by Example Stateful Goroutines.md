---
Description: Go by Example: Stateful Goroutines
Notes: In the previous example we used explicit locking with
mutexes to synchronize access to shared state
across multiple goroutines. Another option is to use the
built-in synchronization features of  goroutines and
channels to achieve the same result. This channel-based
approach aligns with Go’s ideas of sharing memory by
communicating and having each piece of data owned
by exactly 1 goroutine.
author: 
Url: https://gobyexample.com/stateful-goroutines
Created: "2025-01-29  02:45:35"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Stateful Goroutines

source: https://gobyexample.com/stateful-goroutines

> ## Excerpt
> In the previous example we used explicit locking with
mutexes to synchronize access to shared state
across multiple goroutines. Another option is to use the
built-in synchronization features of  goroutines and
channels to achieve the same result. This channel-based
approach aligns with Go’s ideas of sharing memory by
communicating and having each piece of data owned
by exactly 1 goroutine.

---
<table><tbody><tr><td><p>In the previous example we used explicit locking with <a href="https://gobyexample.com/mutexes">mutexes</a> to synchronize access to shared state across multiple goroutines. Another option is to use the built-in synchronization features of goroutines and channels to achieve the same result. This channel-based approach aligns with Go’s ideas of sharing memory by communicating and having each piece of data owned by exactly 1 goroutine.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/TBcWd-OfnaA"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"math/rand"</span>
</span></span><span><span>    <span>"sync/atomic"</span>
</span></span><span><span>    <span>"time"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td><p>In this example our state will be owned by a single goroutine. This will guarantee that the data is never corrupted with concurrent access. In order to read or write that state, other goroutines will send messages to the owning goroutine and receive corresponding replies. These <code>readOp</code> and <code>writeOp</code> <code>struct</code>s encapsulate those requests and a way for the owning goroutine to respond.</p></td><td><pre><code><span><span><span>type</span> <span>readOp</span> <span>struct</span> <span>{</span>
</span></span><span><span>    <span>key</span>  <span>int</span>
</span></span><span><span>    <span>resp</span> <span>chan</span> <span>int</span>
</span></span><span><span><span>}</span>
</span></span><span><span><span>type</span> <span>writeOp</span> <span>struct</span> <span>{</span>
</span></span><span><span>    <span>key</span>  <span>int</span>
</span></span><span><span>    <span>val</span>  <span>int</span>
</span></span><span><span>    <span>resp</span> <span>chan</span> <span>bool</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>As before we’ll count how many operations we perform.</p></td><td><pre><code><span><span>    <span>var</span> <span>readOps</span> <span>uint64</span>
</span></span><span><span>    <span>var</span> <span>writeOps</span> <span>uint64</span></span></span></code></pre></td></tr><tr><td><p>The <code>reads</code> and <code>writes</code> channels will be used by other goroutines to issue read and write requests, respectively.</p></td><td><pre><code><span><span>    <span>reads</span> <span>:=</span> <span>make</span><span>(</span><span>chan</span> <span>readOp</span><span>)</span>
</span></span><span><span>    <span>writes</span> <span>:=</span> <span>make</span><span>(</span><span>chan</span> <span>writeOp</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Here is the goroutine that owns the <code>state</code>, which is a map as in the previous example but now private to the stateful goroutine. This goroutine repeatedly selects on the <code>reads</code> and <code>writes</code> channels, responding to requests as they arrive. A response is executed by first performing the requested operation and then sending a value on the response channel <code>resp</code> to indicate success (and the desired value in the case of <code>reads</code>).</p></td><td><pre><code><span><span>    <span>go</span> <span>func</span><span>()</span> <span>{</span>
</span></span><span><span>        <span>var</span> <span>state</span> <span>=</span> <span>make</span><span>(</span><span>map</span><span>[</span><span>int</span><span>]</span><span>int</span><span>)</span>
</span></span><span><span>        <span>for</span> <span>{</span>
</span></span><span><span>            <span>select</span> <span>{</span>
</span></span><span><span>            <span>case</span> <span>read</span> <span>:=</span> <span>&lt;-</span><span>reads</span><span>:</span>
</span></span><span><span>                <span>read</span><span>.</span><span>resp</span> <span>&lt;-</span> <span>state</span><span>[</span><span>read</span><span>.</span><span>key</span><span>]</span>
</span></span><span><span>            <span>case</span> <span>write</span> <span>:=</span> <span>&lt;-</span><span>writes</span><span>:</span>
</span></span><span><span>                <span>state</span><span>[</span><span>write</span><span>.</span><span>key</span><span>]</span> <span>=</span> <span>write</span><span>.</span><span>val</span>
</span></span><span><span>                <span>write</span><span>.</span><span>resp</span> <span>&lt;-</span> <span>true</span>
</span></span><span><span>            <span>}</span>
</span></span><span><span>        <span>}</span>
</span></span><span><span>    <span>}()</span></span></span></code></pre></td></tr><tr><td><p>This starts 100 goroutines to issue reads to the state-owning goroutine via the <code>reads</code> channel. Each read requires constructing a <code>readOp</code>, sending it over the <code>reads</code> channel, and then receiving the result over the provided <code>resp</code> channel.</p></td><td><pre><code><span><span>    <span>for</span> <span>r</span> <span>:=</span> <span>0</span><span>;</span> <span>r</span> <span>&lt;</span> <span>100</span><span>;</span> <span>r</span><span>++</span> <span>{</span>
</span></span><span><span>        <span>go</span> <span>func</span><span>()</span> <span>{</span>
</span></span><span><span>            <span>for</span> <span>{</span>
</span></span><span><span>                <span>read</span> <span>:=</span> <span>readOp</span><span>{</span>
</span></span><span><span>                    <span>key</span><span>:</span>  <span>rand</span><span>.</span><span>Intn</span><span>(</span><span>5</span><span>),</span>
</span></span><span><span>                    <span>resp</span><span>:</span> <span>make</span><span>(</span><span>chan</span> <span>int</span><span>)}</span>
</span></span><span><span>                <span>reads</span> <span>&lt;-</span> <span>read</span>
</span></span><span><span>                <span>&lt;-</span><span>read</span><span>.</span><span>resp</span>
</span></span><span><span>                <span>atomic</span><span>.</span><span>AddUint64</span><span>(</span><span>&amp;</span><span>readOps</span><span>,</span> <span>1</span><span>)</span>
</span></span><span><span>                <span>time</span><span>.</span><span>Sleep</span><span>(</span><span>time</span><span>.</span><span>Millisecond</span><span>)</span>
</span></span><span><span>            <span>}</span>
</span></span><span><span>        <span>}()</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td><p>We start 10 writes as well, using a similar approach.</p></td><td><pre><code><span><span>    <span>for</span> <span>w</span> <span>:=</span> <span>0</span><span>;</span> <span>w</span> <span>&lt;</span> <span>10</span><span>;</span> <span>w</span><span>++</span> <span>{</span>
</span></span><span><span>        <span>go</span> <span>func</span><span>()</span> <span>{</span>
</span></span><span><span>            <span>for</span> <span>{</span>
</span></span><span><span>                <span>write</span> <span>:=</span> <span>writeOp</span><span>{</span>
</span></span><span><span>                    <span>key</span><span>:</span>  <span>rand</span><span>.</span><span>Intn</span><span>(</span><span>5</span><span>),</span>
</span></span><span><span>                    <span>val</span><span>:</span>  <span>rand</span><span>.</span><span>Intn</span><span>(</span><span>100</span><span>),</span>
</span></span><span><span>                    <span>resp</span><span>:</span> <span>make</span><span>(</span><span>chan</span> <span>bool</span><span>)}</span>
</span></span><span><span>                <span>writes</span> <span>&lt;-</span> <span>write</span>
</span></span><span><span>                <span>&lt;-</span><span>write</span><span>.</span><span>resp</span>
</span></span><span><span>                <span>atomic</span><span>.</span><span>AddUint64</span><span>(</span><span>&amp;</span><span>writeOps</span><span>,</span> <span>1</span><span>)</span>
</span></span><span><span>                <span>time</span><span>.</span><span>Sleep</span><span>(</span><span>time</span><span>.</span><span>Millisecond</span><span>)</span>
</span></span><span><span>            <span>}</span>
</span></span><span><span>        <span>}()</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td><p>Let the goroutines work for a second.</p></td><td><pre><code><span><span>    <span>time</span><span>.</span><span>Sleep</span><span>(</span><span>time</span><span>.</span><span>Second</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Finally, capture and report the op counts.</p></td><td><pre><code><span><span>    <span>readOpsFinal</span> <span>:=</span> <span>atomic</span><span>.</span><span>LoadUint64</span><span>(</span><span>&amp;</span><span>readOps</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"readOps:"</span><span>,</span> <span>readOpsFinal</span><span>)</span>
</span></span><span><span>    <span>writeOpsFinal</span> <span>:=</span> <span>atomic</span><span>.</span><span>LoadUint64</span><span>(</span><span>&amp;</span><span>writeOps</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"writeOps:"</span><span>,</span> <span>writeOpsFinal</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td><p>Running our program shows that the goroutine-based state management example completes about 80,000 total operations.</p></td><td><pre><code><span><span><span>$</span> go run stateful-goroutines.go
</span></span><span><span><span>readOps: 71708
</span></span></span><span><span><span>writeOps: 7177</span></span></span></code></pre></td></tr><tr><td><p>For this particular case the goroutine-based approach was a bit more involved than the mutex-based one. It might be useful in certain cases though, for example where you have other channels involved or when managing multiple such mutexes would be error-prone. You should use whichever approach feels most natural, especially with respect to understanding the correctness of your program.</p></td><td></td></tr></tbody></table>

Next example: [Sorting](https://gobyexample.com/sorting).
