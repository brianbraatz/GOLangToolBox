---
Description: Go by Example: Timers
Notes: We often want to execute Go code at some point in the
future, or repeatedly at some interval. Go’s built-in
timer and ticker features make both of these tasks
easy. We’ll look first at timers and then
at tickers.
author: 
Url: https://gobyexample.com/timers
Created: "2025-01-29  02:45:15"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Timers

source: https://gobyexample.com/timers

> ## Excerpt
> We often want to execute Go code at some point in the
future, or repeatedly at some interval. Go’s built-in
timer and ticker features make both of these tasks
easy. We’ll look first at timers and then
at tickers.

---
<table><tbody><tr><td><p>We often want to execute Go code at some point in the future, or repeatedly at some interval. Go’s built-in <em>timer</em> and <em>ticker</em> features make both of these tasks easy. We’ll look first at timers and then at <a href="https://gobyexample.com/tickers">tickers</a>.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/gF7VLRz3URM"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"time"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>Timers represent a single event in the future. You tell the timer how long you want to wait, and it provides a channel that will be notified at that time. This timer will wait 2 seconds.</p></td><td><pre><code><span><span>    <span>timer1</span> <span>:=</span> <span>time</span><span>.</span><span>NewTimer</span><span>(</span><span>2</span> <span>*</span> <span>time</span><span>.</span><span>Second</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>The <code>&lt;-timer1.C</code> blocks on the timer’s channel <code>C</code> until it sends a value indicating that the timer fired.</p></td><td><pre><code><span><span>    <span>&lt;-</span><span>timer1</span><span>.</span><span>C</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"Timer 1 fired"</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>If you just wanted to wait, you could have used <code>time.Sleep</code>. One reason a timer may be useful is that you can cancel the timer before it fires. Here’s an example of that.</p></td><td><pre><code><span><span>    <span>timer2</span> <span>:=</span> <span>time</span><span>.</span><span>NewTimer</span><span>(</span><span>time</span><span>.</span><span>Second</span><span>)</span>
</span></span><span><span>    <span>go</span> <span>func</span><span>()</span> <span>{</span>
</span></span><span><span>        <span>&lt;-</span><span>timer2</span><span>.</span><span>C</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"Timer 2 fired"</span><span>)</span>
</span></span><span><span>    <span>}()</span>
</span></span><span><span>    <span>stop2</span> <span>:=</span> <span>timer2</span><span>.</span><span>Stop</span><span>()</span>
</span></span><span><span>    <span>if</span> <span>stop2</span> <span>{</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"Timer 2 stopped"</span><span>)</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td><p>Give the <code>timer2</code> enough time to fire, if it ever was going to, to show it is in fact stopped.</p></td><td><pre><code><span><span>    <span>time</span><span>.</span><span>Sleep</span><span>(</span><span>2</span> <span>*</span> <span>time</span><span>.</span><span>Second</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td><p>The first timer will fire ~2s after we start the program, but the second should be stopped before it has a chance to fire.</p></td><td><pre><code><span><span><span>$</span> go run timers.go
</span></span><span><span><span>Timer 1 fired
</span></span></span><span><span><span>Timer 2 stopped</span></span></span></code></pre></td></tr></tbody></table>

Next example: [Tickers](https://gobyexample.com/tickers).
