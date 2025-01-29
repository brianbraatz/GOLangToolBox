---
Description: Go by Example: Command-Line Subcommands
Notes: Some command-line tools, like the go tool or git
have many subcommands, each with its own set of
flags. For example, go build and go get are two
different subcommands of the go tool.
The flag package lets us easily define simple
subcommands that have their own flags.
author: 
Url: https://gobyexample.com/command-line-subcommands
Created: "2025-01-29  02:48:23"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Command-Line Subcommands

source: https://gobyexample.com/command-line-subcommands

> ## Excerpt
> Some command-line tools, like the go tool or git
have many subcommands, each with its own set of
flags. For example, go build and go get are two
different subcommands of the go tool.
The flag package lets us easily define simple
subcommands that have their own flags.

---
<table><tbody><tr><td><p>Some command-line tools, like the <code>go</code> tool or <code>git</code> have many <em>subcommands</em>, each with its own set of flags. For example, <code>go build</code> and <code>go get</code> are two different subcommands of the <code>go</code> tool. The <code>flag</code> package lets us easily define simple subcommands that have their own flags.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/DkvdHKK-XCv"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"flag"</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"os"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>We declare a subcommand using the <code>NewFlagSet</code> function, and proceed to define new flags specific for this subcommand.</p></td><td><pre><code><span><span>    <span>fooCmd</span> <span>:=</span> <span>flag</span><span>.</span><span>NewFlagSet</span><span>(</span><span>"foo"</span><span>,</span> <span>flag</span><span>.</span><span>ExitOnError</span><span>)</span>
</span></span><span><span>    <span>fooEnable</span> <span>:=</span> <span>fooCmd</span><span>.</span><span>Bool</span><span>(</span><span>"enable"</span><span>,</span> <span>false</span><span>,</span> <span>"enable"</span><span>)</span>
</span></span><span><span>    <span>fooName</span> <span>:=</span> <span>fooCmd</span><span>.</span><span>String</span><span>(</span><span>"name"</span><span>,</span> <span>""</span><span>,</span> <span>"name"</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>For a different subcommand we can define different supported flags.</p></td><td><pre><code><span><span>    <span>barCmd</span> <span>:=</span> <span>flag</span><span>.</span><span>NewFlagSet</span><span>(</span><span>"bar"</span><span>,</span> <span>flag</span><span>.</span><span>ExitOnError</span><span>)</span>
</span></span><span><span>    <span>barLevel</span> <span>:=</span> <span>barCmd</span><span>.</span><span>Int</span><span>(</span><span>"level"</span><span>,</span> <span>0</span><span>,</span> <span>"level"</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>The subcommand is expected as the first argument to the program.</p></td><td><pre><code><span><span>    <span>if</span> <span>len</span><span>(</span><span>os</span><span>.</span><span>Args</span><span>)</span> <span>&lt;</span> <span>2</span> <span>{</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"expected 'foo' or 'bar' subcommands"</span><span>)</span>
</span></span><span><span>        <span>os</span><span>.</span><span>Exit</span><span>(</span><span>1</span><span>)</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td><p>Check which subcommand is invoked.</p></td><td><pre><code><span><span>    <span>switch</span> <span>os</span><span>.</span><span>Args</span><span>[</span><span>1</span><span>]</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>For every subcommand, we parse its own flags and have access to trailing positional arguments.</p></td><td><pre><code><span><span>    <span>case</span> <span>"foo"</span><span>:</span>
</span></span><span><span>        <span>fooCmd</span><span>.</span><span>Parse</span><span>(</span><span>os</span><span>.</span><span>Args</span><span>[</span><span>2</span><span>:])</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"subcommand 'foo'"</span><span>)</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"  enable:"</span><span>,</span> <span>*</span><span>fooEnable</span><span>)</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"  name:"</span><span>,</span> <span>*</span><span>fooName</span><span>)</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"  tail:"</span><span>,</span> <span>fooCmd</span><span>.</span><span>Args</span><span>())</span>
</span></span><span><span>    <span>case</span> <span>"bar"</span><span>:</span>
</span></span><span><span>        <span>barCmd</span><span>.</span><span>Parse</span><span>(</span><span>os</span><span>.</span><span>Args</span><span>[</span><span>2</span><span>:])</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"subcommand 'bar'"</span><span>)</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"  level:"</span><span>,</span> <span>*</span><span>barLevel</span><span>)</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"  tail:"</span><span>,</span> <span>barCmd</span><span>.</span><span>Args</span><span>())</span>
</span></span><span><span>    <span>default</span><span>:</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"expected 'foo' or 'bar' subcommands"</span><span>)</span>
</span></span><span><span>        <span>os</span><span>.</span><span>Exit</span><span>(</span><span>1</span><span>)</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go build command-line-subcommands.go </span></span></code></pre></td></tr><tr><td><p>First invoke the foo subcommand.</p></td><td><pre><code><span><span><span>$</span> ./command-line-subcommands foo -enable -name=joe a1 a2
</span></span><span><span><span>subcommand 'foo'
</span></span></span><span><span><span>  enable: true
</span></span></span><span><span><span>  name: joe
</span></span></span><span><span><span>  tail: [a1 a2]</span></span></span></code></pre></td></tr><tr><td><p>Now try bar.</p></td><td><pre><code><span><span><span>$</span> ./command-line-subcommands bar -level 8 a1
</span></span><span><span><span>subcommand 'bar'
</span></span></span><span><span><span>  level: 8
</span></span></span><span><span><span>  tail: [a1]</span></span></span></code></pre></td></tr><tr><td><p>But bar won’t accept foo’s flags.</p></td><td><pre><code><span><span><span>$</span> ./command-line-subcommands bar -enable a1
</span></span><span><span><span>flag provided but not defined: -enable
</span></span></span><span><span><span>Usage of bar:
</span></span></span><span><span><span>  -level int
</span></span></span><span><span><span>        level</span></span></span></code></pre></td></tr><tr><td><p>Next we’ll look at environment variables, another common way to parameterize programs.</p></td><td></td></tr></tbody></table>

Next example: [Environment Variables](https://gobyexample.com/environment-variables).
