---
layout: post
title: 'Disable Web Search Result in Windows Search 2019'
date: 2019-08-04
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- system
tags:
- windows
meta:
  _edit_last: '1'
permalink: "/disable-web-search-result-in-windows-search"
comments: true
---

__TL;DR__: download this [windows reg file](https://github.com/HangYang/disable-windows-web-search) and double click to import it.
OR
- copy the code from below
- open you favourite text editor, or just use notepad
- paste the code into it
- save the file with `.reg` extension
- double click the file 


```
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Search ]
"ConnectedSearchUseWebOverMeteredConnections"=dword:00000000
"AllowCortana"=dword:00000000
"DisableWebSearch "=dword:00000001
"ConnectedSearchUseWeb"=dword:00000000

[HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Search]
"CortanaConsent"=dword:00000000
"BingSearchEnabled"=dword:00000000
"AllowSearchToUseLocation"=dword:00000000
```


Windows is promoting it's `Cortana` and Bing search for a long time. One of the most annoying thing is that it's showing web search content when you search in start menu.

So you press `Windows` button, type some keywords, all you want to do is just access your installed app or file quickly, but then you saw some shitty stuff in the result list.

Yes, it's showing web search content and even some so called `search suggesttion`. it's based on your keywords and some trends on the web, since you are searching how to disable
this, I know that you also think it's totally garbage. 

In the beginning, Windows gave us an option in the search menu to turn this off. But then Windows known that most of the users hated it, so it just removed this option...

I have to use group policy, regeditor to disable it, and have to search for this every time when it updates. 

To do it step by step is a bit complicated and it's totally a waste of time. So I just create this reg file so that anyone who want to do this can do it by one click.

Comment for these reg code in case someone doubt it:

---

`"ConnectedSearchUseWebOverMeteredConnections"=dword:00000000 ` // _disable web search use mobile connection

`"AllowCortana"=dword:00000000`// disable Cortana

`"DisableWebSearch "=dword:00000001` // disable web search

`"ConnectedSearchUseWeb"=dword:00000000` // disabled web searech connection

`"CortanaConsent"=dword:00000000` // disable Cortana

`"BingSearchEnabled"=dword:00000000` // disable bing search in start menu

`"AllowSearchToUseLocation"=dword:00000000` // disable search feature access your location

---
Enjoy :) 
