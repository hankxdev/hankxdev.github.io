---
layout: post
title: 'Enable HTTPS on local, even with a customizable domain'
date: 2021-09-14
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- programming
- tips
tags:
- https
- web development
permalink: "/2021-09-14-enable-https-and-domain-on-local"
comments: true
---

Normally, when you're debugging your web app on local, you can access it with either `http://localhost:PORT` or `http://127.0.0.1:POST`.

The `POST` might be `8080` or `3000` or what's ever.

But sometimes you might need to access your local web app with `https`, like `https://localhost:8080`. So you search online
with `local https`, tons of posts/tutorials teach you how to generate self-signed SSL certificate and assign to your localhost.

As an app developer, you might feel it's too complicated and don't want to spend half an hour on it.

So here I found the easiest way to achieve this with just one small tool and 1 line command, without changing anything in your actual app.

This tool is (**local-ssl-proxy**)[https://www.npmjs.com/package/local-ssl-proxy] , it is an open sourced npm package. so you can just install it by running
```shell
npm install -g local-ssl-proxy
```
Then you can just access your local web app with this command(let's assume the app is running on 8080 port): 
```
local-ssl-proxy -s 8081 -t 8080
```

In this way, your web app's url will be `https://localhost:8081`. And you can still access your app from the original http url and port.

The **-s** is the port that the app will be proxies to, the **8080** is the actual port your app running on. 

### what's more?

If you don't like to use the localhost, or you have to assign as domain to your local app. you can simply make it with 2 more steps.

- add a line in your computer's **hosts** file.
  - if you are on Windows, the hosts file's path is `c:\windows\system32\drivers\etc\hosts`
  - on Mac and Linux the path simply is `/etc/hosts`
  - you need Admin/root privilege to modify it
  
  The line would be 
  ```shell
  127.0.0.1 YOUR_DOMAIN
  ```
  The `YOUR_DOMAIN` can be anything, you don't even register the domain, because it only works on your computer.

  But don't use some famous one like youtube.com or google.com, some browser would block it.

  
  Let's say we use the `hank.momane` in below example.

- Then run the proxy like this:
```shell
local-ssl-proxy -s 443 -t 8080 -n hank.momane
```  

So by using the SSL port **443** and an extra parameter **-n**, now you can access your
app via `https://hank.momane`.


