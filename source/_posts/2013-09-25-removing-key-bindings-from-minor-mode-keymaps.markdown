---
layout: post
title: "Removing key bindings from minor mode keymaps"
date: 2013-09-25 12:26
comments: true
categories:
- Modes
---

Often minor modes don't respect standard keybinding conventions and
use some user reserved keys (like `C-c a`). Occasionally two minor
modes would have conflicting keybindings or a minor mode would
keybindings conflicting with a major mode. I guess you can imagine
similar problems. Dealing with them is fairly straight-forward - we
have to either unbind or rebind the offending binding:

``` cl
;; remove keybinding
(define-key minor-mode-map (kbd "C-c c") nil)

;; change keybinding
(define-key minor-mode-map (kbd "C-c c") (kbd "C-c C-c"))
```

Generally speaking you can use `define-key` to alter the keymap of a
major mode as well, but those are rarely offenders when it comes to
picking appropriate keybindings for their keymaps.

Normally you'd want to invoke the above code right after the related
minor (or major) mode is loaded:

``` cl
(eval-after-load "minor-mode"
  '(define-key minor-mode-map (kbd "C-c c") nil))
```

I'm not sure if one can have a minor mode having different keymaps in
different major modes. I can certainly imagine situations when this
would be useful. If someone knows how this could be done - please,
share this knowledge in the comments.
