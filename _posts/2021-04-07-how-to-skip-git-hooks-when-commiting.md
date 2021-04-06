---
layout: post
title: 'how-to-skip-git-hooks-when-committing'
date: 2021-04-07
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
permalink: "/how-to-skip-git-hooks-when-committing"
comments: true
---


Well,  it's not very recommended skipping git hooks. These hooks are often for formatting code, running tests, etc.

But life happens, sometimes you want to commit something quickly or even an empty commit to the server so that you can 
trigger some CI/CD, but you have to wait for 5 min for those tests running.

So if you want to skip git hooks while commting, simply run command like this:

```bash
git commit --no-verify -m "YOUR COMMIT MESSAGE"
```

or for short
```bash
git commit -n -m "YOUR COMMIT MESSAGE"
```

BTW, the command to push an empty commit is

```bash
git commit --allow-empty -m "YOUR COMMIT MESSAGE"
```

Just remember only use these commands when you are really urgent and confident about your change.

















