---
layout: post
usemathjax: true
title: Metric Spaces - The Basics
description: What are metric spaces, and why should I care?
summary: Motivation and introduction for metric spaces, and a few fun examples.
tags: [geometry]
---

## Intro

In my senior year of college, I took a course on Euclidean and non-Euclidean Geometry.[^1] Euclidean geometry is what we normally think of when doing geometry. Here it is, visually.

![euclidean geometry]({{ site.baseurl }}/assets/metric-spaces/euclidean.png)

Tha angles of a triangle sum to 180 degrees, and the angles of the circle sum to $$2\pi$$ radians. Parallel lines never meet, and the "direct path" is the shortest.

However, other perfectly valid models of geometry exist and are collectively referred to as "non-Euclidean". The first non-Euclidean geometry we studied was Elliptic geometry, which can be thought of as happening on the surface of a sphere. I've illustrated this below using the same objects from the first picture.

![elliptic geometry]({{ site.baseurl }}/assets/metric-spaces/elliptic.png)

Intuitively, these objects are stretched over the surface of the sphere, so we get larger angles, and lines will always converge.[^2]

The final geometry we discussed was Hyperbolic geometry, which can be thought of happening on a saddle.

![hyperbolic geometry]({{ site.baseurl }}/assets/metric-spaces/hyperbolic.png)

Again, the shape of the space changes the properties of our normal objects like triangles, circles, and parallel lines.

In the course, we discussed the differences between these geometries through their treatment of parallel lines. As we know, in Euclidean geometry parallel lines stay the same distance from each other. We can see that in Elliptic geometry they converge, and in Hyperbolic geometry they diverge.

While this is an interesting way of studying the differences, I wasn't totally satisfied. I enjoy working with things in an algebraic way, and after some research, I found the algebraic generalization of these geometries: **Metric Spaces**.

## What's a Metric Space?

A Metric Space is a mathematical object with two parts. First, a set $$M$$. Commonly, this will be a set of vectors, but it could also comprised of functions or even strings.

Second, we need a _metric_ $$d(a, b): M \times M \rightarrow \mathcal{R}$$, or a distance that we can use to compare items from these sets. This metric has to follow a few axioms:

1. $$d(x, y) = 0 \iff x = y$$
2. $$d(x, y) = d(y, x)$$
3. $$d(x, z) \leq d(x, y) + d(y, z)$$

In plain English, that is

1. A point has distance 0 from itself.
2. Two points have the same distance from each other.
3. A direct path will always have the shortest distance. This expression is also known as the Triangle Inequlity.

These are all reasonable requirements for a distance function, and it's not too hard to show that normal Euclidean distance ($$d_e (a, b) = \sqrt{(a_x - b_x)^2 + (a_y - b_y)^2}$$ in the 2d plane) follows all these rules. Try it!

From these axioms, we can derive that $$d(x, y) \geq 0$$ in just a few steps. I also reccomend that you try showing this!

We can also define Metrics for Elliptic[^3] and Hyperbolic[^4] geometry, but the definitions are hard to parse and I'd like to focus on other things. Follow the links in the footnotes for good explorations of their metrics.

## Fun Metric Spaces

### Manhattan Distance / Taxicab Geometry

This metric comes up from time to time in Computer Science. The idea is to imagine the coordinate plane as a city, where you can't cut through blocks. In order to get from $$(0, 0)$$ to $$(1, 1)$$, we have to go up and to the left in some order.

Formally speaking, for $$p = (p_1, p_2), q = (q_1, q_2), p, q \in \mathbb{Z}$$, we define $$d_{\text{manhattan}}(p, q) = \mid p_1 - q_1 \mid + \mid p_2 - q_2 \mid$$.

Let's get visual.

![manhattan disance]({{ site.baseurl }}/assets/metric-spaces/manhattan1.png)

There are plenty of routes from $$(1, 1)$$ to $$(3, 3)$$, all with distance 4. I've shown three of them above, but there are plenty more. This reveals an interesting property: unlike Euclidean geometry there is no unique shortest path.

Circles are usually defined as the set of all points of distance $$r$$ from some center point. Let's look at circles here:

![manhattan circle]({{ site.baseurl }}/assets/metric-spaces/manhattan_circle.png)

Circles look a bit different! If we're using the city example, we can think of a circle as all the intersections you can get to by walking $$r$$ blocks.

### Post Office Metric

The idea for this metric is that all paths must pass through some central source, like a letter going through the post office. This is sometimes called the British Rail Metric (or the equivalent for various different countries/cities).

Formally, for $$p = (p_1, p_2), q = (q_1, q_2)$$, we define $$d_{\text{po}}(p, q) = \mid p_1 + q_1 \mid + \mid p_2 + q_2 \mid$$.

Let's see how paths differ from Euclidean geometry.

![post office path]({{ site.baseurl }}/assets/metric-spaces/po_path.jpg)

Clearly paths here are a lot longer. Let's ponder this while we examine circles. We'll start with three unit circles centered about different points.

![post office circle]({{ site.baseurl }}/assets/metric-spaces/po_circle_1.png)

Unlike Euclidean geometry, objects change based on their position relative to the origin. This should be clear from the metric, but might make more sense visually. Let's try one more example in this metric:

![post office circle]({{ site.baseurl }}/assets/metric-spaces/po_circle_2.jpg)

With this, we just demonstrated that even given two very different radii, by centering about different points, we can get equal circles.

So in both of the metric spaces we've examined, we've shown that objects that are unique in Euclidean geometry aren't always unique in other metrics.

### Levenshtein distance

As a final example, we'll consider something completely different. As mentioned above we can also define metrics for other objects, such as strings. The concept of distance between strings comes up in in certain areas Computer Science and Linguistics. One way of measuring distance is the _Levenshtein_ distance, which is the minimum number of single-character edits (addition, substitutions, or deletions) required to transform one string into the other. More formally, for strings $$a, b$$, take $$\text{lev}_{a, b}(\mid a \mid, \mid b \mid)$$, where

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

If we look at this for a bit, we can figure out that it follows all of our axioms. Despite not being vectors in the coordinate plane like we're used to, we can still define a sense of distance that makes a lot of sense.

As with the previous metrics, we'll go through an example, and ponder what a circle becomes in this metric.

![Levenshtein distance example]({{ site.baseurl }}/assets/metric-spaces/l-dist.jpg)

The two

If we keep the idea that a circle is the set of all things that are distance $$r$$ from some center object, then we get a very natural definition of a circle being the set of all strings one edit away from a starting string. If _cat_ is our starting point, it's circle would contain a lot of strings, including _at_, _cats_, _aat_, _bat_, _ecat_, and so on.

### Normed Spaces

One important complement to Euclidean Distance and Manahttan distance is Chebyshev distance, defined as $$d_c(x, y) = \text{max}_{i} (\mid x_i - y_i \mid)$$. These three distances correspond to common _norms_[^5] - metrics on vectors that have to follow more rules. These extra rules give more structure to the resulting metric space, and we call them _normed vector spaces_.

## Why we care about Metric Spaces

These spaces are interesting in their own right, and we can come up with a lot of fun examples. But how do they fit into the bigger picture of math?

As it turns out, by generalizing the idea of distance as a metric, we also get a generalized form of convergence[^6]. This lets us take a lot of ideas from calculus/analysis and apply them to other things. This field is called Differental Geometry.

From a Metric Space, you can easily define a Topological Space[^7]. I don't have enough experience with Topology to dive deeper here, but it seems to be an interesting connection if you want to dive in to Topology.

### Footnotes

[^1]: We followed "The Four Pillars of Geometry" by John Stillwell.
[^2]: In Elliptic/Spherical Geometry, lines are defined as _Great Circles_ along the circle. A Great Circle is a _section_ of a sphere that contains its diameter. An example would be the equator.
[^3]: [https://mphitchman.com/geometry/section5-3.html](https://mphitchman.com/geometry/section5-3.html)
[^4]: [https://mphitchman.com/geometry/section6-3.html](https://mphitchman.com/geometry/section6-3.html)
[^5]: https://en.wikipedia.org/wiki/Norm_(mathematics)
[^6]: Convergence being when two values are arbitrarily close to each other.
[^7]: [https://en.wikipedia.org/wiki/Topological_space](https://en.wikipedia.org/wiki/Topological_space)
