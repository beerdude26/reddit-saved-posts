---
kind: thread
author: TheCriticalSkeptic
domain: self.haskell
is_self: true
created: 1422067474
permalink: /r/haskell/comments/2th4ks/how_i_learned_to_understand_monads/
id: 2th4ks
name: t3_2th4ks
subreddit: haskell
subreddit_id : t5_2qh36
title: How I learned to understand Monads
url: https://www.reddit.com/r/haskell/comments/2th4ks/how_i_learned_to_understand_monads/
---

Since learning about Monads, I've also learned about Traversable, Foldable, Lenses, Conduits/Pipes and a myriad of other concepts that are super useful. But the language embeds so many useful structures in Monads, I just don't think a new person can get very far without learning them.

I want to talk a bit about my journey to understanding Monads to discuss what I think is missing a little from all the talk, discussion, wiki articles, tutorials and blog posts.

When I first had something "stuck" in a Monad and wanted to get it out I gave up. In the end I decided to thread a state around manually. Then it happened a second time and a third time. Eventually I learned I could chain things together using `&gt;&gt;=` to do the same thing. I learned I could do this:

    someFunction :: MyData -&gt; a -&gt; (a,MyData)
    -- transform to this, and bind together a chain of them with
    someFunction' :: a -&gt; MyType a
    -- and eventually, instead of writing my own I could use State
    someFunction'' :: a -&gt; State MyType a

I finally thought I got it. Then I had a `[MyData a]` and needed to get `MyData [a]` and learned about sequence. And then I thought I understood Monads.

Then I had something like this: `foo a &gt;&gt;= bar &gt;&gt;= foobar &gt;&gt;= etc...` and learned that `do` notation wasn't just for IO. And then I thought I understood Monads.

Then I realised the difference between a type constructor and a data constructor. I learned I could `map Just xs` using the Just constructor like I could with any other function. Then it hit me that "everything is a function" including Monads.

And then I wrote my own `join` function (I even called it join) before discovering I'd seen it before. Then I realised realised bind was `join . fmap`. It started to occur to me that I never really understood Monads when I first thought I did. But when I eventually got to mapM, mapM_, foldrM, etc. I was really starting to get a hang of it.

And then I learned how `ST s` threads an existential `forall s` around to prevent a mutable state from leaking. And boy did that turn my understanding upside down. I started to learn why `unsafePerformIO` and other unsafe functions were named as such.

Most recently I learned how to use Transformers so that I could "lift" functions from all the Monads in my stack to a single type.

**So what?**

Where am I going with this? What I realised I needed was a volume of exposure.

Before I get to that, I'd like to say that I could have used a bit of a Rosetta Stone. I actually don't know if this would help other many people, but eventually I realised that if Monads could work in OO, they might look like this:

    Interface Monad&lt;A&gt;
    
    public static final Monad&lt;A&gt; return(A a);
    public static final Monad&lt;A&gt; join(Monad&lt;Monad&lt;A&gt;&gt; mma);
    public static final &lt;B&gt; Monad&lt;B&gt; bind(Function&lt;A,Monad&lt;B&gt;&gt; f, Monad&lt;A&gt; ma);

I mean, it's not like there aren't OO languages with type signatures. Granted such an interface isn't possible in any OO language I know (especially return). But it is possible to implement on a per Monad basis. And I actually did a few tests with Java writing my own Maybe (side note: wow that was hard... Either would have been way easier than Maybe. How did I ever work without multiple data constructors?).

So that was one problem: the idea that the concept couldn't be explained in terms I already knew was pretty prevalent. I don't think we necessarily need to tell imperative people that everything they've learned so far is wrong.

The other problem was a lack of "complete" examples. I consider Monad (like any type class) to be ~~equivalent to~~ almost but not entirely unlike an OO interface. Like any interface it has a lot of really useful functions. I found most of them by getting stuck and typing stuff like `m (m a) -&gt; m a` into Hoogle and hoping it existed.

One could quite easily explain how all of the key functions work using just Maybe and Data.Map. Everything from `fmap` to `sequence` could be covered by example because of the `lookup` function. e.g. `M.lookup a mb &gt;&gt;= \b -&gt; M.lookup b mc`. It could also be a good opportunity to learn about some of the Maybe specific functions (e.g. the difference between `catMaybes` and `sequence`).

Then expand on examples for Either, State, Reader, Writer, etc. etc. I admit these wouldn't come as easily, but the idea would be to teach people "*a* Monad" rather than "Monads". 

Basically, instead trying to figure out "What is a Monad", I could really have used a whole bunch of examples for different ways to use the Monadic "interface" to solve a problem. A potential downside to this is that you risk oversimplifying the usefulness of having a Monad. On the other hand, learning to use a particular Monad in its full, one at a time, could also be helpful.

I certainly don't think it should be the only way to teach Monads. But volume of exposure was a key part of my understanding. And there were a lot of resources explaining the theory and the "big picture" (the "depth") rather than examples of use (the "breadth").

**LYAH**

I thought LYAH was great and it sort of does [what I described above](http://learnyouahaskell.com/a-fistful-of-monads). But it falls over in a few places:

1. It spends heaps of time on the theory and talking about "Monads" as this esoteric thing
2. It delves into MonadPlus as part of the first lesson on Monads... I'm not really sure why `guard` gets introduced so early, when `join` happens on the next chapter and `sequence` is omitted entirely. It does at least spend a decent time on `mapM_`, `foldM`, etc.
3. There are 2 "projects" I guess you could call them, but no exercises (I'm aware this is a general criticism people have)
4. It doesn't cover the same ground for each Monad, so it's hard to really get a sense that its reusable syntax. 

I remember getting up to that section and actually wondering whether or not I made a mistake learning Haskell. It all just seemed too hard. I persevered and went and read the million Monad tutorials people had written and eventually learned enough to be able to have this criticism of it. Don't get me wrong, LYAH is excellent, but I'm sure I'm not the only one that got lost at that point.


About 6 months in to Haskell and I thought I'd share my thoughts. Hopefully I didn't ramble too much. I feel like I've not just learned a new programming language but a new way of thinking. The digital world would be a better place if more things were written in Haskell. I hope we can do more to encourage newbies.
