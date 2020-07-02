---
layout: post
title: How to fix You have to set a contact email in Chrome Web Store
date: 2020-07-02
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- programming
- chrome
tags:
- chrome extension
- web extension
meta:
  _edit_last: '1'
permalink: "/fix-you-have-to-set-a-contract-email-chrome-web-store"
comments: true
---

I have multiple accounts in Chrome Web Store to manage multiple Chrome extensions.

Today I found that one of my extension [one click extensions manager](https://chrome.google.com/webstore/detail/one-click-extensions-mana/pbgjpgbpljobkekbhnnmlikbbfhbhmem) did not get updated as schedule. which is very abnormal because it's scheduled by Github action, and the log shows that the latest version had been submitted to the store several days ago.

In the dashboard it's telling me to add a contract email in my account so that I could publish it. And I already added it long time ago. 

After several meaningless refreshes and clicking on the save button, I realized it might because of my other accounts. So I switched to other accounts and found there is one account without contact email. And the item got published once I fixed this issue.

So weird because it never asks me to add contact email before. And the store hint is so unclear, it needs you to add contact email on every account, not just the current one.

Honestly, the new Chrome web store dashboard is not as easy to use as the old one.
Only the UI is fresher than before.

<img src="../img/chrome-web-store-ask-contact-email.png" style="margin-bottom:15px;" alt="chrome web store asks for contact email" width="800"/>


Also, got an email from Microsoft Edge team, they ask me to submit my extension to Edge store, as Edge is using Chromium now. So if you have published Chrome extension before, you can try 
to submit it to Edge store too. The process would take less than 30 min to do it. 

And, the Edge store dashboard is hard to use too, especially if your extension surppots multiple language, you will need to set information like logo, screenshot, description for every
language. insane, right?.
 



