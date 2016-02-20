---
kind: comment
author: Drezil
created: 1438021050
id: cti0qj0
name: t1_cti0qj0
subreddit: haskell
subreddit_id : t5_2qh36
thread_id: t3_3esjzc
parent_comment: t1_cthzfc9
---

i would throw in mtl/transformers, too.

And attoparsec (as a concrete example on how to use little combinators for parsing).

Generally in Haskell its: Build small blocks, compose them together.
In many languages this cannot be done (because of improper/asynchronic error-handling, not enough abstraction or other causes). So its "understand the little, understand the big".

In this sense i would recommend the Typeclassopedia (https://wiki.haskell.org/Typeclassopedia) for the general abstractions which get used inside the other given libraries.

edit: i learned it best when looking at examples of stuff (esp. RWST, attoparsec, yesod) and then read the "abstract nonsens" on typeclassopedia for a more general view.

i "understood" lenses after https://skillsmatter.com/skillscasts/4251-lenses-compositional-data-access-and-manipulation monads after https://www.youtube.com/watch?v=b0EF0VTs9Dc and stm after https://www.youtube.com/watch?v=hlyQjK1qjw8 .. but thats just my opinion. YMMV.
