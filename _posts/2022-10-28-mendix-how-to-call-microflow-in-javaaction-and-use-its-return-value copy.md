---
layout: post
title: 'Mendix: How to call Microflow in Java Action and use its return value'
type: post
date: 2022-10-28
comments: true
categories:
- programming
tags:
- Mendix
- LowCode
---


After you dive into Mendix for a longer time, you would find yourself writing java code now and then. Don't worry, good news is that you don't need to write a lot of java code, Mendix is Low Code anyway.

In Mendix, java code is been called Java Action.

And you will also find you have to call Microflow in your java code. And in the latest version, approx Mendix 8.1, calling a Microflow can be in this way:

```java
com.mendix.core.Core.microflowCall("YourModule.SUB_ShowMessage")
.inTransaction(true)
.withParam("Name", "Hank")
.withParam("Message", "Just another developer")
.execute(this.getContext());
```

This will call your Microflow `SUB_ShowMessage` in your `YourModule` module, passing **Name** and **Message** to it.

Sometimes if your Microflow has too many parameters, clearly chaining too many **withParam** is not a proper way. You can use **HashMap**

```java
java.util.Map<String, Object> params = new java.util.HashMap<>();
params.put("Name", "Hank");
params.put("Message", "Just another developer");
params.put("note", "This seems also a lot of code")
com.mendix.core.Core.microflowCall("YourModule.SUB_ShowMessage")
.inTransaction(true)
.withParams(params)
.execute(this.getContext());
```

You can see there is no return value in the Microflow or you don't want/need to use the return value of it.

But what about you want to use it?

If your Microflow returns a simple value, like *String*, *Long/Integer*, *Boolean*, then it's easy, just assign it to your Java variable:
```java
Boolean mfValue = com.mendix.core.Core.microflowCall("YourModule.SUB_ShowMessageWithReturnValue")
.inTransaction(true)
.withParam("Name", "Hank")
.withParam("Message", "Just another developer")
.execute(this.getContext());

// then you can use the mfValue
``` 

Well, this seems easy, what if the Microflow returns an object? 

When a Microflow returns an Object, it will lose its Entity definition and returns an interface  **IMendixObject*. You can not use it without init it with the corresponding Entity. Let's say, it returns a **System.User* entity, then you will do this to use it:
```java
// returns IMendixObject 
IMendixObject mendixObj = com.mendix.core.Core.microflowCall("YourModule.SUB_ShowMessageWithReturnValue")
.inTransaction(true)
.withParam("Name", "Hank")
.withParam("Message", "Just another developer")
.execute(this.getContext());

// init with Entity's init function 
  final User user = User.initialize(this.getContext(), mendixObj);
```

---EOF---