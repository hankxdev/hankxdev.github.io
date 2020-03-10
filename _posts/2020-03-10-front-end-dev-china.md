---
layout: post
title: 'Boost your Frontend developing speed in China'
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
permalink: "/boost-your-developing-speed-in-china"
comments: true
---

Waiting for something is wasting time, especially when developing, you always need to wait for compiling, wait for install dependencies...

And if you are in China, this waiting time will be much longer because of some well known reason. 

Here are some changes that will save you some time in China if you are doing frontend development. 

## Ruby

change your gem source to China mirror, source: https://ruby-china.org/
```
gem source -a https://gems.ruby-china.com
```

## npm
change your npm source to China mirror, source , source: https://developer.aliyun.com/mirror/NPM
```
npm config set registry https://registry.npm.taobao.org
```

or you can also install a `cnpm`, use `cnpm` rather than `npm`, to avoid change the source url permanently.
```
$ npm install -g cnpm --registry=https://registry.npm.taobao.org
``` 

## yarn
Same as npm.

```
yarn config set registry https://registry.npm.taobao.org --global
```
there is no `cyarn` though

## ubuntu
change sourcelist, check [this post](https://momane.com/change-ubuntu-18.04-source-to-china-mirror)





