---
Description: Go by Example: Temporary Files and Directories
Notes: Throughout program execution, we often want to create
data that isn’t needed after the program exits.
Temporary files and directories are useful for this
purpose since they don’t pollute the file system over
time.
author: 
Url: https://gobyexample.com/temporary-files-and-directories
Created: "2025-01-29  02:48:08"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Temporary Files and Directories

source: https://gobyexample.com/temporary-files-and-directories

> ## Excerpt
> Throughout program execution, we often want to create
data that isn’t needed after the program exits.
Temporary files and directories are useful for this
purpose since they don’t pollute the file system over
time.

---
<table><tbody><tr><td><p>Throughout program execution, we often want to create data that isn’t needed after the program exits. <em>Temporary files and directories</em> are useful for this purpose since they don’t pollute the file system over time.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/hVcPg9RH3_V"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"os"</span>
</span></span><span><span>    <span>"path/filepath"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>check</span><span>(</span><span>e</span> <span>error</span><span>)</span> <span>{</span>
</span></span><span><span>    <span>if</span> <span>e</span> <span>!=</span> <span>nil</span> <span>{</span>
</span></span><span><span>        <span>panic</span><span>(</span><span>e</span><span>)</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>The easiest way to create a temporary file is by calling <code>os.CreateTemp</code>. It creates a file <em>and</em> opens it for reading and writing. We provide <code>""</code> as the first argument, so <code>os.CreateTemp</code> will create the file in the default location for our OS.</p></td><td><pre><code><span><span>    <span>f</span><span>,</span> <span>err</span> <span>:=</span> <span>os</span><span>.</span><span>CreateTemp</span><span>(</span><span>""</span><span>,</span> <span>"sample"</span><span>)</span>
</span></span><span><span>    <span>check</span><span>(</span><span>err</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Display the name of the temporary file. On Unix-based OSes the directory will likely be <code>/tmp</code>. The file name starts with the prefix given as the second argument to <code>os.CreateTemp</code> and the rest is chosen automatically to ensure that concurrent calls will always create different file names.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"Temp file name:"</span><span>,</span> <span>f</span><span>.</span><span>Name</span><span>())</span></span></span></code></pre></td></tr><tr><td><p>Clean up the file after we’re done. The OS is likely to clean up temporary files by itself after some time, but it’s good practice to do this explicitly.</p></td><td><pre><code><span><span>    <span>defer</span> <span>os</span><span>.</span><span>Remove</span><span>(</span><span>f</span><span>.</span><span>Name</span><span>())</span></span></span></code></pre></td></tr><tr><td><p>We can write some data to the file.</p></td><td><pre><code><span><span>    <span>_</span><span>,</span> <span>err</span> <span>=</span> <span>f</span><span>.</span><span>Write</span><span>([]</span><span>byte</span><span>{</span><span>1</span><span>,</span> <span>2</span><span>,</span> <span>3</span><span>,</span> <span>4</span><span>})</span>
</span></span><span><span>    <span>check</span><span>(</span><span>err</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>If we intend to write many temporary files, we may prefer to create a temporary <em>directory</em>. <code>os.MkdirTemp</code>’s arguments are the same as <code>CreateTemp</code>’s, but it returns a directory <em>name</em> rather than an open file.</p></td><td><pre><code><span><span>    <span>dname</span><span>,</span> <span>err</span> <span>:=</span> <span>os</span><span>.</span><span>MkdirTemp</span><span>(</span><span>""</span><span>,</span> <span>"sampledir"</span><span>)</span>
</span></span><span><span>    <span>check</span><span>(</span><span>err</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"Temp dir name:"</span><span>,</span> <span>dname</span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span>    <span>defer</span> <span>os</span><span>.</span><span>RemoveAll</span><span>(</span><span>dname</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Now we can synthesize temporary file names by prefixing them with our temporary directory.</p></td><td><pre><code><span><span>    <span>fname</span> <span>:=</span> <span>filepath</span><span>.</span><span>Join</span><span>(</span><span>dname</span><span>,</span> <span>"file1"</span><span>)</span>
</span></span><span><span>    <span>err</span> <span>=</span> <span>os</span><span>.</span><span>WriteFile</span><span>(</span><span>fname</span><span>,</span> <span>[]</span><span>byte</span><span>{</span><span>1</span><span>,</span> <span>2</span><span>},</span> <span>0666</span><span>)</span>
</span></span><span><span>    <span>check</span><span>(</span><span>err</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go run temporary-files-and-directories.go
</span></span><span><span><span>Temp file name: /tmp/sample610887201
</span></span></span><span><span><span>Temp dir name: /tmp/sampledir898854668</span></span></span></code></pre></td></tr></tbody></table>

Next example: [Embed Directive](https://gobyexample.com/embed-directive).
