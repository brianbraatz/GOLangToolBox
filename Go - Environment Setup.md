---
Description: Go - Environment Setup
Notes: Go - Environment Setup - If you are still willing to set up your environment for Go programming language, you need the following two software available on your computer ?
author: 
Url: https://www.tutorialspoint.com/go/go_environment.htm
Created: "2025-01-29  02:32:03"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go - Environment Setup

source: https://www.tutorialspoint.com/go/go_environment.htm

> ## Excerpt
> Go - Environment Setup - If you are still willing to set up your environment for Go programming language, you need the following two software available on your computer ?

---
___

___

## Local Environment Setup

If you are still willing to set up your environment for Go programming language, you need the following two software available on your computer −

-   A text editor
-   Go compiler

## Text Editor

You will require a text editor to type your programs. Examples of text editors include Windows Notepad, OS Edit command, Brief, Epsilon, EMACS, and vim or vi.

The name and version of text editors can vary on different operating systems. For example, Notepad is used on Windows, and vim or vi is used on Windows as well as Linux or UNIX.

The files you create with the text editor are called **source files**. They contain program source code. The source files for Go programs are typically named with the extension **".go"**.

Before starting your programming, make sure you have a text editor in place and you have enough experience to write a computer program, save it in a file, compile it, and finally execute it.

[

Explore our **latest online courses** and learn new skills at your own pace. Enroll and become a certified expert to boost your career.

](https://www.tutorialspoint.com/latest/courses?utm_source=tutorialspoint&utm_medium=tutorials_3p&utm_campaign=internal)

## The Go Compiler

The source code written in source file is the human readable source for your program. It needs to be compiled and turned into machine language so that your CPU can actually execute the program as per the instructions given. The Go programming language compiler compiles the source code into its final executable program.

Go distribution comes as a binary installable for FreeBSD (release 8 and above), Linux, Mac OS X (Snow Leopard and above), and Windows operating systems with 32-bit (386) and 64-bit (amd64) x86 processor architectures.

The following section explains how to install Go binary distribution on various OS.

## Download Go Archive

Download the latest version of Go installable archive file from [Go Downloads](https://golang.org/dl/). The following version is used in this tutorial: _go1.4.windows-amd64.msi_.

It is copied it into C:\\>go folder.

| OS | Archive name |
| --- | --- |
| Windows | go1.4.windows-amd64.msi |
| Linux | go1.4.linux-amd64.tar.gz |
| Mac | go1.4.darwin-amd64-osx10.8.pkg |
| FreeBSD | go1.4.freebsd-amd64.tar.gz |

## Installation on UNIX/Linux/Mac OS X, and FreeBSD

Extract the download archive into the folder /usr/local, creating a Go tree in /usr/local/go. For example −

tar -C /usr/local -xzf go1.4.linux-amd64.tar.gz

Add /usr/local/go/bin to the PATH environment variable.

| OS | Output |
| --- | --- |
| Linux | export PATH = $PATH:/usr/local/go/bin |
| Mac | export PATH = $PATH:/usr/local/go/bin |
| FreeBSD | export PATH = $PATH:/usr/local/go/bin |

## Installation on Windows

Use the MSI file and follow the prompts to install the Go tools. By default, the installer uses the Go distribution in c:\\Go. The installer should set the c:\\Go\\bin directory in Window's PATH environment variable. Restart any open command prompts for the change to take effect.

## Verifying the Installation

Create a go file named test.go in **C:\\>Go\_WorkSpace**.

### File: test.go

```go
package main

import "fmt"

func main() {
   fmt.Println("Hello, World!")
}
```

Now run test.go to see the result −

```
C:\Go_WorkSpace&gt;go run test.go
```

### Output

```
Hello, World!
```
