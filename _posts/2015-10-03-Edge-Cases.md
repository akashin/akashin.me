---
layout: post
title:  "Edge Cases"
date:   2015-02-17 11:04:01
categories: post
---
Some edge cases and cautionary examples on using Markdown for writing content using this theme. In particular, list syntax can really knot things up.
<!--more-->

* Table of contents
{:toc}

### Mathjax improperly parsing greater and less than and ampersands inside blocks

{% math %}
D = \left(\begin{matrix}
  1 & -1 & & & & \\
  &    & \cdots &   & \\
  &    &        & 1 & -1
\end{matrix}
\right)
{% endmath %}


Random additional math

{% math %}
    \sum_{i = 1}^{n} i = \frac{n(n + 1)}{2}
{% endmath %}

{% fullwidth "assets/img/rhino.png" "Tufte's pet rhino (via <a href=\"//www.edwardtufte.com/tufte/\">Edward Tufte</a>)" %}
