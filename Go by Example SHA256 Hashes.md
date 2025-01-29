---
Description: Go by Example: SHA256 Hashes
Notes: SHA256 hashes are
frequently used to compute short identities for binary
or text blobs. For example, TLS/SSL certificates use SHA256
to compute a certificate’s signature. Here’s how to compute
SHA256 hashes in Go.
author: 
Url: https://gobyexample.com/sha256-hashes
Created: "2025-01-29  02:47:48"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: SHA256 Hashes

source: https://gobyexample.com/sha256-hashes

> ## Excerpt
> SHA256 hashes are
frequently used to compute short identities for binary
or text blobs. For example, TLS/SSL certificates use SHA256
to compute a certificate’s signature. Here’s how to compute
SHA256 hashes in Go.

---
<table><tbody><tr><td><p><a href="https://en.wikipedia.org/wiki/SHA-2"><em>SHA256 hashes</em></a> are frequently used to compute short identities for binary or text blobs. For example, TLS/SSL certificates use SHA256 to compute a certificate’s signature. Here’s how to compute SHA256 hashes in Go.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/IHM1lZVm_Jm"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td><p>Go implements several hash functions in various <code>crypto/*</code> packages.</p></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"crypto/sha256"</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span>
</span></span><span><span>    <span>s</span> <span>:=</span> <span>"sha256 this string"</span></span></span></code></pre></td></tr><tr><td><p>Here we start with a new hash.</p></td><td><pre><code><span><span>    <span>h</span> <span>:=</span> <span>sha256</span><span>.</span><span>New</span><span>()</span></span></span></code></pre></td></tr><tr><td><p><code>Write</code> expects bytes. If you have a string <code>s</code>, use <code>[]byte(s)</code> to coerce it to bytes.</p></td><td><pre><code><span><span>    <span>h</span><span>.</span><span>Write</span><span>([]</span><span>byte</span><span>(</span><span>s</span><span>))</span></span></span></code></pre></td></tr><tr><td><p>This gets the finalized hash result as a byte slice. The argument to <code>Sum</code> can be used to append to an existing byte slice: it usually isn’t needed.</p></td><td><pre><code><span><span>    <span>bs</span> <span>:=</span> <span>h</span><span>.</span><span>Sum</span><span>(</span><span>nil</span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>s</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Printf</span><span>(</span><span>"%x\n"</span><span>,</span> <span>bs</span><span>)</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td><p>Running the program computes the hash and prints it in a human-readable hex format.</p></td><td><pre><code><span><span><span>$</span> go run sha256-hashes.go
</span></span><span><span><span>sha256 this string
</span></span></span><span><span><span>1af1dfa857bf1d8814fe1af8983c18080019922e557f15a8a...</span></span></span></code></pre></td></tr><tr><td><p>You can compute other hashes using a similar pattern to the one shown above. For example, to compute SHA512 hashes import <code>crypto/sha512</code> and use <code>sha512.New()</code>.</p></td><td></td></tr><tr><td><p>Note that if you need cryptographically secure hashes, you should carefully research <a href="https://en.wikipedia.org/wiki/Cryptographic_hash_function">hash strength</a>!</p></td><td></td></tr></tbody></table>

Next example: [Base64 Encoding](https://gobyexample.com/base64-encoding).
