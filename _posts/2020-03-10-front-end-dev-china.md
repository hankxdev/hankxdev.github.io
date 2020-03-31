---
layout: post
title: Boost your Frontend development speed in China
date: 2020-03-10
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- programming
tags:
- yarn
- npm
- ruby
- ubuntu
meta:
  _edit_last: '1'
permalink: "/boost-your-development-speed-in-china"
comments: true
---

Waiting for something is wasting time, especially when development, you always need to wait for compiling, wait for install dependencies...

And if you are in China, this waiting time will be much longer because of some well known reason. 

Here are some changes that will save you some time in China if you are doing frontend development. 

## Ruby and Rails

change your gem source to China mirror, source: https://ruby-china.org/
```bash
gem source -a https://gems.ruby-china.com
```

## npm
change your npm source to China mirror, source , source: https://developer.aliyun.com/mirror/NPM
```bash
npm config set registry https://registry.npm.taobao.org
```

or you can also install a `cnpm`, use `cnpm` rather than `npm`, to avoid change the source url permanently.
```bash
$ npm install -g cnpm --registry=https://registry.npm.taobao.org
``` 

## yarn
Same as npm.

```bash
yarn config set registry https://registry.npm.taobao.org --global
```
there is no `cyarn` though

## ubuntu
change sourcelist, check [this post](/change-ubuntu-18-04-source-to-china-mirror)

## homebrew
change homebrew core source and repo to USTC (University of Science and Technology of China) [Mirror](https://lug.ustc.edu.cn/wiki/mirrors/help/brew.git).

- change brew.git:
  
  ```bash
   cd "$(brew --repo)"
   git remote set-url origin https://mirrors.ustc.edu.cn/brew.git
  ```
- change homebrew-core.git
  
  ```bash
   cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core"
   git remote set-url origin https://mirrors.ustc.edu.cn/homebrew-core.git
  ```
- change homebrew bottles source
  
  for `bash` user 
  ```bash
   echo 'export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.ustc.edu.cn/homebrew-bottles' >> ~/.bash_profile
   source ~/.bash_profile
  ```
  for `zsh` user 
  ```bash
   echo 'export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.ustc.edu.cn/homebrew-bottles' >> ~/.zshrc
   source ~/.zshrc
  ```





