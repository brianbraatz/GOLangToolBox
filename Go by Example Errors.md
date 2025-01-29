---
Description: Go by Example: Errors
Notes: In Go it’s idiomatic to communicate errors via an
explicit, separate return value. This contrasts with
the exceptions used in languages like Java and Ruby and
the overloaded single result / error value sometimes
used in C. Go’s approach makes it easy to see which
functions return errors and to handle them using the
same language constructs employed for other,
non-error tasks.
author: 
Url: https://gobyexample.com/errors
Created: "2025-01-29  02:44:35"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Errors

source: https://gobyexample.com/errors

> ## Excerpt
> In Go it’s idiomatic to communicate errors via an
explicit, separate return value. This contrasts with
the exceptions used in languages like Java and Ruby and
the overloaded single result / error value sometimes
used in C. Go’s approach makes it easy to see which
functions return errors and to handle them using the
same language constructs employed for other,
non-error tasks.

---
<table><tbody><tr><td><p>In Go it’s idiomatic to communicate errors via an explicit, separate return value. This contrasts with the exceptions used in languages like Java and Ruby and the overloaded single result / error value sometimes used in C. Go’s approach makes it easy to see which functions return errors and to handle them using the same language constructs employed for other, non-error tasks.</p><p>See the documentation of the <a href="https://pkg.go.dev/errors">errors package</a> and <a href="https://go.dev/blog/go1.13-errors">this blog post</a> for additional details.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/j6odYuFpOeb"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"errors"</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td><p>By convention, errors are the last return value and have type <code>error</code>, a built-in interface.</p></td><td><pre><code><span><span><span>func</span> <span>f</span><span>(</span><span>arg</span> <span>int</span><span>)</span> <span>(</span><span>int</span><span>,</span> <span>error</span><span>)</span> <span>{</span>
</span></span><span><span>    <span>if</span> <span>arg</span> <span>==</span> <span>42</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p><code>errors.New</code> constructs a basic <code>error</code> value with the given error message.</p></td><td><pre><code><span><span>        <span>return</span> <span>-</span><span>1</span><span>,</span> <span>errors</span><span>.</span><span>New</span><span>(</span><span>"can't work with 42"</span><span>)</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td><p>A <code>nil</code> value in the error position indicates that there was no error.</p></td><td><pre><code><span><span>    <span>return</span> <span>arg</span> <span>+</span> <span>3</span><span>,</span> <span>nil</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td><p>A sentinel error is a predeclared variable that is used to signify a specific error condition.</p></td><td><pre><code><span><span><span>var</span> <span>ErrOutOfTea</span> <span>=</span> <span>fmt</span><span>.</span><span>Errorf</span><span>(</span><span>"no more tea available"</span><span>)</span>
</span></span><span><span><span>var</span> <span>ErrPower</span> <span>=</span> <span>fmt</span><span>.</span><span>Errorf</span><span>(</span><span>"can't boil water"</span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>makeTea</span><span>(</span><span>arg</span> <span>int</span><span>)</span> <span>error</span> <span>{</span>
</span></span><span><span>    <span>if</span> <span>arg</span> <span>==</span> <span>2</span> <span>{</span>
</span></span><span><span>        <span>return</span> <span>ErrOutOfTea</span>
</span></span><span><span>    <span>}</span> <span>else</span> <span>if</span> <span>arg</span> <span>==</span> <span>4</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>We can wrap errors with higher-level errors to add context. The simplest way to do this is with the <code>%w</code> verb in <code>fmt.Errorf</code>. Wrapped errors create a logical chain (A wraps B, which wraps C, etc.) that can be queried with functions like <code>errors.Is</code> and <code>errors.As</code>.</p></td><td><pre><code><span><span>        <span>return</span> <span>fmt</span><span>.</span><span>Errorf</span><span>(</span><span>"making tea: %w"</span><span>,</span> <span>ErrPower</span><span>)</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span>    <span>return</span> <span>nil</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span>
</span></span><span><span>    <span>for</span> <span>_</span><span>,</span> <span>i</span> <span>:=</span> <span>range</span> <span>[]</span><span>int</span><span>{</span><span>7</span><span>,</span> <span>42</span><span>}</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>It’s common to use an inline error check in the <code>if</code> line.</p></td><td><pre><code><span><span>        <span>if</span> <span>r</span><span>,</span> <span>e</span> <span>:=</span> <span>f</span><span>(</span><span>i</span><span>);</span> <span>e</span> <span>!=</span> <span>nil</span> <span>{</span>
</span></span><span><span>            <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"f failed:"</span><span>,</span> <span>e</span><span>)</span>
</span></span><span><span>        <span>}</span> <span>else</span> <span>{</span>
</span></span><span><span>            <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"f worked:"</span><span>,</span> <span>r</span><span>)</span>
</span></span><span><span>        <span>}</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span>    <span>for</span> <span>i</span> <span>:=</span> <span>range</span> <span>5</span> <span>{</span>
</span></span><span><span>        <span>if</span> <span>err</span> <span>:=</span> <span>makeTea</span><span>(</span><span>i</span><span>);</span> <span>err</span> <span>!=</span> <span>nil</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p><code>errors.Is</code> checks that a given error (or any error in its chain) matches a specific error value. This is especially useful with wrapped or nested errors, allowing you to identify specific error types or sentinel errors in a chain of errors.</p></td><td><pre><code><span><span>            <span>if</span> <span>errors</span><span>.</span><span>Is</span><span>(</span><span>err</span><span>,</span> <span>ErrOutOfTea</span><span>)</span> <span>{</span>
</span></span><span><span>                <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"We should buy new tea!"</span><span>)</span>
</span></span><span><span>            <span>}</span> <span>else</span> <span>if</span> <span>errors</span><span>.</span><span>Is</span><span>(</span><span>err</span><span>,</span> <span>ErrPower</span><span>)</span> <span>{</span>
</span></span><span><span>                <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"Now it is dark."</span><span>)</span>
</span></span><span><span>            <span>}</span> <span>else</span> <span>{</span>
</span></span><span><span>                <span>fmt</span><span>.</span><span>Printf</span><span>(</span><span>"unknown error: %s\n"</span><span>,</span> <span>err</span><span>)</span>
</span></span><span><span>            <span>}</span>
</span></span><span><span>            <span>continue</span>
</span></span><span><span>        <span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"Tea is ready!"</span><span>)</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go run errors.go
</span></span><span><span><span>f worked: 10
</span></span></span><span><span><span>f failed: can't work with 42
</span></span></span><span><span><span>Tea is ready!
</span></span></span><span><span><span>Tea is ready!
</span></span></span><span><span><span>We should buy new tea!
</span></span></span><span><span><span>Tea is ready!
</span></span></span><span><span><span>Now it is dark.</span></span></span></code></pre></td></tr></tbody></table>

Next example: [Custom Errors](https://gobyexample.com/custom-errors).
