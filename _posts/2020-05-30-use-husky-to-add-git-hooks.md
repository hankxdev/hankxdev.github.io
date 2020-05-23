---
layout: post
title: Use Husky to manage git hooks
date: 2020-05-20
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- programming
tags:
- javascript
- git
meta:
  _edit_last: '1'
permalink: "/use-husky-to-manage-git-hooks"
comments: true
---

[Git hooks](https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks) is a powerful tool to make your life easier.

 It fires off custom scripts when certain important actions occur. one common scene like:  you want to lint your code every time when you commit
 changes, so that your code has a good style and following your team's code specification. Or you want to run test before pushing your code/
 
 >Like many other Version Control Systems, Git has a way to fire off custom scripts when certain important actions occur. There are two groups of these hooks: client-side and server-side. Client-side hooks are triggered by operations such as committing and merging, while server-side hooks run on network operations such as receiving pushed commits. You can use these hooks for all sorts of reasons.
 
 With git hooks, you can make these actions automatically.
 
 While [__husky__](https://www.npmjs.com/package/husky) is a tool to make Git hooks easier to use. To use it is very easy
 
 First you install it as a development dependency with npm:
 
 ```bash
npm install husky --save-dev
```
 
 OR __yarn__:
```bash
yarn add husky -D
``` 

Then in your `package.json` , add:
```json
{
  "husky": {
    "hooks": {
      "pre-commit": "yarn lint",
      "pre-push": "yarn test",
      "...": "..."
    }
  }
}
```

In the example, we added 2 hooks, `pre-commit` and `pre-push`, they are meant what they named.

- __pre-commit__ means, every time you run `git commit`, it will run `yarn lint` first, and commit the code if `yarn lint` passes without error.
- __pre-push__ run command `yarn test` when you run `git push`
- `yarn lint` and `yarn test` are commands that you define in your `scripts` in package.json. normally those commands that you runs manually, like
`yarn start` or `yarn dev`, etc. you can add any command you want and run the, in the hooks.

Pretty straight forward and easy :)


