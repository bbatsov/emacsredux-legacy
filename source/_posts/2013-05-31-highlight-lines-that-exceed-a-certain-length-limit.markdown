---
layout: post
title: "Highlight lines that exceed a certain length limit"
date: 2013-05-31 15:18
comments: true
categories:
- Utilities
---

When you're writing code you usually have to take into account the
programming language's convention for maximum line length. Most
programming languages urge hackers to keep line length under 80
characters(although in recent years it has often been argued that such
rules should be relaxed to 100-120 characters, given the state of
current computer displays).

There are many ways to highlight lines that exceed a certain length in
Emacs, but I find one to be particularly elegant - the use of the
built-in `whitespace-mode`. Most people use `whitespace-mode` to
visualize spaces, tabs and trailing whitespace, but it can actually do
a bit more that that. Here's the magic config:

``` cl
(require 'whitespace)
(setq whitespace-line-column 80) ;; limit line length
(setq whitespace-style '(lines-tail))

(add-hook 'prog-mode-hook 'whitespace-mode)
```

The above snippet will enable `whitespace-mode` only in major modes
for programming. If you want to enable `whitespace-mode` everywhere
you might want to do this instead:

``` cl
(global-whitespace-mode +1)
```

Here's the result:

{% img /images/articles/long-lines.png %}

It will probably come as no surprise that this functionality is
enabled out-of-the-box in [Prelude](https://github.com/bbatsov/prelude)
