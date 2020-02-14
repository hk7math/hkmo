---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "JS | 位元運算 Bitwise Operator"
subtitle: ""
summary: ""
authors: []
tags: ["Javascript", "數學 Math"]
categories: []
date: 2020-02-14T10:52:38+08:00
lastmod: 2020-14-02T10:52:38+08:00
featured: false
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []
---
The following is my solution regarding a CodeSignal Problem [addTwoDigits](https://app.codesignal.com/challenge/BRW53NHcPd238GxxB)

1st Draft (61 Chars) makes use of reduce
```javascript
addTwoDigits=n=>
  (""+n).split("").reduce((x,y)=>
    x+Number(y)
  ,0)
```

2nd Draft (49 Chars) deploys a recursive skill
```javascript
f = addTwoDigits = n => n<10 
  ? n
  : n%10 + f(Math.floor(n/10))
```

It turns out I ignored the constraints that the number has only 2 digits... but I learnt a new trick from the best solutionsss
```javascript
addTwoDigits = n => n%10 + n/10|0
```

After some [researches](https://stackoverflow.com/questions/654057/where-would-i-use-a-bitwise-operator-in-javascript), there are quite some magical uses for the | bitwise operator, e.g. x|0 can function as:

1. Math.floor(x) for postive x

2. parseInt(x) for string x

3. 0 for many special x (NaN, Infinity, null, undefined, [], {} ...)