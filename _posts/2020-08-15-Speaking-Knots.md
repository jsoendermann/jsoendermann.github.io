---
layout: post
tags: random greatest-hits
title: "Speaking Knots"
---
![door]({{ '/images/knots/door.jpg' | relative_url}})

The other day I watched "See" on Apple TV+. The premise of the show is that after some apocalyptic event, humanity has lost its sense of sight and all humans are born blind. I quite enjoyed watching it but I can’t say I care much whether it gets extended for another season.

Anyway, one thing they do in the show is tie knots in strings and ropes to communicate. People trace the strings with their fingers, reading them like books. The system is never explained in much detail but people in the show are able to send messages that way. I thought this was a very cool idea and started thinking about how to design a system like that.

Initially, I considered a knot-based morse code with either two types of knots or the presence/absence of one type of knot to represent dots and dashes. Since that would mean up to five knots per letter, however, and I wanted to keep the number of knots as low as possible, I decided to come up with my own encodings of the Latin alphabet. To keep things simple, I used a fixed number of knots per letter.

Given these constraints, I had to decide how many different types of knots my system would be based on. Since there are 26 letters in the English alphabet, the only numbers that make sense are 2, 3 and 6. Two types of knots require five knots per letter, three types require three knots and six types require two.

My last major contact with the world of knots was as a young boy on vacation with my parents at the North Sea coast, learning about knots used on fishing ships. Since I don’t remember much about those knots, I hit google to see what was on offer. Turns out that (like for everything in this world) there is a community of knotters online. 

To be suitable for this projects, the knots had to fulfil the following requirements:
- **Distinctiveness**: they had to be distinct to the touch so that the “reader” could tell them apart without needing a sense of sight.
- **Pull resistance**: I’m sure there’s a term of art for this in professional knot tying. The knots should not come undone when pulling on opposite ends of the string.
- **Placability**: choosing a location on the string and placing the knot there should be easy. This is probably true for all knots with sufficient practice but it’s easier for some than for others.
- **Locality**: it should be possible to tie the knot without having to pull through one end of the string. Turns out there’s a phrase for this, knots of this kind are [tied in the bight](https://en.wikipedia.org/wiki/Bight_%28knot%29%23In_the_bight).

![test-knots]({{ '/images/knots/test-knots2.jpg' | relative_url}})
*Testing different knots. Turns out twisted twine is not ideal for tying knots.*

After an evening of playing around with different knots, these are the ones I ended up choosing:

- [**Overhand**](https://en.wikipedia.org/wiki/Overhand_knot): this is the most fundamental knot and my go-to to tie anything together.
- [**Butterfly**](https://en.wikipedia.org/wiki/Butterfly_loop): this knot creates a nice distinctive loop.
- **Butterfly + 1**: this is what I called a butterfly knot with an additional overhand knot in the loop.
- **Butterfly + 2**: same as above but with two overhand knots.
- [**Barrel**](https://www.101knots.com/barrel-knot.html): this knot creates barrel along the string.
- [**Double figure-eight**](https://en.wikipedia.org/wiki/Double_figure-eight_loop): a knot that forms two loops.

Six knots with two knots per character give us 6^2 = 36 possible combinations which is exactly what we need for 26 letters and 10 digits (no spaces or lowercase letters exist in this encoding). One optimisation I made in mapping these combinations to the different letters and digits was to assign each knot a difficulty value (turns out I was pretty off in my guesses of how difficult each knot would be to tie). Each possible combination of two knots then had a combined difficulty equal to the sum of the difficulties of each constituent knot. I assigned the letters in order of frequency such that the most frequent letters would be easiest to tie, the remaining ten combinations I assigned to the ten digits at random. This is the mapping I ended up with:

![test-knots]({{ '/images/knots/mapping.jpg' | relative_url}})
*Mapping knots to letters & digits.*

Reading about knots online, I discovered that paracord is the medium of choice for people who pursue this hobby. I got some and it is a much more pleasurable experience to tie with compared to the cheap twine I was using before. Another purchase I made was what seems to be the authoritative source on knots: The Ashley Book of Knots. I have only skimmed the book so far but if I ever make a version two of the speaking knots, I’m certain it will be a repository of possible knots to integrate into any future encoding.

After tying a few one letter strings, I eventually tied this seven meter beast:

![human-rights]({{ '/images/knots/human-rights.jpg' | relative_url}})
*"All human beings are born free and equal in dignity and rights"*

After trying out the system, here are some things I learned about the different knots:

- **Overhand**: the fact that this is not tied in the bight makes this much more annoying to tie than I first thought. I would not include this knot again for this reason.
- **Butterfly**: this knot and its variants are perfectly suited for this project and don't have any downsides.
- **Barrel**: this knot is aesthetically pleasing but not only is it not tied in the bight, it needs three pull-throughs to be completed! There does seem to be a variant of it that doesn’t have this downside but I haven’t played with it yet.
- **Double figure-eight**: this knot works but it wastes a lot of string and has a very thick main part that the two loops grow out of. It’s also hard to distinguish from the butterfly by touch alone.

I might decide to spend more time on this project in the future but for now, I’m happy with how much fun I’ve already had with it. If I do, these are some ideas for possibly improvements and additions:

- Different knots/different mapping based on what I learned about the knots I chose.
- Some way of preventing the reader to get out of sync with which pairs on the string form the letters. If either the author or the reader of the message accidentally skip one knot, the message ends up garbled. This isn’t a big issue since when that happens, all that’s required is to shift one knot and try again. 
- Single knots for common letters or even words to speed up the tying process. This would also help with synchronisation. 
- Some way of indicating the direction a string is meant to be read in. Maybe a bead tied into the string. I considered beads also as part of the encoding but decided against it so that no additional material would be needed to write a message.
- Splicing together pieces of string. The [blood knot](https://en.wikipedia.org/wiki/Blood_knot) should make this possible. Since it looks very similar to the barrel knot that’s part of the current encoding, I would probably have to choose between the two. This could indicate a space. Assembling longer messages from multiple pieces of string would also somewhat solve the problem of having to tie knots that are not died in the bight in long pieces of string.
- The distance between two knots could be integrated into the encoding and assigned some significance.
- Maybe some completely different way of encoding meaning that isn’t based on the Latin alphabet. [Shorthand](https://en.wikipedia.org/wiki/Shorthand) could be a possible source of inspiration for a writing system that is designed for speed. Googling for similar ideas, I found the [Quipu](https://en.wikipedia.org/wiki/Quipu) system used by the Inca people. I couldn’t find much about how specifically it worked and maybe that knowledge isn’t extant but it would be cool to learn more about it.