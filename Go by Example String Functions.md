---
Description: Go by Example: String Functions
Notes: Here’s a sample of the functions available in
strings. Since these are functions from the
package, not methods on the string object itself,
we need pass the string in question as the first
argument to the function. You can find more
functions in the strings
package docs.
author: 
Url: https://gobyexample.com/string-functions
Created: "2025-01-29  02:47:09"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: String Functions

source: https://gobyexample.com/string-functions

> ## Excerpt
> Here’s a sample of the functions available in
strings. Since these are functions from the
package, not methods on the string object itself,
we need pass the string in question as the first
argument to the function. You can find more
functions in the strings
package docs.

---
Here’s a sample of the functions available in `strings`. Since these are functions from the package, not methods on the string object itself, we need pass the string in question as the first argument to the function. You can find more functions in the [`strings`](https://pkg.go.dev/strings) package docs.

```
<span><span>    <span>p</span><span>(</span><span>"Contains:  "</span><span>,</span> <span>s</span><span>.</span><span>Contains</span><span>(</span><span>"test"</span><span>,</span> <span>"es"</span><span>))</span>
</span></span><span><span>    <span>p</span><span>(</span><span>"Count:     "</span><span>,</span> <span>s</span><span>.</span><span>Count</span><span>(</span><span>"test"</span><span>,</span> <span>"t"</span><span>))</span>
</span></span><span><span>    <span>p</span><span>(</span><span>"HasPrefix: "</span><span>,</span> <span>s</span><span>.</span><span>HasPrefix</span><span>(</span><span>"test"</span><span>,</span> <span>"te"</span><span>))</span>
</span></span><span><span>    <span>p</span><span>(</span><span>"HasSuffix: "</span><span>,</span> <span>s</span><span>.</span><span>HasSuffix</span><span>(</span><span>"test"</span><span>,</span> <span>"st"</span><span>))</span>
</span></span><span><span>    <span>p</span><span>(</span><span>"Index:     "</span><span>,</span> <span>s</span><span>.</span><span>Index</span><span>(</span><span>"test"</span><span>,</span> <span>"e"</span><span>))</span>
</span></span><span><span>    <span>p</span><span>(</span><span>"Join:      "</span><span>,</span> <span>s</span><span>.</span><span>Join</span><span>([]</span><span>string</span><span>{</span><span>"a"</span><span>,</span> <span>"b"</span><span>},</span> <span>"-"</span><span>))</span>
</span></span><span><span>    <span>p</span><span>(</span><span>"Repeat:    "</span><span>,</span> <span>s</span><span>.</span><span>Repeat</span><span>(</span><span>"a"</span><span>,</span> <span>5</span><span>))</span>
</span></span><span><span>    <span>p</span><span>(</span><span>"Replace:   "</span><span>,</span> <span>s</span><span>.</span><span>Replace</span><span>(</span><span>"foo"</span><span>,</span> <span>"o"</span><span>,</span> <span>"0"</span><span>,</span> <span>-</span><span>1</span><span>))</span>
</span></span><span><span>    <span>p</span><span>(</span><span>"Replace:   "</span><span>,</span> <span>s</span><span>.</span><span>Replace</span><span>(</span><span>"foo"</span><span>,</span> <span>"o"</span><span>,</span> <span>"0"</span><span>,</span> <span>1</span><span>))</span>
</span></span><span><span>    <span>p</span><span>(</span><span>"Split:     "</span><span>,</span> <span>s</span><span>.</span><span>Split</span><span>(</span><span>"a-b-c-d-e"</span><span>,</span> <span>"-"</span><span>))</span>
</span></span><span><span>    <span>p</span><span>(</span><span>"ToLower:   "</span><span>,</span> <span>s</span><span>.</span><span>ToLower</span><span>(</span><span>"TEST"</span><span>))</span>
</span></span><span><span>    <span>p</span><span>(</span><span>"ToUpper:   "</span><span>,</span> <span>s</span><span>.</span><span>ToUpper</span><span>(</span><span>"test"</span><span>))</span>
</span></span><span><span><span>}</span></span></span>
```
