---
layout: post
usemathjax: true
title: Fractional Calculus
description: Generalizing the derivative to rational orders.
summary:
tags: [calculus]
---

In my second year of college, I took a small course on visualization using Mathematica. For our final project, we got to pick a topic and present on it. I explored Fractional Derivatives, a way of generalizing derivatives to rational orders (i.e. the 1.5th derivative). In this post I'll explore them the same way I did for that presentation.

# Derivatives: A Recap

The derivative of a function $$f$$, written $$f'(x) = \frac{d}{dx} f(x)$$ gives the rate of change of $$f$$ at some point $$x$$. We can then take the derivative of $$f'(x)$$, giving the second derivative $$f''(x)$$, and generally[^1] we can repeat this as much as we'd like. The number of times we take the derivative is called the _order_. Clearly, just be repeated taking derivatives we can find the $$n$$th derivative, where $$n$$ is an integer.

Mention fractional here??

COOL LEAD IN!

## Taylor Series and Polynomials

Using the derivative, we can write any function as a taylor series. If we make it an infinite sum, it equals the function (I think)

This is key to reason about frac derivs in the way that I studied them. Why?

## Derivatives of Polynomials

polynomials are the first things we learn the shortcuts to the derivatives for. we also just showed that we can express any function as a polynomial. So if we can find a way to generalize for a polynomial, we've cracked this whole thing open.

HERE'S THE FORMULA

so what would it take for $$n$$ to be rational and not integer? we gotta extend the factorial

# Extending the factorial: The Gamma Function

- Generalizes factorial
- Show a graphy graph

# Taylor Series Analysis

- we know how to derivative of polynomial in general form
- since we can write any function as a taylor series, we can write as a sum of polynomials
- wow we're in business!

- show some examples
  - sin, cos, exp

# A More General Approach

As fun as that is, it's difficult, and there are plenty of extra special functions. How do we come up with a general form?

- we actually do the integral first (thanks cauchy :))
- and then by taking the derivative, we reach what we want

# Code

Before I wrote this post, I wrote mathematica and sage packages. Try them out, and feel free to contribute if there are any issues.

# Footnotes

[^1]: Of course, some functions are not differentable. We'll ignore those and speak generally, assuming $$f$$ is.
