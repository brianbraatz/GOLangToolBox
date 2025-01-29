---
Description: Go by Example: Time Formatting / Parsing
Notes: Go supports time formatting and parsing via
pattern-based layouts.
author: 
Url: https://gobyexample.com/time-formatting-parsing
Created: "2025-01-29  02:47:38"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Time Formatting / Parsing

source: https://gobyexample.com/time-formatting-parsing

> ## Excerpt
> Go supports time formatting and parsing via
pattern-based layouts.

---
<table><tbody><tr><td><p>Go supports time formatting and parsing via pattern-based layouts.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/BoZYtr_2j66"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"time"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span>
</span></span><span><span>    <span>p</span> <span>:=</span> <span>fmt</span><span>.</span><span>Println</span></span></span></code></pre></td></tr><tr><td><p>Here’s a basic example of formatting a time according to RFC3339, using the corresponding layout constant.</p></td><td><pre><code><span><span>    <span>t</span> <span>:=</span> <span>time</span><span>.</span><span>Now</span><span>()</span>
</span></span><span><span>    <span>p</span><span>(</span><span>t</span><span>.</span><span>Format</span><span>(</span><span>time</span><span>.</span><span>RFC3339</span><span>))</span></span></span></code></pre></td></tr><tr><td><p>Time parsing uses the same layout values as <code>Format</code>.</p></td><td><pre><code><span><span>    <span>t1</span><span>,</span> <span>e</span> <span>:=</span> <span>time</span><span>.</span><span>Parse</span><span>(</span>
</span></span><span><span>        <span>time</span><span>.</span><span>RFC3339</span><span>,</span>
</span></span><span><span>        <span>"2012-11-01T22:08:41+00:00"</span><span>)</span>
</span></span><span><span>    <span>p</span><span>(</span><span>t1</span><span>)</span></span></span></code></pre></td></tr><tr><td><p><code>Format</code> and <code>Parse</code> use example-based layouts. Usually you’ll use a constant from <code>time</code> for these layouts, but you can also supply custom layouts. Layouts must use the reference time <code>Mon Jan 2 15:04:05 MST 2006</code> to show the pattern with which to format/parse a given time/string. The example time must be exactly as shown: the year 2006, 15 for the hour, Monday for the day of the week, etc.</p></td><td><pre><code><span><span>    <span>p</span><span>(</span><span>t</span><span>.</span><span>Format</span><span>(</span><span>"3:04PM"</span><span>))</span>
</span></span><span><span>    <span>p</span><span>(</span><span>t</span><span>.</span><span>Format</span><span>(</span><span>"Mon Jan _2 15:04:05 2006"</span><span>))</span>
</span></span><span><span>    <span>p</span><span>(</span><span>t</span><span>.</span><span>Format</span><span>(</span><span>"2006-01-02T15:04:05.999999-07:00"</span><span>))</span>
</span></span><span><span>    <span>form</span> <span>:=</span> <span>"3 04 PM"</span>
</span></span><span><span>    <span>t2</span><span>,</span> <span>e</span> <span>:=</span> <span>time</span><span>.</span><span>Parse</span><span>(</span><span>form</span><span>,</span> <span>"8 41 PM"</span><span>)</span>
</span></span><span><span>    <span>p</span><span>(</span><span>t2</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>For purely numeric representations you can also use standard string formatting with the extracted components of the time value.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Printf</span><span>(</span><span>"%d-%02d-%02dT%02d:%02d:%02d-00:00\n"</span><span>,</span>
</span></span><span><span>        <span>t</span><span>.</span><span>Year</span><span>(),</span> <span>t</span><span>.</span><span>Month</span><span>(),</span> <span>t</span><span>.</span><span>Day</span><span>(),</span>
</span></span><span><span>        <span>t</span><span>.</span><span>Hour</span><span>(),</span> <span>t</span><span>.</span><span>Minute</span><span>(),</span> <span>t</span><span>.</span><span>Second</span><span>())</span></span></span></code></pre></td></tr><tr><td><p><code>Parse</code> will return an error on malformed input explaining the parsing problem.</p></td><td><pre><code><span><span>    <span>ansic</span> <span>:=</span> <span>"Mon Jan _2 15:04:05 2006"</span>
</span></span><span><span>    <span>_</span><span>,</span> <span>e</span> <span>=</span> <span>time</span><span>.</span><span>Parse</span><span>(</span><span>ansic</span><span>,</span> <span>"8:41PM"</span><span>)</span>
</span></span><span><span>    <span>p</span><span>(</span><span>e</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go run time-formatting-parsing.go 
</span></span><span><span><span>2014-04-15T18:00:15-07:00
</span></span></span><span><span><span>2012-11-01 22:08:41 +0000 +0000
</span></span></span><span><span><span>6:00PM
</span></span></span><span><span><span>Tue Apr 15 18:00:15 2014
</span></span></span><span><span><span>2014-04-15T18:00:15.161182-07:00
</span></span></span><span><span><span>0000-01-01 20:41:00 +0000 UTC
</span></span></span><span><span><span>2014-04-15T18:00:15-00:00
</span></span></span><span><span><span>parsing time "8:41PM" as "Mon Jan _2 15:04:05 2006": ...</span></span></span></code></pre></td></tr></tbody></table>

Next example: [Random Numbers](https://gobyexample.com/random-numbers).
