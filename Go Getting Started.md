---
Description: Go Getting Started
Notes: W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.
author: 
Url: https://www.w3schools.com/go/go_getting_started.php
Created: "2025-01-29  02:24:59"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go Getting Started

source: https://www.w3schools.com/go/go_getting_started.php

> ## Excerpt
> W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.

---
## Go Getting Started

___

## Go Get Started

To start using Go, you need two things:

-   A text editor, like VS Code, to write Go code
-   A compiler, like GCC, to translate the Go code into a language that the computer will understand

There are many text editors and compilers to choose from. In this tutorial, we will use an IDE (see below).

___

## Go Install

You can find the relevant installation files at [https://golang.org/dl/](https://golang.org/dl/).

Follow the instructions related to your operating system. To check if Go was installed successfully, you can run the following command in a terminal window:

go version

Which should show the version of your Go installation.

___

## Go Install IDE

An IDE (Integrated Development Environment) is used to edit AND compile the code.

Popular IDE's include Visual Studio Code (VS Code), Vim, Eclipse, and Notepad. These are all free, and they can be used to both edit and debug Go code.

**Note:** Web-based IDE's can work as well, but functionality is limited.

We will use **VS Code** in our tutorial, which we believe is a good place to start.

You can find the latest version of VS Code at [https://code.visualstudio.com/](https://code.visualstudio.com/).

___

## Go Quickstart

Let's create our first Go program.

-   Launch the VS Code editor
-   Open the extension manager or alternatively, press `Ctrl + Shift + x`
-   In the search box, type "go" and hit enter
-   Find the Go extension by the GO team at Google and install the extension
-   After the installation is complete, open the command palette by pressing `Ctrl + Shift + p`
-   Run the `Go: Install/Update Tools` command
-   Select all the provided tools and click OK

VS Code is now configured to use Go.

Open up a terminal window and type:

go mod init example.com/hello

Do not worry if you do not understand why we type the above command. Just think of it as something that you always do, and that you will learn more about in a later chapter.

Create a new file (`File > New File`). Copy and paste the following code and save the file as `helloworld.go` (`File > Save As`):

#### helloworld.go

package main  
import ("fmt")  
  
func main() {  
  fmt.Println("Hello World!")  
}  

Now, run the code: Open a terminal in VS Code and type:

go run .\\helloworld.go

**Congratulations**! You have now written and executed your first Go program.

If you want to save the program as an executable, type and run:

go build .\\helloworld.go

___

## Learning Go At W3Schools

When learning Go at W3Schools.com, you can use our "Try it Yourself" tool. It shows both the code and the result. This will make it easier for you to understand every part as we move forward:

### helloworld.go

Code:

package main  
import ("fmt")  
  
func main() {  
 fmt.Println("Hello World!")  
}

Result:

`Hello World!`

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_helloworld)

  

Track your progress - it's free!

   [![Get Certified](https://www.w3schools.com/images/img_fa_up_300.png)](https://campus.w3schools.com/products/w3schools-full-access-course)
