---
layout: post
title:      "#uniq vs #uniq!"
date:       2018-05-22 13:30:07 -0400
permalink:  uniq_vs_uniq
---

After getting to practice with arrays over and over again, I have learned that there are numerous methods which help one to iterate over them. One of the really useful things that I have learned is the use of methods with and without '!'. Utilizing '!' at the end of an array method will return the modified original array or `nil`. By not utilizing '!', it will return a new array. So, to give an example of this, I have decided to explain the differences between the `#uniq` and `#uniq!` methods. 
## `#uniq`
`#uniq` returns a new array by removing all duplicates in `self` 
<br><br>
```uniq → new_array```
<br><br>
```array = [“a”, “b”, “a”, “c”, “c”, “d”]``` 
<br>
```array.uniq #=> [“a”, “b”, “c”, “d”]``` 
<br><br>
`#uniq` can also accept a block 
<br><br>
```uniq {|item| block} → new_array```
<br><br>
```array = [[“student”, “sam”], [“student”, “george”], [“teacher”, “matz”]]```
<br>
```array.uniq {|s| s.first} #=> [[“student”, “sam], [“teacher”, “matz”]]```
## `#uniq!`
`#uniq!` returns the original array after removing all duplicates in `self` or returns `nil` if there are no duplicates.
<br><br>
```uniq! → array or nil```
<br><br>
```array = [“a”, “b”, “b”, “a”, “c”]```
<br>
```array.uniq! #=> [“a”, “b”, “c”]``` 
<br><br>
```array = [“a”, “b”, “c”]```
<br>
```array.uniq! #=> nil```
<br><br>
`#uniq!` can also accept a block 
<br><br>
```uniq! {|item| block} → array or nil```
<br><br>
```array = [[“student”, “sam”], [“student”, “george”], [“teacher”, “matz”]]```
<br>
```array.uniq! {|s| s.first} #=> [[“student”, “sam], [“teacher”, “matz”]]```
<br><br><br>
### References
https://ruby-doc.org/core-2.2.0/Array.html#method-i-uniq
<br>
https://stackoverflow.com/questions/33923492/ruby-what-is-the-difference-between-uniq-and-uniq
<br>
https://apidock.com/ruby/Array/uniq%21
<br>
https://apidock.com/ruby/Array/uniq
