---
kind: comment
author: PM_ME_UR_OBSIDIAN
created: 1429630789
id: cqjpnr3
name: t1_cqjpnr3
subreddit: haskell
subreddit_id : t5_2qh36
thread_id: t3_33chyv
parent_comment: t3_33chyv
---

&gt;There is a stark contrast in the way OO languages and Haskell should be looked at. In OO languages, we try to answer the question “*What can we do with data?*” whereas in functional languages we try to answer the question “*How is data constructed?*”.

I used to fervently disagree with this. However, I've been working on a term paper on the algebra-coalgebra duality, and it seems that functional programming maps to algebra while OOP maps to coalgebra. For example, classes can be defined through copattern-matching! I grudgingly changed my mind - this research completely redefined OOP for me.

&gt;Think more and type less

Funny, for me FP is "think less and type more" - i.e. static types lighten the cognitive burden of programming!

&gt;Haskell is *lazy*. There is no particular order in which functions will be evaluated

There is an order, it's called "outside-in". Outer definitions are expanded first. This has an impact on memory usage, for example.

&gt;     printToScreen :: String &gt; IO ()

Syntax error: should be `-&gt;`, not `&gt;`.

&gt;This is because Haskell expects you to pass a `String`, but in reality a `Num` is passed to it.

There's a conceptual error here. An `Integer` is being passed, which implements the `Num` typeclass. It would technically be possible for `String` to implement `Num` (though it wouldn't make any sense). What you meant is "...in reality an `Integer` is passed to it".

Think of typeclasses like interfaces in Java. They're not exactly the same thing, but they serve a broadly similar purpose.

&gt;     pair :: l1 l2 = [(x, y) | x &lt;- l1, y &lt;- l2]

What's the reason for the `::` here? Also, [here's an interesting alternative way to do it - kind of a mind twister.](http://stackoverflow.com/a/4119898/1056174)

Finally - welcome to Haskell. As a first advanced topic, I recommend [free monad composition](http://programmers.stackexchange.com/questions/242795/what-is-the-free-monad-interpreter-pattern). Basically, you design a set of domain-specific languages which you compose together for your application. Among other things, this makes unit testing extremely easy. The best resource I know on the subject is [this talk](https://www.parleys.com/tutorial/composable-application-architecture-reasonably-priced-monads), however it's in Scala.
