---
layout: post
usemathjax: true
title: WIP - Metric Spaces
description: What are metric spaces, and why should I care?
summary: Motivation and introduction for metric spaces, and a few fun examples.
tags: [geometry]
---

## Intro

In my senior year of college, I took a course on Euclidean and non-Euclidean Geometry.[^1] Euclidean geometry, pictured below, is what we normally think of when doing geometry.

![euclidean geometry]({{ site.baseurl }}/assets/metric-spaces/euclidean.png)

However, other perfectly valid models of geometry exist, and are collectively referred to as "non-Euclidean". In the course I was in, the first such geometry was Elliptic geometry, which can be thought of as happening on the surface of a sphere. I've illustrated below how that looks, using the same objects as the first picture.

![elliptic geometry]({{ site.url }}/assets/metric-spaces/elliptic.png)

And to complete the geometries we dicussed in my course, we have Hyperbolic geometry, again, drawn below.

![hyperbolic geometry]({{ site.url }}/assets/metric-spaces/hyperbolic.png)

In this post, we're not going to get deep into these. I've tried to include some links at the bottom that seem like good resources, if you're interested in learning more.

In the course, we discussed the differences between these geometries through their treatment of parallel lines. As we know, in Euclidean geometry, parallel lines stay the same distance from each other. We can see that in Elliptic, they converge, and in Hyperbolic they diverge.

While this is an interesting way of studying the differences, I wasn't totally satisfied. I enjoy working with things in an algebraic way, and after some research, I found the algebraic generalization of these geometries: **Metric Spaces**.

## What's a Metric Space?

A Metric Space is a mathematical object with two parts. First, a set $$M$$. Commonly, this will be a set of vectors, but it could also comprised of functions, or even strings.

Second, we need a _metric_ $$d(a, b): M \times M \rightarrow \mathcal{R}$$, or a distance that we can use to compare items from these sets. This metric has to follow a few axioms:

1. $$d(x, y) = 0 \iff x = y$$
2. $$d(x, y) = d(y, x)$$
3. $$d(x, z) \leq d(x, y) + d(y, z)$$

In plain english, that is

1. A point has distance 0 from itself.
2. Two points have the same distance from each other.
3. A direct path will always have the shortest distance. This expression is also known as the Triangle Inequlity.

These are all reasonable requirements for a distance function, and it's not too hard to show that normal Euclidean distance ($$d_e (a, b) = \sqrt{(a_x - b_x)^2 + (a_y - b_y)^2}$$ in the 2d plane) meets all these rules. Try it!

From these axioms, we can derive that $$d(x, y) \geq 0$$ in just a few steps. I also reccomend that you try showing this!

We can also define Metrics for Elliptic[^2] and Hyperbolic[^3] geometry, but the definitions are hard to parse and I'd like to focus on other things. Follow the links in the footnotes for good explorations of their metrics.

## Fun Metric Spaces

### Manhattan Distance / Taxicab Geometry

This is a metric that comes up from time to time in computer science. The idea is to imagine the coordinate plane as a city, where you can't cut through alleys/buildings. In order to get from (0, 0) to (1, 1), we have to go up, and to the left in some order.

Putting this as a formula, for $$p = (p_1, p_2), q = (q_1, q_2), p, q \in \mathbb{Z}$$, we have the metric $$d_m(p, q) = \mid p_1 - q_1 \mid + \mid p_2 - q_2 \mid$$.

Let's get visual.

![manhattan disance]({{ site.baseurl }}/assets/metric-spaces/manhattan1.png)

To get from $$(1, 1)$$ to $$(3, 3)$$ we have plenty of choice for our route, all of which are the same distance of 4. This reveals an interesting property: unlike Euclidean geometry, we don't have a unique shortest path.

Circles also look a bit different! Intuitively, we can think of a circle as all the intersections you can get to by walking $$r$$ blocks.

![manhattan circle]({{ site.baseurl }}/assets/metric-spaces/manhattan_circle.png)

### Post Office Metric

The idea for this metric is that all paths must pass through some central source. This is sometimes called the British Rail Metric (or the equivalent for various different countries/cities).

Putting this as a formula, for $$p = (p_1, p_2), q = (q_1, q_2)$$, we have the metric $$d_m(p, q) = \mid p_1 + q_1 \mid + \mid p_2 + q_2 \mid$$.

Let's compare a Euclidean path with a path in this metric.

![post office path]({{ site.baseurl }}/assets/metric-spaces/po_path.jpg)

Clearly, paths here are a lot longer. If we turn our attention again to circles, we get some really interesting results.

![post office circle]({{ site.baseurl }}/assets/metric-spaces/po_circle_1.png)

In the picture above, I've drawn three circles, all of radius 1, centered about 3 different points.

![post office circle]({{ site.baseurl }}/assets/metric-spaces/po_circle_2.jpg)

With this, we just demonstrated that even given two very different radii, by centering about different points, we can get circles that can be considered equal.

With both of these Metrics, we've been able to find things like shortest paths and circles that are always unique in Euclidean geometry, but not in these other geometries.

### Levenshtein distance

As a final example, we'll consider something completely different. As mentioned above, we can also define metrics for other objects, such as strings. The concept of distance between strings comes up in in certain areas Computer Science and Linguistics. One way of measuring distance is the _Levenshtein_ distance, which is the minimum number of single-character edits (addition, substitutions, or deletions) required to transform one string into the other. More formally, for strings $$a, b$$, take $$\text{lev}_{a, b}(\mid a \mid, \mid b \mid)$$, where

$$
\text{lev}_{a,b}(i, j) = \begin{cases}
\text{max}(i, j) \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \text{if min}(i, j) = 0 \\
\text{min} \begin{cases}
\text{lev}_{a,b}(i - 1, j) + 1 \\
\text{lev}_{a,b}(i, j - 1) + 1 \\
\text{lev}_{a,b}(i - 1, j = 1) + 1_{a_i \neq b_j}\\
\end{cases} \text{otherwise}
\end{cases}
$$

If we look at this for a bit, we can figure out that it meets all of our axioms.

- example(s) and vague comment about how so wildly different than geometry yet still shares some notions
- "circle" could be all strings 1 edit away.

## Why we care about Metric Spaces

These spaces are interesting in their own right, and we can come up with a lot of fun examples. But how do they fit into the bigger picture of math?

As it turns out, by generalizing the idea of distance as a metric, we also get a generalized form of convergence[^4]. This lets us take a lot of ideas from calculus/analysis and apply them to other things. This field is called Differental Geometry.

From a Metric Space, you can easiliy define a Topological Space[^5]. I don't have enough experience with Topology to dive deeper here, but it seems to be an interesting connection if you want to dive in to Topology.

### Footnotes

[^1]: We followed "The Four Pillars of Geometry" by John Stillwell.
[^2]: [https://mphitchman.com/geometry/section5-3.html](https://mphitchman.com/geometry/section5-3.html)
[^3]: [https://mphitchman.com/geometry/section6-3.html](https://mphitchman.com/geometry/section6-3.html)
[^4]: Convergence being when two values are arbitrarily close to each other.
[^5]: [https://en.wikipedia.org/wiki/Topological_space](https://en.wikipedia.org/wiki/Topological_space)
