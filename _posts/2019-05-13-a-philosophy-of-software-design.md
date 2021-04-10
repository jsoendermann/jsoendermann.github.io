---
layout: post
title:  "Book Notes: \"A Philosophy of Software Design\""
tags: compsci books
---
<img style="max-width: 50%; float: left; box-shadow: 0 14px 28px rgba(0,0,0,0.25), 0 10px 10px rgba(0,0,0,0.22); border: none; margin: 0 40px 20px 0;" src="{{ '/images/phil-software-design.jpg' | relative_url}}">

If you want to become a better programmer and you look for books to read, the same titles will keep coming up. *Clean Code* and *The Pragmatic Programmer* are both classics that I see recommended constantly. After reading those and a few other, I came to the conclusion that this type of book wasn't for me. To me, it felt like they  combine trite and useless advice like "your code should be simple, not complicated" with ideas that sound like they'd help but actually end up making code worse like "shorter functions are always better than longer ones."

<!--break-->

This was my attitude when I started reading "A Philosophy of Software Design" by John Ousterhout. It's a short book of about 150 pages of A5 but it still took me a week to finish since it's so dense. If you read programming books to confirm what a rockstar coder you already are, reading this book will be a frustrating experience: it's full of controversial opinions, some of which you'll probably disagree with. If, however, you're looking to have your opinions challenged and want to learn a new way to think about code complexity and what to do about it, this might be the book for you.

The rest of this blog post is a combination of my highlights with some of my own opinions on them.

## Complexity

The foundational concept the rest of the book concerns itself with minimizing.

### Symptoms

1. **change amplification:** making a change to the system needs modifications to the code in many different places
2. **cognitive load:** things for the programmer to keep in mind, he gives `malloc` as an example since you need to remember to `free`
3. **unknown unknowns:** non-obvious things the programmer needs to know to accomplish a task

### Causes

1. **dependencies:** a piece of code cannot be understood or modified without another piece
2. **obscurity:** important information that is not obvious from looking at the code

## Deep modules

The book uses modules in a general sense as anything that allows hiding an implementation behind a public interface. This could be a class or a function, or something else, depending on the programming language. These modules are "deep" when they hide a substantial implementation and design decisions behind a simple interface. These decisions should not leak to other modules. 

Design focusing on the knowledge that's needed, not on order.

Representations used internally should be different from those used in the interface.

Choose simplicity of your interface over simplicity of its implementation.

When introducing configuration parameters, ask yourself if a user of your module can make a better decision than you can right now.

Separate general code from special-purpose code.

Each method should do one thing and do it completely.

## Errors

When possible, define errors out of existence, e.g. by turning errors into noops.

## Comments

Capture ideas that are in your mind at the time of designing your code but that aren't reflected in the code.

Consumers of your module should not have to read its implementation.

Augment your code by providing comments at a different level of detail.

Separate interface comments from implementation comments.

*What* and *why* not *how*.