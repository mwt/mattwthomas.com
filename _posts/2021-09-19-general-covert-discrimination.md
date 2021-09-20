---
title: "General Covert Discrimination"
author: "Matthew Wildrick Thomas"
layout: "post"
tag: ["math", "economics", "notes"]
date: "2021-09-19"
use_math: true
last_modified_at: "2021-09-19"
description: "Thoughts on efficient revenue maximizing symmetric contests"
---

I show that any efficient two player symmetric allocation rule between risk neutral, heterogenous players generates weakly less revenue than one of two contests. The revenue maximizing efficient symmetric contest is an all-pay auction with bid caps [(Che and Gale 1998)](https://econpapers.repec.org/RePEc:aea:aecrev:v:88:y:1998:i:3:p:643-51) when heterogeneity is low and a difference form contest [(Che and Gale 2000)](https://econpapers.repec.org/RePEc:eee:gamebe:v:30:y:2000:i:1:p:22-43) when heterogeneity is high.

![plot of optimal revenue vs Tullock contests](/assets/images/posts/2021/pure-covert-discrimination.svg){: width="600px"}
{: .text-center}

## Introduction

Contests are models of conflict in which risk neutral players exert costly effort to win a prize. When one player is more capable than another, contests become less competitive. This lack of competitiveness decreases total effort. A contest designer can use two common tools to increase the total effort: minimum requirements and direct discrimination.

Minimum requirements (i.e. reserve bids) allow the contest designer to require either player to exert some minimum amount of effort to qualify for the prize. A large enough minimum requirement can make the lack of competition from a competitor irrelevant. For example, a professional figure skater would not need to exert much effort to beat me in a figure skating competition. However, if winning a large prize requires a high score, then the professional is not really competing against me. He is competing against this minimum threshold.  

Direct discrimination allows the contest designer to discriminate against the stronger player to reduce or remove her advantage. Handicaps in sporting events are a common example. This requires the contest designer to know which contestant is more talented. Otherwise, the designer does not know who to handicap. If this information is known, direct discrimination can be used to level the playing field of any contest.

We consider an alternative way of maximizing revenue -- covert discrimination. The contest designer maximizes the revenue of a contest without imposing any minimum requirement or treating contestants differently. We show that she is unable to achieve the first best. However, allowing direct discrimination or an arbitrarily small minimum requirement ensures that the first best can be achieved.

## Model

Suppose that the prize of contest is worth one to both players. So, the two players have the same value. However, their scores have different costs. In particular, we will say that the score is $$k > 1$$ times more costly for Player 2 than for Player 1. You can interpret this as saying that Player 1 is more skilled. So, it takes less effort for her to produce a high score.

The probability of Player $$i$$ winning the prize in a contest when she chooses score $$s_i$$ and her opponent chooses score $$s_{-i}$$ is:

$$
    p_{i}(s_i, s_{-i}).
$$

The final payoffs are:

$$
    U_1(s_1, s_2) = p_1 (s_1, s_2) - s_1
$$

$$
    U_2(s_1, s_2) = p_2 (s_2, s_1) - k s_2.
$$


We define two properties that are central to our analysis:

* A contest satisfies *no minimum requirement* iff $$p_1 (x, y) + p_2 (y, x) = 1$$ for all $$x,y \geq 0$$.
* A contest satisfies *no direct discrimination* iff $$p_1 (x, y) = p_2 (x, y)$$ for all $$x,y \geq 0$$.

Note that these conditions jointly imply $$p_i(x,x) = 0.5$$. 

## Contest design

Suppose that there is some contest designer who can choose $$p_1, p_2$$ in order to maximize the expected revenue, $$E[s_1 + s_2]$$ given the (possibly mixed) strategies of the players. If strategies are pure, then the revenue is deterministic. Note that incentive compatibility implies

$$
    E[s_1 + k s_2] \leq E[p_1 (s_1, s_2) + p_2 (s_2, s_1)] \leq 1.
$$

Therefore, expected revenue is bound above by $$1 - (k - 1) E[s_2]$$ and the first best is achieved iff $$s_1 = 1$$ and $$s_2 = 0$$.[^fbns] We can immediately see that no contest which satisfies both no minimum requirement and no direct discrimination will achieve the first best. This is because both players receive a payoff of zero in the first best, but Player 1 can choose zero instead of one to receive a payoff of $$p(0,0) = 0.5$$.

### Minimum requirement

If we allow for a minimum requirement, but still enforce no direct discrimination, is is easy for the designer to achieve the first best. For example, the "price contest"

$$
    p(x, y) = 
    \begin{cases}
        0           &\text{if } x < \max(y,1) \\
        \frac{1}{2} &\text{if } x \geq 1, x=y \\
        1           &\text{if } x \geq 1, x > y
    \end{cases}
$$

achieves the first best because Player 1 is willing to meet the minimum requirement of 1 and Player 2 is not.

One might wonder if the designer can still extract the full surplus with a smaller minimum requirement. The answer is yes. In fact, $$p(0,0) = 0$$ is necessary and sufficient for the first best to be attainable without direct discrimination. That is, the designer need only be able to withhold the prize when both players play zero. To see this, consider the following contest which satisfies both properties except at zero.

$$
    p(x,y) =
    \begin{cases}
        1           &\text{if } x-y >1 \\
        x-y         &\text{if } x-y \in(0,1] \\
        0           &\text{if } x = y = 0 \\
        \frac{1}{2} &\text{if } x=y \neq 0 \\
        1+x-y       &\text{if } x-y <0.
    \end{cases}
$$

This contest has an equilibrium at the first best. This is still true for any minimum requirement in $$[0,1]$$.


### Direct discrimination

Direct discrimination is similar to a minimum requirement. It is possible to mimic any minimum requirement through direct discrimination by promising the prize to the weaker player whenever the requirement is not met. In particular, take either example from the minimum requirement section and set $$p_1(x,y) = p(x,y)$$ and $$p_2(y,x) = 1 - p(x,y)$$. Such a contest clearly has no minimum requirement, but will be strategically equivalent to the original contest. For example, consider the "price contest". With this transformation,

$$
    p_1(x, y) = 
    \begin{cases}
        0           &\text{if } x < \max(y,1) \\
        \frac{1}{2} &\text{if } x \geq 1, x=y \\
        1           &\text{if } x \geq 1, x > y
    \end{cases}
$$

$$
    p_2(x, y) = 
    \begin{cases}
        0           &\text{if } y \geq 1, y > x \\
        \frac{1}{2} &\text{if } y \geq 1, x=y \\
        1           &\text{if } y < \max(x,1).
    \end{cases}
$$

This contest has an equilibrium at the first best.

### Covert discrimination

In equilibrium, each Player must weakly prefer her equilibrium payoff over copying the strategy of her opponent. Therefore, the following weak incentive compatibility condition is necessary for equilibrium:

$$
    \frac{1}{2} - E[s_2] \leq E[U_1(s_1, s_2)].
$$

Together with $$E[U_2(s_1, s_2)] \geq 0$$ this implies

$$
    \begin{aligned}
        \frac{1}{2} - E[s_2] &\leq E[U_1(s_1, s_2) + U_2(s_1, s_2)] \\
        \frac{1}{2} - E[s_2] &\leq 1 - E[s_1 + k s_2]
    \end{aligned}
$$

where the last line follows from no minimum requirement. Rearranging this equation gives an upper bound on the revenue:

$$
    E[s_1 + s_2] \leq \frac{1}{2} + (2 - k) E[s_2]
$$

which can be further bounded by

$$
    E[s_1 + s_2] \leq
    \begin{cases}
        \frac{1}{k} &\text{if } k < 2 \\
        \frac{1}{2} &\text{if } k \geq 2.
    \end{cases}
$$

I show by construction that this upper bound is tight. That is, there exist optimal contests which achieve these bounds.

The second bound comes from the fact that $$E[s_2] \leq \frac{1}{2k}$$ because Player 2 cannot win with probability more than one half. To see this, consider that the following two conditions must hold in equilibrium

$$
    \begin{aligned}
        \frac{1}{2} - k E[s_1] &\leq E[p(s_2, s_1) - k s_2] \\
        E[s_2] &\leq E[s_1] + (k)^{-1} \left(E[p(s_2, s_1)] - \frac{1}{2}\right)
    \end{aligned}
$$

and

$$
    \begin{aligned}
        \frac{1}{2} - E[s_2]  &\leq E[p(s_1, s_2) - s_1] \\
        E[s_2] &\geq E[s_1] + \left(E[p(s_2, s_1)] - \frac{1}{2}\right)
    \end{aligned}
$$

which imply $$E[p(s_2, s_1)] \leq \frac{1}{2}$$. 

*Case 1:* $$k < 2$$. This means that revenue cannot exceed $$\frac{1}{k}$$. We can reach this upper bound with an all-pay auction with a bid cap at $$\frac{1}{2k}$$ as in [Che and Gale (1998)](https://econpapers.repec.org/RePEc:aea:aecrev:v:88:y:1998:i:3:p:643-51). That is

$$
    p(x,y) =
    \begin{cases}
        1           &\text{if } \frac{1}{2k} \geq x > y \text{ or } y > \frac{1}{2k} \\
        \frac{1}{2} &\text{if } x=y \\
        0           &\text{if } \frac{1}{2k} \geq y > x \text{ or } x > \frac{1}{2k}.
    \end{cases}
$$

This has an equilibrium at $$s_1 = s_2 = \frac{1}{2k}$$ which achieves the upper bound for $$k < 2$$.

*Case 2:* $$k \geq 2$$. The above implies that revenue cannot exceed one half. Consider the following difference form contest as in [Che and Gale (2000)](https://econpapers.repec.org/RePEc:eee:gamebe:v:30:y:2000:i:1:p:22-43):

$$
    p(x,y) =
    \begin{cases}
        1                   &\text{if } x-y > \frac{1}{2} \\
        \frac{1}{2} + x-y   &\text{if } x-y \in \left[-\frac{1}{2},\frac{1}{2}\right] \\
        0                   &\text{if } x-y < - \frac{1}{2}
    \end{cases}
$$

The above contest has an equilibrium at $$s_1 = \frac{1}{2}$$ and $$s_2 = 0$$ which achieves the upper bound for $$k \geq 2$$.

---

[^fbns]: Note that these strategies must be pure because no mixed strategy can have expectation zero and no individually rational mixed strategy can have expectation one.
