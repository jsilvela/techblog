+++
tags = ["math"]
categories = []
title = "Polynomials are strange"
date = 2021-02-19T20:49:18+01:00
draft = false
+++

{{<mathjax>}}

## Two-headed things

Polynomials are unexpectedly strange.
They're familiar from primary school, probably the first *functions* we study.
But start studying abstract algebra or
algebraic geometry, and they turn into two-headed beasts.

In abstract algebra you start to emphasize the algebraic structure of polynomials.
You define addition of two polynomials much like you define component-wise
addition of vectors. Multiplication gives polynomials a **ring** structure.

The textbook definition of the polynomial ring $latex K[x]$ over a
field $latex K$ de-emphasizes that polynomials are functions.
You could use vector notation to make this even clearer.

$latex a x^2 + b x + c \equiv (a, b, c) \in K[x] $

Algebra books define the **evaluation homomorphism** to treat
function-ness separately. Given the polynomial ring
$latex K[x]$ and $latex\alpha \in K$, the application:

$latex ev_{\alpha}: K[x] \rightarrow K $

$latex ev_{\alpha}(f) = f(\alpha) $

is easily proven to be a ring homomorphism.

You could do without the functional part of polynomials a lot of the time. But
sometimes that part comes to the rescue in surprising ways.

## Nullstellensatz

This famous theorem of Hilbert left me a bit confused initially.

Essentially, it says that the set of **algebraic varieties** in $latex \mathbb{C}^n$
is in 1-1 correspondence with the set of **radical ideals**
in $latex \mathbb{C}[x_1,..,x_n]$.

An **ideal** of a ring is a subset of the ring that is closed under additions,
and such that the product of an element in the ideal with *any* element in the
ring, is also in the ideal.

A **radical ideal** is an ideal where, if some power of an element belongs,
then the element belongs.

An example of a non-radical ideal is the ideal generated by $latex f(x) = x^2$,
aka $latex (x^2)$. $latex f(x) = x$ does not belong to the ideal, but
$latex f(x) = x^2$ does.

**Fact**: *the* ideal of polynomials that are zero on an algebraic
variety $latex V$ is a radical ideal. \
This is almost trivial. Say $latex f \in K[x]$, and $latex f^k$ is zero
over $latex V$. Because the polynomial *function* takes values in a field, and
a field is an integral domain, we must have $latex f(x) = 0,  \forall x \in V$.

There you have it, the function-ness saves the day. Otherwise, proving that an
ideal is radical may be no picnic.

You noticed I said "*the* ideal of polynomials that are..." \
There is generally more than one ideal whose polynomials are zero on a variety,
but there is only one ideal that contains all the polynomials that are zero on the variety,
and it happens to be radical.

Nullstellensatz gives us
a 1-1 correspondence between the variety $latex V$ and *the* radical idea
of polynomials that are zero on $latex V$.

### An exercise

This exercise from *An Invitation to Algebraic Geometry* by Karen E. Smith
et. al. took me a while to solve:

**Exercise 2.3.1 (abridged)** *Check that the ideal $latex (xy, xz)$ is radical.*

There's an algebraic route to this, which seemed forbidding to me: to imagine
some $latex f^k$ in the ideal, and prove that $latex f$ must also be in the ideal.

But the Nullstellensatz opens up a different path: Prove that $latex (xy, xz)$
is *the* ideal of functions that are zero on the variety
defined by $latex (xy, xz)$.

This sounds silly to the point of tautology. One would expect that any ideal
$latex I$ should be *the* ideal for the variety it defines. Yet...

We can define a variety using a non-radical ideal. Think of the ideal $latex I$
generated
by $latex (x^2 - 1)^2$. Its associated variety is $latex V=\\{1, -1\\}$.
But there is a radical ideal, $latex I = (x^2 - 1)$, which is *the* ideal
associated with the variety $latex V$.

How do we prove that $latex (xy, xz)$ is *the* ideal? We need to prove that
any function that is zero on the variety must be in the ideal.
The variety is easily seen to be
$latex V=\\{(x,y,z) \in \mathbb{C}^3, x=0 \text{ or } y=z=0\\}$

Say a polynomial $latex g$ is zero on $latex V$. Since $latex x=0 \rightarrow g=0$,
we can deduce that it must be divisible by $latex x$. Indeed, by long division,

$latex g = q x + r(y, z)$, and if we let $latex x=0$, we see we must
have $latex r(y, z) = 0$.

Let's study the quotient $latex q$. Clearly, like $latex g$,
$latex q=0 \text{ if } y=z=0$

Let's try to divide $latex q$ by $latex y$. If it is fully divisible
by $latex y$, say $latexq = q_0 y$, we're done,
because $latex g = x q_0y \rightarrow g \in (xy, xz)$.

Let's assume there's a remainder:

$latex q = q_1y + r_1(x, z)$

Let's divide again, this time $latex r_1$ by $latex z$.

$latex q = q_1y + q_2z + r_2(x)$

Since $latex q = 0$ when $latex y=z=0$, we must have $latex r_2(x) = 0$.

So,

$latex q = q_1y + q_2z \rightarrow g = x q_1 y + x q_2z \rightarrow g \in (xy, xz)$

We conclude that $latex (xy, xz)$ is *the* ideal for $latex V$, so it's radical.

Note that:

- The long division algorithm is algebraic, mostly
- But we used the function values to annul remainders

It still surprises me to switch back and forth on polynomials,
more so than with other objects of dual nature.