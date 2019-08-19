---
title: "Incrementality in software systems"
layout: post
---

I've been recently looking into a question of making machine learning
experimentation faster when it comes to the supporting software infrastructure.
Nowadays, researchers spend non-trivial amount of time waiting for their tools
to boot up even *before* the actual training of their model starts!
One typical example of the boot up sequence would be:
1. Acquire compute resources - e.g. get your cloud instance with enough resources up and running
2. Set up all dependencies of your project - e.g. `apt get install && pip install requirements.txt`
3. Upload the code of your model - e.g. `git clone myproject.git`
4. Start you execution environment - e.g. `python3 myproject/train.py`
5. Load up Python imports
6. Load the dataset from network
7. Execute a first useful line of your code

Not only that there is a lot of **incidental complexity** involved along the way, but it's also
painfully slow to repeat these steps every time you change a single line of your Python code.

Can we do better? For sure! First of all, you'll notice that there is no need to repeat steps
1, 2 and 3 unless you need to get another machine (e.g. to get a fancier GPU).
How about steps 4a and 4b? Can we avoid repeating them unless something about imports or dataset changes?
And if not, what makes them different from steps 1, 2 and 3 in that regard?

This all brings us to a question of **incrementality** - how do we design our systems in such way
that we don't need to do the same thing twice?

We are going to apply the following 3-step thinking process:

1. Generate a collection of concrete solutions (possibly partial) to incrementality problem
2. Try to fit describe all solutions with a general model
3. Use this model to fill the gaps and predict other possible solutions

Brute-force tree traversal:
- Checkpointing
- Backtracking
- Re-doing

Example solutions:
- Docker
- OverlayFS
- CRIU

{% mermaid %}
graph TD;
  A-->B;
  A-->C;
  B-->D;
  C-->D;
{% endmermaid %}
