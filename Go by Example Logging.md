---
Description: Go by Example: Logging
Notes: The Go standard library provides straightforward
tools for outputting logs from Go programs, with
the log package for
free-form output and the
log/slog package for
structured output.
author: 
Url: https://gobyexample.com/logging
Created: "2025-01-29  02:48:31"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Logging

source: https://gobyexample.com/logging

> ## Excerpt
> The Go standard library provides straightforward
tools for outputting logs from Go programs, with
the log package for
free-form output and the
log/slog package for
structured output.

---
<table><tbody><tr><td><p>The Go standard library provides straightforward tools for outputting logs from Go programs, with the <a href="https://pkg.go.dev/log">log</a> package for free-form output and the <a href="https://pkg.go.dev/log/slog">log/slog</a> package for structured output.</p></td><td><a href="https://go.dev/play/p/Qd0uCqBlYUn"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"bytes"</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"log"</span>
</span></span><span><span>    <span>"os"</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span>    <span>"log/slog"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>Simply invoking functions like <code>Println</code> from the <code>log</code> package uses the <em>standard</em> logger, which is already pre-configured for reasonable logging output to <code>os.Stderr</code>. Additional methods like <code>Fatal*</code> or <code>Panic*</code> will exit the program after logging.</p></td><td><pre><code><span><span>    <span>log</span><span>.</span><span>Println</span><span>(</span><span>"standard logger"</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Loggers can be configured with <em>flags</em> to set their output format. By default, the standard logger has the <code>log.Ldate</code> and <code>log.Ltime</code> flags set, and these are collected in <code>log.LstdFlags</code>. We can change its flags to emit time with microsecond accuracy, for example.</p></td><td><pre><code><span><span>    <span>log</span><span>.</span><span>SetFlags</span><span>(</span><span>log</span><span>.</span><span>LstdFlags</span> <span>|</span> <span>log</span><span>.</span><span>Lmicroseconds</span><span>)</span>
</span></span><span><span>    <span>log</span><span>.</span><span>Println</span><span>(</span><span>"with micro"</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>It also supports emitting the file name and line from which the <code>log</code> function is called.</p></td><td><pre><code><span><span>    <span>log</span><span>.</span><span>SetFlags</span><span>(</span><span>log</span><span>.</span><span>LstdFlags</span> <span>|</span> <span>log</span><span>.</span><span>Lshortfile</span><span>)</span>
</span></span><span><span>    <span>log</span><span>.</span><span>Println</span><span>(</span><span>"with file/line"</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>It may be useful to create a custom logger and pass it around. When creating a new logger, we can set a <em>prefix</em> to distinguish its output from other loggers.</p></td><td><pre><code><span><span>    <span>mylog</span> <span>:=</span> <span>log</span><span>.</span><span>New</span><span>(</span><span>os</span><span>.</span><span>Stdout</span><span>,</span> <span>"my:"</span><span>,</span> <span>log</span><span>.</span><span>LstdFlags</span><span>)</span>
</span></span><span><span>    <span>mylog</span><span>.</span><span>Println</span><span>(</span><span>"from mylog"</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>We can set the prefix on existing loggers (including the standard one) with the <code>SetPrefix</code> method.</p></td><td><pre><code><span><span>    <span>mylog</span><span>.</span><span>SetPrefix</span><span>(</span><span>"ohmy:"</span><span>)</span>
</span></span><span><span>    <span>mylog</span><span>.</span><span>Println</span><span>(</span><span>"from mylog"</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Loggers can have custom output targets; any <code>io.Writer</code> works.</p></td><td><pre><code><span><span>    <span>var</span> <span>buf</span> <span>bytes</span><span>.</span><span>Buffer</span>
</span></span><span><span>    <span>buflog</span> <span>:=</span> <span>log</span><span>.</span><span>New</span><span>(</span><span>&amp;</span><span>buf</span><span>,</span> <span>"buf:"</span><span>,</span> <span>log</span><span>.</span><span>LstdFlags</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>This call writes the log output into <code>buf</code>.</p></td><td><pre><code><span><span>    <span>buflog</span><span>.</span><span>Println</span><span>(</span><span>"hello"</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>This will actually show it on standard output.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Print</span><span>(</span><span>"from buflog:"</span><span>,</span> <span>buf</span><span>.</span><span>String</span><span>())</span></span></span></code></pre></td></tr><tr><td><p>The <code>slog</code> package provides <em>structured</em> log output. For example, logging in JSON format is straightforward.</p></td><td><pre><code><span><span>    <span>jsonHandler</span> <span>:=</span> <span>slog</span><span>.</span><span>NewJSONHandler</span><span>(</span><span>os</span><span>.</span><span>Stderr</span><span>,</span> <span>nil</span><span>)</span>
</span></span><span><span>    <span>myslog</span> <span>:=</span> <span>slog</span><span>.</span><span>New</span><span>(</span><span>jsonHandler</span><span>)</span>
</span></span><span><span>    <span>myslog</span><span>.</span><span>Info</span><span>(</span><span>"hi there"</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>In addition to the message, <code>slog</code> output can contain an arbitrary number of key=value pairs.</p></td><td><pre><code><span><span>    <span>myslog</span><span>.</span><span>Info</span><span>(</span><span>"hello again"</span><span>,</span> <span>"key"</span><span>,</span> <span>"val"</span><span>,</span> <span>"age"</span><span>,</span> <span>25</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td><p>Sample output; the date and time emitted will depend on when the example ran.</p></td><td><pre><code><span><span><span>$</span> go run logging.go
</span></span><span><span><span>2023/08/22 10:45:16 standard logger
</span></span></span><span><span><span>2023/08/22 10:45:16.904141 with micro
</span></span></span><span><span><span>2023/08/22 10:45:16 logging.go:40: with file/line
</span></span></span><span><span><span>my:2023/08/22 10:45:16 from mylog
</span></span></span><span><span><span>ohmy:2023/08/22 10:45:16 from mylog
</span></span></span><span><span><span>from buflog:buf:2023/08/22 10:45:16 hello</span></span></span></code></pre></td></tr><tr><td><p>These are wrapped for clarity of presentation on the website; in reality they are emitted on a single line.</p></td><td><pre><code><span><span><span>{"time":"2023-08-22T10:45:16.904166391-07:00",
</span></span></span><span><span><span> "level":"INFO","msg":"hi there"}
</span></span></span><span><span><span>{"time":"2023-08-22T10:45:16.904178985-07:00",
</span></span></span><span><span><span>    "level":"INFO","msg":"hello again",
</span></span></span><span><span><span>    "key":"val","age":25}</span></span></span></code></pre></td></tr></tbody></table>

Next example: [HTTP Client](https://gobyexample.com/http-client).
