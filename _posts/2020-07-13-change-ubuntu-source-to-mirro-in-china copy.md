---
layout: post
title: 'Change Ubuntu 20.04 update source to mirror site in China'
date: 2020-07-13
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
meta:
  _edit_last: '1'
permalink: "/change-ubuntu-20-04-source-to-china-mirror"
comments: true
---

Ubuntu 20.04 has been released for a while, its code is `Focal Fossa`.  Again, if you are in China, better change the update source to mirror sites.

This post is just a copy from [Change Ubuntu 18.04 update source to mirror site in China](https://momane.com/change-ubuntu-18-04-source-to-china-mirror), and I just replaced the source url from thoes ones of 18.04 to 20.04

Here are several famous mirror sites. What you need todo is pick one from below and edit `etc/apt/sources.list`, replace the content in this file.

There are some links beend commented out. 

- starts with`deb-src` is for source code, without them the speed would be even faster
- the one with `focal-proposed` are just proposed updates, only enable them if you know the risk.

**Better backup you `etc/apt/sources.list` before you do this**

#### 163 (netease)
_source:http://mirrors.163.com/_
````
deb http://mirrors.163.com/ubuntu/ focal main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ focal-security main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ focal-updates main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ focal-backports main restricted universe multiverse
# deb http://mirrors.163.com/ubuntu/ focal-proposed main restricted universe multiverse
# deb-src http://mirrors.163.com/ubuntu/ focal main restricted universe multiverse
# deb-src http://mirrors.163.com/ubuntu/ focal-security main restricted universe multiverse
# deb-src http://mirrors.163.com/ubuntu/ focal-updates main restricted universe multiverse
# deb-src http://mirrors.163.com/ubuntu/ focal-proposed main restricted universe multiverse
# deb-src http://mirrors.163.com/ubuntu/ focal-backports main restricted universe multiverse
```` 

#### alibaba (aliyun)
_source:https://opsx.alibaba.com/mirror_
````
deb http://mirrors.aliyun.com/ubuntu/ focal main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ focal-security main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ focal-updates main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ focal-backports main restricted universe multiverse
# deb http://mirrors.aliyun.com/ubuntu/ focal-proposed main restricted universe multiverse
# deb-src http://mirrors.aliyun.com/ubuntu/ focal main restricted universe multiverse
# deb-src http://mirrors.aliyun.com/ubuntu/ focal-security main restricted universe multiverse
# deb-src http://mirrors.aliyun.com/ubuntu/ focal-backports main restricted universe multiverse
# deb-src http://mirrors.aliyun.com/ubuntu/ focal-updates main restricted universe multiverse
# deb-src http://mirrors.aliyun.com/ubuntu/ focal-proposed main restricted universe multiverse
````
And here are also two Chinese university mirror, use them only if you are in Chinese university.
#### tsinghua university

````
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-updates main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-backports main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-security main restricted universe multiverse
# deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-proposed main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-updates main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-backports main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-security main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-proposed main restricted universe multiverse
````

#### ustc (university of science and technology of China)
````
deb https://mirrors.ustc.edu.cn/ubuntu/ focal main restricted universe multiverse
deb https://mirrors.ustc.edu.cn/ubuntu/ focal-updates main restricted universe multiverse
deb https://mirrors.ustc.edu.cn/ubuntu/ focal-backports main restricted universe multiverse
deb https://mirrors.ustc.edu.cn/ubuntu/ focal-security main restricted universe multiverse
# deb https://mirrors.ustc.edu.cn/ubuntu/ focal-proposed main restricted universe multiverse
# deb-src https://mirrors.ustc.edu.cn/ubuntu/ focal main restricted universe multiverse
# deb-src https://mirrors.ustc.edu.cn/ubuntu/ focal-updates main restricted universe multiverse
# deb-src https://mirrors.ustc.edu.cn/ubuntu/ focal-backports main restricted universe multiverse
# deb-src https://mirrors.ustc.edu.cn/ubuntu/ focal-security main restricted universe multiverse
# deb-src https://mirrors.ustc.edu.cn/ubuntu/ focal-proposed main restricted universe multiverse
````

Enjoy:)

