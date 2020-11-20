# evil-tmux-navigator

A fork of a fork of a port of
[vim-tmux-navigator](https://github.com/christoomey/vim-tmux-navigator).
The code is identical to the upstream fork (unless I've let it get out of date);
I just corrected errors in the README.

This is meant to work with [evil](http://www.emacswiki.org/emacs/Evil)
which gives you vim bindings in emacs.

Install it with something like

```elisp
(straight-use-package
  '(evil-tmux-navigator :type git :host github :repo "ambirdsall/evil-tmux-navigator"))
```

or however you'd like, and make sure to make some keybindings for it. I use doom, so:

```elisp
(map!
 :ni "C-h" #'evil-tmux-navigator-left
 :ni "C-j" #'evil-tmux-navigator-down
 :ni "C-k" #'evil-tmux-navigator-up
 :ni "C-l" #'evil-tmux-navigator-right)
```

You also have to setup commands in your `~/.tmux.conf`:

```
bind -n C-h run "(tmux display-message -p '#{pane_current_command}' | grep -iqE '(^|\/)vim(diff)?$|emacs.*$' && tmux send-keys C-h) || tmux select-pane -L"
bind -n C-j run "(tmux display-message -p '#{pane_current_command}' | grep -iqE '(^|\/)vim(diff)?$|emacs.*$' && tmux send-keys C-j) || tmux select-pane -D"
bind -n C-k run "(tmux display-message -p '#{pane_current_command}' | grep -iqE '(^|\/)vim(diff)?$|emacs.*$' && tmux send-keys C-k) || tmux select-pane -U"
bind -n C-l run "(tmux display-message -p '#{pane_current_command}' | grep -iqE '(^|\/)vim(diff)?$|emacs.*$' && tmux send-keys C-l) || tmux select-pane -R"
```

#### Troubleshooting

Good luck!
