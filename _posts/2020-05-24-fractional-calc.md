---
layout: post
usemathjax: true
title: Fractional Calculus
description: Generalizing the derivative.
summary: We tale a step-by-step approach to generalizing the derivative to real orders. We end with a generalized form that works for all functions.
tags: [calculus]
---

In my second year of college, I took a small course on visualization using Mathematica. Our final project was to research, visualize, and present a topic of our choosing. I presented on Fractional Derivatives, which generalize the derivative to real orders. For instance, we can define a "half derivative". In this post I'll approach them in two ways. First, in the same way I did in the presentation, trying to build intuition and derive them from the ground up. The second way takes a more general approach that addresses many issues we'll encounter in part one.

# Derivatives: A Recap

As a quick recap, the derivative of a function $$f(x)$$ gives the rate of change of $$f$$ with respect to $$x$$. Usually we denote this as $$\frac{d}{dx}$$ or $$f'(x)$$. Since $$f'(x)$$ is also a function, we can take its serivative call the result the second derivative of $$f(x)$$. We can keep repeatedly do this $$n$$ times, and call it the $$n$$th derivative, or a derivative of **order** $$n$$. We write this as $$f^{(n)}(x)$$ or $$\frac{d^n}{dx^n}$$.

At this point, one might wonder if we can generalize derivatives further. The generalization we'll look at is allowing the order to be any real number.

## Derivatives of Polynomials

Single term polynomials of the form $$x^n$$ are some of the first functions we learn to differentiate. As such, they're a natural starting point for our exploration.

First, let's look at the first few derivatives of $$x^n$$. $$f'(x) = nx^{n-1}$$, $$f''(x) = (n)(n-1)x^{n-2}$$. In general, $$f^{(a)}(x) = (n)(n-1) \dots (n - a + 1)x^{n-a}$$.

From this form, it's not clear how we'd write this if $$a$$ is not an integer. A reasonable approach is to rewrite it and see if we can spot a next step. One way we could do this is by consolidating all the leading terms.

If we look back at our function, we can notice that it is the first $$a$$ terms of the factorial, also known as a _falling factorial_. Rewriting, we get $$f^{(a)}(x) = \frac{n!}{(n - a)!}x^{n-a}$$.

This form has some issues. Namely, if $$n$$ and $$a$$ are not integers, this doesn't make sense. The factorial is only defined for non-negative integers. But if we could extend the factorial, then this formula should give us a real-ordered derivative. So let's shift our focus to the factorial.

# Extending the factorial: The Gamma Function

As a reminder, the factorial is defined as $$n! = n * (n - 1) * (n - 2) * \dots * 3 * 2 * 1$$.

Figuring out what this should look like for real numbers is hard. It's also outside of the scope of this post. I think it'd be interesting to do a deep dive and derive it as much as possible, but for this post, let's say we have a function $$\Gamma(n)$$, such that $$\Gamma (n) = (n - 1)!$$. The Gamma function isn't easy to understand[^1], and hard to manually evaluate, so we'll gloss over it and just look at the graph.

![Graph of the Gamma Function from -5 to 5]({{ site.baseurl }}/assets/fractional-calc/gamma.jpg)

Here, I've plotted $$\Gamma(n)$$ and $$(n-1)!$$. A few things to note:

- As we wanted, Gamma interpolates $$(n - 1)!$$, and gives values for most real numbers.
- Gamma is not defined at non-positive integers.

## Testing it out

Now that we've extended the factorial, let's revisit our formula. Substituting Gamma as appropriate, we come up with $$f^{(a)}(x) = \frac{\Gamma (n + 1)}{\Gamma (n - a + 1)}x^{n-a}$$.

We can go ahead and immediately put it to use. Consider $$f(x) = x^2$$. We'll look at its derivatives for orders in the domain $$[0, 2]$$. I've also plotted the integer-order derivatives we're used to. Before proceeding to the graph below, try to think of what it should look like.

![Fractional derivate of x^2 with orders from 0 to 2]({{ site.baseurl }}/assets/fractional-calc/fracx2.gif)

I think this result is really cool to look at. I also think it works like you'd hope it would, which is cool. However, at this point it's still not clear what fractional derivatives actually represent. That is, we can understand the first derivative as being the rate of change, and each successive derivative the rate of change of that. Not being able to assign a physical or geometric meaning in that way is really frustrating. This is the first major snag of this approach - it doesn't reveal any meaning or greater truth. We'll address this later, but for now we'll take this definition to its limit.

We know that the derivative is linear, i.e. $$\frac{d}{dx}(af(x) + bg(x)) = a\frac{d}{dx}f(x) + b\frac{d}{dx}g(x)$$, and our changes so far preserve linearity.

So with this in mind, we've actually defined the fractional derivative for all polynomials!

Well, almost. It turns out there's a _slight_ issue.

## Polynomials

Using an example is a great way to find an issue. Let's take $$f(x) = x^2 + 2$$ and find out where our definition fails. I encourage you to try it yourself before reading the rest of this section.

As a benchmark, our new definition must agree with normal derivatives of integer orders. So, if we take the first derivative, we should get $$f'(x) = 2x$$.

So with $$a = 1$$, $$x^2$$ becomes $$\frac{\Gamma(3)}{\Gamma(2)}x^1 = \frac{2!}{1!}x = 2x$$. So far so good.

$$2$$ implicitly has a $$x^0$$ term, so $$n = 0$$. So, we get $$\frac{\Gamma(1)}{\Gamma(0)}2x^0$$. Unfortunately, $$\Gamma(0)$$ is undefined. More generally, it's undefined at every non-positive integer. This is the second major snag of this approach. With normal derivatives, if $$a > n$$ then the term evaluates to zero. Fractional derivatives must zero out at these integer powers where $$a > n$$, but not at non-integer powers where the same is true.

Luckily, if we look at $$\Gamma(n)$$, we can see that the function goes to $$\pm \infty$$ at non-positive integers, so we can wave our hands and say that as a result, the terms we're concerned about will go to zero. This isn't really great math, but we'll bear with it a bit longer.

# Differentiating more functions

So, we've very roughly defined the fractional derivative for all polynomials. What can we do for functions like $$sin(x)$$ and $$e^x$$?

## Taylor Series

The **Taylor Series** of a function is a way to approximate it using a polynomial. We _center_ it about some point $$y$$, and take the value of derivatives of that function at that point to write terms.

Formally, we have $$\sum_{n=0}^{\infty} \frac{f^{(n)}(y)}{n!}(x-y)^n$$.

For many functions, with enough terms the Taylor Series is a great approximation[^2]. We'll use it to explore $$sin(x)$$ and $$e^x$$, and then cover why it doesn't work in general.

## Some examples

First, let's try $$sin(x)$$, centered about $$x = 0$$. We know[^3] that the Taylor Series is $$x - \frac{x^3}{3!} + \frac{x^5}{5!} - \frac{x^7}{7!} + \cdots$$. I used Mathematica to plot $$sin(x), cos(x)$$, and the Fractional Derivative using the Taylor Series for $$a \in [0, 2]$$.

![Graph of the fractional derivatives of sin(x)]({{ site.baseurl }}/assets/fractional-calc/sin.gif)

We know that there's just a phase shift of $$\frac{\pi}{2}$$ between sine and cosine, so it makes a lot of sense that the fractional derivative also shows a clear phase shift.

Next, let's try this for $$e^{2x}$$. The Taylor Series is $$1 + 2x + 2x^2 + 4\frac{x^6}{3} + \cdots $$.

![Graph of the fractional derivatives of sin(x)]({{ site.baseurl }}/assets/fractional-calc/exp.gif)

Once again, we don't get any surprises.

Let's see where this all breaks down. Taylor Series have issues representing $$ln(x)$$, and becomes more inaccurate the more terms in the Taylor Series. A picture is worth a thousand words, so let's take a look.

![Graph of the fractional derivatives of ln(x)]({{ site.baseurl }}/assets/fractional-calc/ln.gif)

As fun as this approach was, this is the final nail in the coffin for it.

# A More General Approach

While I think the approach we took is interesting and works for some of these simple examples, it doesn't work in general. Let's recap the issues:

1. While this form was easy to derive, it's not necesarily meaningful.
2. Gamma is undefined at non-positive integers. We hand-waved this issue away, but we need to address it.
3. This approach relies on Taylor Series, which require many terms to be accurate, and aren't useful for all functions.

We want to come up with a new approach that addresses these issues. The approach we'll take actually involves starting with the integral.

We were able to define fractional derivatives, so why not fractional integrals? Our quest here is much easier, as we can start with Cauchy's repeated integration formula $$f^{(-n)}(x) = \frac{1}{(n-1)!}\int_{\alpha}^x (x-t)^{n-1}f(t) dt$$.

We see a factorial, and we know what to do: $$\mathcal{I}^n = f^{(-n)}(x) = \frac{1}{\Gamma(n)}\int_a^x (x-t)^{n-1}f(t) dt$$.

In one easy step, we've defined a fractional integral, that doesn't suffer from issues (2) and (3). We'll get back to (1) later.

We also know that roughly speaking, integrals and derivatives cancel each other out. So taking a fractional integral and then a whole derivative of higher order would be equivalent to taking a fractional derivative of their difference in orders.

Formally, we can write $$\large{\frac{d^a}{dx^a}f = \frac{d^{\lceil a \rceil}}{dx^{\lceil a \rceil}} \mathcal{I}^{\lceil a \rceil - a}f}$$.

And in two easy steps, we've defined a fractional derivative. It's certainly much harder to evaluate than what we had before, but it is more correct, and has a few really interesting properties.

The main property I want to talk about comes from the bounds of integration in our formula. If you'll notice, we added a constant, which I have written as $$\alpha$$. It's arbritrary, but obviously changing it will change our result.

To consolidate all of the work we've done in this section, and to emphasize that constant, we're going to combine it all into a single operator. This is known as the Riemann–Liouville differintegral.

$$
{}_{\alpha} D_{x}^{a} f(x) = \begin{cases}
\frac{d^{\lceil a \rceil}}{dx^{\lceil a \rceil}} \mathcal{I}^{\lceil a \rceil - a}f(x) \quad \quad a \gt 0 \\
f(x) \quad  \quad \quad \quad \quad \quad \quad a = 0\\
\mathcal{I}^{-a} f(x)  \quad \quad \quad \quad \quad a \lt 0\\
\end{cases}
$$

And there you have it, a single operator to rule them all.

## Applications

We still haven't answered the fundemental question: what does a fractional derivative mean?

Aside from being a cool generalization, the introduction of this arbitrary $$\alpha$$ is actually really powerful.

In calculus, much of what we do is "local". That is, a derivative at a point will only rely on values at or infinitely close to that point. But here, we've created an integral that is non-local. From what I gather, this could be applied to proccesses with differing time scales, or other complicated interactions. Essentially, it's better able to represent complex physical processes that have a sort of outside interference.

# Code

Before I wrote this post, I wrote mathematica and sage packages that implement the Riemann–Liouville differentegral. Try them out, and feel free to contribute if there are any issues.

- SageMath
- Mathematica

# Sources

I used these a lot to either use precise language or learn about the topics at hand. For any given topic, the Wikipedia page is also a pretty good place to start.

1. https://mathworld.wolfram.com/Derivative.html
2. http://vectron.mathem.pub.ro/dgds/v15/D15-ta.pdf

# Footnotes

[^1]: Formally, $$\Gamma(z) = \int_{0}^{\infty} x^{z-1}e^{-x}dx, \mathcal{R}(z) > 0$$. We then use $$\Gamma(z) = \frac{\Gamma(z + 1)}{z}$$ to extend it to non-integer negatives.
[^2]: For some functions, like $$ln(x)$$, it diverges for $$x > 1$$. We'll observe this later.
[^3]: It's a standard, interesting result. It's tedious, but not too hard to compute given the definition.
