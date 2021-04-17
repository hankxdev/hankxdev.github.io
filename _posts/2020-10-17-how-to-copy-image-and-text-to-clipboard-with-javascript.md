---
layout: post
title: 'How to copy image and text to clipboard with JavaScript'
date: 2020-10-18
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- programming
tags:
- javascript
meta:
  _edit_last: '1'
permalink: "/how-to-copy-image-and-text-to-clipboard-with-javascript"
comments: true
---

I used to saw my colleague add a 30kb lib only to implement a copy function
that when the user clicks on a text, copy it to the clipboard.
 
And I also saw someone still trying to use flash or Clipboard lib to do the same thing.

#### Here is how to copy text to your clipboard with JavaScript with just several lines of code. And it's cross-browser
and device. No need for any 3rd party lib.

```javascript
function copyToClipboard(text){
 const ta = document.createElement('textarea');
 ta.value = this.url;
 document.body.appendChild(ta);
 //hide it
 ta.style.padding = 0;
 ta.style.border = 'none';
 ta.style.outline = 'none';
 ta.style.boxShadow = 'none';
 //select the text
 ta.focus();
 ta.select();
 document.execCommand('copy');
 document.body.removeChild(ta);
}
```

it's very simple, you just append an invisible textarea to the page, set value as the text you want to copy,
and run `document.execCommand('copy')`. Then remove the textarea from the page.

#### here is how to copy the image to your clipboard with JavaScript
Note that this one only works on Chrome and Edge right now (2020-10)
https://caniuse.com/mdn-api_clipboarditem

This requires you to use `canvas` to port the image to blob first.

```javascript
function imageToBlob(imageURL) {
  const img = new Image;
  const c = document.createElement("canvas");
  const ctx = c.getContext("2d");
  img.crossOrigin = "";
  img.src = imageURL;
  return new Promise(resolve => {
    img.onload = function () {
      c.width = this.naturalWidth;
      c.height = this.naturalHeight;
      ctx.drawImage(this, 0, 0);
      c.toBlob((blob) => {
        // here the image is a blob
        resolve(blob)
      }, "image/png", 0.75);
    };
  })
}
```

Then use the `Clipboard` API to do the magic

```javascript

async function copyImage(imageURL){
  const blob = await imageToBlob(imageURL)
  const item = new ClipboardItem({ "image/png": blob });
  navigator.clipboard.write([item]);
}
```

Simple as that.