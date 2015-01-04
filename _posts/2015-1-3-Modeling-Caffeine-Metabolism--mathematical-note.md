---
layout: post
title: Modeling Caffeine Metabolism - mathematical note

---

I wanted to make a quick mathematical note on the long term behavior of our caffeine metabolism function. In the previous post, we came up with the expressions 

$$f(t)=d\cdot e^{-t/\tau}$$ as the exponential decay for a single dose of $$d~$$ milligrams at time $$t$$.

$$\displaystyle f(t) = d e^{-t/\tau} \left(\frac{1-e^{a(n+1)/\tau}}{1-e^{a/\tau}}\right)$$ for the behavior at time $$t~$$ for a dose of $$d~$$ mg delivered every $$a~$$ hours, where $$n=\lfloor t/a \rfloor$$.

In this post, we'll look at the long term behavior using two similar approaches. The quantity we are most interested in is the amount of active caffeine that is always present regardless of where the person is along the dosing cycle, i.e. the lowest point along the exponential curve (just before the spike up).

**Approach 1 - Infinite Series**

We know that just before $$t=a$$ (just before the spike), we have that the amount is given by $$d e^{-a/\tau}$$. Similarly, just before $$t=2a$$, we have that the amount is given by $$de^{-a/\tau} + de^{-2a/\tau}$$. Generalizing to $$t=\infty a$$, we have the amount given by the infinite series

$$\displaystyle T = de^{-a/\tau} + de^{-2a/\tau} + de^{-3a/\tau} + \ldots = \frac{de^{-a/\tau}}{1-e^{-a/\tau}}$$

where we have summed the infinite series. This expression gives us the desired quantity.

**Approach 2 - Extending Finite Series**

We are interested in the behavior at times just before a new dose. We can represent these times as $$t=ma-\epsilon$$ where $$m$$ is a positive integer and $$\epsilon \ll a$$. We use $$\epsilon$$ so that we are working just before the new dose, occurring at $$t=ma$$.

We can also calculate $$n=\left\lfloor \frac{ma-\epsilon}{a}\right\rfloor = \left\lfloor m - \frac{\epsilon}{a}\right\rfloor = m-1$$.

We can substitute into our formula for $$f(t)$$	.

$$f(ma-\epsilon) = d e^{-(ma-\epsilon)/\tau} \left(\frac{1-e^{am/\tau}}{1-e^{a/\tau}}\right)$$

$$f(ma-\epsilon) = d \left(\frac{e^{-ma/\tau} - e^{-am/\tau}e^{am/\tau}}{1-e^{a/\tau}} \right) e^{\epsilon/\tau}$$

$$f(ma-\epsilon) = d\left( \frac{e^{-ma/\tau} - 1}{1-e^{a/\tau}} \right) e^{\epsilon/\tau}$$

$$f(ma-\epsilon) = d\left(\frac{e^{-ma/\tau} - 1}{e^{a/\tau}(e^{-a/\tau}-1)} \right) e^{\epsilon/\tau}$$

$$f(ma-\epsilon) = de^{-a/\tau}\left(\frac{1-e^{-ma/\tau}}{1-e^{-a/\tau}} \right) e^{\epsilon/\tau}$$

Now we consider the limit we are working in--unbounded $$m$$ and small $$\epsilon$$. As $$m\rightarrow \infty$$, $$e^{-ma/\tau} \rightarrow 0$$ and as $$\epsilon\rightarrow 0$$, $$e^{\epsilon/\tau} \rightarrow 1$$. Accordingly, we have this expression approaching $$\displaystyle\frac{de^{-a/\tau}}{1-e^{-a/\tau}}$$ as found previously.

Through two slightly different approaches, we were able to determine the long term behavior of the function. For very large $$m$$, we have that the function spikes up to

$$\displaystyle \frac{d}{1-e^{-a/\tau}} $$ at $$t=ma$$ 

and decays down to

$$\displaystyle \frac{de^{-a/\tau}}{1-e^{-a/\tau}}$$ just before $$t=(m+1)a$$.
