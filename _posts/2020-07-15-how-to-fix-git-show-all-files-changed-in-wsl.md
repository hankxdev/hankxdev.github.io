---
layout: post
title: 'How to fix Git show all file as modified in WSL'
date: 2020-07-15
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- system
tags:
- windows
- ubuntu
- wsl
meta:
  _edit_last: '1'
permalink: "/how-to-fix-git-show-all-file-as-modified-in-wsl"
comments: true
---

## Solution
If you open your code in Windows, and run git in WSL bash, you will have a big chance to meet an issue that `git status` shows all your
file get modified.
To fix the issue, run this in WSL bash:
```bash
git config --global core.autocrlf true
```

Normally I use OSX, but today I have to go back to my Windows PC to try an extension on Edge.

I'm using WSL (that's Windows Subsystem for Linux) to manage and build my projects.

After I cloned my repo from Github, I tried to create a new branch for Edge version. But after I ran `git branch branchname`
, it told me that there were changes need to commit first.

So I ran `git status`, to check what's been changed. Then I got this:

<img src="../img/wsl-change-all.png" alt="all files modified">

This was a simple app. so it's basically showing that every file got modified. But I hadn't do anything to any file. 

It's because I was using git in WSL, but I opened files in Windows system. So the line ending is `CRLF`, but git thought it's on Linux so the 
line should ends with `LF`.

So the fix command will tell git to use `CRLF` and line ending.
