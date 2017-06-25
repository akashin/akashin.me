---
layout: post
title: "Oh c'mon, Bash!"
date:   2017-06-21 12:00:00
categories: post
---

Trying to streamline my workflow with tmux I've found one more weirdness (surprise!) in Bash.

I was trying to build a command alias `tmx` that will take a single argument - name of the session, and connect to the session if it already exists, or create a new session with this name. This is both shorter (no need to type `attach -t`), and involves less cognitive overhead.

My first try was the following:

```bash
function tmx {
    name=$1
    if tmux list-sessions | grep -qv "^${name}:"; then
        tmux attach -t "${name}"
    else
        tmux new-session -s "${name}"
    fi
}
```
