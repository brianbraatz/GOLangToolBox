---
Description: Go by Example: File Paths
Notes: The filepath package provides functions to parse
and construct file paths in a way that is portable
between operating systems; dir/file on Linux vs.
dir\file on Windows, for example.
author: 
Url: https://gobyexample.com/file-paths
Created: "2025-01-29  02:48:03"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: File Paths

source: https://gobyexample.com/file-paths

> ## Excerpt
> The filepath package provides functions to parse
and construct file paths in a way that is portable
between operating systems; dir/file on Linux vs.
dir\file on Windows, for example.

---
<table><tbody><tr><td><p>The <code>filepath</code> package provides functions to parse and construct <em>file paths</em> in a way that is portable between operating systems; <code>dir/file</code> on Linux vs. <code>dir\file</code> on Windows, for example.</p></td><td><a href="https://go.dev/play/p/5h3lUytvmyO"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"path/filepath"</span>
</span></span><span><span>    <span>"strings"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p><code>Join</code> should be used to construct paths in a portable way. It takes any number of arguments and constructs a hierarchical path from them.</p></td><td><pre><code><span><span>    <span>p</span> <span>:=</span> <span>filepath</span><span>.</span><span>Join</span><span>(</span><span>"dir1"</span><span>,</span> <span>"dir2"</span><span>,</span> <span>"filename"</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"p:"</span><span>,</span> <span>p</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>You should always use <code>Join</code> instead of concatenating <code>/</code>s or <code>\</code>s manually. In addition to providing portability, <code>Join</code> will also normalize paths by removing superfluous separators and directory changes.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>filepath</span><span>.</span><span>Join</span><span>(</span><span>"dir1//"</span><span>,</span> <span>"filename"</span><span>))</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>filepath</span><span>.</span><span>Join</span><span>(</span><span>"dir1/../dir1"</span><span>,</span> <span>"filename"</span><span>))</span></span></span></code></pre></td></tr><tr><td><p><code>Dir</code> and <code>Base</code> can be used to split a path to the directory and the file. Alternatively, <code>Split</code> will return both in the same call.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"Dir(p):"</span><span>,</span> <span>filepath</span><span>.</span><span>Dir</span><span>(</span><span>p</span><span>))</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"Base(p):"</span><span>,</span> <span>filepath</span><span>.</span><span>Base</span><span>(</span><span>p</span><span>))</span></span></span></code></pre></td></tr><tr><td><p>We can check whether a path is absolute.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>filepath</span><span>.</span><span>IsAbs</span><span>(</span><span>"dir/file"</span><span>))</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>filepath</span><span>.</span><span>IsAbs</span><span>(</span><span>"/dir/file"</span><span>))</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span>    <span>filename</span> <span>:=</span> <span>"config.json"</span></span></span></code></pre></td></tr><tr><td><p>Some file names have extensions following a dot. We can split the extension out of such names with <code>Ext</code>.</p></td><td><pre><code><span><span>    <span>ext</span> <span>:=</span> <span>filepath</span><span>.</span><span>Ext</span><span>(</span><span>filename</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>ext</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>To find the file’s name with the extension removed, use <code>strings.TrimSuffix</code>.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>strings</span><span>.</span><span>TrimSuffix</span><span>(</span><span>filename</span><span>,</span> <span>ext</span><span>))</span></span></span></code></pre></td></tr><tr><td><p><code>Rel</code> finds a relative path between a <em>base</em> and a <em>target</em>. It returns an error if the target cannot be made relative to base.</p></td><td><pre><code><span><span>    <span>rel</span><span>,</span> <span>err</span> <span>:=</span> <span>filepath</span><span>.</span><span>Rel</span><span>(</span><span>"a/b"</span><span>,</span> <span>"a/b/t/file"</span><span>)</span>
</span></span><span><span>    <span>if</span> <span>err</span> <span>!=</span> <span>nil</span> <span>{</span>
</span></span><span><span>        <span>panic</span><span>(</span><span>err</span><span>)</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>rel</span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span>    <span>rel</span><span>,</span> <span>err</span> <span>=</span> <span>filepath</span><span>.</span><span>Rel</span><span>(</span><span>"a/b"</span><span>,</span> <span>"a/c/t/file"</span><span>)</span>
</span></span><span><span>    <span>if</span> <span>err</span> <span>!=</span> <span>nil</span> <span>{</span>
</span></span><span><span>        <span>panic</span><span>(</span><span>err</span><span>)</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>rel</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go run file-paths.go
</span></span><span><span><span>p: dir1/dir2/filename
</span></span></span><span><span><span>dir1/filename
</span></span></span><span><span><span>dir1/filename
</span></span></span><span><span><span>Dir(p): dir1/dir2
</span></span></span><span><span><span>Base(p): filename
</span></span></span><span><span><span>false
</span></span></span><span><span><span>true
</span></span></span><span><span><span>.json
</span></span></span><span><span><span>config
</span></span></span><span><span><span>t/file
</span></span></span><span><span><span>../c/t/file</span></span></span></code></pre></td></tr></tbody></table>

Next example: [Directories](https://gobyexample.com/directories).
