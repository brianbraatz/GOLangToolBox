---
Description: Go Maps
Notes: W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.
author: 
Url: https://www.w3schools.com/go/go_maps.php
Created: "2025-01-29  02:30:37"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go Maps

source: https://www.w3schools.com/go/go_maps.php

> ## Excerpt
> W3Schools offers free online tutorials, references and exercises in all the major languages of the web. Covering popular subjects like HTML, CSS, JavaScript, Python, SQL, Java, and many, many more.

---
## Go Maps

___

## Go Maps

Maps are used to store data values in key:value pairs.

Each element in a map is a key:value pair.

A map is an unordered and changeable collection that does not allow duplicates.

The length of a map is the number of its elements. You can find it using the `len()` function.

The default value of a map is nil.

Maps hold references to an underlying hash table.

Go has multiple ways for creating maps.

___

## Create Maps Using `var` and `:=`

### Syntax

var _a_ = map\[KeyType\]ValueType{_key1_:_value1_, _key2_:_value2_,...}  
_b_ := map\[KeyType\]ValueType{_key1_:_value1_, _key2_:_value2_,...}  

### Example

This example shows how to create maps in Go. Notice the order in the code and in the output

package main  
import ("fmt")

func main() {  
  var a = map\[string\]string{"brand": "Ford", "model": "Mustang", "year": "1964"}  
  b := map\[string\]int{"Oslo": 1, "Bergen": 2, "Trondheim": 3, "Stavanger": 4}  
  
  fmt.Printf("a\\t%v\\n", a)  
  fmt.Printf("b\\t%v\\n", b)  
}

Result:

`a   map[brand:Ford model:Mustang year:1964]   b   map[Bergen:2 Oslo:1 Stavanger:4 Trondheim:3]   `

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_maps1)

**Note:** The order of the map elements defined in the code is different from the way that they are stored. The data are stored in a way to have efficient data retrieval from the map.

___

___

## Create Maps Using `make()`Function:

### Syntax

var _a_ = make(map\[KeyType\]ValueType)  
_b_ := make(map\[KeyType\]ValueType)  

### Example

This example shows how to create maps in Go using the `make()`function.

package main  
import ("fmt")

func main() {  
  var a = make(map\[string\]string)

  a\["brand"\] = "Ford"  
  a\["model"\] = "Mustang"  
  a\["year"\] = "1964"  
                                   
  b := make(map\[string\]int)  
  b\["Oslo"\] = 1  
  b\["Bergen"\] = 2  
  b\["Trondheim"\] = 3  
  b\["Stavanger"\] = 4  
  
  fmt.Printf("a\\t%v\\n", a)  
  fmt.Printf("b\\t%v\\n", b)  
}

Result:

`a   map[brand:Ford model:Mustang year:1964]   b   map[Bergen:2 Oslo:1 Stavanger:4 Trondheim:3]   `

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_maps2)

___

## Create an Empty Map

There are two ways to create an empty map. One is by using the `make()`function and the other is by using the following syntax.

### Syntax

var _a_ map\[KeyType\]ValueType  

**Note:** The `make()`function is the right way to create an empty map. If you make an empty map in a different way and write to it, it will causes a runtime panic.

### Example

This example shows the difference between declaring an empty map using with the `make()`function and without it.

package main  
import ("fmt")

func main() {  
  var a = make(map\[string\]string)  
  var b map\[string\]string  
  
  fmt.Println(a == nil)  
  fmt.Println(b == nil)  
}

Result:

`false   true   `

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_maps3)

___

## Allowed Key Types

The map key can be of any data type for which the equality operator (`==`) is defined. These include:

-   Booleans
-   Numbers
-   Strings
-   Arrays
-   Pointers
-   Structs
-   Interfaces (as long as the dynamic type supports equality)

Invalid key types are:

-   Slices
-   Maps
-   Functions

These types are invalid because the equality operator (`==`) is not defined for them.

___

## Allowed Value Types

The map values can be **any** type.

___

## Access Map Elements

You can access map elements by:

### Syntax

_value_ = _map\_name_\[key\]  

### Example

package main  
import ("fmt")

func main() {  
  var a = make(map\[string\]string)  
  a\["brand"\] = "Ford"  
  a\["model"\] = "Mustang"  
  a\["year"\] = "1964"  
  
  fmt.Printf(a\["brand"\])  
}

Result:

`Ford   `

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_maps4)

___

## Update and Add Map Elements

Updating or adding an elements are done by:

### Syntax

_map\_name_\[key\] = value  

### Example

This example shows how to update and add elements to a map.

package main  
import ("fmt")

func main() {  
  var a = make(map\[string\]string)  
  a\["brand"\] = "Ford"  
  a\["model"\] = "Mustang"  
  a\["year"\] = "1964"  
  
  fmt.Println(a)  
  
  a\["year"\] = "1970"

  a\["color"\] = "red"  
  
  fmt.Println(a)  
}

Result:

`map[brand:Ford model:Mustang year:1964]   map[brand:Ford color:red model:Mustang year:1970]   `

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_maps5)

___

## Remove Element from Map

Removing elements is done using the `delete()` function.

### Syntax

delete(_map\_name_, key)  

### Example

package main  
import ("fmt")

func main() {  
  var a = make(map\[string\]string)  
  a\["brand"\] = "Ford"  
  a\["model"\] = "Mustang"  
  a\["year"\] = "1964"  
  
  fmt.Println(a)  
  
  delete(a,"year")  
  
  fmt.Println(a)  
}

Result:

`map[brand:Ford model:Mustang year:1964]   map[brand:Ford model:Mustang]   `

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_maps6)

___

## Check For Specific Elements in a Map

You can check if a certain key exists in a map using:

### Syntax

_val_, _ok_ :=_map\_name_\[key\]  

If you only want to check the existence of a certain key, you can use the blank identifier (`_`) in place of val.

### Example

package main  
import ("fmt")

func main() {  
  var a = map\[string\]string{"brand": "Ford", "model": "Mustang", "year": "1964", "day":""}  
  
  val1, ok1 := a\["brand"\] 

  val2, ok2 := a\["color"\]   
  val3, ok3 := a\["day"\]     
  \_, ok4 := a\["model"\]      
  
  fmt.Println(val1, ok1)  
  fmt.Println(val2, ok2)  
  fmt.Println(val3, ok3)  
  fmt.Println(ok4)  
}

Result:

`Ford true    false    true   true   `

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_maps7)

#### Example Explained

In this example, we checked for existence of different keys in the map.

The key "_color_" does not exist in the map. So the value is an empty string ('').

The _ok2_ variable is used to find out if the key exist or not. Because we would have got the same value if the value of the "color" key was empty. This is the case for _val3_.

___

## Maps Are References

Maps are references to hash tables.

If two map variables refer to the same hash table, changing the content of one variable affect the content of the other.

### Example

package main  
import ("fmt")

func main() {  
  var a = map\[string\]string{"brand": "Ford", "model": "Mustang", "year": "1964"}  
  b := a  
  
  fmt.Println(a)  
  fmt.Println(b)  
  
  b\["year"\] = "1970"  
  fmt.Println("After change to b:")  
  
  fmt.Println(a)  
  fmt.Println(b)  
}

Result:

`map[brand:Ford model:Mustang year:1964]   map[brand:Ford model:Mustang year:1964]   After change to b:   map[brand:Ford model:Mustang year:1970]   map[brand:Ford model:Mustang year:1970]`

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_maps8)

___

## Iterate Over Maps

You can use `range` to iterate over maps.

### Example

This example shows how to iterate over the elements in a map. Note the order of the elements in the output.

package main  
import ("fmt")

func main() {  
  a := map\[string\]int{"one": 1, "two": 2, "three": 3, "four": 4}

  for k, v := range a {  
    fmt.Printf("%v : %v, ", k, v)  
  }  
}

Result:

`two : 2, three : 3, four : 4, one : 1,   `

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_maps10)

___

## Iterate Over Maps in a Specific Order

Maps are unordered data structures. If you need to iterate over a map in a specific order, you must have a separate data structure that specifies that order.

### Example

package main  
import ("fmt")

func main() {  
  a := map\[string\]int{"one": 1, "two": 2, "three": 3, "four": 4}

  var b \[\]string             

  b = append(b, "one", "two", "three", "four")  
  
  for k, v := range a {          
    fmt.Printf("%v : %v, ", k, v)  
  }  
  
  fmt.Println()  
  
  for \_, element := range b {    
    fmt.Printf("%v : %v, ", element, a\[element\])  
  }  
}

Result:

`two : 2, three : 3, four : 4, one : 1,   one : 1, two : 2, three : 3, four : 4,   `

[Try it Yourself »](https://www.w3schools.com/go/trygo.php?filename=demo_maps10)

  

Track your progress - it's free!
