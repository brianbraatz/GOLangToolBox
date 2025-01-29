---
Description: Go by Example: Regular Expressions
Notes: Go offers built-in support for regular expressions.
Here are some examples of  common regexp-related tasks
in Go.
author: 
Url: https://gobyexample.com/regular-expressions
Created: "2025-01-29  02:47:19"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Regular Expressions

source: https://gobyexample.com/regular-expressions

> ## Excerpt
> Go offers built-in support for regular expressions.
Here are some examples of  common regexp-related tasks
in Go.

---
Go offers built-in support for [regular expressions](https://en.wikipedia.org/wiki/Regular_expression). Here are some examples of common regexp-related tasks in Go.

[![](https://gobyexample.com/play.png "Run code")](https://go.dev/play/p/fI2YIfYsCaL)![](https://gobyexample.com/clipboard.png "Copy code")

```
<span><span><span>package</span> <span>main</span></span></span>
```

```
<span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"bytes"</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"regexp"</span>
</span></span><span><span><span>)</span></span></span>
```

```
<span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span>
```

This tests whether a pattern matches a string.

```
<span><span>    <span>match</span><span>,</span> <span>_</span> <span>:=</span> <span>regexp</span><span>.</span><span>MatchString</span><span>(</span><span>"p([a-z]+)ch"</span><span>,</span> <span>"peach"</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>match</span><span>)</span></span></span>
```

Above we used a string pattern directly, but for other regexp tasks you’ll need to `Compile` an optimized `Regexp` struct.

```
<span><span>    <span>r</span><span>,</span> <span>_</span> <span>:=</span> <span>regexp</span><span>.</span><span>Compile</span><span>(</span><span>"p([a-z]+)ch"</span><span>)</span></span></span>
```

Many methods are available on these structs. Here’s a match test like we saw earlier.

```
<span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>r</span><span>.</span><span>MatchString</span><span>(</span><span>"peach"</span><span>))</span></span></span>
```

This finds the match for the regexp.

```
<span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>r</span><span>.</span><span>FindString</span><span>(</span><span>"peach punch"</span><span>))</span></span></span>
```

This also finds the first match but returns the start and end indexes for the match instead of the matching text.

```
<span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"idx:"</span><span>,</span> <span>r</span><span>.</span><span>FindStringIndex</span><span>(</span><span>"peach punch"</span><span>))</span></span></span>
```

The `Submatch` variants include information about both the whole-pattern matches and the submatches within those matches. For example this will return information for both `p([a-z]+)ch` and `([a-z]+)`.

```
<span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>r</span><span>.</span><span>FindStringSubmatch</span><span>(</span><span>"peach punch"</span><span>))</span></span></span>
```

Similarly this will return information about the indexes of matches and submatches.

```
<span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>r</span><span>.</span><span>FindStringSubmatchIndex</span><span>(</span><span>"peach punch"</span><span>))</span></span></span>
```

The `All` variants of these functions apply to all matches in the input, not just the first. For example to find all matches for a regexp.

```
<span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>r</span><span>.</span><span>FindAllString</span><span>(</span><span>"peach punch pinch"</span><span>,</span> <span>-</span><span>1</span><span>))</span></span></span>
```

These `All` variants are available for the other functions we saw above as well.

```
<span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"all:"</span><span>,</span> <span>r</span><span>.</span><span>FindAllStringSubmatchIndex</span><span>(</span>
</span></span><span><span>        <span>"peach punch pinch"</span><span>,</span> <span>-</span><span>1</span><span>))</span></span></span>
```

Providing a non-negative integer as the second argument to these functions will limit the number of matches.

```
<span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>r</span><span>.</span><span>FindAllString</span><span>(</span><span>"peach punch pinch"</span><span>,</span> <span>2</span><span>))</span></span></span>
```

Our examples above had string arguments and used names like `MatchString`. We can also provide `[]byte` arguments and drop `String` from the function name.

```
<span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>r</span><span>.</span><span>Match</span><span>([]</span><span>byte</span><span>(</span><span>"peach"</span><span>)))</span></span></span>
```

When creating global variables with regular expressions you can use the `MustCompile` variation of `Compile`. `MustCompile` panics instead of returning an error, which makes it safer to use for global variables.

```
<span><span>    <span>r</span> <span>=</span> <span>regexp</span><span>.</span><span>MustCompile</span><span>(</span><span>"p([a-z]+)ch"</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>"regexp:"</span><span>,</span> <span>r</span><span>)</span></span></span>
```

The `regexp` package can also be used to replace subsets of strings with other values.

```
<span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>r</span><span>.</span><span>ReplaceAllString</span><span>(</span><span>"a peach"</span><span>,</span> <span>"&lt;fruit&gt;"</span><span>))</span></span></span>
```

The `Func` variant allows you to transform matched text with a given function.

```
<span><span>    <span>in</span> <span>:=</span> <span>[]</span><span>byte</span><span>(</span><span>"a peach"</span><span>)</span>
</span></span><span><span>    <span>out</span> <span>:=</span> <span>r</span><span>.</span><span>ReplaceAllFunc</span><span>(</span><span>in</span><span>,</span> <span>bytes</span><span>.</span><span>ToUpper</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>string</span><span>(</span><span>out</span><span>))</span>
</span></span><span><span><span>}</span></span></span>
```
