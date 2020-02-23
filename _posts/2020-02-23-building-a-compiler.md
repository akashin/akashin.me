---
title: "Building a compiler"
layout: post
---

I finally decided to embark on the journey of building a real compiler to better understand
how various pieces work under the hood. I'm particularly interested in error reporting,
intermediate representation and code optimization.

I'll be following the guidance from [Crafting Interpreters](http://craftinginterpreters.com)
online book which so far proved to be quite easy to follow and full of fascinating facts from
programming history.

I'm planning not to follow the steps in the book too closely but rather pick the way that I
feel makes most sense to optimize my learning and venture deeper into the topics I consider
interesting. The first such change is using Python instead of Java for the interpreter
implementation. As far as I can tell, this shouldn't be a big deal, but I hope it will help me
to get a bit more familiar with Py3 and modern tooling like static type checking.

As I go through it, I want to share some of the detours I'll be taking on this blog, so stay tuned!
