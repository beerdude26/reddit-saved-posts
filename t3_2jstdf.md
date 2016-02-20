---
kind: thread
author: fluffynukeit
domain: self.haskell
is_self: true
created: 1413824727
permalink: /r/haskell/comments/2jstdf/what_is_your_experience_with_making_haskell/
id: 2jstdf
name: t3_2jstdf
subreddit: haskell
subreddit_id : t5_2qh36
title: What is your experience with making Haskell plugins?
url: https://www.reddit.com/r/haskell/comments/2jstdf/what_is_your_experience_with_making_haskell/
---

I spent a lot of time this past weekend trying to implement some "plugin" functionality for my project.  My program processes data written in different, custom file formats, and I thought it would make sense for each format to be handled by a different plugin.  Need to read a new kind of file?  There's a plugin for that.  Drop the plugin into the right location and you're good to go.  At least that's the idea.  I wasn't looking for anything fancy like supporting arbitrary languages in plugins: just plugins written in Haskell (possibly using C library and bindings) that get used by a Haskell program.

In practice, the waters are rather muddy, and it seemed like every couple of steps I took, I would get some new insight or feedback telling me I was on the wrong path.  There are old blog posts, newer blog posts, allegedly "broken" libraries (plugins), arguably newer and working libraries (hlint), the capabilities of the GHC API (again, old vs new) and digging through its scarce documentation and large codebase, pre-compile vs compile the source vs interpret the source, ghc flags -static -dynamic -shared -fPIC, static lib vs shared lib, plugins written in Haskell to be used by other languages and include the GHC RTS inside, cabal flags and options, "home modules", "interface files", including dependencies or not, not being able to find dependencies, current ghci requiring .so files (I think?), interprocess comm, and probably a quite a few other issues.  These were the ones I remember off the top of my head.

So after spinning my wheels, I thought I should take a breath and ask the community.  What is your experience with writing plugin functionality for Haskell?  What scope is feasible, and what is possible?  Is it as much a science project as my recent experience suggests?  Are there smarter approaches to take?  Are there any active projects that successfully make use of plugins?  Any insight is much appreciated!
