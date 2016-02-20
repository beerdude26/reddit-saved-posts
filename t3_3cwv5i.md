---
kind: thread
author: quchen
domain: self.haskell
is_self: true
created: 1436623095
permalink: /r/haskell/comments/3cwv5i/haskells_type_system_eliminates_entire_classes_of/
id: 3cwv5i
name: t3_3cwv5i
subreddit: haskell
subreddit_id : t5_2qh36
title: "Haskell's type system eliminates entire classes of bugs" - which ones?
url: https://www.reddit.com/r/haskell/comments/3cwv5i/haskells_type_system_eliminates_entire_classes_of/
---

The claim is true in most of our experiences, but as hard of a selling point as "makes you a better programmer" is. I was wondering what kinds of bugs people found in other languages that would have been impossible in reasonably written Haskell code.

- Null pointers are impossible
- "What are the legal values of this parameter" is usually trivial to answer
- Wrong argument order is likely to cause type errors
- Wrong argument count *will* cause type errors
- Calling a convenience function never changes that function (e.g. a "validate" function that resets some counters, which I've recently seen)

I think summing up these kinds of things with one paragraph each would make the argument much stronger.
