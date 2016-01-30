---
layout: post
title: "super-save"
date: 2016-01-30 11:26
comments: true
categories:
- misc
---

A while back I wrote
[an article on saving buffers when they lose focus](http://batsov.com/articles/2012/03/08/emacs-tip-number-5-save-buffers-automatically-on-buffer-or-window-switch/).

Recently I've packaged (an improved version of) this functionality
into a tiny global minor mode called
[super-save](https://github.com/bbatsov/super-save).

The package is available on MELPA and MELPA Stable and enabling it is trivial:

``` cl
(super-save-mode +1)
```

If you're like me and don't care about the backups created by the
built-in `auto-save-mode`, you can disable it aftewards:

``` cl
(setq auto-save-default nil)
```

I wouldn't really recommend doing this until I've added a bit of
functionality to save the current buffer when you're not typing, but
the option obviously exists. I've been using Emacs for over 10 years
now and I've never needed the auto-created backups - I'm either very
lucky or this is less useful than it's supposed to be.
