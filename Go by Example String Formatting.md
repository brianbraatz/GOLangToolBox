---
Description: Go by Example: String Formatting
Notes: Go offers excellent support for string formatting in
the printf tradition. Here are some examples of
common string formatting tasks.
author: 
Url: https://gobyexample.com/string-formatting
Created: "2025-01-29  02:47:13"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: String Formatting

source: https://gobyexample.com/string-formatting

> ## Excerpt
> Go offers excellent support for string formatting in
the printf tradition. Here are some examples of
common string formatting tasks.

---
Go offers excellent support for string formatting in the `printf` tradition. Here are some examples of common string formatting tasks.

[![](https://gobyexample.com/play.png "Run code")](https://go.dev/play/p/EZCZX1Uwp6D)![](https://gobyexample.com/clipboard.png "Copy code")

```
<span><span><span>package</span> <span>main</span></span></span>
```

```
<span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"os"</span>
</span></span><span><span><span>)</span></span></span>
```

```
<span><span><span>type</span> <span>point</span> <span>struct</span> <span>{</span>
</span></span><span><span>    <span>x</span><span>,</span> <span>y</span> <span>int</span>
</span></span><span><span><span>}</span></span></span>
```

```
<span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span>
```

Go offers several printing “verbs” designed to format general Go values. For example, this prints an instance of our `point` struct.

```
<span><span>    <span>p</span> <span>:=</span> <span>point</span><span>{</span><span>1</span><span>,</span> <span>2</span><span>}</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Printf</span><span>(</span><span>"struct1: %v\n"</span><span>,</span> <span>p</span><span>)</span></span></span>
```

If the value is a struct, the `%+v` variant will include the struct’s field names.

```
<span><span>    <span>fmt</span><span>.</span><span>Printf</span><span>(</span><span>"struct2: %+v\n"</span><span>,</span> <span>p</span><span>)</span></span></span>
```

The `%#v` variant prints a Go syntax representation of the value, i.e. the source code snippet that would produce that value.

```
<span><span>    <span>fmt</span><span>.</span><span>Printf</span><span>(</span><span>"struct3: %#v\n"</span><span>,</span> <span>p</span><span>)</span></span></span>
```

To print the type of a value, use `%T`.

```
<span><span>    <span>fmt</span><span>.</span><span>Printf</span><span>(</span><span>"type: %T\n"</span><span>,</span> <span>p</span><span>)</span></span></span>
```

Formatting booleans is straight-forward.

```
<span><span>    <span>fmt</span><span>.</span><span>Printf</span><span>(</span><span>"bool: %t\n"</span><span>,</span> <span>true</span><span>)</span></span></span>
```

There are many options for formatting integers. Use `%d` for standard, base-10 formatting.

```
<span><span>    <span>fmt</span><span>.</span><span>Printf</span><span>(</span><span>"int: %d\n"</span><span>,</span> <span>123</span><span>)</span></span></span>
```

This prints a binary representation.

```
<span><span>    <span>fmt</span><span>.</span><span>Printf</span><span>(</span><span>"bin: %b\n"</span><span>,</span> <span>14</span><span>)</span></span></span>
```

This prints the character corresponding to the given integer.

```
<span><span>    <span>fmt</span><span>.</span><span>Printf</span><span>(</span><span>"char: %c\n"</span><span>,</span> <span>33</span><span>)</span></span></span>
```

`%x` provides hex encoding.

```
<span><span>    <span>fmt</span><span>.</span><span>Printf</span><span>(</span><span>"hex: %x\n"</span><span>,</span> <span>456</span><span>)</span></span></span>
```

There are also several formatting options for floats. For basic decimal formatting use `%f`.

```
<span><span>    <span>fmt</span><span>.</span><span>Printf</span><span>(</span><span>"float1: %f\n"</span><span>,</span> <span>78.9</span><span>)</span></span></span>
```

`%e` and `%E` format the float in (slightly different versions of) scientific notation.

```
<span><span>    <span>fmt</span><span>.</span><span>Printf</span><span>(</span><span>"float2: %e\n"</span><span>,</span> <span>123400000.0</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Printf</span><span>(</span><span>"float3: %E\n"</span><span>,</span> <span>123400000.0</span><span>)</span></span></span>
```

For basic string printing use `%s`.

```
<span><span>    <span>fmt</span><span>.</span><span>Printf</span><span>(</span><span>"str1: %s\n"</span><span>,</span> <span>"\"string\""</span><span>)</span></span></span>
```

To double-quote strings as in Go source, use `%q`.

```
<span><span>    <span>fmt</span><span>.</span><span>Printf</span><span>(</span><span>"str2: %q\n"</span><span>,</span> <span>"\"string\""</span><span>)</span></span></span>
```

As with integers seen earlier, `%x` renders the string in base-16, with two output characters per byte of input.

```
<span><span>    <span>fmt</span><span>.</span><span>Printf</span><span>(</span><span>"str3: %x\n"</span><span>,</span> <span>"hex this"</span><span>)</span></span></span>
```

To print a representation of a pointer, use `%p`.

```
<span><span>    <span>fmt</span><span>.</span><span>Printf</span><span>(</span><span>"pointer: %p\n"</span><span>,</span> <span>&amp;</span><span>p</span><span>)</span></span></span>
```

When formatting numbers you will often want to control the width and precision of the resulting figure. To specify the width of an integer, use a number after the `%` in the verb. By default the result will be right-justified and padded with spaces.

```
<span><span>    <span>fmt</span><span>.</span><span>Printf</span><span>(</span><span>"width1: |%6d|%6d|\n"</span><span>,</span> <span>12</span><span>,</span> <span>345</span><span>)</span></span></span>
```

You can also specify the width of printed floats, though usually you’ll also want to restrict the decimal precision at the same time with the width.precision syntax.

```
<span><span>    <span>fmt</span><span>.</span><span>Printf</span><span>(</span><span>"width2: |%6.2f|%6.2f|\n"</span><span>,</span> <span>1.2</span><span>,</span> <span>3.45</span><span>)</span></span></span>
```

To left-justify, use the `-` flag.

```
<span><span>    <span>fmt</span><span>.</span><span>Printf</span><span>(</span><span>"width3: |%-6.2f|%-6.2f|\n"</span><span>,</span> <span>1.2</span><span>,</span> <span>3.45</span><span>)</span></span></span>
```

You may also want to control width when formatting strings, especially to ensure that they align in table-like output. For basic right-justified width.

```
<span><span>    <span>fmt</span><span>.</span><span>Printf</span><span>(</span><span>"width4: |%6s|%6s|\n"</span><span>,</span> <span>"foo"</span><span>,</span> <span>"b"</span><span>)</span></span></span>
```

To left-justify use the `-` flag as with numbers.

```
<span><span>    <span>fmt</span><span>.</span><span>Printf</span><span>(</span><span>"width5: |%-6s|%-6s|\n"</span><span>,</span> <span>"foo"</span><span>,</span> <span>"b"</span><span>)</span></span></span>
```

So far we’ve seen `Printf`, which prints the formatted string to `os.Stdout`. `Sprintf` formats and returns a string without printing it anywhere.

```
<span><span>    <span>s</span> <span>:=</span> <span>fmt</span><span>.</span><span>Sprintf</span><span>(</span><span>"sprintf: a %s"</span><span>,</span> <span>"string"</span><span>)</span>
</span></span><span><span>    <span>fmt</span><span>.</span><span>Println</span><span>(</span><span>s</span><span>)</span></span></span>
```

You can format+print to `io.Writers` other than `os.Stdout` using `Fprintf`.

```
<span><span>    <span>fmt</span><span>.</span><span>Fprintf</span><span>(</span><span>os</span><span>.</span><span>Stderr</span><span>,</span> <span>"io: an %s\n"</span><span>,</span> <span>"error"</span><span>)</span>
</span></span><span><span><span>}</span></span></span>
```
