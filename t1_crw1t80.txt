---
kind: comment
author: RedditWithBorders
created: 1433472352
id: crw1t80
name: t1_crw1t80
subreddit: haskell
subreddit_id : t5_2qh36
thread_id: t3_38kuzk
parent_comment: t1_crvtd8s
---

I did deployment manually. I pretty much followed the README I created in my Github repo, except for one small change.

To run in 'production', I used upstart/initctl on Ubuntu following [this SO answer](http://stackoverflow.com/a/11304866). If you want your process to be automatically reloaded, I think you can add `respawn` to the configuration script.

Since I was running on a droplet with 512mb RAM, I had to create a temporary swap file, described in [this SO answer](http://stackoverflow.com/a/28207691), in order to install cabal and the dependencies.

I currently have no health checks in place for my website. It won't automatically respawn, either. I haven't noticed any performance problems (yet). I get about ~400 visitors per day, so I don't see performance being an issue just yet.

I'm starting small and scaling as necessary. I hope that answered some questions, but if you want to know something specific, I'll try to answer it.
