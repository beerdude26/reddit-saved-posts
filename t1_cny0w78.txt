---
kind: comment
author: sh0rug0ru
created: 1421989365
id: cny0w78
name: t1_cny0w78
subreddit: haskell
subreddit_id : t5_2qh36
thread_id: t3_2tbbxh
parent_comment: t1_cny0g47
---

That's because we usually think of lists based on the basic list operations, like cons, folds and maps, which is the common vernacular with other FP languages. The list monad is also a cool execution environment. The IO monad is an execution environment for IO actions, an environment which interacts well with other Haskell types.

When I say "use the list monad", I mean use the list execution environment. When I say "use the IO monad", I mean use the IO execution environment. When I say "use the xyz monad", I mean use the xyz execution environment.
