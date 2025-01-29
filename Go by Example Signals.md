---
Description: Go by Example: Signals
Notes: Sometimes we’d like our Go programs to intelligently
handle Unix signals.
For example, we might want a server to gracefully
shutdown when it receives a SIGTERM, or a command-line
tool to stop processing input if it receives a SIGINT.
Here’s how to handle signals in Go with channels.
author: 
Url: https://gobyexample.com/signals
Created: "2025-01-29  02:48:51"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Signals

source: https://gobyexample.com/signals

> ## Excerpt
> Sometimes we’d like our Go programs to intelligently
handle Unix signals.
For example, we might want a server to gracefully
shutdown when it receives a SIGTERM, or a command-line
tool to stop processing input if it receives a SIGINT.
Here’s how to handle signals in Go with channels.

---
<table><tbody><tr><td><p>Sometimes we’d like our Go programs to intelligently handle <a href="https://en.wikipedia.org/wiki/Unix_signal">Unix signals</a>. For example, we might want a server to gracefully shutdown when it receives a <code>SIGTERM</code>, or a command-line tool to stop processing input if it receives a <code>SIGINT</code>. Here’s how to handle signals in Go with channels.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/RKLAbvblJMQ"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"os"</span>
</span></span><span><span>    <span>"os/signal"</span>
</span></span><span><span>    <span>"syscall"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>Go signal notification works by sending <code>os.Signal</code> values on a channel. We’ll create a channel to receive these notifications. Note that this channel should be buffered.</p></td><td><pre><code><span><span>    <span>sigs</span> <span>:=</span> <span>make</span><span>(</span><span>chan</span> <span>os</span><span>.</span><span>Signal</span><span>,</span> <span>1</span><span>)</span></span></span></code></pre></td></tr><tr><td><p><code>signal.Notify</code> registers the given channel to receive notifications of the specified signals.</p></td><td><pre><code><span><span>    <span>signal</span><span>.</span><span>Notify</span><span>(</span><span>sigs</span><span>,</span> <span>syscall</span><span>.</span><span>SIGINT</span><span>,</span> <span>syscall</span><span>.</span><span>SIGTERM</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>We could receive from <code>sigs</code> here in the main function, but let’s see how this could also be done in a separate goroutine, to demonstrate a more realistic scenario of graceful shutdown.</p></td><td><pre><code><span><span>    <span>done</span> <span>:=</span> <span>make</span><span>(</span><span>chan</span> <span>bool</span><span>,</span> <span>1</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>This goroutine executes a blocking receive for signals. When it gets one it’ll print it out and then notify the program that it can finish.</p></td><td><pre><code><span><span>    <span>go</span> <span>func</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span>        <span>sig</span> <span>:=</span> <span>&lt;-</span><span>sigs</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>()</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>sig</span><span>)</span>
</span></span><span><span>        <span>done</span> <span>&lt;-</span> <span>true</span>
</span></span><span><span>    <span>}()</span></span></span></code></pre></td></tr><tr><td><p>The program will wait here until it gets the expected signal (as indicated by the goroutine above sending a value on <code>done</code>) and then exit.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"awaiting signal"</span><span>)</span>
</span></span><span><span>    <span>&lt;-</span><span>done</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"exiting"</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td><p>When we run this program it will block waiting for a signal. By typing <code>ctrl-C</code> (which the terminal shows as <code>^C</code>) we can send a <code>SIGINT</code> signal, causing the program to print <code>interrupt</code> and then exit.</p></td><td><pre><code><span><span><span>$</span> go run signals.go
</span></span><span><span><span>awaiting signal
</span></span></span><span><span><span>^C
</span></span></span><span><span><span>interrupt
</span></span></span><span><span><span>exiting</span></span></span></code></pre></td></tr></tbody></table>

Next example: [Exit](https://gobyexample.com/exit).
