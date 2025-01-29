---
Description: Go by Example: JSON
Notes: Go offers built-in support for JSON encoding and
decoding, including to and from built-in and custom
data types.
author: 
Url: https://gobyexample.com/json
Created: "2025-01-29  02:47:24"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: JSON

source: https://gobyexample.com/json

> ## Excerpt
> Go offers built-in support for JSON encoding and
decoding, including to and from built-in and custom
data types.

---
Go offers built-in support for JSON encoding and decoding, including to and from built-in and custom data types.

[![](https://gobyexample.com/play.png "Run code")](https://go.dev/play/p/zwf9dZ4pUPW)![](https://gobyexample.com/clipboard.png "Copy code")

```
<span><span><span>package</span> <span>main</span></span></span>
```

```
<span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"encoding/json"</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"os"</span>
</span></span><span><span>    <span>"strings"</span>
</span></span><span><span><span>)</span></span></span>
```

We’ll use these two structs to demonstrate encoding and decoding of custom types below.

```
<span><span><span>type</span> <span>response1</span> <span>struct</span> <span>{</span>
</span></span><span><span>    <span>Page</span>   <span>int</span>
</span></span><span><span>    <span>Fruits</span> <span>[]</span><span>string</span>
</span></span><span><span><span>}</span></span></span>
```

Only exported fields will be encoded/decoded in JSON. Fields must start with capital letters to be exported.

```
<span><span><span>type</span> <span>response2</span> <span>struct</span> <span>{</span>
</span></span><span><span>    <span>Page</span>   <span>int</span>      <span>`json:"page"`</span>
</span></span><span><span>    <span>Fruits</span> <span>[]</span><span>string</span> <span>`json:"fruits"`</span>
</span></span><span><span><span>}</span></span></span>
```

```
<span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span>
```

First we’ll look at encoding basic data types to JSON strings. Here are some examples for atomic values.

```
<span><span>    <span>bolB</span><span>,</span> <span>_</span> <span>:=</span> <span>json</span><span>.</span><span>Marshal</span><span>(</span><span>true</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>string</span><span>(</span><span>bolB</span><span>))</span></span></span>
```

```
<span><span>    <span>intB</span><span>,</span> <span>_</span> <span>:=</span> <span>json</span><span>.</span><span>Marshal</span><span>(</span><span>1</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>string</span><span>(</span><span>intB</span><span>))</span></span></span>
```

```
<span><span>    <span>fltB</span><span>,</span> <span>_</span> <span>:=</span> <span>json</span><span>.</span><span>Marshal</span><span>(</span><span>2.34</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>string</span><span>(</span><span>fltB</span><span>))</span></span></span>
```

```
<span><span>    <span>strB</span><span>,</span> <span>_</span> <span>:=</span> <span>json</span><span>.</span><span>Marshal</span><span>(</span><span>"gopher"</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>string</span><span>(</span><span>strB</span><span>))</span></span></span>
```

And here are some for slices and maps, which encode to JSON arrays and objects as you’d expect.

```
<span><span>    <span>slcD</span> <span>:=</span> <span>[]</span><span>string</span><span>{</span><span>"apple"</span><span>,</span> <span>"peach"</span><span>,</span> <span>"pear"</span><span>}</span>
</span></span><span><span>    <span>slcB</span><span>,</span> <span>_</span> <span>:=</span> <span>json</span><span>.</span><span>Marshal</span><span>(</span><span>slcD</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>string</span><span>(</span><span>slcB</span><span>))</span></span></span>
```

```
<span><span>    <span>mapD</span> <span>:=</span> <span>map</span><span>[</span><span>string</span><span>]</span><span>int</span><span>{</span><span>"apple"</span><span>:</span> <span>5</span><span>,</span> <span>"lettuce"</span><span>:</span> <span>7</span><span>}</span>
</span></span><span><span>    <span>mapB</span><span>,</span> <span>_</span> <span>:=</span> <span>json</span><span>.</span><span>Marshal</span><span>(</span><span>mapD</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>string</span><span>(</span><span>mapB</span><span>))</span></span></span>
```

The JSON package can automatically encode your custom data types. It will only include exported fields in the encoded output and will by default use those names as the JSON keys.

```
<span><span>    <span>res1D</span> <span>:=</span> <span>&amp;</span><span>response1</span><span>{</span>
</span></span><span><span>        <span>Page</span><span>:</span>   <span>1</span><span>,</span>
</span></span><span><span>        <span>Fruits</span><span>:</span> <span>[]</span><span>string</span><span>{</span><span>"apple"</span><span>,</span> <span>"peach"</span><span>,</span> <span>"pear"</span><span>}}</span>
</span></span><span><span>    <span>res1B</span><span>,</span> <span>_</span> <span>:=</span> <span>json</span><span>.</span><span>Marshal</span><span>(</span><span>res1D</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>string</span><span>(</span><span>res1B</span><span>))</span></span></span>
```

You can use tags on struct field declarations to customize the encoded JSON key names. Check the definition of `response2` above to see an example of such tags.

```
<span><span>    <span>res2D</span> <span>:=</span> <span>&amp;</span><span>response2</span><span>{</span>
</span></span><span><span>        <span>Page</span><span>:</span>   <span>1</span><span>,</span>
</span></span><span><span>        <span>Fruits</span><span>:</span> <span>[]</span><span>string</span><span>{</span><span>"apple"</span><span>,</span> <span>"peach"</span><span>,</span> <span>"pear"</span><span>}}</span>
</span></span><span><span>    <span>res2B</span><span>,</span> <span>_</span> <span>:=</span> <span>json</span><span>.</span><span>Marshal</span><span>(</span><span>res2D</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>string</span><span>(</span><span>res2B</span><span>))</span></span></span>
```

Now let’s look at decoding JSON data into Go values. Here’s an example for a generic data structure.

```
<span><span>    <span>byt</span> <span>:=</span> <span>[]</span><span>byte</span><span>(</span><span>`{"num":6.13,"strs":["a","b"]}`</span><span>)</span></span></span>
```

We need to provide a variable where the JSON package can put the decoded data. This `map[string]interface{}` will hold a map of strings to arbitrary data types.

```
<span><span>    <span>var</span> <span>dat</span> <span>map</span><span>[</span><span>string</span><span>]</span><span>interface</span><span>{}</span></span></span>
```

Here’s the actual decoding, and a check for associated errors.

```
<span><span>    <span>if</span> <span>err</span> <span>:=</span> <span>json</span><span>.</span><span>Unmarshal</span><span>(</span><span>byt</span><span>,</span> <span>&amp;</span><span>dat</span><span>);</span> <span>err</span> <span>!=</span> <span>nil</span> <span>{</span>
</span></span><span><span>        <span>panic</span><span>(</span><span>err</span><span>)</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>dat</span><span>)</span></span></span>
```

In order to use the values in the decoded map, we’ll need to convert them to their appropriate type. For example here we convert the value in `num` to the expected `float64` type.

```
<span><span>    <span>num</span> <span>:=</span> <span>dat</span><span>[</span><span>"num"</span><span>].(</span><span>float64</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>num</span><span>)</span></span></span>
```

Accessing nested data requires a series of conversions.

```
<span><span>    <span>strs</span> <span>:=</span> <span>dat</span><span>[</span><span>"strs"</span><span>].([]</span><span>interface</span><span>{})</span>
</span></span><span><span>    <span>str1</span> <span>:=</span> <span>strs</span><span>[</span><span>0</span><span>].(</span><span>string</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>str1</span><span>)</span></span></span>
```

We can also decode JSON into custom data types. This has the advantages of adding additional type-safety to our programs and eliminating the need for type assertions when accessing the decoded data.

```
<span><span>    <span>str</span> <span>:=</span> <span>`{"page": 1, "fruits": ["apple", "peach"]}`</span>
</span></span><span><span>    <span>res</span> <span>:=</span> <span>response2</span><span>{}</span>
</span></span><span><span>    <span>json</span><span>.</span><span>Unmarshal</span><span>([]</span><span>byte</span><span>(</span><span>str</span><span>),</span> <span>&amp;</span><span>res</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>res</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>res</span><span>.</span><span>Fruits</span><span>[</span><span>0</span><span>])</span></span></span>
```

In the examples above we always used bytes and strings as intermediates between the data and JSON representation on standard out. We can also stream JSON encodings directly to `os.Writer`s like `os.Stdout` or even HTTP response bodies.

```
<span><span>    <span>enc</span> <span>:=</span> <span>json</span><span>.</span><span>NewEncoder</span><span>(</span><span>os</span><span>.</span><span>Stdout</span><span>)</span>
</span></span><span><span>    <span>d</span> <span>:=</span> <span>map</span><span>[</span><span>string</span><span>]</span><span>int</span><span>{</span><span>"apple"</span><span>:</span> <span>5</span><span>,</span> <span>"lettuce"</span><span>:</span> <span>7</span><span>}</span>
</span></span><span><span>    <span>enc</span><span>.</span><span>Encode</span><span>(</span><span>d</span><span>)</span></span></span>
```

Streaming reads from `os.Reader`s like `os.Stdin` or HTTP request bodies is done with `json.Decoder`.

```
<span><span>    <span>dec</span> <span>:=</span> <span>json</span><span>.</span><span>NewDecoder</span><span>(</span><span>strings</span><span>.</span><span>NewReader</span><span>(</span><span>str</span><span>))</span>
</span></span><span><span>    <span>res1</span> <span>:=</span> <span>response2</span><span>{}</span>
</span></span><span><span>    <span>dec</span><span>.</span><span>Decode</span><span>(</span><span>&amp;</span><span>res1</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>res1</span><span>)</span>
</span></span><span><span><span>}</span></span></span>
```
