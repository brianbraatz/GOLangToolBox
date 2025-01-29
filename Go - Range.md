---
Description: Go - Range
Notes: Go - Range - The range keyword is used in for loop to iterate over items of an array, slice, channel or map. With array and slices, it returns the index of the item as integer. With maps, it returns the key of the next key-value pair. Range either returns one value or two. If only one value is used on the left o
author: 
Url: https://www.tutorialspoint.com/go/go_range.htm
Created: "2025-01-29  02:37:15"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go - Range

source: https://www.tutorialspoint.com/go/go_range.htm

> ## Excerpt
> Go - Range - The range keyword is used in for loop to iterate over items of an array, slice, channel or map. With array and slices, it returns the index of the item as integer. With maps, it returns the key of the next key-value pair. Range either returns one value or two. If only one value is used on the left o

---
___

___

The **range** keyword is used in **for** loop to iterate over items of an array, slice, channel or map. With array and slices, it returns the index of the item as integer. With maps, it returns the key of the next key-value pair. Range either returns one value or two. If only one value is used on the left of a range expression, it is the 1st value in the following table.

| Range expression | 1st Value | 2nd Value(Optional) |
| --- | --- | --- |
| Array or slice a \[n\]E | index i int | a\[i\] E |
| String s string type | index i int | rune int |
| map m map\[K\]V | key k K | value m\[k\] V |
| channel c chan E | element e E | none |

## Example

The following paragraph shows how to use range −

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

func main</span><span>()</span><span> </span><span>{</span><span>
   </span><span>/* create a slice */</span><span>
   numbers </span><span>:=</span><span> </span><span>[]</span><span>int</span><span>{</span><span>0</span><span>,</span><span>1</span><span>,</span><span>2</span><span>,</span><span>3</span><span>,</span><span>4</span><span>,</span><span>5</span><span>,</span><span>6</span><span>,</span><span>7</span><span>,</span><span>8</span><span>}</span><span> 
   
   </span><span>/* print the numbers */</span><span>
   </span><span>for</span><span> i</span><span>:=</span><span> range numbers </span><span>{</span><span>
      fmt</span><span>.</span><span>Println</span><span>(</span><span>"Slice item"</span><span>,</span><span>i</span><span>,</span><span>"is"</span><span>,</span><span>numbers</span><span>[</span><span>i</span><span>])</span><span>
   </span><span>}</span><span>
   
   </span><span>/* create a map*/</span><span>
   countryCapitalMap </span><span>:=</span><span> map</span><span>[</span><span>string</span><span>]</span><span> </span><span>string</span><span> </span><span>{</span><span>"France"</span><span>:</span><span>"Paris"</span><span>,</span><span>"Italy"</span><span>:</span><span>"Rome"</span><span>,</span><span>"Japan"</span><span>:</span><span>"Tokyo"</span><span>}</span><span>
   
   </span><span>/* print map using keys*/</span><span>
   </span><span>for</span><span> country </span><span>:=</span><span> range countryCapitalMap </span><span>{</span><span>
      fmt</span><span>.</span><span>Println</span><span>(</span><span>"Capital of"</span><span>,</span><span>country</span><span>,</span><span>"is"</span><span>,</span><span>countryCapitalMap</span><span>[</span><span>country</span><span>])</span><span>
   </span><span>}</span><span>
   
   </span><span>/* print map using key-value*/</span><span>
   </span><span>for</span><span> country</span><span>,</span><span>capital </span><span>:=</span><span> range countryCapitalMap </span><span>{</span><span>
      fmt</span><span>.</span><span>Println</span><span>(</span><span>"Capital of"</span><span>,</span><span>country</span><span>,</span><span>"is"</span><span>,</span><span>capital</span><span>)</span><span>
   </span><span>}</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
Slice item 0 is 0
Slice item 1 is 1
Slice item 2 is 2
Slice item 3 is 3
Slice item 4 is 4
Slice item 5 is 5
Slice item 6 is 6
Slice item 7 is 7
Slice item 8 is 8
Capital of France is Paris
Capital of Italy is Rome
Capital of Japan is Tokyo
Capital of France is Paris
Capital of Italy is Rome
Capital of Japan is Tokyo
```
