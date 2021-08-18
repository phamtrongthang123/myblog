---
title: "Implicit notation in Kullback-Leibler divergence"
date: "2021-08-18"

tags: 
- Note 
- EN
---

**What do we know about KL div, the definition?**

`$$
D_{\mathrm{KL}}(P \| Q)=\sum_{x \in \mathcal{X}} P(x) \log \left(\frac{P(x)}{Q(x)}\right)
$$`

**The behaviour?**



![Fitting a unimodal approximating distribution q (red) to a multimodal p (blue). Using KL(p||q) leads to a q that tries to cover both modes (a). However, using KL(q||p) forces q to choose one of the two modes of p (b, c).](https://ermongroup.github.io/cs228-notes/assets/img/kldiv.png)

Fitting a unimodal approximating distribution q (red) to a multimodal $p$ (blue). Using KL(p || q) leads to a q that tries to cover both modes (a). However, using `$\mathrm{KL}(\mathrm{q}|| \mathrm{p})$` forces `$q$` to choose one of the two modes of `$p(b, c)$`.

**Well, you see**

I used to use this notation instead as definition:
`$$
D_{\mathrm{KL}}(P - Q)=\sum_{x \in \mathcal{X}} P(x) \log P(x) - \log Q(x)
$$`
Because it is easier to rememeber, I mean there are two minus sign! 

But later date when I notice the behaviour as the above image, there is something new clicking in my head. 

**The left term is meant to be smaller than the right term.** 

- `Using KL(p||q) leads to a q that tries to cover both modes`

- `Using KL(q||p) forces q to choose one of the two modes of p.` <= This also mean: Using KL(p || q) leads to p **tries fit into** q.

The new connection here is, `$p \in q$`. right? , the left term p is trying to be a component of the right term q. 

**The cross entropy is also funny**

You already know that 
`$$
H(p, q)=H(p)+D_{\mathrm{KL}}(p \| q)
$$`

or

`$$
D_{\mathrm{KL}}(p \| q)= H(p, q) - H(p) \\ 
\text{Div = CrossEntropy - AnchorEntropy}
$$`

The equation makes me think: "They really hate p, dont they?" 

They want to make the p as unimportant as possible or something. 

It's just a matter of saying, but the relationship is clear that **p is meant to be belong to q**.



Bluntly, those implicit meaning just to help myself to not mistake notation anymore. They won't help you choose which one to work with anyway. Maybe I will use `$D_{\mathrm{KL}}(p \in q)$` for the fun of it.

