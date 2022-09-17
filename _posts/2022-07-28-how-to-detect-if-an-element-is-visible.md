---
layout: post
title: 'JavaScript :How to detect if an element is visible'
type: post
comments: true
categories:
- programming
tags:
- JavaScript
- CSS
---


There are many ways to detect if an element is visible on page. like

```javascript
element.style.display !== none && element.visibility !== hidden
```


And what if you want to detect if an elemtn is in current viewport?

Easy, right? You just need to use `getBoundingClientRect`,  check if it's top and bottom are all in viewport:
```javascript
const position = element.getBoundingClientRect();

if(position.top >= 0 && position.bottom <= window.innerHeight) {
  //it's in
}

```

Or, there is another way, with `IntersectionObserver` [https://developer.mozilla.org/en-US/docs/Web/API/Intersection_Observer_API]. It can observe a target element and you can do something while the target elment enters or leaves viewport.

```javascript
var observer = new IntersectionObserver(function(entries) {
	if(entries[0].isIntersecting === true)
		console.log('Element has just become visible in screen');
}, { threshold: [1] });

observer.observe(element);
```

Note that the `threshold`, it is a number between 0 and 1, that represents the viewable area of the target element in the screen. For example, 0 represents no area of element is visible. A value of 0.10 represents about 10% area is viewable in screen. Value of 1 means element is fully viewable in screen.
You can even specify multiple thresholds.


Now think about another scenario, what if an element is visible, but it's parent is not visible? like:
```html
<div class="parent" style="disply: none">
  <div class="child" style="display: block">
    I'm not visible
  </div>
</div>
```

If you run `document.querySelector('child').style.display === 'block'`, you will get a **true**. 


How to fix this?

Well we can use `offsetParent`. The HTMLElement.offsetParent read-only property returns a reference to the element which is the closest (nearest in the containment hierarchy) positioned ancestor element.

so if `elment.offsetParent === null`, then we can tell that the `element` is not visible.

