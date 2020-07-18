---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "FullStackOpen 4"
subtitle: ""
summary: ""
authors: []
tags: ["debug"]
categories: []
date: 2020-07-18T19:29:25+08:00
lastmod: 2020-07-18T19:29:25+08:00
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
Jest is timeout occasionally
![](/post/fullstackopen-4/error.jpg)

Reference: 
https://stackoverflow.com/questions/49603939/async-callback-was-not-invoked-within-the-5000ms-timeout-specified-by-jest-setti

Like+1 via Mongoose
Wrong
```javascript
blogsRouter.put('/:id', async (req, res) => {
  await Blog.findByIdAndUpdate(
    req.params.id, 
    {$inc: {'blog.likes' : 1}},
    {new: true},
  )
  res.status(202).end()
})
```

Correct
```javascript
blogsRouter.put('/:id', async (req, res) => {
  await Blog.findByIdAndUpdate(
    req.params.id, 
    {$inc: {likes : 1}},
    {new: true},
  )
  res.status(202).end()
})
```

Reference: 
https://docs.mongodb.com/manual/reference/operator/update/inc/#example