---
layout: post
title: "Monads as a first class esoterism"
categories: ["FP", "Scala"]
date: "2016-05-11 01:01:16 -0300"
---

When writing functional programs, we often operate with the so called `Monads`. In this blog, I'll try to simplify this mysticism.

I am not *stating* that knowing the [Monad Laws/Theory][4d28355e] is irrelevant, but a lot of the *buzzing* around makes people and developers believe they are some type of Guru of life when talking about `Monads`, creating some kind of obscure _impossible-to-process_ reasoning about them, when they are really more a pattern than anything else.

Let's begin with some simple snippets.

Imagine you are analyzing some word occurrences in a story. These come in lines of the following form:

````
It was with considerable reluctance that I abandoned in favour of the
present undertaking what had long been a favourite project: that of a new
edition of Shelton's "Don Quixote," which has now become a somewhat
scarce book. There are some--and I confess myself to be one--for whom
Shelton's racy old version, with all its defects, has a charm that no
modern translation, however skilful or correct, could possess. Shelton
had the inestimable advantage of belonging to the same generation as
Cervantes; "Don Quixote" had to him a vitality that only a contemporary
could feel; it cost him no dramatic effort to see things as Cervantes saw
them; there is no anachronism in his language; he put the Spanish of
Cervantes into the English of Shakespeare. Shakespeare himself most
likely knew the book; he may have carried it home with him in his
saddle-bags to Stratford on one of his last journeys, and under the
mulberry tree at New Place joined hands with a kindred genius in its
pages.
````

The strategy to make a word count would be:

- Read the file line by line and store it in a collection, for example, a `List`.
- Split each line by their separator, in this case it would be a `\\s+` or a white space character.
- Group the occurrences of each word in a `Map` or similar structure with their count.
- Make whatever analysis you want to make.

Let's see how we would go about that.

## Entering the caveats of `List`

For the first step, we need to get hold of a way to read the file, so I downloaded El Quixote de la Mancha from [Project Gutenberg][Quixote-link]. I in particular used `scala.io.Source` to get hold of the file given the path to get an `Array[String]`, with each element being a line, like this:

<script src="https://gist.github.com/tomduhourq/636137ebfabd0c0c914114a0235bab19.js"></script>





  [4d28355e]: https://en.wikipedia.org/wiki/Monad_(category_theory)#Formal_definition "Category Theory and Monads"
  [Quixote-link]: http://www.gutenberg.org/cache/epub/996/pg996.txt "Don Quixote full txt"
