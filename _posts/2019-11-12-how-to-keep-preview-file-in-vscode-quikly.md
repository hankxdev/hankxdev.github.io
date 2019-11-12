---
layout: post
title: how to keep preview file in VS Code quickly
date: 2019-11-12
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- programming
tags:
- vscode
meta:
  _edit_last: '1'
permalink: "/how-to-keep-preview-file-in-vscode-quickly"
comments: true
---

You are a VS Code master, you barely use mouse when coding.

You want to edit a file A in your project.

You open A via hotkey, CMD+Shif+R (yes, I came from eclipse).

Before you editing A, you want to check some reference in another file B.

You open B with same hotkey, you got your information.

Then you want to go back to A to make your editing.

Where is my file A? That one with 1000 rows of code, it was there just before.

Alright I can just open it again, CMD SHIFT R, yes, it comes back.

WTF, Why is B gone?


This happens a lot before to me, I have to double click the file in the project file list to keep it open.

It's because VS Code thinks that you just want to `preview` the file when you single click the file or open it with hotkey.

But it's really annoying that you want to open multiple files in editor and keep them open.

So here is a quicky way to do this:

Press a __CMD + S__ (Ctrl+S on Windows, that's hotkey for `save` ) once you open the file. You will notice that the file name font in tab becomes regular from italic. 




