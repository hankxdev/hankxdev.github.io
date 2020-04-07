---
layout: post
title: Use document.execCommand to set value in editable field and trigger events
date: 2020-04-07
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- programming
tags:
- javascript
- chrome extension
- browser extension
meta:
  _edit_last: '1'
permalink: "/use-document-execcommand-to-set-value"
comments: true
---


**NOTE: This [`document.execCommand`](https://developer.mozilla.org/en-US/docs/Web/API/Document/execCommand) api has been marked as `Obsolete`. However, given the situation that new API is still under construction, so it's still safe to use it for now and maybe for next few years.**

To set value in editable filed like input, textarea with javascript is a common requirement in browser extension or other script development. 
Normally you just need to do something like `document.querySelector('input').value="text you want to set"` to get the job done easily and quickly.

But life is not always so easy. Actually most of the time you need to do more in browser extension development. The input fileds always bond many events like `beforeinput`, `input`,`change`, or even `focus`, `active`. If you just set the `value` by javascript, you will also need to trigger these events manually in next steps.

And before that you will need to find out what events you need to trigger. It gonna take you some time.


With this `document.execCoomand`, you can do it easily.

The syntax is like this:
>document.execCommand(aCommandName, aShowDefaultUI, aValueArgument)

There is a **insertTest** you can use to set value. 
>Inserts the given plain text at the insertion point (deletes selection).

so to insert text in to a field, you just, focus the field -> select the field -> execute the command, like so:

```javascript
const element = document.querySelector("#target")
element.focus()
element.select()
document.execCommand("insertText", false, "text you want to set")
```

The best of this API is that, **it imitates user input event, make it like human being activity, trigger all bond events on the filed**.

This API is very powerful, there are a bunch of commands you can use to make you life easier. 

You can read it's doc on MDN to get more details: https://developer.mozilla.org/en-US/docs/Web/API/Document/execCommand
