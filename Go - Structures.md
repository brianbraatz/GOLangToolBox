---
Description: Go - Structures
Notes: Go arrays allow you to define variables that can hold several data items of the same kind. Structure is another user-defined data type available in Go programming, which allows you to combine data items of different kinds.
author: 
Url: https://www.tutorialspoint.com/go/go_structures.htm
Created: "2025-01-29  02:37:02"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go - Structures

source: https://www.tutorialspoint.com/go/go_structures.htm

> ## Excerpt
> Go arrays allow you to define variables that can hold several data items of the same kind. Structure is another user-defined data type available in Go programming, which allows you to combine data items of different kinds.

---
___

___

Go arrays allow you to define variables that can hold several data items of the same kind. **Structure** is another user-defined data type available in Go programming, which allows you to combine data items of different kinds.

Structures are used to represent a record. Suppose you want to keep track of the books in a library. You might want to track the following attributes of each book −

-   Title
-   Author
-   Subject
-   Book ID

In such a scenario, structures are highly useful.

## Defining a Structure

To define a structure, you must use **type** and **struct** statements. The struct statement defines a new data type, with multiple members for your program. The type statement binds a name with the type which is struct in our case. The format of the struct statement is as follows −

```
<span>type struct_variable_type </span><span>struct</span><span> </span><span>{</span><span>
   member definition</span><span>;</span><span>
   member definition</span><span>;</span><span>
   </span><span>...</span><span>
   member definition</span><span>;</span><span>
</span><span>}</span>
```

Once a structure type is defined, it can be used to declare variables of that type using the following syntax.

```
variable_name := structure_variable_type {value1, value2...valuen}
```

## Accessing Structure Members

To access any member of a structure, we use the **member access operator (.).** The member access operator is coded as a period between the structure variable name and the structure member that we wish to access. You would use **struct** keyword to define variables of structure type. The following example explains how to use a structure −

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

type </span><span>Books</span><span> </span><span>struct</span><span> </span><span>{</span><span>
   title </span><span>string</span><span>
   author </span><span>string</span><span>
   subject </span><span>string</span><span>
   book_id </span><span>int</span><span>
</span><span>}</span><span>
func main</span><span>()</span><span> </span><span>{</span><span>
   </span><span>var</span><span> </span><span>Book1</span><span> </span><span>Books</span><span>    </span><span>/* Declare Book1 of type Book */</span><span>
   </span><span>var</span><span> </span><span>Book2</span><span> </span><span>Books</span><span>    </span><span>/* Declare Book2 of type Book */</span><span>
 
   </span><span>/* book 1 specification */</span><span>
   </span><span>Book1</span><span>.</span><span>title </span><span>=</span><span> </span><span>"Go Programming"</span><span>
   </span><span>Book1</span><span>.</span><span>author </span><span>=</span><span> </span><span>"Mahesh Kumar"</span><span>
   </span><span>Book1</span><span>.</span><span>subject </span><span>=</span><span> </span><span>"Go Programming Tutorial"</span><span>
   </span><span>Book1</span><span>.</span><span>book_id </span><span>=</span><span> </span><span>6495407</span><span>

   </span><span>/* book 2 specification */</span><span>
   </span><span>Book2</span><span>.</span><span>title </span><span>=</span><span> </span><span>"Telecom Billing"</span><span>
   </span><span>Book2</span><span>.</span><span>author </span><span>=</span><span> </span><span>"Zara Ali"</span><span>
   </span><span>Book2</span><span>.</span><span>subject </span><span>=</span><span> </span><span>"Telecom Billing Tutorial"</span><span>
   </span><span>Book2</span><span>.</span><span>book_id </span><span>=</span><span> </span><span>6495700</span><span>
 
   </span><span>/* print Book1 info */</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span> </span><span>"Book 1 title : %s\n"</span><span>,</span><span> </span><span>Book1</span><span>.</span><span>title</span><span>)</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span> </span><span>"Book 1 author : %s\n"</span><span>,</span><span> </span><span>Book1</span><span>.</span><span>author</span><span>)</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span> </span><span>"Book 1 subject : %s\n"</span><span>,</span><span> </span><span>Book1</span><span>.</span><span>subject</span><span>)</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span> </span><span>"Book 1 book_id : %d\n"</span><span>,</span><span> </span><span>Book1</span><span>.</span><span>book_id</span><span>)</span><span>

   </span><span>/* print Book2 info */</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span> </span><span>"Book 2 title : %s\n"</span><span>,</span><span> </span><span>Book2</span><span>.</span><span>title</span><span>)</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span> </span><span>"Book 2 author : %s\n"</span><span>,</span><span> </span><span>Book2</span><span>.</span><span>author</span><span>)</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span> </span><span>"Book 2 subject : %s\n"</span><span>,</span><span> </span><span>Book2</span><span>.</span><span>subject</span><span>)</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span> </span><span>"Book 2 book_id : %d\n"</span><span>,</span><span> </span><span>Book2</span><span>.</span><span>book_id</span><span>)</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
Book 1 title      : Go Programming
Book 1 author     : Mahesh Kumar
Book 1 subject    : Go Programming Tutorial
Book 1 book_id    : 6495407
Book 2 title      : Telecom Billing
Book 2 author     : Zara Ali
Book 2 subject    : Telecom Billing Tutorial
Book 2 book_id    : 6495700
```

[

Explore our **latest online courses** and learn new skills at your own pace. Enroll and become a certified expert to boost your career.

](https://www.tutorialspoint.com/latest/courses?utm_source=tutorialspoint&utm_medium=tutorials_3p&utm_campaign=internal)

## Structures as Function Arguments

You can pass a structure as a function argument in very similar way as you pass any other variable or pointer. You would access structure variables in the same way as you did in the above example −

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

type </span><span>Books</span><span> </span><span>struct</span><span> </span><span>{</span><span>
   title </span><span>string</span><span>
   author </span><span>string</span><span>
   subject </span><span>string</span><span>
   book_id </span><span>int</span><span>
</span><span>}</span><span>
func main</span><span>()</span><span> </span><span>{</span><span>
   </span><span>var</span><span> </span><span>Book1</span><span> </span><span>Books</span><span>    </span><span>/* Declare Book1 of type Book */</span><span>
   </span><span>var</span><span> </span><span>Book2</span><span> </span><span>Books</span><span>    </span><span>/* Declare Book2 of type Book */</span><span>
 
   </span><span>/* book 1 specification */</span><span>
   </span><span>Book1</span><span>.</span><span>title </span><span>=</span><span> </span><span>"Go Programming"</span><span>
   </span><span>Book1</span><span>.</span><span>author </span><span>=</span><span> </span><span>"Mahesh Kumar"</span><span>
   </span><span>Book1</span><span>.</span><span>subject </span><span>=</span><span> </span><span>"Go Programming Tutorial"</span><span>
   </span><span>Book1</span><span>.</span><span>book_id </span><span>=</span><span> </span><span>6495407</span><span>

   </span><span>/* book 2 specification */</span><span>
   </span><span>Book2</span><span>.</span><span>title </span><span>=</span><span> </span><span>"Telecom Billing"</span><span>
   </span><span>Book2</span><span>.</span><span>author </span><span>=</span><span> </span><span>"Zara Ali"</span><span>
   </span><span>Book2</span><span>.</span><span>subject </span><span>=</span><span> </span><span>"Telecom Billing Tutorial"</span><span>
   </span><span>Book2</span><span>.</span><span>book_id </span><span>=</span><span> </span><span>6495700</span><span>
 
   </span><span>/* print Book1 info */</span><span>
   printBook</span><span>(</span><span>Book1</span><span>)</span><span>

   </span><span>/* print Book2 info */</span><span>
   printBook</span><span>(</span><span>Book2</span><span>)</span><span>
</span><span>}</span><span>
func printBook</span><span>(</span><span> book </span><span>Books</span><span> </span><span>)</span><span> </span><span>{</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span> </span><span>"Book title : %s\n"</span><span>,</span><span> book</span><span>.</span><span>title</span><span>);</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span> </span><span>"Book author : %s\n"</span><span>,</span><span> book</span><span>.</span><span>author</span><span>);</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span> </span><span>"Book subject : %s\n"</span><span>,</span><span> book</span><span>.</span><span>subject</span><span>);</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span> </span><span>"Book book_id : %d\n"</span><span>,</span><span> book</span><span>.</span><span>book_id</span><span>);</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
Book title     : Go Programming
Book author    : Mahesh Kumar
Book subject   : Go Programming Tutorial
Book book_id   : 6495407
Book title     : Telecom Billing
Book author    : Zara Ali
Book subject   : Telecom Billing Tutorial
Book book_id   : 6495700
```

## Pointers to Structures

You can define pointers to structures in the same way as you define pointer to any other variable as follows −

```
var struct_pointer *Books
```

Now, you can store the address of a structure variable in the above defined pointer variable. To find the address of a structure variable, place the & operator before the structure's name as follows −

```
struct_pointer = &amp;Book1;
```

To access the members of a structure using a pointer to that structure, you must use the "." operator as follows −

```
struct_pointer.title;
```

Let us re-write the above example using structure pointer −

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

type </span><span>Books</span><span> </span><span>struct</span><span> </span><span>{</span><span>
   title </span><span>string</span><span>
   author </span><span>string</span><span>
   subject </span><span>string</span><span>
   book_id </span><span>int</span><span>
</span><span>}</span><span>
func main</span><span>()</span><span> </span><span>{</span><span>
   </span><span>var</span><span> </span><span>Book1</span><span> </span><span>Books</span><span>   </span><span>/* Declare Book1 of type Book */</span><span>
   </span><span>var</span><span> </span><span>Book2</span><span> </span><span>Books</span><span>   </span><span>/* Declare Book2 of type Book */</span><span>
 
   </span><span>/* book 1 specification */</span><span>
   </span><span>Book1</span><span>.</span><span>title </span><span>=</span><span> </span><span>"Go Programming"</span><span>
   </span><span>Book1</span><span>.</span><span>author </span><span>=</span><span> </span><span>"Mahesh Kumar"</span><span>
   </span><span>Book1</span><span>.</span><span>subject </span><span>=</span><span> </span><span>"Go Programming Tutorial"</span><span>
   </span><span>Book1</span><span>.</span><span>book_id </span><span>=</span><span> </span><span>6495407</span><span>

   </span><span>/* book 2 specification */</span><span>
   </span><span>Book2</span><span>.</span><span>title </span><span>=</span><span> </span><span>"Telecom Billing"</span><span>
   </span><span>Book2</span><span>.</span><span>author </span><span>=</span><span> </span><span>"Zara Ali"</span><span>
   </span><span>Book2</span><span>.</span><span>subject </span><span>=</span><span> </span><span>"Telecom Billing Tutorial"</span><span>
   </span><span>Book2</span><span>.</span><span>book_id </span><span>=</span><span> </span><span>6495700</span><span>
 
   </span><span>/* print Book1 info */</span><span>
   printBook</span><span>(&amp;</span><span>Book1</span><span>)</span><span>

   </span><span>/* print Book2 info */</span><span>
   printBook</span><span>(&amp;</span><span>Book2</span><span>)</span><span>
</span><span>}</span><span>
func printBook</span><span>(</span><span> book </span><span>*</span><span>Books</span><span> </span><span>)</span><span> </span><span>{</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span> </span><span>"Book title : %s\n"</span><span>,</span><span> book</span><span>.</span><span>title</span><span>);</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span> </span><span>"Book author : %s\n"</span><span>,</span><span> book</span><span>.</span><span>author</span><span>);</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span> </span><span>"Book subject : %s\n"</span><span>,</span><span> book</span><span>.</span><span>subject</span><span>);</span><span>
   fmt</span><span>.</span><span>Printf</span><span>(</span><span> </span><span>"Book book_id : %d\n"</span><span>,</span><span> book</span><span>.</span><span>book_id</span><span>);</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
Book title     : Go Programming
Book author    : Mahesh Kumar
Book subject   : Go Programming Tutorial
Book book_id   : 6495407
Book title     : Telecom Billing
Book author    : Zara Ali
Book subject   : Telecom Billing Tutorial
Book book_id   : 6495700
```
