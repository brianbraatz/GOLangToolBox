---
Description: Go - Maps
Notes: Go - Maps - Go provides another important data type named map which maps unique keys to values. A key is an object that you use to retrieve a value at a later date. Given a key and a value, you can store the value in a Map object. After the value is stored, you can retrieve it by using its key.
author: 
Url: https://www.tutorialspoint.com/go/go_maps.htm
Created: "2025-01-29  02:37:21"
Modified: 
Tags:
  - LatextTemplate
Keywords: []
---

# Go - Maps

source: https://www.tutorialspoint.com/go/go_maps.htm

> ## Excerpt
> Go - Maps - Go provides another important data type named map which maps unique keys to values. A key is an object that you use to retrieve a value at a later date. Given a key and a value, you can store the value in a Map object. After the value is stored, you can retrieve it by using its key.

---
___

___

Go provides another important data type named map which maps unique keys to values. A key is an object that you use to retrieve a value at a later date. Given a key and a value, you can store the value in a Map object. After the value is stored, you can retrieve it by using its key.

## Defining a Map

You must use **make** function to create a map.

```
/* declare a variable, by default map will be nil*/
var map_variable map[key_data_type]value_data_type

/* define the map as nil map can not be assigned any value*/
map_variable = make(map[key_data_type]value_data_type)
```

## Example

The following example illustrates how to create and use a map −

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

func main</span><span>()</span><span> </span><span>{</span><span>
   </span><span>var</span><span> countryCapitalMap map</span><span>[</span><span>string</span><span>]</span><span>string</span><span>
   </span><span>/* create a map*/</span><span>
   countryCapitalMap </span><span>=</span><span> make</span><span>(</span><span>map</span><span>[</span><span>string</span><span>]</span><span>string</span><span>)</span><span>
   
   </span><span>/* insert key-value pairs in the map*/</span><span>
   countryCapitalMap</span><span>[</span><span>"France"</span><span>]</span><span> </span><span>=</span><span> </span><span>"Paris"</span><span>
   countryCapitalMap</span><span>[</span><span>"Italy"</span><span>]</span><span> </span><span>=</span><span> </span><span>"Rome"</span><span>
   countryCapitalMap</span><span>[</span><span>"Japan"</span><span>]</span><span> </span><span>=</span><span> </span><span>"Tokyo"</span><span>
   countryCapitalMap</span><span>[</span><span>"India"</span><span>]</span><span> </span><span>=</span><span> </span><span>"New Delhi"</span><span>
   
   </span><span>/* print map using keys*/</span><span>
   </span><span>for</span><span> country </span><span>:=</span><span> range countryCapitalMap </span><span>{</span><span>
      fmt</span><span>.</span><span>Println</span><span>(</span><span>"Capital of"</span><span>,</span><span>country</span><span>,</span><span>"is"</span><span>,</span><span>countryCapitalMap</span><span>[</span><span>country</span><span>])</span><span>
   </span><span>}</span><span>
   
   </span><span>/* test if entry is present in the map or not*/</span><span>
   capital</span><span>,</span><span> ok </span><span>:=</span><span> countryCapitalMap</span><span>[</span><span>"United States"</span><span>]</span><span>
   
   </span><span>/* if ok is true, entry is present otherwise entry is absent*/</span><span>
   </span><span>if</span><span>(</span><span>ok</span><span>){</span><span>
      fmt</span><span>.</span><span>Println</span><span>(</span><span>"Capital of United States is"</span><span>,</span><span> capital</span><span>)</span><span>  
   </span><span>}</span><span> </span><span>else</span><span> </span><span>{</span><span>
      fmt</span><span>.</span><span>Println</span><span>(</span><span>"Capital of United States is not present"</span><span>)</span><span> 
   </span><span>}</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
Capital of India is New Delhi
Capital of France is Paris
Capital of Italy is Rome
Capital of Japan is Tokyo
Capital of United States is not present
```

[

Explore our **latest online courses** and learn new skills at your own pace. Enroll and become a certified expert to boost your career.

](https://www.tutorialspoint.com/latest/courses?utm_source=tutorialspoint&utm_medium=tutorials_3p&utm_campaign=internal)

## delete() Function

delete() function is used to delete an entry from a map. It requires the map and the corresponding key which is to be deleted. For example −

```
<span>package</span><span> main

</span><span>import</span><span> </span><span>"fmt"</span><span>

func main</span><span>()</span><span> </span><span>{</span><span>   
   </span><span>/* create a map*/</span><span>
   countryCapitalMap </span><span>:=</span><span> map</span><span>[</span><span>string</span><span>]</span><span> </span><span>string</span><span> </span><span>{</span><span>"France"</span><span>:</span><span>"Paris"</span><span>,</span><span>"Italy"</span><span>:</span><span>"Rome"</span><span>,</span><span>"Japan"</span><span>:</span><span>"Tokyo"</span><span>,</span><span>"India"</span><span>:</span><span>"New Delhi"</span><span>}</span><span>
   
   fmt</span><span>.</span><span>Println</span><span>(</span><span>"Original map"</span><span>)</span><span>   
   
   </span><span>/* print map */</span><span>
   </span><span>for</span><span> country </span><span>:=</span><span> range countryCapitalMap </span><span>{</span><span>
      fmt</span><span>.</span><span>Println</span><span>(</span><span>"Capital of"</span><span>,</span><span>country</span><span>,</span><span>"is"</span><span>,</span><span>countryCapitalMap</span><span>[</span><span>country</span><span>])</span><span>
   </span><span>}</span><span>
   
   </span><span>/* delete an entry */</span><span>
   </span><span>delete</span><span>(</span><span>countryCapitalMap</span><span>,</span><span>"France"</span><span>);</span><span>
   fmt</span><span>.</span><span>Println</span><span>(</span><span>"Entry for France is deleted"</span><span>)</span><span>  
   
   fmt</span><span>.</span><span>Println</span><span>(</span><span>"Updated map"</span><span>)</span><span>   
   
   </span><span>/* print map */</span><span>
   </span><span>for</span><span> country </span><span>:=</span><span> range countryCapitalMap </span><span>{</span><span>
      fmt</span><span>.</span><span>Println</span><span>(</span><span>"Capital of"</span><span>,</span><span>country</span><span>,</span><span>"is"</span><span>,</span><span>countryCapitalMap</span><span>[</span><span>country</span><span>])</span><span>
   </span><span>}</span><span>
</span><span>}</span>
```

When the above code is compiled and executed, it produces the following result −

```
Original Map
Capital of France is Paris
Capital of Italy is Rome
Capital of Japan is Tokyo
Capital of India is New Delhi
Entry for France is deleted
Updated Map
Capital of India is New Delhi
Capital of Italy is Rome
Capital of Japan is Tokyo
```
