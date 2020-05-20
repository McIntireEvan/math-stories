---
layout: post
usemathjax: true
title: Fractional Calculus
description: Generalizing the derivative to rational orders.
summary: Generalizing the derivative to rational orders.
tags: [calculus]
---

In my second year of college, I took a small course on visualization using Mathematica. For our final project, we got to pick a topic and present on it. I explored Fractional Derivatives, a way of generalizing derivatives to rational orders (i.e. the 1.5th derivative). In this post I'll explore them the same way I did for that presentation.

# Derivatives: A Recap

The derivative of a function $$f$$, written $$f'(x) = \frac{d}{dx} f(x)$$ gives the rate of change of $$f$$ at some point $$x$$. We can then take the derivative of $$f'(x)$$, giving the second derivative $$f''(x)$$, and generally[^1] we can repeat this as much as we'd like. The number of times we take the derivative is called the _order_. Clearly, just be repeated taking derivatives we can find the $$n$$th derivative, where $$n$$ is an integer. As notation, we say $$f^{(n)}(x) = \frac{d^n}{dx^n}$$

Can we go further? Can we define the derivative for more orders? As it turns out, yes. Let's get started.

## Derivatives of Polynomials

One of the first functions we take the derivative of is $$f(x) = x^n$$. Then $$f'(x) = nx^{n-1}, f''(x) = (n)(n-1)x^{n-2}$$, and in general $$f^{(a)}(x) = (n)(n-1) \dots (n - a + 1)x^{n-a}$$.

This breaks down if $$a$$ isn't an integer. Say $$a = 0.5$$, how do we do that? I don't think it's clear what to do, but a good first step is to rewrite it. For simplicity, assume $$n$$ is an Integer. We can take all the coefficients and condense it into one expression

$$f^{(a)}(x) = \frac{n!}{(n - a)!}x^{n-a}$$

Clearly, we have to edit the fractorial to support rational numbers

# Extending the factorial: The Gamma Function

As a reminder, the factorial is defined as $$n! = n * (n - 1) * (n - 2) * \dots * 3 * 2 * 1$$.

Figuring out what this should look like for real numbers is hard. It's also a bit outside of the scope of this post. I think it'd be interesting to do a deep dive and derive it as much as possible, but that'll come later.

For now, let's say we have a function $$\Gamma$$, such that $$\Gamma (n) = (n - 1)!$$. The Gamma function deserves a post of its own, so for now let's just treat it as a sort of black box that just does what we want. It's not particularly easy to evaluate by hand, so we're not missing a lot.

(PLOT HERE)

Now that we have our function, let's put it to use.

$$f^{(a)}(x) = \frac{\Gamma (n + 1)}{\Gamma (n - a + 1)}x^{n-a}$$

## Testing it out

I've plotted $$2, 2x, \text{and} x^2$$. Using the definition we just came up with, I've plotted the fractional derivative with varying orders from 0 to 2.

![Fractional derivate of x^2 with orders from 0 to 2]({{ site.baseurl }}/assets/fractional-calc/fracx2.gif)

## Polynomials

With this, we've actually gotten all derivs, woooow cool

How do we extend to everything?

# Taylor Series

## Rewriting Polynomails

We can write any function as a taylor series, and it's just a polynomial :wink:

Using the derivative, we can write any function as a taylor series. If we make it an infinite sum, it equals the function (I think)

so bam we can do all polynomals so all we gotta do is yeet on the taylor series

# trig functions

- show some examples
  - sin, cos, exp

# A More General Approach

As fun as that is, it's difficult, and there are plenty of extra special functions. How do we come up with a general form?

- we actually do the integral first (thanks cauchy :))
- and then by taking the derivative, we reach what we want

# Code

Before I wrote this post, I wrote mathematica and sage packages. Try them out, and feel free to contribute if there are any issues.

- SageMath (python)
- Mathematica

# Footnotes

[^1]: Of course, some functions are not differentable. We'll ignore those and speak generally, assuming $$f$$ is.
[^2]: If $$n$$ is not an integer we can't actually write it this way, but that's okay.
