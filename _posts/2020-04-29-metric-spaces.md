---
layout: post
usemathjax: true
title: Metric Spaces
description: What are metric spaces, and why should I care?
summary: Motivation and introduction for metric spaces, and a few fun examples.
tags: [geometry]
---

## Intro

In my senior year of college, I took a class[^1] on Euclidean and non-Euclidean Geometry. Euclidean geometry, pictured below, is what we normally think of when doing geometry.

(IMAGE HERE)

However, other perfectly valid models of geometry exist, and are collectively referred to as "non-Euclidean". In the course I was in, the first such geometry was Elliptic geometry, which can be thought of as happening on the surface of a sphere. I've illustrated before how that looks, using the same objects as the first picture.

(IMAGE HERE)

And to complete the geometry we dicussed in my course, we have hyperbolic geometry, again, drawn below.

(IMAGE HERE)

In this post, we're not going to get deep into these. I've tried to include some links at the bottom that seem like good resources, if you're interested in learning more.

In the course, we discussed the differences between these geometries through their treatment of parallel lines. As we know, in Euclidean Geometry, parallel lines stay the same distance from each other. We can see that in elliptic, they converge, and in hyperbolic they diverge.

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
3. A direct path will always have the shortest distance. This expression is also known as the triangle inequlity.

These are all reasonable requirements for a distance function, and it's not too hard to show that normal Euclidean distance ($$d_e (a, b) = \sqrt{(a_x - b_x)^2 + (a_y - b_y)^2}$$ in the 2d plane) meets all these rules. Try it!

From these axioms, we can derivate that $$d(x, y) \geq 0$$ in just a few steps. I also reccomend that you try showing this!

(Might include the metrics for ellip/hyperb, but they're kinda obtuse? Or is it that they're unique because of parallel lines, rather than metrics?)[^2],[^3]

## Fun Metric Spaces

### Manhattan Distance / Taxicab Geometry

This is a metric that comes up from time to time in computer science. The idea is to imagine the coordinate plane as a city, where you can't cut through alleys/buildings. In order to get from (0, 0) to (1, 1), we have to go up, and to the left in some order.

In a formula, this is for $$p = (p_1, p_2), q = (q_1, q_2)$$, we have the formula $$d_m(p, q) = \mid p_1 - q_1 \mid + \mid p_2 - q_2 \mid$$.

Here's some visuals:

(SOME IMAGES HERE)

### Post Office Metric

The idea for this metric is that all paths must pass through some central source. This is sometimes called the British Rail Metric (or the equivalent for various different countries/cities).

In a formula, this is for $$p = (p_1, p_2), q = (q_1, q_2)$$, we have the formula $$d_m(p, q) = \mid p_1 + q_1 \mid + \mid p_2 + q_2 \mid$$.

Here's some visuals:

(SOME IMAGES HERE)

## Why we care about Metric Spaces

- More general thing of topology, I guess?
- Generalizes convergence and distance.

### Sources

- a
- b

### Footnotes

[^1]: We followed "The Four Pillars of Geometry" by John Stillwell
[^2]: [https://mphitchman.com/geometry/section5-3.html](https://mphitchman.com/geometry/section5-3.html)
[^3]: [https://mphitchman.com/geometry/section6-3.html](https://mphitchman.com/geometry/section6-3.html)