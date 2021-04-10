---
layout: post
tags: compsci
---
**Update**: A poster about this project was accepted to [Euro LLVM][eurollvm]. Come and say hi if you're going!

Anyone who has ever had to write code in Matlab, scipy, R or any other
scientific computing framework/language will realise that [Julia][julia] is
a Good Idea: an open, properly designed programming language for
science. I've played around with Julia a couple of times so I was very excited when I got the chance to work on a Julia related project for the [Modern Compiler Design][l25] course here in the Computer Lab. 

[The result][pdf] turned out quite interesting, I use the LLVM polyhedral optimisation framework polly to hoist the array bounds checks that Julia generates for all array accesses out of loop nests. This brings a speed up in itself but the true advantage it brings is that it makes futher optimisations of the loop nest possible.

[julia]:        http://julialang.org/
[l25]:          http://www.cl.cam.ac.uk/teaching/1415/L25/
[pdf]:          /files/report_mcd.pdf
[eurollvm]:     http://llvm.org/devmtg/2015-04/
