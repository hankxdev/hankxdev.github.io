---
layout: post
title: 'How to fix: Enzyme expects an adapter to be configured'
date: 2021-01-13
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- programming
- front-end
tags:
- react
- jest
meta:
  _edit_last: '1'
permalink: "/how-ro-fix-enzyme-expects-an-adapter-to-be-configured"
comments: true
---


Working on updating a legacy React project. It's still using React 8 and Node 7.9, I'd like to upgrate it
to the latest React and Node.

The upgrading process was boring and straight forward, I just upgrade the dependencies and fix those broken changes in some
dependencies, luckily most of them do need any chang.

#### Problem
But when I run jest test, there is an error popup in almost every test file:

```
Enzyme Internal Error: Enzyme expects an adapter to be configured, but found none. To
configure an adapter, you should call `Enzyme.configure({ adapter: new Adapter() })` 
before using any of Enzyme's top level APIs, where `Adapter` is the adapter 
corresponding to the library currently being tested. For example:

          import Adapter from 'enzyme-adapter-react-16';
```

Searched a bit, it looks like after Enzyme 3.0 and React15, you have to configure the `Adapter` to run the tests.

#### Solution
To fix it is very simple, just put these lines on the top of your test file:
```
import { configure } from 'enzyme';
import Adapter from 'enzyme-adapter-react-15';

configure({ adapter: new Adapter() });
```

While `enzyme-adapter-react-15` is also needed, you will need to use correct version per your react version.

But, what if your project is very large, it has like more than 30 test files, is it mean that you will need to 
put these line on top of every of your test file?

Of course no, here is what you should do.

- create a js file, name it as `jestConfig.js` or any name you think is best. put it in any path in your 
project.
- either create a `jest.config.js` in your project root or a block in `package.json` file
- put/append these content into it:


```
 "jest": {
    // ... other jest configrations
    "setupFilesAfterEnv": ["<rootDir>/path/to/your/jestConfig.js"],
  }
```

Notice that some tutorial might suggest you to do this with old Enzyme version
```
 "jest": {
    // ... other jest configrations
    "setupTestFrameworkScriptFile": "<rootDir>/path/to/your/jestConfig.js"
  }
```

In newer version the key has been changed from `setupTestFrameworkScriptFile` to `setupFilesAfterEnv`, and 
you can use multiple config file since it now uses array as value.

#### what about React 17

While the most recent official `ezyme-adapter-react` is for 16, the 17 is not surpported yet, so if you 
are using React 17, here is another unofficial package you can use [@wojtekmaj/enzyme-adapter-react-17](https://www.npmjs.com/package/@wojtekmaj/enzyme-adapter-react-17)

It has more than 6k downloads every week now, seems reliable.
















