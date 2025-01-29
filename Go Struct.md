---
Description: Go Struct
Notes: W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.
author: 
Url: https://www.w3schools.com/go/go_struct.php
Created: "2025-01-29  02:30:29"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go Struct

source: https://www.w3schools.com/go/go_struct.php

> ## Excerpt
> W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.

---
## Go Struct

___

## Go Structures

A struct (short for structure) is used to create a collection of members of different data types, into a single variable.

While arrays are used to store multiple values of the same data type into a single variable, structs are used to store multiple values of different data types into a single variable.

A struct can be useful for grouping data together to create records.

___

## Declare a Struct

To declare a structure in Go, use the `type` and `struct` keywords:

### Syntax

type _struct\_name_ struct {  
  _member1_ _datatype_;  
  _member2_ _datatype_;  
  _member3_ _datatype_;  
  ...  
}

### Example

Here we declare a struct type `Person` with the following members: `name`, `age`, `job` and `salary`:

type Person struct {  
  name string  
  age int  
  job string  
  salary int  
}

**Tip:** Notice that the struct members above have different data types. `name` and `job` is of type string, while `age` and `salary` is of type int.

___

## Access Struct Members

To access any member of a structure, use the dot operator (.) between the structure variable name and the structure member:

### Example

package main  
import ("fmt")

type Person struct {  
  name string  
  age int  
  job string  
  salary int  
}

func main() {  
  var pers1 Person  
  var pers2 Person

    pers1.name = "Hege"  
  pers1.age = 45  
  pers1.job = "Teacher"  
  pers1.salary = 6000

    pers2.name = "Cecilie"  
  pers2.age = 24  
  pers2.job = "Marketing"  
  pers2.salary = 4500

    fmt.Println("Name: ", pers1.name)  
  fmt.Println("Age: ", pers1.age)  
  fmt.Println("Job: ", pers1.job)  
  fmt.Println("Salary: ", pers1.salary)

    fmt.Println("Name: ", pers2.name)  
  fmt.Println("Age: ", pers2.age)  
  fmt.Println("Job: ", pers2.job)  
  fmt.Println("Salary: ", pers2.salary)  
}

Result:

`Name: Hege   Age: 45   Job: Teacher   Salary: 6000   Name: Cecilie   Age: 24   Job: Marketing   Salary: 4500`

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_struct1)

___

___

## Pass Struct as Function Arguments

You can also pass a structure as a function argument, like this:

### Example

package main  
import ("fmt")

type Person struct {  
  name string  
  age int  
  job string  
  salary int  
}

func main() {  
  var pers1 Person  
  var pers2 Person

    pers1.name = "Hege"  
  pers1.age = 45  
  pers1.job = "Teacher"  
  pers1.salary = 6000

    pers2.name = "Cecilie"  
  pers2.age = 24  
  pers2.job = "Marketing"  
  pers2.salary = 4500

    printPerson(pers1)  
  
    printPerson(pers2)  
}

func printPerson(pers Person) {  
  fmt.Println("Name: ", pers.name)  
  fmt.Println("Age: ", pers.age)  
  fmt.Println("Job: ", pers.job)  
  fmt.Println("Salary: ", pers.salary)  
}

Result:

`Name: Hege   Age: 45   Job: Teacher   Salary: 6000   Name: Cecilie   Age: 24   Job: Marketing   Salary: 4500`

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_struct3)

  

Track your progress - it's free!

   [![Get Certified](https://www.w3schools.com/images/img_course_up_300.png)](https://campus.w3schools.com/collections/course-catalog)
