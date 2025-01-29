---
Description: Go by Example: Testing and Benchmarking
Notes: Unit testing is an important part of writing
principled Go programs. The testing package
provides the tools we need to write unit tests
and the go test command runs tests.
author: 
Url: https://gobyexample.com/testing-and-benchmarking
Created: "2025-01-29  02:48:14"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go by Example: Testing and Benchmarking

source: https://gobyexample.com/testing-and-benchmarking

> ## Excerpt
> Unit testing is an important part of writing
principled Go programs. The testing package
provides the tools we need to write unit tests
and the go test command runs tests.

---
<table><tbody><tr><td><p>Unit testing is an important part of writing principled Go programs. The <code>testing</code> package provides the tools we need to write unit tests and the <code>go test</code> command runs tests.</p></td><td></td></tr><tr><td><p>For the sake of demonstration, this code is in package <code>main</code>, but it could be any package. Testing code typically lives in the same package as the code it tests.</p></td><td><a href="https://go.dev/play/p/PlzU16wwEWE"><img title="Run code" src="https://gobyexample.com/play.png"></a><img title="Copy code" src="https://gobyexample.com/clipboard.png"><pre><code><span><span><span>package</span> <span>main</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span><span>import</span> <span>(</span>
</span></span><span><span>    <span>"fmt"</span>
</span></span><span><span>    <span>"testing"</span>
</span></span><span><span><span>)</span></span></span></code></pre></td></tr><tr><td><p>We’ll be testing this simple implementation of an integer minimum. Typically, the code we’re testing would be in a source file named something like <code>intutils.go</code>, and the test file for it would then be named <code>intutils_test.go</code>.</p></td><td><pre><code><span><span><span>func</span> <span>IntMin</span><span>(</span><span>a</span><span>,</span> <span>b</span> <span>int</span><span>)</span> <span>int</span> <span>{</span>
</span></span><span><span>    <span>if</span> <span>a</span> <span>&lt;</span> <span>b</span> <span>{</span>
</span></span><span><span>        <span>return</span> <span>a</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span>    <span>return</span> <span>b</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td><p>A test is created by writing a function with a name beginning with <code>Test</code>.</p></td><td><pre><code><span><span><span>func</span> <span>TestIntMinBasic</span><span>(</span><span>t</span> <span>*</span><span>testing</span><span>.</span><span>T</span><span>)</span> <span>{</span>
</span></span><span><span>    <span>ans</span> <span>:=</span> <span>IntMin</span><span>(</span><span>2</span><span>,</span> <span>-</span><span>2</span><span>)</span>
</span></span><span><span>    <span>if</span> <span>ans</span> <span>!=</span> <span>-</span><span>2</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p><code>t.Error*</code> will report test failures but continue executing the test. <code>t.Fatal*</code> will report test failures and stop the test immediately.</p></td><td><pre><code><span><span>        <span>t</span><span>.</span><span>Errorf</span><span>(</span><span>"IntMin(2, -2) = %d; want -2"</span><span>,</span> <span>ans</span><span>)</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td><p>Writing tests can be repetitive, so it’s idiomatic to use a <em>table-driven style</em>, where test inputs and expected outputs are listed in a table and a single loop walks over them and performs the test logic.</p></td><td><pre><code><span><span><span>func</span> <span>TestIntMinTableDriven</span><span>(</span><span>t</span> <span>*</span><span>testing</span><span>.</span><span>T</span><span>)</span> <span>{</span>
</span></span><span><span>    <span>var</span> <span>tests</span> <span>=</span> <span>[]</span><span>struct</span> <span>{</span>
</span></span><span><span>        <span>a</span><span>,</span> <span>b</span> <span>int</span>
</span></span><span><span>        <span>want</span> <span>int</span>
</span></span><span><span>    <span>}{</span>
</span></span><span><span>        <span>{</span><span>0</span><span>,</span> <span>1</span><span>,</span> <span>0</span><span>},</span>
</span></span><span><span>        <span>{</span><span>1</span><span>,</span> <span>0</span><span>,</span> <span>0</span><span>},</span>
</span></span><span><span>        <span>{</span><span>2</span><span>,</span> <span>-</span><span>2</span><span>,</span> <span>-</span><span>2</span><span>},</span>
</span></span><span><span>        <span>{</span><span>0</span><span>,</span> <span>-</span><span>1</span><span>,</span> <span>-</span><span>1</span><span>},</span>
</span></span><span><span>        <span>{</span><span>-</span><span>1</span><span>,</span> <span>0</span><span>,</span> <span>-</span><span>1</span><span>},</span>
</span></span><span><span>    <span>}</span></span></span></code></pre></td></tr><tr><td><p>t.Run enables running “subtests”, one for each table entry. These are shown separately when executing <code>go test -v</code>.</p></td><td><pre><code><span><span>    <span>for</span> <span>_</span><span>,</span> <span>tt</span> <span>:=</span> <span>range</span> <span>tests</span> <span>{</span></span></span></code></pre></td></tr><tr><td></td><td><pre><code><span><span>        <span>testname</span> <span>:=</span> <span>fmt</span><span>.</span><span>Sprintf</span><span>(</span><span>"%d,%d"</span><span>,</span> <span>tt</span><span>.</span><span>a</span><span>,</span> <span>tt</span><span>.</span><span>b</span><span>)</span>
</span></span><span><span>        <span>t</span><span>.</span><span>Run</span><span>(</span><span>testname</span><span>,</span> <span>func</span><span>(</span><span>t</span> <span>*</span><span>testing</span><span>.</span><span>T</span><span>)</span> <span>{</span>
</span></span><span><span>            <span>ans</span> <span>:=</span> <span>IntMin</span><span>(</span><span>tt</span><span>.</span><span>a</span><span>,</span> <span>tt</span><span>.</span><span>b</span><span>)</span>
</span></span><span><span>            <span>if</span> <span>ans</span> <span>!=</span> <span>tt</span><span>.</span><span>want</span> <span>{</span>
</span></span><span><span>                <span>t</span><span>.</span><span>Errorf</span><span>(</span><span>"got %d, want %d"</span><span>,</span> <span>ans</span><span>,</span> <span>tt</span><span>.</span><span>want</span><span>)</span>
</span></span><span><span>            <span>}</span>
</span></span><span><span>        <span>})</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr><tr><td><p>Benchmark tests typically go in <code>_test.go</code> files and are named beginning with <code>Benchmark</code>. The <code>testing</code> runner executes each benchmark function several times, increasing <code>b.N</code> on each run until it collects a precise measurement.</p></td><td><pre><code><span><span><span>func</span> <span>BenchmarkIntMin</span><span>(</span><span>b</span> <span>*</span><span>testing</span><span>.</span><span>B</span><span>)</span> <span>{</span></span></span></code></pre></td></tr><tr><td><p>Typically the benchmark runs a function we’re benchmarking in a loop <code>b.N</code> times.</p></td><td><pre><code><span><span>    <span>for</span> <span>i</span> <span>:=</span> <span>0</span><span>;</span> <span>i</span> <span>&lt;</span> <span>b</span><span>.</span><span>N</span><span>;</span> <span>i</span><span>++</span> <span>{</span>
</span></span><span><span>        <span>IntMin</span><span>(</span><span>1</span><span>,</span> <span>2</span><span>)</span>
</span></span><span><span>    <span>}</span>
</span></span><span><span><span>}</span></span></span></code></pre></td></tr></tbody></table>

<table><tbody><tr><td><p>Run all tests in the current project in verbose mode.</p></td><td><pre><code><span><span><span>$</span> go test -v
</span></span><span><span><span>== RUN   TestIntMinBasic
</span></span></span><span><span><span>--- PASS: TestIntMinBasic (0.00s)
</span></span></span><span><span><span>=== RUN   TestIntMinTableDriven
</span></span></span><span><span><span>=== RUN   TestIntMinTableDriven/0,1
</span></span></span><span><span><span>=== RUN   TestIntMinTableDriven/1,0
</span></span></span><span><span><span>=== RUN   TestIntMinTableDriven/2,-2
</span></span></span><span><span><span>=== RUN   TestIntMinTableDriven/0,-1
</span></span></span><span><span><span>=== RUN   TestIntMinTableDriven/-1,0
</span></span></span><span><span><span>--- PASS: TestIntMinTableDriven (0.00s)
</span></span></span><span><span><span>    --- PASS: TestIntMinTableDriven/0,1 (0.00s)
</span></span></span><span><span><span>    --- PASS: TestIntMinTableDriven/1,0 (0.00s)
</span></span></span><span><span><span>    --- PASS: TestIntMinTableDriven/2,-2 (0.00s)
</span></span></span><span><span><span>    --- PASS: TestIntMinTableDriven/0,-1 (0.00s)
</span></span></span><span><span><span>    --- PASS: TestIntMinTableDriven/-1,0 (0.00s)
</span></span></span><span><span><span>PASS
</span></span></span><span><span><span>ok      examples/testing-and-benchmarking    0.023s</span></span></span></code></pre></td></tr><tr><td><p>Run all benchmarks in the current project. All tests are run prior to benchmarks. The <code>bench</code> flag filters benchmark function names with a regexp.</p></td><td><pre><code><span><span><span>$</span> go test -bench=.
</span></span><span><span><span>goos: darwin
</span></span></span><span><span><span>goarch: arm64
</span></span></span><span><span><span>pkg: examples/testing
</span></span></span><span><span><span>BenchmarkIntMin-8 1000000000 0.3136 ns/op
</span></span></span><span><span><span>PASS
</span></span></span><span><span><span>ok      examples/testing-and-benchmarking    0.351s</span></span></span></code></pre></td></tr></tbody></table>

Next example: [Command-Line Arguments](https://gobyexample.com/command-line-arguments).
