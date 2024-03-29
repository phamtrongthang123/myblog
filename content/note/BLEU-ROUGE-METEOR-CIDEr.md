---
title: "BLEU, ROUGE-L, METEOR, CIDEr. A brief talk"
date: "2021-08-18"

tags: 
- Note 
- EN
---



## Timeline

Main timeline:

- July 2002: Kishore Papineni, Salim Roukos, Todd Ward, and Wei-Jing Zhu from IBM published BLEU at ACL.
- July 25 - 26, 2004: Chin-Yew Lin from Information Sciences Institute, University of Southern California published ROUGE at the Workshop on Text Summarization Branches Out (WAS 2004).
- 2005: Satanjeev Banerjee and Alon Lavie from Language Technologies Institute, Carnegie Mellon University published METEOR at ACL 2005. And they continue published papers on each variant (or improved version) at ACL 2007, ACL 2008, Springer article 2010, NAACL/HLT 2010, ACL 2010, EMNLP 2011, and EACL 2014. 
- 2015: Ramakrishna Vedantam, Devi Parikh from Virgnia Tech and C. Lawrence Zitnick from Microsoft Research published CIDEr at CVPR15.
- 2016: Anderson published SPICE. 

## A brief history

Machine translation field started to move from the 1950s. But even until 2000 still there are no way to automatically evaluate the generated sentences. Portable computer and phone would moving strongly soon and the evolution of computing power would rise. So people started think how to do evaluation without human hand.

The first method to introduce was BLEU. Even this metric has many flaws, but it marked the beginning of the machine translation evaluation research. 

### BLEU, ROUGE-L, METEOR, CIDEr, and SPICE.

#### BLEU

BLEU is simple enough, we count each n-gram is correct and their apperance  number, then divided by total numebr of n-gram in the candidate sentences (number of guess), there we have precision. 

Modified precision a bit and a length penalty, there we have BLEU. 

 #### CIDEr

CIDEr is compute with 3 equations like this, detail about the notation please read the paper.

`$$
\begin{array}{c}
g_{k}\left(s_{i j}\right)= 
\frac{h_{k}\left(s_{i j}\right)}{\sum_{\omega_{l} \in \Omega} h_{l}\left(s_{i j}\right)} \log \left(\frac{|I|}{\sum_{I_{p} \in I} \min \left(1, \sum_{q} h_{k}\left(s_{p q}\right)\right)}\right)
\end{array}
$$`

`$$
\operatorname{CIDEr}_{n}\left(c_{i}, S_{i}\right)=\frac{1}{m} \sum_{j} \frac{\boldsymbol{g}^{n}\left(c_{i}\right) \cdot \boldsymbol{g}^{\boldsymbol{n}}\left(s_{i j}\right)}{\left\|\boldsymbol{g}^{\boldsymbol{n}}\left(c_{i}\right)\right\|\left\|\boldsymbol{g}^{\boldsymbol{n}}\left(s_{i j}\right)\right\|}
$$`

`$$
\operatorname{CIDEr}\left(c_{i}, S_{i}\right)=\sum_{n=1}^{N} w_{n} \operatorname{CIDEr}_{n}\left(c_{i}, S_{i}\right)
$$`

For each n-gram, compute their "weight", counting how many images that contain it, then reverse, then log, we have the right term of first equation. For that same n-gram, we count number of it in the sentence, then count on the whole refs, divide then, we have left term. Hence the weight. Combine those weights into a vector corresponding to a sequence of n-gram (from a sentence, either candidate or ref), compute cosine similarity, we have the n-gram CIDEr, combine all `n` for n-gram, we have final CIDEr. 

The thing is, CIDEr don't use F-score. This makes it special, does not mean it is good enough though.

 #### The others

- ROUGE-L is computed by the length of longest common subsequence (LCS) between candidate and target, then divided by length of candidate for Precision, and ref for Recall, finally put them into F-score. 
- METEOR is more complicated, to be consider a match, there are many match: exact match (character by character), stem match (fish = fishes), synonym (use wordnet to check), paraphase (follow by paraphrase table). Then with a special criteria, they use beam search to count the match, then compute P and R, then F-score 
- SPICE: they convert the sentence to semantic graph (counter the disavantage of match n-gram where semantic is not accounted for), they use a model or algorithm for this. Then extract tuples of objects, attributes, and relationships, then count number of match, then here we go again to the F-score. 

If you ask me which one is the best, I would vote SPICE and METEOR, but which one I would use to train my model, sadly I'll choose CIDEr, because it fasts. 

Anyway, the thing with the others is that they all use F-score, even though, you know, F-score is just a combination of P and R. 

**To be honest, at this point, I don't know why F-score.**

You see, Harmonic mean in naive math is to compute the average, where we fix the distance right? I mean distance / time, if we fix time, we use arimethic mean, fix distance we use harmonic mean. But this does not bring any bell to F-score, there is no analogy here. 

Maybe I will find the answer at later date.