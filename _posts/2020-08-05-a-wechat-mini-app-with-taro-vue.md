---
layout: post
title: '用 Taro 和 Vue 写了一个微信小程序'
date: 2020-08-05
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- programming
tags:
- wechat
meta:
  _edit_last: '1'
permalink: "/a-wechat-mini-app-with-taro-vue"
comments: true
---

最近尝试写微信小程序，毕竟是现在的趋势。然后发现因为入场太晚，各种轮子已经造得遍地飞了。比如这里有一个框架，出自京东，叫做Taro，它的目的是写一份代码，就可以在诸如微信、支付宝、字节跳动（它家的什么app支持小程序？）等端作为小程序运行。

于是拿来试了以下。我本来只熟悉Vue的，这个Taro原生支持React，代码风格也都是React的样式。虽说现在3.0以上支持Vue了，可是要做的时候还是有一些转换成本。

然后框架本身也还存在一些bug，不过一次编写，多端运行还是挺有意思的。

项目地址：https://github.com/hankxdev/taro-v2ex

以下内容来自README：

### Taro + Taro-UI + Vue + V2EX API 多端小程序

如题，这是一个使用了这几个技术的练习项目。我是第一次使用Taro和写微信小程序。Taro官方有个[渐进式教程](https://taro-docs.jd.com/taro/docs/guide/)，使用的也是V2EX的API。
#### 技术栈：
- [Taro](https://github.com/NervJS/taro)
- [Taro-UI](https://github.com/NervJS/taro-ui)
- [Taro-ui-vue](http://taro-ui-vue.fontend.com/)
- [V2EX API](https://github.com/igaozp/V2EX-API)
- Vue
- Vuex
- SCSS
- Typescript

#### 本地运行和测试
- `yarn`
- `yarn dev:weapp`
- 因为调用了v2ex 的API，用自己的微信小程序ID的话，需要去后台设置一下域名白名单，否则 API 调用会失败。

#### 比教程多了一些的是：
- 代码完整。官方教程的代码比较零散，甚至有些跑不通。
- 用户详情页面和节点详情页面
- 全部使用真正的V2EX API 而不是使用自定义数据
- 自定义 Tabbar
- 使用了Taro-UI来做界面


#### 项目存在的问题：
以下是我知道的主要问题。大佬们如果发现新问题或者知道这些问题的答案，欢迎提 issues 或者 PR， 望不吝赐教。

- 几个页面在切换的时候并不会刷新。这里怀疑是Taro的bug，文档中写的 [onShow](https://nervjs.github.io/taro/docs/vue/#onshow-1) 方法并不能在页面显示的时候被成功调用。
- 不怎么好看。因为主要用来熟悉Taro以及微信小程序和多端小程序开发，因此并未在界面上花功夫，几乎没有怎么写样式。使用的全都是Taro-UI 默认的组件。
- 有点卡。一方面v2ex并未提供分页的API。有些 endpoints 诸如获得节点列表、帖子列表等，都是一大堆上千条数据一下子全返回。网络慢的时候导致卡顿更加明显。
- TypeScript 使用并不规范。我很少写 TypeScript。也一直懒得学，因此基本上都是用JavaScript 的写法在写 TypeScript。同样，写好或者学习 TypeScript 也并不是我写本项目的目的。略过。
- CustomTabBar 的实现并不规范。现在的做法是写一个 CustomTabBar, 然后放置进每个页面中。正确的做法应该是。
1. 在 `app.config.ts` 中的`tabList` 里，设置 `custom: true`
2. 在 `src` 目录下新建 `custome-tab-bar` 文件夹
3. 在 `custome-tab-bar` 下面添加 `index.js`,`index.wxml`, `index.wxss` 来自定义 tabbar 的样式和行为。 需要注意的是，这里不能直接写 `index.vue`，编译不出来的。



![hot](https://github.com/hankxdev/taro-v2ex/raw/master/readme/hot.png)
