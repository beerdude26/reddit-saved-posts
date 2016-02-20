---
kind: comment
author: AlpMestan
created: 1433601097
id: crxj2bx
name: t1_crxj2bx
subreddit: haskell
subreddit_id : t5_2qh36
thread_id: t3_38rusu
parent_comment: t1_crxii0y
---

We (well, Andres Löh, mostly) have revamped the internals of the routing machinery to make it sublinear and also overall nicer and easier to work with. Aside from faster routing, this gives us a better story for auth, good enough that we might provide generic combinators (that Aaron Levin started working on) for that, probably just requiring an auth lookup function from the user or something. This is what is hinted at by Andres at the very bottom of this thread. I think it is safe to say that we will "soon" have a module or package that facilitates auth-protecting (parts of or entire) APIs while leaving the specifics of the auth backend for you to provide, just by using a couple of types (combinators) and functions.

In the meantime, I have been using [various](http://github.com/zalora/sproxy) [options](https://hackage.haskell.org/package/wai-extra-3.0.7.1/docs/Network-Wai-Middleware-HttpAuth.html) (but also http servers in front of the app that serve as proxies which filter requests using digest auth). Looking forward to what will come out of #70.
