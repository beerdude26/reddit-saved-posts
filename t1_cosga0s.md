---
kind: comment
author: julesjacobs
created: 1424525839
id: cosga0s
name: t1_cosga0s
subreddit: haskell
subreddit_id : t5_2qh36
thread_id: t3_2wnfpf
parent_comment: t3_2wnfpf
---

You can think about type classes in a similar way as you think about OOP interfaces: the only way to use the type is with the functions specified in the interface. The difference is that the v-table for type classes flows along with the type, rather than along with the values as is the case with OOP.

For specific type classes like Functor and Monad it can indeed be hard to get intuition about operations since the abstraction is so general.

For Functor it may help to think in terms of interaction. If you have some generic type `F a` you may be able to interact with it in many ways, but in the end there is only two things that can happen with values of type `a`: you can put values of type `a` into `F a`, or you can get values of type `a` out of `F a`. For example if you have the type `F a = List a`, then you can get values of type `a` out of the list. If you have the type `F a = a -&gt; Bool` you can't get a's out of it but you can put values into it. If you have `F a = (a, Bool) -&gt; (a, Int)` you can put values into it and get values out of it. A type `F a` is a Functor if you can only get values out of it, and not put values into it. So List is a functor but `a -&gt; Bool` is not. What `fmap` does is it puts a kind of post-processing step after a value. Given a function `a -&gt; b` and a value `F a`, it produces an `F b`. Whenever you want to get a value out of the `F b`, it takes the corresponding value out of the `F a`, then applies the function `a -&gt; b` to it to get a `b`. This is a covariant functor (the Functor type class in Haskell). Dually you also have contravariant functors (the Contravariant type class in Haskell). They are types where you can only put values into them, and not get values out of them, like `a -&gt; Bool`. The `contramap` of a contravariant functor does a pre-processing step instead of a post-processing step. When you have a value of type `F b`, and a function of type `a -&gt; b` then it creates a value of type `F a` by using the `a -&gt; b` as a pre-processor: every time you put a value of type `a` into it, it first converts it into type `b`, then puts it into the value of type `F b`. If a type `F a` has both inputs of type `a` and outputs of type `a`, like `(a, Bool) -&gt; (a, Int)`, then it cannot be a covariant functor and it cannot be a contravariant functor either, but it can be a bifunctor. A bifunctor does both pre-processing and post processing with the bimap operation: `f a -&gt; (a -&gt; b, b -&gt; a) -&gt; f b`. It uses the `a -&gt; b` to do post-processing and the `b -&gt; a` to do pre-processing. *Every* type is a bifunctor.

In summary: you can think of fmap as a kind of generalized post-processing, and contramap as generalized pre-processing, and bimap combines the two.

There's more than one way to think about functors in general, this is just how I think about them.

Monads are a bit more difficult to think about in general terms. One way to think about them is in terms of the continuation monad. The continuation monad is in a sense the most general monad, and any other monad is a special case of it. So if you want to know what a monadic piece of code does you can mentally substitute the continuation monad, and any other monad is going to have more restrictive behavior than that.
