---
layout: post
title: 'MySQL: Sort Number in String Format'
date: 2019-05-21
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- database
- programming
tags:
- mysql
- sort
meta:
  _edit_last: '1'
permalink: "/mysql-how-to-sort-number-in-string-format"
comments: true
---
TL;DR: use `key_name` `*` `1`; like
```
 select id, name, age from users order by salary * 1
```

Well, it's better to store number data in number format in the database. But there is always accident, sometimes you or
your colleague just stored some number into database with string format, of cause with some reason.

And one day you need to get data from that table and sort the result by that string-number column. Then you found something 
is not right.

If you run command like this:  
```
select "1000" > "2"
```
you will find that the result is *0*. it means,
**100 < 2**. that's because mysql just compare these 2 values in as string. thus **2 > 1**.

There are several work around to make this works, like  use [conv()](https://dev.mysql.com/doc/refman/8.0/en/mathematical-functions.html#function_conv).
So write your sql like this:
```
select * from users order by conv(`salary`, 10, 10)
```
`conv(original_value, from_base, to_base)` is a mysql function, to convert a value from a base to another base, like you can also 
convert a numeric base system 2 to numeric base system 10.

But there is another shorter and cooler way to do this. that's mul the value by 1. Like so:
```
select * from users order by salary * 1
```
Work like a charm.

Need to notice that if the value is too large, the result will be in *Scientific notation* like `1e17`.

-EOF-
