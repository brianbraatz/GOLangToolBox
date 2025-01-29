---
Description: Go by Example: Base64 Encoding
Notes: Go provides built-in support for base64
encoding/decoding.
author: 
Url: https://gobyexample.com/base64-encoding
Created: "2025-01-29  02:47:51"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Base64 Encoding

source: https://gobyexample.com/base64-encoding

> ## Excerpt
> Go provides built-in support for base64
encoding/decoding.

---
<table><tbody><tr><td><p>Go provides built-in support for <a href="https://en.wikipedia.org/wiki/Base64">base64 encoding/decoding</a>.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/yztzkirFEvv"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td><p>This syntax imports the <code>encoding/base64</code> package with the <code>b64</code> name instead of the default <code>base64</code>. It’ll save us some space below.</p></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>b64</span> <span>"encoding/base64"</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>Here’s the <code>string</code> we’ll encode/decode.</p></td><td><pre><code><span><span>    <span>data</span> <span>:=</span> <span>"abc123!?$*&amp;()'-=@~"</span></span></span></code></pre></td></tr><tr><td><p>Go supports both standard and URL-compatible base64. Here’s how to encode using the standard encoder. The encoder requires a <code>[]byte</code> so we convert our <code>string</code> to that type.</p></td><td><pre><code><span><span>    <span>sEnc</span> <span>:=</span> <span>b64</span><span>.</span><span>StdEncoding</span><span>.</span><span>EncodeToString</span><span>([]</span><span>byte</span><span>(</span><span>data</span><span>))</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>sEnc</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>Decoding may return an error, which you can check if you don’t already know the input to be well-formed.</p></td><td><pre><code><span><span>    <span>sDec</span><span>,</span> <span>_</span> <span>:=</span> <span>b64</span><span>.</span><span>StdEncoding</span><span>.</span><span>DecodeString</span><span>(</span><span>sEnc</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>string</span><span>(</span><span>sDec</span><span>))</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>()</span></span></span></code></pre></td></tr><tr><td><p>This encodes/decodes using a URL-compatible base64 format.</p></td><td><pre><code><span><span>    <span>uEnc</span> <span>:=</span> <span>b64</span><span>.</span><span>URLEncoding</span><span>.</span><span>EncodeToString</span><span>([]</span><span>byte</span><span>(</span><span>data</span><span>))</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>uEnc</span><span>)</span>
</span></span><span><span>    <span>uDec</span><span>,</span> <span>_</span> <span>:=</span> <span>b64</span><span>.</span><span>URLEncoding</span><span>.</span><span>DecodeString</span><span>(</span><span>uEnc</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>string</span><span>(</span><span>uDec</span><span>))</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td><p>The string encodes to slightly different values with the standard and URL base64 encoders (trailing <code>+</code> vs <code>-</code>) but they both decode to the original string as desired.</p></td><td><pre><code><span><span><span>$</span> go run base64-encoding.go
</span></span><span><span><span>YWJjMTIzIT8kKiYoKSctPUB+
</span></span></span><span><span><span>abc123!?$*&amp;()'-=@~</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>YWJjMTIzIT8kKiYoKSctPUB-
</span></span></span><span><span><span>abc123!?$*&amp;()'-=@~</span></span></span></code></pre></td></tr></tbody></table>

Next example: [Reading Files](https://gobyexample.com/reading-files).
