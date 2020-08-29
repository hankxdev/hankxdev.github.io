---
layout: post
title: 'Use git archive to zip your source code'
date: 2020-08-29
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
permalink: "/how-to-zip-only-source-code"
comments: true
---

To zip compiled project file is easy, normally I just use [archivejs](), write a small nodejs script, and then add a script in `package.json`.

And then I need to zip the source code only. Exclude the dist folder, the huge `node_modules` folder and other folders.

Basically just source code and exclude everything in .gitignore file.

I tried to use `archivejs`'s `glob` api. Like so:

```javascript
archive.glob('**', {
  ignore: ['folder/**', 'file']
})
```

But I could not make it works, it either zip nothing or zip everything in my folder, I think it's because the path that I set is not correct. And I don't want to 
spend too much time on reading and exploring archivejs's api doc.

So I came to use `zip` command in terminal. To use it is very simple, just use `-x` to exclude file, like this

```bash
zip -r output.zip directory -x \*\*/\*/node_modules/\*
```

Which is great. But the command is too long and if there are many files you want to exclude, you will need to write down them every time.

At the same time I found that with `git archive` I can do this easily. so just run 

```bash
git archive --format=zip HEAD -o zipfile.zip
```

it will pack all your source code into zip file, exclude everything in the .gitignore file. Super neat.