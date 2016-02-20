---
kind: comment
author: continuational
created: 1438589305
id: ctpph0j
name: t1_ctpph0j
subreddit: haskell
subreddit_id : t5_2qh36
thread_id: t3_3fk2b3
parent_comment: t1_ctpoqx7
---

I think he's referring to the realization that `IO a` is a value, and not something that performs side effects on its own. That means you can re-use an `IO a` value to perform the same effect multiple times, eg:

    myAction :: IO ()
    myAction = putStrLn "hello"

    main = do
        myAction
        myAction

