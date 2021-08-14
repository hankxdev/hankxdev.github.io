---
layout: post
title: 'Do not store file outside of WSL, it is slow'
date: 2021-08-14
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- programming
tags:
- wsl
permalink: "/do-not-store-file-outside-of-wsl-file-system-its-slow"
comments: true
---

For some reason, I have switch back to Windows OS after years of working on MacOS.

Most of the time I'm working on frontend projects, so to get better DX, I use Windows Subsystem for Linux (WSL for short). 
And I'm using version 2 of it.

But I'm not a fancy Vim programmer, I heavily relay on IDEs like  VS Code and WebStorm. So I still have to install these IDEs
on the Windows.

I'm able to install zsh, oh-my-zsh, fuck, p10k along with other tools in the WSL, gives me a similar experience as on Mac.

At the first I put the project on Windows file system, because in this way I can easily access the file from IDE. 
And then in the WSL2 terminal, I go to the Windows path like this:
```shell
cd /mnt/DISK/PROJECT_FOLDER
```
I can run all these frontend commands like `yarn`, `nvm`. Seems smooth.

Soon I find a big issue. The hot module replacement not working, the building process is very slow. I have to restart the project 
dev command after making change to the code. Clearly this is not an acceptable solution.

After searching a bit on the internet, I move the project back to WSL file system, then every thing works perfectly. The building is faster,
the HMR is working. 

To access the file in WSL from IDEs, VS Code has [extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl) 
to open file from WSL easily, just install it, and in the terminal, just switch to the project folder and type `code .`. Or in the IDE, click `File-Open Folder`, 
it will show your linux home folder by default. For WebStorm, it will also show the WSL folder in the open file dialog.

Finally, I can use my i7+32G Windows, don't need to listen to the crazy fan noise on the MBP :D

