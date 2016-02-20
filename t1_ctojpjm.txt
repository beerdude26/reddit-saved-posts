---
kind: comment
author: aseipp
created: 1438486712
id: ctojpjm
name: t1_ctojpjm
subreddit: haskell
subreddit_id : t5_2qh36
thread_id: t3_3fh21j
parent_comment: t3_3fh21j
---

It's really about correctness, here. From an implementors point of view, you don't even need GADTs for the first example, you can use phantom types - and even then, the real difference is in the type signature of `eval :: Expr a -&gt; a` vs `eval :: Expr -&gt; Evaled`.

Remember, when you ask for something like `id :: a -&gt; a` there are really only so many actual definitions of this function that can exist. That is, parametric type variables are a form of abstraction/constraint, in the sense you must work with any `a` - so you can't touch it.

What this basically means is that *it is much more likely your GADT version is correct*. That's the real benefit - because it has more constraints imposed on the implementation: for your second program, there are a lot more 'type checkable' definitions that would be an incorrect implementation, e.g. `eval _ = EvaledB $ B True` type checks but is totally wrong. You can't make such mistakes with a GADT or phantom-types approach.

As a side note, a GADT like this:

    data Foo a where
      Frob :: Int -&gt; Foo Int
      Blob :: Bool -&gt; Foo Bool

Translates roughly into a thing like this (you can actually write this too if you use `-XTypeFamilies`):

    data Foo a
      = (a ~ Int) =&gt; Frob a
      | (a ~ Bool) =&gt; Blob a

So when you say something like `Frob 2` you're really carrying around a type equality constraint, saying that the type variable `a` is `Int`. So GADTs form a kind of witness for a type equality. But also GADTs are really about how you index/access the `a` too: pattern matching will automatically refine the types of some variables for those particular cases. For example, GHC refines the type variable in your first example to be `Int` or `Bool` depending on if you match the first two patterns.
