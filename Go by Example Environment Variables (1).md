---
Description: Go by Example: Environment Variables
Notes: Environment variables
are a universal mechanism for conveying configuration
information to Unix programs.
Let’s look at how to set, get, and list environment variables.
author: 
Url: https://gobyexample.com/environment-variables
Created: "2025-01-29  02:48:26"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Environment Variables

source: https://gobyexample.com/environment-variables

> ## Excerpt
> Environment variables
are a universal mechanism for conveying configuration
information to Unix programs.
Let’s look at how to set, get, and list environment variables.

---
<table><tbody><tr><td><p><a href="https://en.wikipedia.org/wiki/Environment_variable">Environment variables</a> are a universal mechanism for <a href="https://www.12factor.net/config">conveying configuration information to Unix programs</a>. Let’s look at how to set, get, and list environment variables.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/2jmwXM264NC"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"os"</span>
</span></span><span><span>    <span>"strings"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>To set a key/value pair, use <code>os.Setenv</code>. To get a value for a key, use <code>os.Getenv</code>. This will return an empty string if the key isn’t present in the environment.</p></td><td><pre><code><span><span>    <span>os</span><span>.</span><span>Setenv</span><span>(</span><span>"FOO"</span><span>,</span> <span>"1"</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"FOO:"</span><span>,</span> <span>os</span><span>.</span><span>Getenv</span><span>(</span><span>"FOO"</span><span>))</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"BAR:"</span><span>,</span> <span>os</span><span>.</span><span>Getenv</span><span>(</span><span>"BAR"</span><span>))</span></span></span></code></pre></td></tr><tr><td><p>Use <code>os.Environ</code> to list all key/value pairs in the environment. This returns a slice of strings in the form <code>KEY=value</code>. You can <code>strings.SplitN</code> them to get the key and value. Here we print all the keys.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>()</span>
</span></span><span><span>    <span>for</span> <span>_</span><span>,</span> <span>e</span> <span>:=</span> <span>range</span> <span>os</span><span>.</span><span>Environ</span><span>()</span> <span>{</span>
</span></span><span><span>        <span>pair</span> <span>:=</span> <span>strings</span><span>.</span><span>SplitN</span><span>(</span><span>e</span><span>,</span> <span>"="</span><span>,</span> <span>2</span><span>)</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>pair</span><span>[</span><span>0</span><span>])</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td><p>Running the program shows that we pick up the value for <code>FOO</code> that we set in the program, but that <code>BAR</code> is empty.</p></td><td><pre><code><span><span><span>$</span> go run environment-variables.go
</span></span><span><span><span>FOO: 1
</span></span></span><span><span><span>BAR: </span></span></span></code></pre></td></tr><tr><td><p>The list of keys in the environment will depend on your particular machine.</p></td><td><pre><code><span><span><span>TERM_PROGRAM
</span></span></span><span><span><span>PATH
</span></span></span><span><span><span>SHELL
</span></span></span><span><span><span>...
</span></span></span><span><span><span>FOO</span></span></span></code></pre></td></tr><tr><td><p>If we set <code>BAR</code> in the environment first, the running program picks that value up.</p></td><td><pre><code><span><span><span>$</span> BAR=2 go run environment-variables.go
</span></span><span><span><span>FOO: 1
</span></span></span><span><span><span>BAR: 2
</span></span></span><span><span><span>...</span></span></span></code></pre></td></tr></tbody></table>

Next example: [Logging](https://gobyexample.com/logging).
