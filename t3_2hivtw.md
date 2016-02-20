---
kind: thread
author: _skp
domain: self.haskell
is_self: true
created: 1411736785
permalink: /r/haskell/comments/2hivtw/minmax/
id: 2hivtw
name: t3_2hivtw
subreddit: haskell
subreddit_id : t5_2qh36
title: minmax
url: https://www.reddit.com/r/haskell/comments/2hivtw/minmax/
---

I came up with the need of using a function that retrieved both minimal and maximal value in a list. I haven’t found that function yet, so I wrote a little implementation:

    minmax :: (Ord a) =&gt; [a] -&gt; (a,a)
    minmax []     = error "empty list: minmax"
    minmax (x:xs) = foldl (\(mn,mx) a -&gt; (min mn a,max mx a)) (x,x) xs

I guess that can also be written as `minmax :: (Ord a,Foldable f)`.

What do you think? Should such a function be in `Data.Ord`, `Data.List` or whatever?
