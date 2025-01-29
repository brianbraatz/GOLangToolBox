---
Description: Go by Example: Command-Line Flags
Notes: Command-line flags
are a common way to specify options for command-line
programs. For example, in wc -l the -l is a
command-line flag.
author: 
Url: https://gobyexample.com/command-line-flags
Created: "2025-01-29  02:48:20"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Command-Line Flags

source: https://gobyexample.com/command-line-flags

> ## Excerpt
> Command-line flags
are a common way to specify options for command-line
programs. For example, in wc -l the -l is a
command-line flag.

---
<table><tbody><tr><td><p><a href="https://en.wikipedia.org/wiki/Command-line_interface#Command-line_option"><em>Command-line flags</em></a> are a common way to specify options for command-line programs. For example, in <code>wc -l</code> the <code>-l</code> is a command-line flag.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/IUPZlYSigc3"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td><p>Go provides a <code>flag</code> package supporting basic command-line flag parsing. We’ll use this package to implement our example command-line program.</p></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"flag"</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>Basic flag declarations are available for string, integer, and boolean options. Here we declare a string flag <code>word</code> with a default value <code>"foo"</code> and a short description. This <code>flag.String</code> function returns a string pointer (not a string value); we’ll see how to use this pointer below.</p></td><td><pre><code><span><span>    <span>wordPtr</span> <span>:=</span> <span>flag</span><span>.</span><span>String</span><span>(</span><span>"word"</span><span>,</span> <span>"foo"</span><span>,</span> <span>"a string"</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>This declares <code>numb</code> and <code>fork</code> flags, using a similar approach to the <code>word</code> flag.</p></td><td><pre><code><span><span>    <span>numbPtr</span> <span>:=</span> <span>flag</span><span>.</span><span>Int</span><span>(</span><span>"numb"</span><span>,</span> <span>42</span><span>,</span> <span>"an int"</span><span>)</span>
</span></span><span><span>    <span>forkPtr</span> <span>:=</span> <span>flag</span><span>.</span><span>Bool</span><span>(</span><span>"fork"</span><span>,</span> <span>false</span><span>,</span> <span>"a bool"</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>It’s also possible to declare an option that uses an existing var declared elsewhere in the program. Note that we need to pass in a pointer to the flag declaration function.</p></td><td><pre><code><span><span>    <span>var</span> <span>svar</span> <span>string</span>
</span></span><span><span>    <span>flag</span><span>.</span><span>StringVar</span><span>(</span><span>&amp;</span><span>svar</span><span>,</span> <span>"svar"</span><span>,</span> <span>"bar"</span><span>,</span> <span>"a string var"</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Once all flags are declared, call <code>flag.Parse()</code> to execute the command-line parsing.</p></td><td><pre><code><span><span>    <span>flag</span><span>.</span><span>Parse</span><span>()</span></span></span></code></pre></td></tr><tr><td><p>Here we’ll just dump out the parsed options and any trailing positional arguments. Note that we need to dereference the pointers with e.g. <code>*wordPtr</code> to get the actual option values.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"word:"</span><span>,</span> <span>*</span><span>wordPtr</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"numb:"</span><span>,</span> <span>*</span><span>numbPtr</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"fork:"</span><span>,</span> <span>*</span><span>forkPtr</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"svar:"</span><span>,</span> <span>svar</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"tail:"</span><span>,</span> <span>flag</span><span>.</span><span>Args</span><span>())</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td><p>To experiment with the command-line flags program it’s best to first compile it and then run the resulting binary directly.</p></td><td><pre><code><span><span><span>$</span> go build command-line-flags.go</span></span></code></pre></td></tr><tr><td><p>Try out the built program by first giving it values for all flags.</p></td><td><pre><code><span><span><span>$</span> ./command-line-flags -word=opt -numb=7 -fork -svar=flag
</span></span><span><span><span>word: opt
</span></span></span><span><span><span>numb: 7
</span></span></span><span><span><span>fork: true
</span></span></span><span><span><span>svar: flag
</span></span></span><span><span><span>tail: []</span></span></span></code></pre></td></tr><tr><td><p>Note that if you omit flags they automatically take their default values.</p></td><td><pre><code><span><span><span>$</span> ./command-line-flags -word=opt
</span></span><span><span><span>word: opt
</span></span></span><span><span><span>numb: 42
</span></span></span><span><span><span>fork: false
</span></span></span><span><span><span>svar: bar
</span></span></span><span><span><span>tail: []</span></span></span></code></pre></td></tr><tr><td><p>Trailing positional arguments can be provided after any flags.</p></td><td><pre><code><span><span><span>$</span> ./command-line-flags -word=opt a1 a2 a3
</span></span><span><span><span>word: opt
</span></span></span><span><span><span>...
</span></span></span><span><span><span>tail: [a1 a2 a3]</span></span></span></code></pre></td></tr><tr><td><p>Note that the <code>flag</code> package requires all flags to appear before positional arguments (otherwise the flags will be interpreted as positional arguments).</p></td><td><pre><code><span><span><span>$</span> ./command-line-flags -word=opt a1 a2 a3 -numb=7
</span></span><span><span><span>word: opt
</span></span></span><span><span><span>numb: 42
</span></span></span><span><span><span>fork: false
</span></span></span><span><span><span>svar: bar
</span></span></span><span><span><span>tail: [a1 a2 a3 -numb=7]</span></span></span></code></pre></td></tr><tr><td><p>Use <code>-h</code> or <code>--help</code> flags to get automatically generated help text for the command-line program.</p></td><td><pre><code><span><span><span>$</span> ./command-line-flags -h
</span></span><span><span><span>Usage of ./command-line-flags:
</span></span></span><span><span><span>  -fork=false: a bool
</span></span></span><span><span><span>  -numb=42: an int
</span></span></span><span><span><span>  -svar="bar": a string var
</span></span></span><span><span><span>  -word="foo": a string</span></span></span></code></pre></td></tr><tr><td><p>If you provide a flag that wasn’t specified to the <code>flag</code> package, the program will print an error message and show the help text again.</p></td><td><pre><code><span><span><span>$</span> ./command-line-flags -wat
</span></span><span><span><span>flag provided but not defined: -wat
</span></span></span><span><span><span>Usage of ./command-line-flags:
</span></span></span><span><span><span>...</span></span></span></code></pre></td></tr></tbody></table>

Next example: [Command-Line Subcommands](https://gobyexample.com/command-line-subcommands).
