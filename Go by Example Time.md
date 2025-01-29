---
Description: Go by Example: Time
Notes: Go offers extensive support for times and durations;
here are some examples.
author: 
Url: https://gobyexample.com/time
Created: "2025-01-29  02:47:29"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Time

source: https://gobyexample.com/time

> ## Excerpt
> Go offers extensive support for times and durations;
here are some examples.

---
<table><tbody><tr><td><p>Go offers extensive support for times and durations; here are some examples.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/YAM3s1KPc8c"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"time"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span>
</span></span><span><span>    <span>p</span> <span>:=</span> <span>fmt</span><span>.</span><span>Println</span></span></span></code></pre></td></tr><tr><td><p>We’ll start by getting the current time.</p></td><td><pre><code><span><span>    <span>now</span> <span>:=</span> <span>time</span><span>.</span><span>Now</span><span>()</span>
</span></span><span><span>    <span>p</span><span>(</span><span>now</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>You can build a <code>time</code> struct by providing the year, month, day, etc. Times are always associated with a <code>Location</code>, i.e. time zone.</p></td><td><pre><code><span><span>    <span>then</span> <span>:=</span> <span>time</span><span>.</span><span>Date</span><span>(</span>
</span></span><span><span>        <span>2009</span><span>,</span> <span>11</span><span>,</span> <span>17</span><span>,</span> <span>20</span><span>,</span> <span>34</span><span>,</span> <span>58</span><span>,</span> <span>651387237</span><span>,</span> <span>time</span><span>.</span><span>UTC</span><span>)</span>
</span></span><span><span>    <span>p</span><span>(</span><span>then</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>You can extract the various components of the time value as expected.</p></td><td><pre><code><span><span>    <span>p</span><span>(</span><span>then</span><span>.</span><span>Year</span><span>())</span>
</span></span><span><span>    <span>p</span><span>(</span><span>then</span><span>.</span><span>Month</span><span>())</span>
</span></span><span><span>    <span>p</span><span>(</span><span>then</span><span>.</span><span>Day</span><span>())</span>
</span></span><span><span>    <span>p</span><span>(</span><span>then</span><span>.</span><span>Hour</span><span>())</span>
</span></span><span><span>    <span>p</span><span>(</span><span>then</span><span>.</span><span>Minute</span><span>())</span>
</span></span><span><span>    <span>p</span><span>(</span><span>then</span><span>.</span><span>Second</span><span>())</span>
</span></span><span><span>    <span>p</span><span>(</span><span>then</span><span>.</span><span>Nanosecond</span><span>())</span>
</span></span><span><span>    <span>p</span><span>(</span><span>then</span><span>.</span><span>Location</span><span>())</span></span></span></code></pre></td></tr><tr><td><p>The Monday-Sunday <code>Weekday</code> is also available.</p></td><td><pre><code><span><span>    <span>p</span><span>(</span><span>then</span><span>.</span><span>Weekday</span><span>())</span></span></span></code></pre></td></tr><tr><td><p>These methods compare two times, testing if the first occurs before, after, or at the same time as the second, respectively.</p></td><td><pre><code><span><span>    <span>p</span><span>(</span><span>then</span><span>.</span><span>Before</span><span>(</span><span>now</span><span>))</span>
</span></span><span><span>    <span>p</span><span>(</span><span>then</span><span>.</span><span>After</span><span>(</span><span>now</span><span>))</span>
</span></span><span><span>    <span>p</span><span>(</span><span>then</span><span>.</span><span>Equal</span><span>(</span><span>now</span><span>))</span></span></span></code></pre></td></tr><tr><td><p>The <code>Sub</code> methods returns a <code>Duration</code> representing the interval between two times.</p></td><td><pre><code><span><span>    <span>diff</span> <span>:=</span> <span>now</span><span>.</span><span>Sub</span><span>(</span><span>then</span><span>)</span>
</span></span><span><span>    <span>p</span><span>(</span><span>diff</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>We can compute the length of the duration in various units.</p></td><td><pre><code><span><span>    <span>p</span><span>(</span><span>diff</span><span>.</span><span>Hours</span><span>())</span>
</span></span><span><span>    <span>p</span><span>(</span><span>diff</span><span>.</span><span>Minutes</span><span>())</span>
</span></span><span><span>    <span>p</span><span>(</span><span>diff</span><span>.</span><span>Seconds</span><span>())</span>
</span></span><span><span>    <span>p</span><span>(</span><span>diff</span><span>.</span><span>Nanoseconds</span><span>())</span></span></span></code></pre></td></tr><tr><td><p>You can use <code>Add</code> to advance a time by a given duration, or with a <code>-</code> to move backwards by a duration.</p></td><td><pre><code><span><span>    <span>p</span><span>(</span><span>then</span><span>.</span><span>Add</span><span>(</span><span>diff</span><span>))</span>
</span></span><span><span>    <span>p</span><span>(</span><span>then</span><span>.</span><span>Add</span><span>(</span><span>-</span><span>diff</span><span>))</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go run time.go
</span></span><span><span><span>2012-10-31 15:50:13.793654 +0000 UTC
</span></span></span><span><span><span>2009-11-17 20:34:58.651387237 +0000 UTC
</span></span></span><span><span><span>2009
</span></span></span><span><span><span>November
</span></span></span><span><span><span>17
</span></span></span><span><span><span>20
</span></span></span><span><span><span>34
</span></span></span><span><span><span>58
</span></span></span><span><span><span>651387237
</span></span></span><span><span><span>UTC
</span></span></span><span><span><span>Tuesday
</span></span></span><span><span><span>true
</span></span></span><span><span><span>false
</span></span></span><span><span><span>false
</span></span></span><span><span><span>25891h15m15.142266763s
</span></span></span><span><span><span>25891.25420618521
</span></span></span><span><span><span>1.5534752523711128e+06
</span></span></span><span><span><span>9.320851514226677e+07
</span></span></span><span><span><span>93208515142266763
</span></span></span><span><span><span>2012-10-31 15:50:13.793654 +0000 UTC
</span></span></span><span><span><span>2006-12-05 01:19:43.509120474 +0000 UTC</span></span></span></code></pre></td></tr><tr><td><p>Next we’ll look at the related idea of time relative to the Unix epoch.</p></td><td></td></tr></tbody></table>

Next example: [Epoch](https://gobyexample.com/epoch).
