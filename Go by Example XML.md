---
Description: Go by Example: XML
Notes: Go offers built-in support for XML and XML-like
formats with the encoding/xml package.
author: 
Url: https://gobyexample.com/xml
Created: "2025-01-29  02:47:27"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: XML

source: https://gobyexample.com/xml

> ## Excerpt
> Go offers built-in support for XML and XML-like
formats with the encoding/xml package.

---
<table><tbody><tr><td><p>Go offers built-in support for XML and XML-like formats with the <code>encoding/xml</code> package.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/vsP5mIrNJOG"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"encoding/xml"</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Plant will be mapped to XML. Similarly to the JSON examples, field tags contain directives for the encoder and decoder. Here we use some special features of the XML package: the <code>XMLName</code> field name dictates the name of the XML element representing this struct; <code>id,attr</code> means that the <code>Id</code> field is an XML <em>attribute</em> rather than a nested element.</p></td><td><pre><code><span><span><span>type</span> <span>Plant</span> <span>struct</span> <span>{</span>
</span></span><span><span>    <span>XMLName</span> <span>xml</span><span>.</span><span>Name</span> <span>`xml:"plant"`</span>
</span></span><span><span>    <span>Id</span>      <span>int</span>      <span>`xml:"id,attr"`</span>
</span></span><span><span>    <span>Name</span>    <span>string</span>   <span>`xml:"name"`</span>
</span></span><span><span>    <span>Origin</span>  <span>[]</span><span>string</span> <span>`xml:"origin"`</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>(</span><span>p</span> <span>Plant</span><span>)</span> <span>String</span><span>()</span> <span>string</span> <span>{</span>
</span></span><span><span>    <span>return</span> <span>fmt</span><span>.</span><span>Sprintf</span><span>(</span><span>"Plant id=%v, name=%v, origin=%v"</span><span>,</span>
</span></span><span><span>        <span>p</span><span>.</span><span>Id</span><span>,</span> <span>p</span><span>.</span><span>Name</span><span>,</span> <span>p</span><span>.</span><span>Origin</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span>
</span></span><span><span>    <span>coffee</span> <span>:=</span> <span>&amp;</span><span>Plant</span><span>{</span><span>Id</span><span>:</span> <span>27</span><span>,</span> <span>Name</span><span>:</span> <span>"Coffee"</span><span>}</span>
</span></span><span><span>    <span>coffee</span><span>.</span><span>Origin</span> <span>=</span> <span>[]</span><span>string</span><span>{</span><span>"Ethiopia"</span><span>,</span> <span>"Brazil"</span><span>}</span></span></span></code></pre></td></tr><tr><td><p>Emit XML representing our plant; using <code>MarshalIndent</code> to produce a more human-readable output.</p></td><td><pre><code><span><span>    <span>out</span><span>,</span> <span>_</span> <span>:=</span> <span>xml</span><span>.</span><span>MarshalIndent</span><span>(</span><span>coffee</span><span>,</span> <span>" "</span><span>,</span> <span>"  "</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>string</span><span>(</span><span>out</span><span>))</span></span></span></code></pre></td></tr><tr><td><p>To add a generic XML header to the output, append it explicitly.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>xml</span><span>.</span><span>Header</span> <span>+</span> <span>string</span><span>(</span><span>out</span><span>))</span></span></span></code></pre></td></tr><tr><td><p>Use <code>Unmarshal</code> to parse a stream of bytes with XML into a data structure. If the XML is malformed or cannot be mapped onto Plant, a descriptive error will be returned.</p></td><td><pre><code><span><span>    <span>var</span> <span>p</span> <span>Plant</span>
</span></span><span><span>    <span>if</span> <span>err</span> <span>:=</span> <span>xml</span><span>.</span><span>Unmarshal</span><span>(</span><span>out</span><span>,</span> <span>&amp;</span><span>p</span><span>);</span> <span>err</span> <span>!=</span> <span>nil</span> <span>{</span>
</span></span><span><span>        <span>panic</span><span>(</span><span>err</span><span>)</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>p</span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span>    <span>tomato</span> <span>:=</span> <span>&amp;</span><span>Plant</span><span>{</span><span>Id</span><span>:</span> <span>81</span><span>,</span> <span>Name</span><span>:</span> <span>"Tomato"</span><span>}</span>
</span></span><span><span>    <span>tomato</span><span>.</span><span>Origin</span> <span>=</span> <span>[]</span><span>string</span><span>{</span><span>"Mexico"</span><span>,</span> <span>"California"</span><span>}</span></span></span></code></pre></td></tr><tr><td><p>The <code>parent&gt;child&gt;plant</code> field tag tells the encoder to nest all <code>plant</code>s under <code>&lt;parent&gt;&lt;child&gt;...</code></p></td><td><pre><code><span><span>    <span>type</span> <span>Nesting</span> <span>struct</span> <span>{</span>
</span></span><span><span>        <span>XMLName</span> <span>xml</span><span>.</span><span>Name</span> <span>`xml:"nesting"`</span>
</span></span><span><span>        <span>Plants</span>  <span>[]</span><span>*</span><span>Plant</span> <span>`xml:"parent&gt;child&gt;plant"`</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span>    <span>nesting</span> <span>:=</span> <span>&amp;</span><span>Nesting</span><span>{}</span>
</span></span><span><span>    <span>nesting</span><span>.</span><span>Plants</span> <span>=</span> <span>[]</span><span>*</span><span>Plant</span><span>{</span><span>coffee</span><span>,</span> <span>tomato</span><span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span>    <span>out</span><span>,</span> <span>_</span> <span>=</span> <span>xml</span><span>.</span><span>MarshalIndent</span><span>(</span><span>nesting</span><span>,</span> <span>" "</span><span>,</span> <span>"  "</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>string</span><span>(</span><span>out</span><span>))</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go run xml.go
</span></span><span><span><span> &lt;plant id="27"&gt;
</span></span></span><span><span><span>   &lt;name&gt;Coffee&lt;/name&gt;
</span></span></span><span><span><span>   &lt;origin&gt;Ethiopia&lt;/origin&gt;
</span></span></span><span><span><span>   &lt;origin&gt;Brazil&lt;/origin&gt;
</span></span></span><span><span><span> &lt;/plant&gt;
</span></span></span><span><span><span>&lt;?xml version="1.0" encoding="UTF-8"?&gt;
</span></span></span><span><span><span> &lt;plant id="27"&gt;
</span></span></span><span><span><span>   &lt;name&gt;Coffee&lt;/name&gt;
</span></span></span><span><span><span>   &lt;origin&gt;Ethiopia&lt;/origin&gt;
</span></span></span><span><span><span>   &lt;origin&gt;Brazil&lt;/origin&gt;
</span></span></span><span><span><span> &lt;/plant&gt;
</span></span></span><span><span><span>Plant id=27, name=Coffee, origin=[Ethiopia Brazil]
</span></span></span><span><span><span> &lt;nesting&gt;
</span></span></span><span><span><span>   &lt;parent&gt;
</span></span></span><span><span><span>     &lt;child&gt;
</span></span></span><span><span><span>       &lt;plant id="27"&gt;
</span></span></span><span><span><span>         &lt;name&gt;Coffee&lt;/name&gt;
</span></span></span><span><span><span>         &lt;origin&gt;Ethiopia&lt;/origin&gt;
</span></span></span><span><span><span>         &lt;origin&gt;Brazil&lt;/origin&gt;
</span></span></span><span><span><span>       &lt;/plant&gt;
</span></span></span><span><span><span>       &lt;plant id="81"&gt;
</span></span></span><span><span><span>         &lt;name&gt;Tomato&lt;/name&gt;
</span></span></span><span><span><span>         &lt;origin&gt;Mexico&lt;/origin&gt;
</span></span></span><span><span><span>         &lt;origin&gt;California&lt;/origin&gt;
</span></span></span><span><span><span>       &lt;/plant&gt;
</span></span></span><span><span><span>     &lt;/child&gt;
</span></span></span><span><span><span>   &lt;/parent&gt;
</span></span></span><span><span><span> &lt;/nesting&gt;</span></span></span></code></pre></td></tr></tbody></table>

Next example: [Time](https://gobyexample.com/time).
