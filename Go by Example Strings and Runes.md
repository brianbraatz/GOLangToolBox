---
Description: Go by Example: Strings and Runes
Notes: A Go string is a read-only slice of bytes. The language
and the standard library treat strings specially - as
containers of text encoded in UTF-8.
In other languages, strings are made of “characters”.
In Go, the concept of a character is called a rune - it’s
an integer that represents a Unicode code point.
This Go blog post is a good
introduction to the topic.
author: 
Url: https://gobyexample.com/strings-and-runes
Created: "2025-01-29  02:43:06"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Strings and Runes

source: https://gobyexample.com/strings-and-runes

> ## Excerpt
> A Go string is a read-only slice of bytes. The language
and the standard library treat strings specially - as
containers of text encoded in UTF-8.
In other languages, strings are made of “characters”.
In Go, the concept of a character is called a rune - it’s
an integer that represents a Unicode code point.
This Go blog post is a good
introduction to the topic.

---
<table><tbody><tr><td><p>A Go string is a read-only slice of bytes. The language and the standard library treat strings specially - as containers of text encoded in <a href="https://en.wikipedia.org/wiki/UTF-8">UTF-8</a>. In other languages, strings are made of “characters”. In Go, the concept of a character is called a <code>rune</code> - it’s an integer that represents a Unicode code point. <a href="https://go.dev/blog/strings">This Go blog post</a> is a good introduction to the topic.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/-iNDXZ9IM3s"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"unicode/utf8"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p><code>s</code> is a <code>string</code> assigned a literal value representing the word “hello” in the Thai language. Go string literals are UTF-8 encoded text.</p></td><td><pre><code><span><span>    <span>const</span> <span>s</span> <span>=</span> <span>"สวัสดี"</span></span></span></code></pre></td></tr><tr><td><p>Since strings are equivalent to <code>[]byte</code>, this will produce the length of the raw bytes stored within.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"Len:"</span><span>,</span> <span>len</span><span>(</span><span>s</span><span>))</span></span></span></code></pre></td></tr><tr><td><p>Indexing into a string produces the raw byte values at each index. This loop generates the hex values of all the bytes that constitute the code points in <code>s</code>.</p></td><td><pre><code><span><span>    <span>for</span> <span>i</span> <span>:=</span> <span>0</span><span>;</span> <span>i</span> <span>&lt;</span> <span>len</span><span>(</span><span>s</span><span>);</span> <span>i</span><span>++</span> <span>{</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Printf</span><span>(</span><span>"%x "</span><span>,</span> <span>s</span><span>[</span><span>i</span><span>])</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>()</span></span></span></code></pre></td></tr><tr><td><p>To count how many <em>runes</em> are in a string, we can use the <code>utf8</code> package. Note that the run-time of <code>RuneCountInString</code> depends on the size of the string, because it has to decode each UTF-8 rune sequentially. Some Thai characters are represented by UTF-8 code points that can span multiple bytes, so the result of this count may be surprising.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"Rune count:"</span><span>,</span> <span>utf8</span><span>.</span><span>RuneCountInString</span><span>(</span><span>s</span><span>))</span></span></span></code></pre></td></tr><tr><td><p>A <code>range</code> loop handles strings specially and decodes each <code>rune</code> along with its offset in the string.</p></td><td><pre><code><span><span>    <span>for</span> <span>idx</span><span>,</span> <span>runeValue</span> <span>:=</span> <span>range</span> <span>s</span> <span>{</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Printf</span><span>(</span><span>"%#U starts at %d\n"</span><span>,</span> <span>runeValue</span><span>,</span> <span>idx</span><span>)</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td><p>We can achieve the same iteration by using the <code>utf8.DecodeRuneInString</code> function explicitly.</p></td><td><pre><code><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"\nUsing DecodeRuneInString"</span><span>)</span>
</span></span><span><span>    <span>for</span> <span>i</span><span>,</span> <span>w</span> <span>:=</span> <span>0</span><span>,</span> <span>0</span><span>;</span> <span>i</span> <span>&lt;</span> <span>len</span><span>(</span><span>s</span><span>);</span> <span>i</span> <span>+=</span> <span>w</span> <span>{</span>
</span></span><span><span>        <span>runeValue</span><span>,</span> <span>width</span> <span>:=</span> <span>utf8</span><span>.</span><span>DecodeRuneInString</span><span>(</span><span>s</span><span>[</span><span>i</span><span>:])</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Printf</span><span>(</span><span>"%#U starts at %d\n"</span><span>,</span> <span>runeValue</span><span>,</span> <span>i</span><span>)</span>
</span></span><span><span>        <span>w</span> <span>=</span> <span>width</span></span></span></code></pre></td></tr><tr><td><p>This demonstrates passing a <code>rune</code> value to a function.</p></td><td><pre><code><span><span>        <span>examineRune</span><span>(</span><span>runeValue</span><span>)</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>examineRune</span><span>(</span><span>r</span> <span>rune</span><span>)</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>Values enclosed in single quotes are <em>rune literals</em>. We can compare a <code>rune</code> value to a rune literal directly.</p></td><td><pre><code><span><span>    <span>if</span> <span>r</span> <span>==</span> <span>'t'</span> <span>{</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"found tee"</span><span>)</span>
</span></span><span><span>    <span>}</span> <span>else</span> <span>if</span> <span>r</span> <span>==</span> <span>'ส'</span> <span>{</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"found so sua"</span><span>)</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go run strings-and-runes.go
</span></span><span><span><span>Len: 18
</span></span></span><span><span><span>e0 b8 aa e0 b8 a7 e0 b8 b1 e0 b8 aa e0 b8 94 e0 b8 b5 
</span></span></span><span><span><span>Rune count: 6
</span></span></span><span><span><span>U+0E2A 'ส' starts at 0
</span></span></span><span><span><span>U+0E27 'ว' starts at 3
</span></span></span><span><span><span>U+0E31 'ั' starts at 6
</span></span></span><span><span><span>U+0E2A 'ส' starts at 9
</span></span></span><span><span><span>U+0E14 'ด' starts at 12
</span></span></span><span><span><span>U+0E35 'ี' starts at 15</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>Using DecodeRuneInString
</span></span></span><span><span><span>U+0E2A 'ส' starts at 0
</span></span></span><span><span><span>found so sua
</span></span></span><span><span><span>U+0E27 'ว' starts at 3
</span></span></span><span><span><span>U+0E31 'ั' starts at 6
</span></span></span><span><span><span>U+0E2A 'ส' starts at 9
</span></span></span><span><span><span>found so sua
</span></span></span><span><span><span>U+0E14 'ด' starts at 12
</span></span></span><span><span><span>U+0E35 'ี' starts at 15</span></span></span></code></pre></td></tr></tbody></table>

Next example: [Structs](https://gobyexample.com/structs).
