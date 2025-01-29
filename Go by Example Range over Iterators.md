---
Description: Go by Example: Range over Iterators
Notes: Starting with version 1.23, Go has added support for
iterators,
which lets us range over pretty much anything!
author: 
Url: https://gobyexample.com/range-over-iterators
Created: "2025-01-29  02:44:32"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Range over Iterators

source: https://gobyexample.com/range-over-iterators

> ## Excerpt
> Starting with version 1.23, Go has added support for
iterators,
which lets us range over pretty much anything!

---
Starting with version 1.23, Go has added support for [iterators](https://go.dev/blog/range-functions), which lets us range over pretty much anything!

[![](https://gobyexample.com/play.png "Run code")](https://go.dev/play/p/JsdFcZac4E-)![](https://gobyexample.com/clipboard.png "Copy code")

```
<span><span><span>package</span> <span>main</span></span></span>
```

```
<span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"iter"</span>
</span></span><span><span>    <span>"slices"</span>
</span></span><span><span><span>)</span></span></span>
```

Let’s look at the `List` type from the [previous example](https://gobyexample.com/generics) again. In that example we had an `AllElements` method that returned a slice of all elements in the list. With Go iterators, we can do it better - as shown below.

```
<span><span><span>type</span> <span>List</span><span>[</span><span>T</span> <span>any</span><span>]</span> <span>struct</span> <span>{</span>
</span></span><span><span>    <span>head</span><span>,</span> <span>tail</span> <span>*</span><span>element</span><span>[</span><span>T</span><span>]</span>
</span></span><span><span><span>}</span></span></span>
```

```
<span><span><span>type</span> <span>element</span><span>[</span><span>T</span> <span>any</span><span>]</span> <span>struct</span> <span>{</span>
</span></span><span><span>    <span>next</span> <span>*</span><span>element</span><span>[</span><span>T</span><span>]</span>
</span></span><span><span>    <span>val</span>  <span>T</span>
</span></span><span><span><span>}</span></span></span>
```

```
<span><span><span>func</span> <span>(</span><span>lst</span> <span>*</span><span>List</span><span>[</span><span>T</span><span>])</span> <span>Push</span><span>(</span><span>v</span> <span>T</span><span>)</span> <span>{</span>
</span></span><span><span>    <span>if</span> <span>lst</span><span>.</span><span>tail</span> <span>==</span> <span>nil</span> <span>{</span>
</span></span><span><span>        <span>lst</span><span>.</span><span>head</span> <span>=</span> <span>&amp;</span><span>element</span><span>[</span><span>T</span><span>]{</span><span>val</span><span>:</span> <span>v</span><span>}</span>
</span></span><span><span>        <span>lst</span><span>.</span><span>tail</span> <span>=</span> <span>lst</span><span>.</span><span>head</span>
</span></span><span><span>    <span>}</span> <span>else</span> <span>{</span>
</span></span><span><span>        <span>lst</span><span>.</span><span>tail</span><span>.</span><span>next</span> <span>=</span> <span>&amp;</span><span>element</span><span>[</span><span>T</span><span>]{</span><span>val</span><span>:</span> <span>v</span><span>}</span>
</span></span><span><span>        <span>lst</span><span>.</span><span>tail</span> <span>=</span> <span>lst</span><span>.</span><span>tail</span><span>.</span><span>next</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span><span>}</span></span></span>
```

All returns an _iterator_, which in Go is a function with a [special signature](https://pkg.go.dev/iter#Seq).

```
<span><span><span>func</span> <span>(</span><span>lst</span> <span>*</span><span>List</span><span>[</span><span>T</span><span>])</span> <span>All</span><span>()</span> <span>iter</span><span>.</span><span>Seq</span><span>[</span><span>T</span><span>]</span> <span>{</span>
</span></span><span><span>    <span>return</span> <span>func</span><span>(</span><span>yield</span> <span>func</span><span>(</span><span>T</span><span>)</span> <span>bool</span><span>)</span> <span>{</span></span></span>
```

The iterator function takes another function as a parameter, called `yield` by convention (but the name can be arbitrary). It will call `yield` for every element we want to iterate over, and note `yield`’s return value for a potential early termination.

```
<span><span>        <span>for</span> <span>e</span> <span>:=</span> <span>lst</span><span>.</span><span>head</span><span>;</span> <span>e</span> <span>!=</span> <span>nil</span><span>;</span> <span>e</span> <span>=</span> <span>e</span><span>.</span><span>next</span> <span>{</span>
</span></span><span><span>            <span>if</span> <span>!</span><span>yield</span><span>(</span><span>e</span><span>.</span><span>val</span><span>)</span> <span>{</span>
</span></span><span><span>                <span>return</span>
</span></span><span><span>            <span>}</span>
</span></span><span><span>        <span>}</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span><span>}</span></span></span>
```

Iteration doesn’t require an underlying data structure, and doesn’t even have to be finite! Here’s a function returning an iterator over Fibonacci numbers: it keeps running as long as `yield` keeps returning `true`.

```
<span><span><span>func</span> <span>genFib</span><span>()</span> <span>iter</span><span>.</span><span>Seq</span><span>[</span><span>int</span><span>]</span> <span>{</span>
</span></span><span><span>    <span>return</span> <span>func</span><span>(</span><span>yield</span> <span>func</span><span>(</span><span>int</span><span>)</span> <span>bool</span><span>)</span> <span>{</span>
</span></span><span><span>        <span>a</span><span>,</span> <span>b</span> <span>:=</span> <span>1</span><span>,</span> <span>1</span></span></span>
```

```
<span><span>        <span>for</span> <span>{</span>
</span></span><span><span>            <span>if</span> <span>!</span><span>yield</span><span>(</span><span>a</span><span>)</span> <span>{</span>
</span></span><span><span>                <span>return</span>
</span></span><span><span>            <span>}</span>
</span></span><span><span>            <span>a</span><span>,</span> <span>b</span> <span>=</span> <span>b</span><span>,</span> <span>a</span><span>+</span><span>b</span>
</span></span><span><span>        <span>}</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span><span>}</span></span></span>
```

```
<span><span><span>func</span> <span>main</span><span>()</span> <span>{</span>
</span></span><span><span>    <span>lst</span> <span>:=</span> <span>List</span><span>[</span><span>int</span><span>]{}</span>
</span></span><span><span>    <span>lst</span><span>.</span><span>Push</span><span>(</span><span>10</span><span>)</span>
</span></span><span><span>    <span>lst</span><span>.</span><span>Push</span><span>(</span><span>13</span><span>)</span>
</span></span><span><span>    <span>lst</span><span>.</span><span>Push</span><span>(</span><span>23</span><span>)</span></span></span>
```

Since `List.All` returns an iterator, we can use it in a regular `range` loop.

```
<span><span>    <span>for</span> <span>e</span> <span>:=</span> <span>range</span> <span>lst</span><span>.</span><span>All</span><span>()</span> <span>{</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>e</span><span>)</span>
</span></span><span><span>    <span>}</span></span></span>
```

Packages like [slices](https://pkg.go.dev/slices) have a number of useful functions to work with iterators. For example, `Collect` takes any iterator and collects all its values into a slice.

```
<span><span>    <span>all</span> <span>:=</span> <span>slices</span><span>.</span><span>Collect</span><span>(</span><span>lst</span><span>.</span><span>All</span><span>())</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"all:"</span><span>,</span> <span>all</span><span>)</span></span></span>
```

```
<span><span>    <span>for</span> <span>n</span> <span>:=</span> <span>range</span> <span>genFib</span><span>()</span> <span>{</span></span></span>
```

Once the loop hits `break` or an early return, the `yield` function passed to the iterator will return `false`.

```
<span><span>        <span>if</span> <span>n</span> <span>&gt;=</span> <span>10</span> <span>{</span>
</span></span><span><span>            <span>break</span>
</span></span><span><span>        <span>}</span>
</span></span><span><span>        <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>n</span><span>)</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span><span>}</span></span></span>
```
