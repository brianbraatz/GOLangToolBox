---
Description: Go by Example: Spawning Processes
Notes: Sometimes our Go programs need to spawn other, non-Go
processes.
author: 
Url: https://gobyexample.com/spawning-processes
Created: "2025-01-29  02:48:43"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Spawning Processes

source: https://gobyexample.com/spawning-processes

> ## Excerpt
> Sometimes our Go programs need to spawn other, non-Go
processes.

---
<table><tbody><tr><td><p>Sometimes our Go programs need to spawn other, non-Go processes.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/rmnQdR-dMWU"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"io"</span>
</span></span><span><span>    <span>"os/exec"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>We’ll start with a simple command that takes no arguments or input and just prints something to stdout. The <code>exec.Command</code> helper creates an object to represent this external process.</p></td><td><pre><code><span><span>    <span>dateCmd</span> <span>:=</span> <span>exec</span><span>.</span><span>Command</span><span>(</span><span>"date"</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>The <code>Output</code> method runs the command, waits for it to finish and collects its standard output. If there were no errors, <code>dateOut</code> will hold bytes with the date info.</p></td><td><pre><code><span><span>    <span>dateOut</span><span>,</span> <span>err</span> <span>:=</span> <span>dateCmd</span><span>.</span><span>Output</span><span>()</span>
</span></span><span><span>    <span>if</span> <span>err</span> <span>!=</span> <span>nil</span> <span>{</span>
</span></span><span><span>        <span>panic</span><span>(</span><span>err</span><span>)</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"&gt; date"</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>string</span><span>(</span><span>dateOut</span><span>))</span></span></span></code></pre></td></tr><tr><td><p><code>Output</code> and other methods of <code>Command</code> will return <code>*exec.Error</code> if there was a problem executing the command (e.g. wrong path), and <code>*exec.ExitError</code> if the command ran but exited with a non-zero return code.</p></td><td><pre><code><span><span>    <span>_</span><span>,</span> <span>err</span> <span>=</span> <span>exec</span><span>.</span><span>Command</span><span>(</span><span>"date"</span><span>,</span> <span>"-x"</span><span>).</span><span>Output</span><span>()</span>
</span></span><span><span>    <span>if</span> <span>err</span> <span>!=</span> <span>nil</span> <span>{</span>
</span></span><span><span>        <span>switch</span> <span>e</span> <span>:=</span> <span>err</span><span>.(</span><span>type</span><span>)</span> <span>{</span>
</span></span><span><span>        <span>case</span> <span>*</span><span>exec</span><span>.</span><span>Error</span><span>:</span>
</span></span><span><span>            <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"failed executing:"</span><span>,</span> <span>err</span><span>)</span>
</span></span><span><span>        <span>case</span> <span>*</span><span>exec</span><span>.</span><span>ExitError</span><span>:</span>
</span></span><span><span>            <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"command exit rc ="</span><span>,</span> <span>e</span><span>.</span><span>ExitCode</span><span>())</span>
</span></span><span><span>        <span>default</span><span>:</span>
</span></span><span><span>            <span>panic</span><span>(</span><span>err</span><span>)</span>
</span></span><span><span>        <span>}</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td><p>Next we’ll look at a slightly more involved case where we pipe data to the external process on its <code>stdin</code> and collect the results from its <code>stdout</code>.</p></td><td><pre><code><span><span>    <span>grepCmd</span> <span>:=</span> <span>exec</span><span>.</span><span>Command</span><span>(</span><span>"grep"</span><span>,</span> <span>"hello"</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Here we explicitly grab input/output pipes, start the process, write some input to it, read the resulting output, and finally wait for the process to exit.</p></td><td><pre><code><span><span>    <span>grepIn</span><span>,</span> <span>_</span> <span>:=</span> <span>grepCmd</span><span>.</span><span>StdinPipe</span><span>()</span>
</span></span><span><span>    <span>grepOut</span><span>,</span> <span>_</span> <span>:=</span> <span>grepCmd</span><span>.</span><span>StdoutPipe</span><span>()</span>
</span></span><span><span>    <span>grepCmd</span><span>.</span><span>Start</span><span>()</span>
</span></span><span><span>    <span>grepIn</span><span>.</span><span>Write</span><span>([]</span><span>byte</span><span>(</span><span>"hello grep\ngoodbye grep"</span><span>))</span>
</span></span><span><span>    <span>grepIn</span><span>.</span><span>Close</span><span>()</span>
</span></span><span><span>    <span>grepBytes</span><span>,</span> <span>_</span> <span>:=</span> <span>io</span><span>.</span><span>ReadAll</span><span>(</span><span>grepOut</span><span>)</span>
</span></span><span><span>    <span>grepCmd</span><span>.</span><span>Wait</span><span>()</span></span></span></code></pre></td></tr><tr><td><p>We omitted error checks in the above example, but you could use the usual <code>if err != nil</code> pattern for all of them. We also only collect the <code>StdoutPipe</code> results, but you could collect the <code>StderrPipe</code> in exactly the same way.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"&gt; grep hello"</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>string</span><span>(</span><span>grepBytes</span><span>))</span></span></span></code></pre></td></tr><tr><td><p>Note that when spawning commands we need to provide an explicitly delineated command and argument array, vs. being able to just pass in one command-line string. If you want to spawn a full command with a string, you can use <code>bash</code>’s <code>-c</code> option:</p></td><td><pre><code><span><span>    <span>lsCmd</span> <span>:=</span> <span>exec</span><span>.</span><span>Command</span><span>(</span><span>"bash"</span><span>,</span> <span>"-c"</span><span>,</span> <span>"ls -a -l -h"</span><span>)</span>
</span></span><span><span>    <span>lsOut</span><span>,</span> <span>err</span> <span>:=</span> <span>lsCmd</span><span>.</span><span>Output</span><span>()</span>
</span></span><span><span>    <span>if</span> <span>err</span> <span>!=</span> <span>nil</span> <span>{</span>
</span></span><span><span>        <span>panic</span><span>(</span><span>err</span><span>)</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"&gt; ls -a -l -h"</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>string</span><span>(</span><span>lsOut</span><span>))</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td><p>The spawned programs return output that is the same as if we had run them directly from the command-line.</p></td><td><pre><code><span><span><span>$</span> go run spawning-processes.go 
</span></span><span><span><span>&gt;</span> date
</span></span><span><span><span>Thu 05 May 2022 10:10:12 PM PDT</span></span></span></code></pre></td></tr><tr><td><p>date doesn’t have a <code>-x</code> flag so it will exit with an error message and non-zero return code.</p></td><td><pre><code><span><span><span>command exited with rc = 1
</span></span></span><span><span><span></span><span>&gt;</span> grep hello
</span></span><span><span><span>hello grep</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>&gt;</span> ls -a -l -h
</span></span><span><span><span>drwxr-xr-x  4 mark 136B Oct 3 16:29 .
</span></span></span><span><span><span>drwxr-xr-x 91 mark 3.0K Oct 3 12:50 ..
</span></span></span><span><span><span>-rw-r--r--  1 mark 1.3K Oct 3 16:28 spawning-processes.go</span></span></span></code></pre></td></tr></tbody></table>

Next example: [Exec'ing Processes](https://gobyexample.com/execing-processes).
