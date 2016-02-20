---
kind: comment
author: deviant-logic
created: 1433382877
id: cruvfqc
name: t1_cruvfqc
subreddit: haskell
subreddit_id : t5_2qh36
thread_id: t3_38g5ts
parent_comment: t3_38g5ts
---

It's important to distinguish between 'closures' and 'first-class functions with lexical scope'.  People will rightly point out (and have) that closures are an implementation detail---in particular, closures are a technique for *implementing* first-class functions with lexical scope.  (The technique is just to represent the function-with-lexical-bindings as a pair of the bindings which are in scope when it's created and the actual code of the function).

In Haskell, bindings can't be mutated, so the idea of a closure hiding mutable state the way an object does in a more OO language doesn't really make sense.  However, in Scheme, say, variables are mutable.  Once you have mutable variables in your language, you're eventually going to want some way to hide your mutable variables from others and share them between your own functions.  The way OO languages provide mechanisms to deal with these necessities is via baroque systems of classes, objects, fields, methods, access control, inheritance, subtyping, and so on.  And that's a lot of machinery to handle \begin{functional-programmer-ranting}what *should be* the *extremely rare*\end{functional-programmer-ranting} cases where you actually need mutable state.  Since you want a language that doesn't absolutely suck to use, you already have first-class functions, obviously, and so it's worth observing that you can take advantage of lexical scope and first-class functions to do all the data-hiding, etc. stuff you need.

An interesting historical note can be found in http://deptinfo.unice.fr/~roy/JAOO-SchemeHistory-2006public.pdf, which is the slides from Guy Steele's talk on the History of Scheme.  Starting on slide 18, he discusses the evolution of Scheme as an experiment to understand objects and actors.
