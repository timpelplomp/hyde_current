---
layout: post
title: The shaky shoulders of giants - tokenisation as a solved problem?
tags: [python, research]
---
> I say with Didacus Stella, a dwarf standing on the shoulders of a giant may see farther than a giant himself.

This quote from *The Anatomy of Melancholy* (1624) by Robert Burton, illustrates the advantages of building on already existing solutions in one's quest to achieve or surpass the state of the art in any number of fields.
In academic writing, especially at the student level, we often subconciously ignore the reality that base-level processing steps are not yet *solved*. 

In other words: while we[^dw] might see farther than the giants our feet rest upon, we often neglect to to look at the giant itself, lest we be made aware of the staggering heights separating us from the ground.
<!--more-->

For the purposes of NLP[^1], this means that we often neglect to examine the foundational technology our approaches depend upon. While this is understandable[^under] for papers limited to a specific size, such as the eight pages commonly requested by the [ACL](https://www.aclweb.org/portal/what-is-cl)[^acl], writing produced at a student level has no similar excuse. Failing to at least acknowledge the reality that even the most basic step, like tokenisation[^2], can yield errors, is a sign of insufficient reflection of the subject matter. 

Read et al. (2012)’s [work](https://www.aclweb.org/anthology/C12-2096.pdf), *Sentence Boundary Detection: A Long Solved Problem?*, helps bring the possible consequences into sharp focus. The following table contains an excerpt of their results, though the stated accuracies are sure to have changed.

| Tokenisers tested on WLB[^wlb] | default | with markup information |
|-------|--------|---------|
| CoreNLP | 89.1 | 90.9 |
| OpenNLP | 90.2 | 92.0 |
| Punkt | 92.8 | 94.5 |
| tokenizer | 93.1 | 94.9 |

These results are striking for two reasons:
1. The accuracies for tokenisers such as *CoreNLP* are strikingly low
2. This can partially be remedied by using markup information to *pre-split* the text before passing it to the tokeniser.

Readers familiar with the tokenisers presented might wonder *why these results differ so substantially from what they expected*. The answer is simple: most accuracies stated on the tokeniser's metaphorical box are derived from well known corpora, following established formatting and language standards, such as the Wall Street Journal (WSJ) corpus. Here, the unsupervised tokeniser *Punkt* can claim an accuracy of 98.3. Noisy and dissimilar datasets, which are usually far more interesting, will perform measurably worse, as shown above. 

Next time, when trying to optimise a language processing task, I will be sure to keep in mind the potential room for optimisation at the base layer and find a firm footing for myself, before climbing steadily upwards.

---

[^1]: Natural language processing
[^2]: The process of splitting a text into its constituents, often on a token and sentence level
[^dw]: Living giants excluded
[^under]: Though any source of errors should naturally be considered during research, even if the inclusion of this consideration is up to each individual researcher.
[^wlb]: 1000 user generated sentences in the Linux domain, an example of a *noisy* text.
[^acl]: Association for Computational Linguistics
