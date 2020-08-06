---
layout: post
title: 'how to use jQuery with TypeScript'
date: 2020-08-06
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- programming
tags:
- TypeScript
meta:
  _edit_last: '1'
permalink: "/how-to-use-jquery-with-typescript"
comments: true
---

It's 2020, why do you still need to use jQuery?

Yeah, jQuery has 53.8k stars on Github. And still, there are more than 97% of websites are using it.

Even if you don't want to use it in your fancy project. It's still a good choice to use it when you are building a demo, prototype, or some small side project. I mean, when you are configuring your fancy project with wepack, react/vue/angular, babel, I already have done a small page which can send request to the API and show the result on the page.

Anyway, if you want to use jQuery with TypeScript. Here are the steps that you need to do.

#### add jquery

```bash
yarn add jquery
```

### add jquery types

this will suppress VS Code complains that it can not find jquery types

```bash
yarn add @types/jquery
```

### config tsconfig.json to suppress another warning message 

> can only be default-imported using the 'allowSyntheticDefaultImports' flagts(1259)
> index.d.ts(35, 1): This module is declared with using 'export =', and can only be used with a default import when using the 'allowSyntheticDefaultImports' flag.

goto your `tsconfig.json` file, add one line in your the `compilerOptions` block. if you don't have this tsconfig file in your project's root folder, then create one.

```json
"allowSyntheticDefaultImports": true,
```

Then you can use jquery in your ts file like this:

```javascript
import $ from 'jquery'

$.ajax().then().catch().finnally()
```
