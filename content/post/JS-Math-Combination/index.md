---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "JS 組合算法 Combination Algorithm"
subtitle: ""
summary: ""
authors: []
tags: ["Javascript", "數學 Math"]
categories: []
date: 2020-01-15T00:48:47+08:00
lastmod: 2020-01-15T00:48:47+08:00
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

This is originally a post in [Dev.to](https://dev.to/hk7math/javascript-big-combination-problem-1lco)

A recent [CodeSignal Challenge](https://app.codesignal.com/challenge/a8GNsYr8FQxZmMhJj?solutionId=MZQa7pP2nzgzzoSev) was to calculate 1000C500 (mod 1e9+7) and I got defeated =(

All my trials exceeded the time limit.. Here is the best JS solution by [psr](https://app.codesignal.com/challenge/a8GNsYr8FQxZmMhJj?solutionId=MZQa7pP2nzgzzoSev)
, could anyone explain what happens in this line??? I learnt ES6 but got no idea about this syntax...
```javascript
f[o = n + 1/k] = o in f
```

Full solution for reference, please tell me to delete this if I violated any rule...
```javascript
f = countWays = (n, k) => f[o = n + 1/k] = o in f
    ? f[o]
    : k 
        ? n && (f(--n, k) + f(n, k - 1)) % (1e9 + 7)
        : 1
```

------

Thanks Barbar's comments in [StackOverflow](https://stackoverflow.com/questions/59775224/seeking-help-on-explanation-for-a-big-combination-algorithm/59789925#59789925), I understand the algorithm now.

I have rewritten the algorithm as follows: 

```javascript
f = nCk = (n, k) => {   //Declare both f and nCk as the same function
let o = n + 1/k         //o will be the key of function object f
f[o] = o in f           //Define f[o] based on a nested ternary expression
    ? f[o]              //Avoid recalculation if f has key o already 
    : k==0              //nC0 is always 1
        ? 1
        : n<k           //nCk is improper and assigned 0 if n<k
            ? 0
            : f(--n, k) //Do recursion nCk = (n-1)Ck + (n-1)C(k-1)
            + f(n, k - 1) 
return f[o]             //Done!
}
```

Here goes a walkthrough of 5C2
```
f(n,k)	n	k	o	f[o]
f(5,2)	5	2	5.5	f[5.5]=f(4,2)+f(4,1) //=10
f(4,2)	4	2	4.5	f[4.5]=f(3,2)+f(3,1) //=6
f(3,2)	3	2	3.5	f[3.5]=f(2,2)+f(2,1) //=3
f(2,2)	2	2	2.5	f[2.5]=f(1,2)+f(1,1) //=1
f(1,2)	1	2	1.5	f[1.5]=f(0,2)+f(0,1) //=0
f(0,2)	0	2	0.5	f[0.5]=0
f(0,1)	0	1	1	f[1]=0
f(1,1)	1	1	2	f[2]=f(0,1)+f(0,0) //=1
f(0,0)	0	0	Inf	f[Inf]=1 //Inf aka Infinity
f(2,1)	2	1	3	f[3]=f(1,1)+f(1,0) //=2
f(1,0)	1	0	Inf	f[Inf]=1
f(3,1)	3	1	4	f[4]=f(2,1)+f(2,0) //=3
f(n,0)	n	0	Inf	f[Inf]=1
f(4,1)	4	1	5	f[5]=f(3,1)+f(3,0) //=4
```

P.S. I got a few takeaways when investigating into this algorithm

1. Double declaration of function on the same line as a trick for recursion

2. Immediate use of a key with its value just assigned

3. Infinity can be used as a key of an object(!)

4. Syntax o in f checks if object f has the key o