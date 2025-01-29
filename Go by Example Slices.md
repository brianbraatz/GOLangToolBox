---
Description: Go by Example: Slices
Notes: Slices are an important data type in Go, giving
a more powerful interface to sequences than arrays.
author: 
Url: https://gobyexample.com/slices
Created: "2025-01-29  02:42:21"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Slices

source: https://gobyexample.com/slices

> ## Excerpt
> Slices are an important data type in Go, giving
a more powerful interface to sequences than arrays.

---
_Slices_ are an important data type in Go, giving a more powerful interface to sequences than arrays.

[![](https://gobyexample.com/play.png "Run code")](https://go.dev/play/p/kiy1StxorBF)![](https://gobyexample.com/clipboard.png "Copy code")

```
<span><span><span>package</span> <span>main</span></span></span>
```

```
<span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"slices"</span>
</span></span><span><span><span>)</span></span></span>
```

```
<span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span>
```

Unlike arrays, slices are typed only by the elements they contain (not the number of elements). An uninitialized slice equals to nil and has length 0.

```
<span><span>    <span>var</span> <span>s</span> <span>[]</span><span>string</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"uninit:"</span><span>,</span> <span>s</span><span>,</span> <span>s</span> <span>==</span> <span>nil</span><span>,</span> <span>len</span><span>(</span><span>s</span><span>)</span> <span>==</span> <span>0</span><span>)</span></span></span>
```

To create an empty slice with non-zero length, use the builtin `make`. Here we make a slice of `string`s of length `3` (initially zero-valued). By default a new slice’s capacity is equal to its length; if we know the slice is going to grow ahead of time, it’s possible to pass a capacity explicitly as an additional parameter to `make`.

```
<span><span>    <span>s</span> <span>=</span> <span>make</span><span>([]</span><span>string</span><span>,</span> <span>3</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"emp:"</span><span>,</span> <span>s</span><span>,</span> <span>"len:"</span><span>,</span> <span>len</span><span>(</span><span>s</span><span>),</span> <span>"cap:"</span><span>,</span> <span>cap</span><span>(</span><span>s</span><span>))</span></span></span>
```

We can set and get just like with arrays.

```
<span><span>    <span>s</span><span>[</span><span>0</span><span>]</span> <span>=</span> <span>"a"</span>
</span></span><span><span>    <span>s</span><span>[</span><span>1</span><span>]</span> <span>=</span> <span>"b"</span>
</span></span><span><span>    <span>s</span><span>[</span><span>2</span><span>]</span> <span>=</span> <span>"c"</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"set:"</span><span>,</span> <span>s</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"get:"</span><span>,</span> <span>s</span><span>[</span><span>2</span><span>])</span></span></span>
```

`len` returns the length of the slice as expected.

```
<span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"len:"</span><span>,</span> <span>len</span><span>(</span><span>s</span><span>))</span></span></span>
```

In addition to these basic operations, slices support several more that make them richer than arrays. One is the builtin `append`, which returns a slice containing one or more new values. Note that we need to accept a return value from `append` as we may get a new slice value.

```
<span><span>    <span>s</span> <span>=</span> <span>append</span><span>(</span><span>s</span><span>,</span> <span>"d"</span><span>)</span>
</span></span><span><span>    <span>s</span> <span>=</span> <span>append</span><span>(</span><span>s</span><span>,</span> <span>"e"</span><span>,</span> <span>"f"</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"apd:"</span><span>,</span> <span>s</span><span>)</span></span></span>
```

Slices can also be `copy`’d. Here we create an empty slice `c` of the same length as `s` and copy into `c` from `s`.

```
<span><span>    <span>c</span> <span>:=</span> <span>make</span><span>([]</span><span>string</span><span>,</span> <span>len</span><span>(</span><span>s</span><span>))</span>
</span></span><span><span>    <span>copy</span><span>(</span><span>c</span><span>,</span> <span>s</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"cpy:"</span><span>,</span> <span>c</span><span>)</span></span></span>
```

Slices support a “slice” operator with the syntax `slice[low:high]`. For example, this gets a slice of the elements `s[2]`, `s[3]`, and `s[4]`.

```
<span><span>    <span>l</span> <span>:=</span> <span>s</span><span>[</span><span>2</span><span>:</span><span>5</span><span>]</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"sl1:"</span><span>,</span> <span>l</span><span>)</span></span></span>
```

This slices up to (but excluding) `s[5]`.

```
<span><span>    <span>l</span> <span>=</span> <span>s</span><span>[:</span><span>5</span><span>]</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"sl2:"</span><span>,</span> <span>l</span><span>)</span></span></span>
```

And this slices up from (and including) `s[2]`.

```
<span><span>    <span>l</span> <span>=</span> <span>s</span><span>[</span><span>2</span><span>:]</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"sl3:"</span><span>,</span> <span>l</span><span>)</span></span></span>
```

We can declare and initialize a variable for slice in a single line as well.

```
<span><span>    <span>t</span> <span>:=</span> <span>[]</span><span>string</span><span>{</span><span>"g"</span><span>,</span> <span>"h"</span><span>,</span> <span>"i"</span><span>}</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"dcl:"</span><span>,</span> <span>t</span><span>)</span></span></span>
```

The `slices` package contains a number of useful utility functions for slices.

```
<span><span>    <span>t2</span> <span>:=</span> <span>[]</span><span>string</span><span>{</span><span>"g"</span><span>,</span> <span>"h"</span><span>,</span> <span>"i"</span><span>}</span>
</span></span><span><span>    <span>if</span> <span>slices</span><span>.</span><span>Equal</span><span>(</span><span>t</span><span>,</span> <span>t2</span><span>)</span> <span>{</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"t == t2"</span><span>)</span>
</span></span><span><span>    <span>}</span></span></span>
```

Slices can be composed into multi-dimensional data structures. The length of the inner slices can vary, unlike with multi-dimensional arrays.

```
<span><span>    <span>twoD</span> <span>:=</span> <span>make</span><span>([][]</span><span>int</span><span>,</span> <span>3</span><span>)</span>
</span></span><span><span>    <span>for</span> <span>i</span> <span>:=</span> <span>0</span><span>;</span> <span>i</span> <span>&lt;</span> <span>3</span><span>;</span> <span>i</span><span>++</span> <span>{</span>
</span></span><span><span>        <span>innerLen</span> <span>:=</span> <span>i</span> <span>+</span> <span>1</span>
</span></span><span><span>        <span>twoD</span><span>[</span><span>i</span><span>]</span> <span>=</span> <span>make</span><span>([]</span><span>int</span><span>,</span> <span>innerLen</span><span>)</span>
</span></span><span><span>        <span>for</span> <span>j</span> <span>:=</span> <span>0</span><span>;</span> <span>j</span> <span>&lt;</span> <span>innerLen</span><span>;</span> <span>j</span><span>++</span> <span>{</span>
</span></span><span><span>            <span>twoD</span><span>[</span><span>i</span><span>][</span><span>j</span><span>]</span> <span>=</span> <span>i</span> <span>+</span> <span>j</span>
</span></span><span><span>        <span>}</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"2d: "</span><span>,</span> <span>twoD</span><span>)</span>
</span></span><span><span><span>}</span></span></span>
```
