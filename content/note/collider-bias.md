---
title: "Collider bias and Informal condition"
date: "2021-08-26"

tags: 
- Note 
- EN
---

Collider bias takes place in this causal graph: 

![image-20210826105438965.png (920×545) (raw.githubusercontent.com)](https://raw.githubusercontent.com/phamtrongthang123/myblog/master/content/note/imgs/collider-bias/image-20210826105438965.png)





Normally, `$corr(A,B) = 0$` (or close to 0). But after we condition on C, say P(A|C) and P(B|C), `$corr(A|C, B|C) \neq 0$`. This artificial correlation between A and B is causing so many problems for science folks. Even after we know there is that kind of problem, it is not an easy problem to avoid. Because this kind of conditioning could occur in the collect sample phase. Or so I say, Informal Condition.

For example, we toss 2 coins independently, 100 times. Now we set a rule: we only write the result down if one of the coins turns head. After the experiment, we will notice whenever one coin turn tail, the other turns head. This rule is a kind of informal condition. Because through this action, we discard all tail-tail results. And the remaining result, corr(A, B) now is $\neq 0$, the same as we set a rigorous condition. This example is easy enough that we could define C as the "sum of A and B", as for A, the head is 1, the tail is 0, the same goes for B, and the rigorous condition is C >= 1. 

But what about other harder example, Monty hall, for example, A is your pick, B is the car position, C is which door to open (from MC point of view), the rule is now after you pick, the MC opens the door that does not contain the prize, then you could switch. This is another form of informal condition that causes collider bias, as you already know, the probability if you switch is 2/3. Now is your exercise: Can you find a way to reconstruct this into rigorous condition? 

![image-20210826111242464.png (1068×679) (raw.githubusercontent.com)](https://raw.githubusercontent.com/phamtrongthang123/myblog/master/content/note/imgs/collider-bias/image-20210826111242464.png)

As the above figure (thanks [1] for this beautiful graph), after we condition with rules, the selected observations now are only a part of the population. the blue Corr line (interrupt line) which is shown as there is no relationship, changed into the red line, which shows that A and B heavily relate to each other. 

The problem of collider bias is not only about we are wrong about correlated relationships, the collected sample we are working on, if affected by this bias, cannot be used to generalize to the population. Any causal relationship that we induce from this sample is for this sample only. How scary is that!

Well, it is not that much from DL folks point of view, as we always saying, the test set is in the same distribution as the train set. Now even people do some research on domain adaptation, those kinds of scenarios are non-existent for them.

At the end of this note, you may have another question: *What if we say, we only collect the sample with a fixed value? Like you know, do() is the same as you fixed the value, then sample it right? Is do() the same as the condition in this situation?* 

Nope, not at all. If you ask this question, you do not fully understand what do() does. 

**do() is forced, if you are a male, do(female), and the random process chose you, you are now female.**

Condition, on the other hand, when we say only collect with a fixed value, what we mean is collect what contains that value. There is no forced here. Everything is followed by your friendly natural process.

==============

Reference:

[1] Griffith, G.J., Morris, T.T., Tudball, M.J. *et al.* Collider bias undermines our understanding of COVID-19 disease risk and severity. *Nat Commun* **11,** 5749 (2020).
