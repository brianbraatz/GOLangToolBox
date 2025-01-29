---
Description: Go by Example: Maps
Notes: Maps are Go’s built-in associative data type
(sometimes called hashes or dicts in other languages).
author: 
Url: https://gobyexample.com/maps
Created: "2025-01-29  02:42:24"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Maps

source: https://gobyexample.com/maps

> ## Excerpt
> Maps are Go’s built-in associative data type
(sometimes called hashes or dicts in other languages).

---
<table><tbody><tr><td><p><em>Maps</em> are Go’s built-in <a href="https://en.wikipedia.org/wiki/Associative_array">associative data type</a> (sometimes called <em>hashes</em> or <em>dicts</em> in other languages).</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/5jpkxJ2T0Lv"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"maps"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>To create an empty map, use the builtin <code>make</code>: <code>make(map[key-type]val-type)</code>.</p></td><td><pre><code><span><span>    <span>m</span> <span>:=</span> <span>make</span><span>(</span><span>map</span><span>[</span><span>string</span><span>]</span><span>int</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Set key/value pairs using typical <code>name[key] = val</code> syntax.</p></td><td><pre><code><span><span>    <span>m</span><span>[</span><span>"k1"</span><span>]</span> <span>=</span> <span>7</span>
</span></span><span><span>    <span>m</span><span>[</span><span>"k2"</span><span>]</span> <span>=</span> <span>13</span></span></span></code></pre></td></tr><tr><td><p>Printing a map with e.g. <code>fmt.Println</code> will show all of its key/value pairs.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"map:"</span><span>,</span> <span>m</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Get a value for a key with <code>name[key]</code>.</p></td><td><pre><code><span><span>    <span>v1</span> <span>:=</span> <span>m</span><span>[</span><span>"k1"</span><span>]</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"v1:"</span><span>,</span> <span>v1</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>If the key doesn’t exist, the <a href="https://go.dev/ref/spec#The_zero_value">zero value</a> of the value type is returned.</p></td><td><pre><code><span><span>    <span>v3</span> <span>:=</span> <span>m</span><span>[</span><span>"k3"</span><span>]</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"v3:"</span><span>,</span> <span>v3</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>The builtin <code>len</code> returns the number of key/value pairs when called on a map.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"len:"</span><span>,</span> <span>len</span><span>(</span><span>m</span><span>))</span></span></span></code></pre></td></tr><tr><td><p>The builtin <code>delete</code> removes key/value pairs from a map.</p></td><td><pre><code><span><span>    <span>delete</span><span>(</span><span>m</span><span>,</span> <span>"k2"</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"map:"</span><span>,</span> <span>m</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>To remove <em>all</em> key/value pairs from a map, use the <code>clear</code> builtin.</p></td><td><pre><code><span><span>    <span>clear</span><span>(</span><span>m</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"map:"</span><span>,</span> <span>m</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>The optional second return value when getting a value from a map indicates if the key was present in the map. This can be used to disambiguate between missing keys and keys with zero values like <code>0</code> or <code>""</code>. Here we didn’t need the value itself, so we ignored it with the <em>blank identifier</em> <code>_</code>.</p></td><td><pre><code><span><span>    <span>_</span><span>,</span> <span>prs</span> <span>:=</span> <span>m</span><span>[</span><span>"k2"</span><span>]</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"prs:"</span><span>,</span> <span>prs</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>You can also declare and initialize a new map in the same line with this syntax.</p></td><td><pre><code><span><span>    <span>n</span> <span>:=</span> <span>map</span><span>[</span><span>string</span><span>]</span><span>int</span><span>{</span><span>"foo"</span><span>:</span> <span>1</span><span>,</span> <span>"bar"</span><span>:</span> <span>2</span><span>}</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"map:"</span><span>,</span> <span>n</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>The <code>maps</code> package contains a number of useful utility functions for maps.</p></td><td><pre><code><span><span>    <span>n2</span> <span>:=</span> <span>map</span><span>[</span><span>string</span><span>]</span><span>int</span><span>{</span><span>"foo"</span><span>:</span> <span>1</span><span>,</span> <span>"bar"</span><span>:</span> <span>2</span><span>}</span>
</span></span><span><span>    <span>if</span> <span>maps</span><span>.</span><span>Equal</span><span>(</span><span>n</span><span>,</span> <span>n2</span><span>)</span> <span>{</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"n == n2"</span><span>)</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td><p>Note that maps appear in the form <code>map[k:v k:v]</code> when printed with <code>fmt.Println</code>.</p></td><td><pre><code><span><span><span>$</span> go run maps.go 
</span></span><span><span><span>map: map[k1:7 k2:13]
</span></span></span><span><span><span>v1: 7
</span></span></span><span><span><span>v3: 0
</span></span></span><span><span><span>len: 2
</span></span></span><span><span><span>map: map[k1:7]
</span></span></span><span><span><span>map: map[]
</span></span></span><span><span><span>prs: false
</span></span></span><span><span><span>map: map[bar:2 foo:1]
</span></span></span><span><span><span>n == n2</span></span></span></code></pre></td></tr></tbody></table>

Next example: [Functions](https://gobyexample.com/functions).
