---
layout: post
title: "Neat tmux alias"
date:   2017-06-25 12:00:00
categories: post
---

{% newthought "Trying to streamline" %} my workflow with [tmux](https://danielmiessler.com/study/tmux/)
I've built a useful bash alias **`tmx`**.
This alias takes a single argument - name of the session, and connects to the session if it already
exists, or creates a new session with this name. The motivation behind it is that it is shorter
(no need to remember and type `attach -t` or `new-session -s`), and also involves less cognitive
overhead (no conditional thinking).

Here is a snippet of shell code that you can add to your `.bashrc`/`.zshrc`/etc:
```bash
function tmx {
    name=$1
    if tmux list-sessions | grep -q "^${name}:"; then
        tmux attach -t "${name}"
    else
        tmux new-session -s "${name}"
    fi
}
```

First, we list all available tmux sessions and then use `grep` to look for the one, that has provided name.
If this search succeeds, the return code of `grep` is zero and we go to the first branch of the `if`
statement and connect to the existing session.
Otherwise, the return code is non-zero and we go to the second branch that creates a new session.

There is one tricky corner-case that needs to be considered, and I leave it to readers to
discover it :) {% sidenote "1" "what happens if there are currently no sessions?" %}

With this alias, connecting to a tmux session *Blog* is as easy as:
```bash
> tmx Blog
```

One additional big plus of this alias comes if you're using tmux over ssh connection (and who doesn't? :)).
To connect or create a tmux session *Blog* on the remote machine you can use:

```bash
> ssh <hostname> -t tmx Blog
```

For this to work don't forget to put `tmx` alias to the top of `.bashrc` if you're using bash or to `.zshenv` if you're using zsh.

Next step would be to extend `tmx` to take arbitrary number of arguments, but honestly, I haven't yet encountered situation when I need it.

This and other useful aliases that I'm using everyday can be found in my [dotfiles](https://github.com/akashin/dotfiles/blob/master/zsh/zshrc.symlink) repository on Github.

Thank you for reading, stay tuned!
