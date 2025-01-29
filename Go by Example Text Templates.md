---
Description: Go by Example: Text Templates
Notes: Go offers built-in support for creating dynamic content or showing customized
output to the user with the text/template package. A sibling package
named html/template provides the same API but has additional security
features and should be used for generating HTML.
author: 
Url: https://gobyexample.com/text-templates
Created: "2025-01-29  02:47:16"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Text Templates

source: https://gobyexample.com/text-templates

> ## Excerpt
> Go offers built-in support for creating dynamic content or showing customized
output to the user with the text/template package. A sibling package
named html/template provides the same API but has additional security
features and should be used for generating HTML.

---
<table><tbody><tr><td><p>Go offers built-in support for creating dynamic content or showing customized output to the user with the <code>text/template</code> package. A sibling package named <code>html/template</code> provides the same API but has additional security features and should be used for generating HTML.</p></td><td></td></tr><tr><td></td><td><a href="https://go.dev/play/p/pDwkw1iMACF"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"os"</span>
</span></span><span><span>    <span>"text/template"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>func</span> <span>main</span><span>()</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>We can create a new template and parse its body from a string. Templates are a mix of static text and “actions” enclosed in <code>{{...}}</code> that are used to dynamically insert content.</p></td><td><pre><code><span><span>    <span>t1</span> <span>:=</span> <span>template</span><span>.</span><span>New</span><span>(</span><span>"t1"</span><span>)</span>
</span></span><span><span>    <span>t1</span><span>,</span> <span>err</span> <span>:=</span> <span>t1</span><span>.</span><span>Parse</span><span>(</span><span>"Value is {{.}}\n"</span><span>)</span>
</span></span><span><span>    <span>if</span> <span>err</span> <span>!=</span> <span>nil</span> <span>{</span>
</span></span><span><span>        <span>panic</span><span>(</span><span>err</span><span>)</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td><p>Alternatively, we can use the <code>template.Must</code> function to panic in case <code>Parse</code> returns an error. This is especially useful for templates initialized in the global scope.</p></td><td><pre><code><span><span>    <span>t1</span> <span>=</span> <span>template</span><span>.</span><span>Must</span><span>(</span><span>t1</span><span>.</span><span>Parse</span><span>(</span><span>"Value: {{.}}\n"</span><span>))</span></span></span></code></pre></td></tr><tr><td><p>By “executing” the template we generate its text with specific values for its actions. The <code>{{.}}</code> action is replaced by the value passed as a parameter to <code>Execute</code>.</p></td><td><pre><code><span><span>    <span>t1</span><span>.</span><span>Execute</span><span>(</span><span>os</span><span>.</span><span>Stdout</span><span>,</span> <span>"some text"</span><span>)</span>
</span></span><span><span>    <span>t1</span><span>.</span><span>Execute</span><span>(</span><span>os</span><span>.</span><span>Stdout</span><span>,</span> <span>5</span><span>)</span>
</span></span><span><span>    <span>t1</span><span>.</span><span>Execute</span><span>(</span><span>os</span><span>.</span><span>Stdout</span><span>,</span> <span>[]</span><span>string</span><span>{</span>
</span></span><span><span>        <span>"Go"</span><span>,</span>
</span></span><span><span>        <span>"Rust"</span><span>,</span>
</span></span><span><span>        <span>"C++"</span><span>,</span>
</span></span><span><span>        <span>"C#"</span><span>,</span>
</span></span><span><span>    <span>})</span></span></span></code></pre></td></tr><tr><td><p>Helper function we’ll use below.</p></td><td><pre><code><span><span>    <span>Create</span> <span>:=</span> <span>func</span><span>(</span><span>name</span><span>,</span> <span>t</span> <span>string</span><span>)</span> <span>*</span><span>template</span><span>.</span><span>Template</span> <span>{</span>
</span></span><span><span>        <span>return</span> <span>template</span><span>.</span><span>Must</span><span>(</span><span>template</span><span>.</span><span>New</span><span>(</span><span>name</span><span>).</span><span>Parse</span><span>(</span><span>t</span><span>))</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td><p>If the data is a struct we can use the <code>{{.FieldName}}</code> action to access its fields. The fields should be exported to be accessible when a template is executing.</p></td><td><pre><code><span><span>    <span>t2</span> <span>:=</span> <span>Create</span><span>(</span><span>"t2"</span><span>,</span> <span>"Name: {{.Name}}\n"</span><span>)</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span>    <span>t2</span><span>.</span><span>Execute</span><span>(</span><span>os</span><span>.</span><span>Stdout</span><span>,</span> <span>struct</span> <span>{</span>
</span></span><span><span>        <span>Name</span> <span>string</span>
</span></span><span><span>    <span>}{</span><span>"Jane Doe"</span><span>})</span></span></span></code></pre></td></tr><tr><td><p>The same applies to maps; with maps there is no restriction on the case of key names.</p></td><td><pre><code><span><span>    <span>t2</span><span>.</span><span>Execute</span><span>(</span><span>os</span><span>.</span><span>Stdout</span><span>,</span> <span>map</span><span>[</span><span>string</span><span>]</span><span>string</span><span>{</span>
</span></span><span><span>        <span>"Name"</span><span>:</span> <span>"Mickey Mouse"</span><span>,</span>
</span></span><span><span>    <span>})</span></span></span></code></pre></td></tr><tr><td><p>if/else provide conditional execution for templates. A value is considered false if it’s the default value of a type, such as 0, an empty string, nil pointer, etc. This sample demonstrates another feature of templates: using <code>-</code> in actions to trim whitespace.</p></td><td><pre><code><span><span>    <span>t3</span> <span>:=</span> <span>Create</span><span>(</span><span>"t3"</span><span>,</span>
</span></span><span><span>        <span>"{{if . -}} yes {{else -}} no {{end}}\n"</span><span>)</span>
</span></span><span><span>    <span>t3</span><span>.</span><span>Execute</span><span>(</span><span>os</span><span>.</span><span>Stdout</span><span>,</span> <span>"not empty"</span><span>)</span>
</span></span><span><span>    <span>t3</span><span>.</span><span>Execute</span><span>(</span><span>os</span><span>.</span><span>Stdout</span><span>,</span> <span>""</span><span>)</span></span></span></code></pre></td></tr><tr><td><p>range blocks let us loop through slices, arrays, maps or channels. Inside the range block <code>{{.}}</code> is set to the current item of the iteration.</p></td><td><pre><code><span><span>    <span>t4</span> <span>:=</span> <span>Create</span><span>(</span><span>"t4"</span><span>,</span>
</span></span><span><span>        <span>"Range: {{range .}}{{.}} {{end}}\n"</span><span>)</span>
</span></span><span><span>    <span>t4</span><span>.</span><span>Execute</span><span>(</span><span>os</span><span>.</span><span>Stdout</span><span>,</span>
</span></span><span><span>        <span>[]</span><span>string</span><span>{</span>
</span></span><span><span>            <span>"Go"</span><span>,</span>
</span></span><span><span>            <span>"Rust"</span><span>,</span>
</span></span><span><span>            <span>"C++"</span><span>,</span>
</span></span><span><span>            <span>"C#"</span><span>,</span>
</span></span><span><span>        <span>})</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td></td><td><pre><code><span><span><span>$</span> go run templates.go 
</span></span><span><span><span>Value: some text
</span></span></span><span><span><span>Value: 5
</span></span></span><span><span><span>Value: [Go Rust C++ C#]
</span></span></span><span><span><span>Name: Jane Doe
</span></span></span><span><span><span>Name: Mickey Mouse
</span></span></span><span><span><span>yes 
</span></span></span><span><span><span>no 
</span></span></span><span><span><span>Range: Go Rust C++ C# </span></span></span></code></pre></td></tr></tbody></table>

Next example: [Regular Expressions](https://gobyexample.com/regular-expressions).
