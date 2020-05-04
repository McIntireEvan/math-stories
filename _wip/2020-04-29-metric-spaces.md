---
layout: post
usemathjax: true
title: Metric Spaces
description: What are metric spaces, and why should I care?
summary: Motivation and introduction for metric spaces, and a few fun examples.
tags: [geometry]
---

## Intro

In my senior year of college, I took a class on Euclidean and non-Euclidean Geometry. Euclidean geometry is what we normally think of when doing geometry.

(IMAGE HERE)

However, other valid models of geometry exist, and are collectively referred to as "non-Euclidean". An example is Elliptic Geometry, which can be thought of as happening on the surface of a sphere.

(IMAGE HERE)

While clearly different, these two models share a lot of ideas, and prompted the question "what's the generalization here?". After some digging, I found **Metric Spaces**.

## What's a Metric Space?

To construct a metric space, you need two things. First, a set $$M$$. Commonly, this will be a set of vectors, but it could also be comprised of functions, or even strings.

Second, we need a _metric_ $$d: M \times M \rightarrow \mathcal{R}$$, or a distance that we can use to compare items from these sets. This metric has to follow a few axioms:

1. $$d(x, y) = 0 \iff x = y$$
2. $$d(x, y) = d(y, x)$$
3. $$d(x, z) \leq d(x, y) + d(y, z)$$

In plain english, that is

1. A point has distance 0 from itself.
2. Two points have the same distance from each other.
3. A direct path will always have the shortest distance. This expression is also known as the triangle inequlity.

These are all reasonable requirements for a distance function, and it's not too hard to show that normal Euclidean distance ($$d_e (a, b) = \sqrt{(a_x - b_x)^2 + (a_y - b_y)^2}$$ in the 2d plane) meets all these rules. Try it!

From these axioms, we can derivate that $$d(x, y) \geq 0$$ in just a few steps.

## Fun Metric Spaces

- manhattan
- british rail

## Why we care about Metric Spaces

- More general thing of topology, I guess?
- Generalizes convergence and distance.

### Sources

- a
- b
