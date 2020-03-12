---
layout: post
title: How to trigger click event in Gmail
date: 2020-03-12
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- programming
tags:
- gmail
- chrome extension
- browser extension
meta:
  _edit_last: '1'
permalink: "/how-to-trigger-click-event-in-gmail"
comments: true
---

If you want to hack Gmail UI, to build web extension or any other similar tool that works on top of Gmail, 
you always want or need to trigger some DOM events in Gmail UI, like you want to click on some buttons/icons,
to send out email, to make the compose window pop out, etc.

You can't do it by simply use `click` function, either by Vanilla JS or jQuery, either `click` or `trigger` function can not
achieve your goal.

You need to do this by using  [`Document.createEvent()`](https://developer.mozilla.org/en-US/docs/Web/API/Document/createEvent).

Take `click` for example, you want to click an `icon`:

```JavaScript
  const mouseDown = document.createEvent('MouseEvents');
  mouseDown.initEvent('mousedown', true, false);
  icon.dispatchEvent(mouseDown);

  const mouseUp = document.createEvent('MouseEvents');
  mouseUp.initEvent('mouseup', true, false);
  icon.dispatchEvent(mouseUp);
```

You may want to make it as a function so that you can use it click any element.
