---
layout: post
title: "Forgot To Stash"
date: "2016-07-06 09:35:36 -0300"
categories: git
---

It is a very common thing to be working on multiple branches when coding. We do this to be neat and maintain our working environment tidy. So yesterday I found myself working on two branches, namely **A** and **B** for simplicity. **B** branched out from **A** because it involved a dependency coming from **A**.

The problem came that **A** had broken tests that **B** would eventually need to continue it's work. But guess what? I did the corrections on **B** for broken tests of **A**.

So I thought: _"What would be the best way to keep my changes I did to **B** and only extract the corrected test for **A**?"_

`git stash` knows it's way. But careful!

`git stash` will grab *EVERYTHING* you've been doing on that branch, and for this case I didn't want that. So, I found out that there's a neat extra param `-p` for you to control what you'll stash out.

It will take you _file per file_ showing you what can you stash:

- If you want to stash the whole file being shown, just `a` on the snippet and the whole file will be stashed
- If you want to stash only the part being shown `y`
- If you don't want that change, `n`
- If you just want to quit and leave the remaining snippets/files unstashed, `q`

After finishing, you'll be left with either what you have chosen as unstashed (being that the result of consequent `n` or `q`) or everything clean because you have stashed everything, leaving in this case `-p` useless, just `stash` the whole thing in that case.
