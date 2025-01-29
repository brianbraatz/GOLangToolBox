---
Description: Go - Basic Syntax
Notes: We discussed the basic structure of a Go program in the previous chapter. Now it will be easy to understand the other basic building blocks of the Go programming language.
author: 
Url: https://www.tutorialspoint.com/go/go_basic_syntax.htm
Created: "2025-01-29  02:32:16"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go - Basic Syntax

source: https://www.tutorialspoint.com/go/go_basic_syntax.htm

> ## Excerpt
> We discussed the basic structure of a Go program in the previous chapter. Now it will be easy to understand the other basic building blocks of the Go programming language.

---
___

___

We discussed the basic structure of a Go program in the previous chapter. Now it will be easy to understand the other basic building blocks of the Go programming language.

## Tokens in Go

A Go program consists of various tokens. A token is either a keyword, an identifier, a constant, a string literal, or a symbol. For example, the following Go statement consists of six tokens −

```go
fmt.Println("Hello, World!")
```

```go
fmt
.
Println
(
   "Hello, World!"
)
```

In a Go program, the line separator key is a statement terminator. That is, individual statements don't need a special separator like “;” in C. The Go compiler internally places “;” as the statement terminator to indicate the end of one logical entity.

For example, take a look at the following statements −

```go
fmt.Println("Hello, World!")
fmt.Println("I am in Go Programming World!")
```

## Comments

Comments are like helping texts in your Go program and they are ignored by the compiler. They start with /\* and terminates with the characters \*/ as shown below −

You cannot have comments within comments and they do not occur within a string or character literals.

## Identifiers

A Go identifier is a name used to identify a variable, function, or any other user-defined item. An identifier starts with a letter A to Z or a to z or an underscore \_ followed by zero or more letters, underscores, and digits (0 to 9).

identifier = letter { letter | unicode\_digit }.

Go does not allow punctuation characters such as @, $, and % within identifiers. Go is a **case-sensitive** programming language. Thus, _Manpower_ and _manpower_ are two different identifiers in Go. Here are some examples of acceptable identifiers −

```
mahesh      kumar   abc   move_name   a_123
myname50   _temp    j      a23b9      retVal
```

## Keywords

The following list shows the reserved words in Go. These reserved words may not be used as constant or variable or any other identifier names.

<table><tbody><tr><td>break</td><td>default</td><td>func</td><td>interface</td><td>select</td></tr><tr><td>case</td><td>defer</td><td>Go</td><td>map</td><td>Struct</td></tr><tr><td>chan</td><td>else</td><td>Goto</td><td>package</td><td>Switch</td></tr><tr><td>const</td><td>fallthrough</td><td>if</td><td>range</td><td>Type</td></tr><tr><td>continue</td><td>for</td><td>import</td><td>return</td><td>Var</td></tr></tbody></table>

## Whitespace in Go

Whitespace is the term used in Go to describe blanks, tabs, newline characters, and comments. A line containing only whitespace, possibly with a comment, is known as a blank line, and a Go compiler totally ignores it.

Whitespaces separate one part of a statement from another and enables the compiler to identify where one element in a statement, such as int, ends and the next element begins. Therefore, in the following statement −

```go
var age int;
```

```go
fruit = apples + oranges;   
```

## Variable Definition

A [variable definition](https://www.tutorialspoint.com/go/go_variables.htm) tells the compiler where and how much storage to create for the variable. Here is the syntax:

```go
var variable_list optional_data_type;
```

An [if statement](https://www.tutorialspoint.com/go/go_if_statement.htm) consists of a boolean expression followed by one or more statements.

```go
if(boolean_expression) {
   
}
```

The syntax of an [if...else statement](https://www.tutorialspoint.com/go/go_if_else_statement.htm) in Go programming language is:

```go
if(boolean_expression) {
   
} else {
   
}
```

The syntax for a [nested if statement](https://www.tutorialspoint.com/go/go_nested_if_statements.htm) is as follows:

```go
if( boolean_expression 1) {
   
   if(boolean_expression 2) {
      
   }
}
```

The syntax for expression [switch statement](https://www.tutorialspoint.com/go/go_switch_statement.htm) in Go programming language is as follows:

```go
switch(boolean-expression or integral type){
   case boolean-expression or integral type :
      statement(s);      
   case boolean-expression or integral type :
      statement(s); 
   
   
   default : 
      statement(s);
}
```

The syntax for a [select statement](https://www.tutorialspoint.com/go/go_select_statement.htm) in Go programming language is as follows:

```go
select {
   case communication clause  :
      statement(s);      
   case communication clause  :
      statement(s); 
   
   default : 
      statement(s);
}
```

A [for loop](https://www.tutorialspoint.com/go/go_for_loop.htm) is a repetition control structure. It allows you to write a loop that needs to execute a specific number of times.

The syntax of for loop in Go programming language is:

```go
for [condition |  ( init; condition; increment ) | Range] {
   statement(s);
}
```

The [nested for loops](https://www.tutorialspoint.com/go/go_nested_loops.htm) allows to use one loop inside another loop. The following section shows a few examples to illustrate the concept:

## The break, continue, and goto statements

These control statements change an execution from its normal sequence.

### break

The syntax for a [break statement](https://www.tutorialspoint.com/go/go_break_statement.htm) in Go is as follows:

```go
break;
```

The syntax for a [continue statement](https://www.tutorialspoint.com/go/go_continue_statement.htm) in Go is as follows:

```go
continue;
```

The syntax for a [goto statement](https://www.tutorialspoint.com/go/go_goto_statement.htm) in Go is as follows:

```go
goto label;
..
.
label: statement;
```
