---
kind: thread
author: ecognium
domain: self.haskell
is_self: true
created: 1438125279
permalink: /r/haskell/comments/3eylp6/testing_servant_persistent_web_app/
id: 3eylp6
name: t3_3eylp6
subreddit: haskell
subreddit_id : t5_2qh36
title: Testing Servant + Persistent Web App
url: https://www.reddit.com/r/haskell/comments/3eylp6/testing_servant_persistent_web_app/
---

I have written a small-ish API and it is getting to a point where I would like to setup some automated tests. I have not written any tests in Haskell before and wanted to see what's the best way to get started. 

I have a `servant` API server and most of my handlers use `persistent`. 

I am thinking of bootstrapping the server with some test cases in the db and then use `HSpec` + `Wreq` to create tests. I have not used either one before so open to other suggestions on how to best approach it. I would like to simulate the test as a client would see the API. 

Are there any starter examples of testing servant + persistent that I can learn from?  Since, the app uses authentication, I want to make sure I will be able to re-use some of the return values (like Auth Token) in down stream tests. 

Thanks! 
