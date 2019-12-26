---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "LaTeX 分行調試"
subtitle: ""
summary: ""
authors: []
tags: [LaTeX]
categories: []
date: 2019-12-26T11:43:00+08:00
lastmod: 2019-12-26T11:43:00+08:00
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

於 [Spectrum](https://spectrum.chat/academic/help/latex-align-environment-not-working~b69aa506-6167-4e62-8352-03fdeb650c91) 看到有人問如何在 Academic 中幫 LaTeX 排版，在[官方文檔](https://sourcethemes.com/academic/docs/writing-markdown-latex/#rm-latex-math)中其實有提及有關方法，但自己也花了些時間才弄清楚，特此記錄解決方法：


```
\begin{align}
    \begin{aligned}
        2x+3 &= 7 & 2x+3-3 &= 7-3 \\
        2x &= 4 & \frac{2x}2 &= \frac42\\
        x &= 2
    \end{aligned}
\end{align}
```

$$
\begin{align}
    \begin{aligned}
        2x+3 &= 7 & 2x+3-3 &= 7-3 \\
        2x &= 4 & \frac{2x}2 &= \frac42\\
        x &= 2
    \end{aligned}
\end{align}
$$

```
\begin{align}
    \begin{aligned}
        2x+3 &= 7 & 2x+3-3 &= 7-3 \\\\
        2x &= 4 & \frac{2x}2 &= \frac42\\\\
        x &= 2
    \end{aligned}
\end{align}
```

\begin{align}
    \begin{aligned}
        2x+3 &= 7 & 2x+3-3 &= 7-3 \\\\
        2x &= 4 & \frac{2x}2 &= \frac42\\\\
        x &= 2
    \end{aligned}
\end{align}