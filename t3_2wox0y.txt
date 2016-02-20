---
kind: thread
author: etrepum
domain: self.haskell
is_self: true
created: 1424552575
permalink: /r/haskell/comments/2wox0y/whats_your_best_explanation_of_haskells_nonstrict/
id: 2wox0y
name: t3_2wox0y
subreddit: haskell
subreddit_id : t5_2qh36
title: What's your best explanation of Haskell's non-strict evaluation?
url: https://www.reddit.com/r/haskell/comments/2wox0y/whats_your_best_explanation_of_haskells_nonstrict/
---

I've been trying to help people get started with Haskell for some time now via exercism.io, and one of the most common stumbling blocks I've seen people run into is developing good intuition for Haskell's evaluation.

Here are the resources I currently recommend:

* http://chimera.labs.oreilly.com/books/1230000000929/ch02.html#sec_par-eval-whnf
* https://hackhands.com/lazy-evaluation-works-haskell/
* https://wiki.haskell.org/Foldr_Foldl_Foldl'

Here are some of the early mistakes that I see very often:

    -- Should be a tail-recursive implementation with strict accumulator
    length [] = 0
    length (x:xs) = 1 + length xs

    -- foldr instead of foldl'
    sum = foldr (+) 0

    reverse = foldr (\x acc -&gt; acc ++ [x]) []

    count = foldr (flip (M.insertWith (+)) 1) M.empty

The best explanation I've been able to come up with is:
If the all of the input must be consumed in order to use any of the result, then a tail-recursive implementation with a strict accumulator (such as foldl') should be used.

Does anyone have other explanations that might be more correct or easier for people new to Haskell to understand? Or any other useful (publicly available) resources that I should link people to?
