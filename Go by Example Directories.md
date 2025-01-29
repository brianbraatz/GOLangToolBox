---
Description: Go by Example: Directories
Notes: Go has several useful functions for working with
directories in the file system.
author: 
Url: https://gobyexample.com/directories
Created: "2025-01-29  02:48:06"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Directories

source: https://gobyexample.com/directories

> ## Excerpt
> Go has several useful functions for working with
directories in the file system.

---
<table><tbody><tr><td><p>Go has several useful functions for working with <em>directories</em> in the file system.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/ORNj2BPrLQr"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"io/fs"</span>
</span></span><span><span>    <span>"os"</span>
</span></span><span><span>    <span>"path/filepath"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>check</span><span>(</span><span>e</span> <span>error</span><span>)</span> <span>{</span>
</span></span><span><span>    <span>if</span> <span>e</span> <span>!=</span> <span>nil</span> <span>{</span>
</span></span><span><span>        <span>panic</span><span>(</span><span>e</span><span>)</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>Create a new sub-directory in the current working directory.</p></td><td><pre><code><span><span>    <span>err</span> <span>:=</span> <span>os</span><span>.</span><span>Mkdir</span><span>(</span><span>"subdir"</span><span>,</span> <span>0755</span><span>)</span>
</span></span><span><span>    <span>check</span><span>(</span><span>err</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>When creating temporary directories, it’s good practice to <code>defer</code> their removal. <code>os.RemoveAll</code> will delete a whole directory tree (similarly to <code>rm -rf</code>).</p></td><td><pre><code><span><span>    <span>defer</span> <span>os</span><span>.</span><span>RemoveAll</span><span>(</span><span>"subdir"</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Helper function to create a new empty file.</p></td><td><pre><code><span><span>    <span>createEmptyFile</span> <span>:=</span> <span>func</span><span>(</span><span>name</span> <span>string</span><span>)</span> <span>{</span>
</span></span><span><span>        <span>d</span> <span>:=</span> <span>[]</span><span>byte</span><span>(</span><span>""</span><span>)</span>
</span></span><span><span>        <span>check</span><span>(</span><span>os</span><span>.</span><span>WriteFile</span><span>(</span><span>name</span><span>,</span> <span>d</span><span>,</span> <span>0644</span><span>))</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span>    <span>createEmptyFile</span><span>(</span><span>"subdir/file1"</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>We can create a hierarchy of directories, including parents with <code>MkdirAll</code>. This is similar to the command-line <code>mkdir -p</code>.</p></td><td><pre><code><span><span>    <span>err</span> <span>=</span> <span>os</span><span>.</span><span>MkdirAll</span><span>(</span><span>"subdir/parent/child"</span><span>,</span> <span>0755</span><span>)</span>
</span></span><span><span>    <span>check</span><span>(</span><span>err</span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span>    <span>createEmptyFile</span><span>(</span><span>"subdir/parent/file2"</span><span>)</span>
</span></span><span><span>    <span>createEmptyFile</span><span>(</span><span>"subdir/parent/file3"</span><span>)</span>
</span></span><span><span>    <span>createEmptyFile</span><span>(</span><span>"subdir/parent/child/file4"</span><span>)</span></span></span></code></pre></td></tr><tr><td><p><code>ReadDir</code> lists directory contents, returning a slice of <code>os.DirEntry</code> objects.</p></td><td><pre><code><span><span>    <span>c</span><span>,</span> <span>err</span> <span>:=</span> <span>os</span><span>.</span><span>ReadDir</span><span>(</span><span>"subdir/parent"</span><span>)</span>
</span></span><span><span>    <span>check</span><span>(</span><span>err</span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"Listing subdir/parent"</span><span>)</span>
</span></span><span><span>    <span>for</span> <span>_</span><span>,</span> <span>entry</span> <span>:=</span> <span>range</span> <span>c</span> <span>{</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>" "</span><span>,</span> <span>entry</span><span>.</span><span>Name</span><span>(),</span> <span>entry</span><span>.</span><span>IsDir</span><span>())</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td><p><code>Chdir</code> lets us change the current working directory, similarly to <code>cd</code>.</p></td><td><pre><code><span><span>    <span>err</span> <span>=</span> <span>os</span><span>.</span><span>Chdir</span><span>(</span><span>"subdir/parent/child"</span><span>)</span>
</span></span><span><span>    <span>check</span><span>(</span><span>err</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Now we’ll see the contents of <code>subdir/parent/child</code> when listing the <em>current</em> directory.</p></td><td><pre><code><span><span>    <span>c</span><span>,</span> <span>err</span> <span>=</span> <span>os</span><span>.</span><span>ReadDir</span><span>(</span><span>"."</span><span>)</span>
</span></span><span><span>    <span>check</span><span>(</span><span>err</span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"Listing subdir/parent/child"</span><span>)</span>
</span></span><span><span>    <span>for</span> <span>_</span><span>,</span> <span>entry</span> <span>:=</span> <span>range</span> <span>c</span> <span>{</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>" "</span><span>,</span> <span>entry</span><span>.</span><span>Name</span><span>(),</span> <span>entry</span><span>.</span><span>IsDir</span><span>())</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td><p><code>cd</code> back to where we started.</p></td><td><pre><code><span><span>    <span>err</span> <span>=</span> <span>os</span><span>.</span><span>Chdir</span><span>(</span><span>"../../.."</span><span>)</span>
</span></span><span><span>    <span>check</span><span>(</span><span>err</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>We can also visit a directory <em>recursively</em>, including all its sub-directories. <code>WalkDir</code> accepts a callback function to handle every file or directory visited.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"Visiting subdir"</span><span>)</span>
</span></span><span><span>    <span>err</span> <span>=</span> <span>filepath</span><span>.</span><span>WalkDir</span><span>(</span><span>"subdir"</span><span>,</span> <span>visit</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td><p><code>visit</code> is called for every file or directory found recursively by <code>filepath.WalkDir</code>.</p></td><td><pre><code><span><span><span>func</span> <span>visit</span><span>(</span><span>path</span> <span>string</span><span>,</span> <span>d</span> <span>fs</span><span>.</span><span>DirEntry</span><span>,</span> <span>err</span> <span>error</span><span>)</span> <span>error</span> <span>{</span>
</span></span><span><span>    <span>if</span> <span>err</span> <span>!=</span> <span>nil</span> <span>{</span>
</span></span><span><span>        <span>return</span> <span>err</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>" "</span><span>,</span> <span>path</span><span>,</span> <span>d</span><span>.</span><span>IsDir</span><span>())</span>
</span></span><span><span>    <span>return</span> <span>nil</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go run directories.go
</span></span><span><span><span>Listing subdir/parent
</span></span></span><span><span><span>  child true
</span></span></span><span><span><span>  file2 false
</span></span></span><span><span><span>  file3 false
</span></span></span><span><span><span>Listing subdir/parent/child
</span></span></span><span><span><span>  file4 false
</span></span></span><span><span><span>Visiting subdir
</span></span></span><span><span><span>  subdir true
</span></span></span><span><span><span>  subdir/file1 false
</span></span></span><span><span><span>  subdir/parent true
</span></span></span><span><span><span>  subdir/parent/child true
</span></span></span><span><span><span>  subdir/parent/child/file4 false
</span></span></span><span><span><span>  subdir/parent/file2 false
</span></span></span><span><span><span>  subdir/parent/file3 false</span></span></span></code></pre></td></tr></tbody></table>

Next example: [Temporary Files and Directories](https://gobyexample.com/temporary-files-and-directories).
