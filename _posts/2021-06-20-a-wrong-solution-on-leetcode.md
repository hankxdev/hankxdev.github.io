---
layout: post
title: 'A wrong solution on Leetcode'
date: 2021-06-21
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- programming
tags:
- git
meta:
  _edit_last: '1'
permalink: "/a-wrong-solution-on-leetcode"
comments: true
---

With all these years as an engineer, I never tried Leetcode.

Maybe it's because I never prepared for interview before.

Well, now I have to, because the company I just joined in 6 month ago, is gonna shutdown 
it's office here.

Technically not shutdown, it just lays off every programmer because it thinks we are more expensive than those in 
another country.

So people all say you have to try Leetcode to practice your programming skill.

As a frontend engineer, why should I try it? Most of the time, I'm building UI, calling API, fighting with webpack configuration, 
cursing Google Lighthouse always gives my webpage low score, 
arguing with designer why is same  font size seems so big on production than on Figma...

After I tried to solve some problems on it, I found it is pretty fun, except it made me think myself not a qualified programmer.

For the problem [palindrome permutation](https://leetcode.com/problems/palindrome-permutation/). I found it's top 1 solution is not correct.

The code is like this:

```javascript
var canPermutePalindrome = function(s) {
  let arr = [...new Set(s.split(""))];
  let m = arr.length - Math.ceil(s.length/2);
  if(arr.length == 1 || m == -1 || m == 0)
  return true;
  return false;
};
```
The code is very short and clean, pretty impressive at the first glance, and most of the cases it works,
Leetcode also thinks it's a correct one.
But if you try with a string `aaaabbbbcc`, it returns `false`, while it should be `true`. `ababccbaba` clearly is a palindrome.
Clearly the test cases could not cover all the scenes
Here is my solution, a simple and basic one:
```javascript
var canPermutePalindrome = function(s) {
    let set = new Set()
    for (const str of s) {
      set.has(str) ? set.delete(str): set.add(str)
    }
    return set.size <= 1
};
```
Basically it uses [`Set`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set) to store the
unique chars in the string, it should be at last only 1 char with odd amount.

It uses 100ms to execute. Not a very good one, but at least it works :D