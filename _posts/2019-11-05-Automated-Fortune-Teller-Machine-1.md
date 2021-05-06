---
layout: post
title: "Automated Fortune Teller Machine – The First"
tags: compsci raspberrypi greatest-hits
---
<img style="max-width: 50%; float: left; margin-right: 2rem; margin-top: 0;" src="{{ '/images/aftm/hero.jpg' | relative_url}}">

A few months ago I came across Lea Albaugh’s [wonderful writeup](http://lea.zone/fortune.html) of a fortune telling machine she built for a friend’s wedding. You should absolutely go and read her blog but in summary, people would choose three cards from multiple decks, each with a one word theme on it, stuff like “symbol”, “mystery”, “contentment” and others that were more relevant to the wedding. They would then insert a coin from a jar of play money and be printed a fortune that was in some way related to the three words they picked. After having had some recent contact with the esoteric and the occult and since I’m always on the lookout for cool projects for my Raspberry Pis, I was immediately inspired to build something similar.

I started out wanting to make something pretty close to the machine described in the post. As I kept mulling the idea over in my head, however, it eventually morphed into something that seemed worthy of its own blog post. The machine that I did end up building got its first public test run at our house warming party two weekends ago. Since seeing it being used by the guests we invited gave me lots of ideas of how to improve it, I decided to write this post with what I’ve built so far and some ideas for version 2.

Since my version of the fortune telling machine was originally designed to be used at a festival (that I didn’t end up going to), I wanted to add a social component to it. Specifically, I wanted fortunes to come with tickets for more fortunes, so that people would have to go and meet people that had already received a fortune to get one for themselves. Initially, I tried to come up with some way to use play money coins for this, like in the original version, but eventually switched to passphrase that would be printed together with the fortunes. This meant that I had to include some way to enter these passphrases. Using a touch display for this was my first idea, however I couldn’t come up with a way to integrate the display into the machine in a way that felt natural. I wanted the machine to have an impersonal and inscrutable feel to it since the randomness of automatically generated fortunes are what I enjoy most about them.

At around the same time, I saw a grand piano somewhere and decided I wanted to use that polished black/gold aesthetic for my machine. Since I started thinking about wood and metal, I came up with the idea of using a grid of mechanic flip switches to enter a passphrase. I still think this would be very cool but didn’t have enough time in the end to build it. The shape I had settled on by then was that of a pyramid and after seeing the pyramid on the back of a dollar bill I had brought back from a trip to the US for some dollar origami, I eventually decided to put a camera in the tip of the pyramid and use QR codes as passphrases. The writing on the front of the pyramid is inspired by a picture of a Bösendorfer grand piano I found online. I tried to make the golden tip of the pyramid look like it floated the way it does on the dollar.

![cardboard]({{ '/images/aftm/cardboard.jpg' | relative_url}})
*The outer shell*

For the actual fortunes, I decided to make selection purely random. I am intrigued by the idea of getting a fresh impulse, new perspective or otherwise disruptive suggestion that horoscopes and fortunes can bring. Emma and I started to write and collect poems, quotes and ideas for fortunes but since the first version of the machine was built in a rush, I ended up just generating tarot fortunes based on the tarot interpretations corpus linked on Lea’s blog. At the bottom of each fortune, I added two QR codes that could be used to get more fortunes.

![lego]({{ '/images/aftm/lego.jpg' | relative_url}})
*Building material for the interior structure*

The shell of the machine was made out of cardboard. Since I have neither access to nor expertise in using a 3D printer, I ended up building the inner structure with a building material I have decades of experience in: legos. This worked reasonably well, although for version 2, I’ll try to think of a better way to hold the printer in place. I used a raspberry pi 3b, the adafruit thermal printer and a cheap camera from Amazon to build the machine. The code was hacked together on the Saturday of the party and is preserved on github for posterity (don’t click if you don’t want to see some truly awful python code.)

![hacking]({{ '/images/aftm/hacking.jpg' | relative_url}})
*Last minute hacking*

Figuring out how to print QR codes with the thermal printer was by far the most difficult part of writing the code. I had to generate the code with a package that outputs PIL images, invert it and then convert the result from an array of monochrome pixels to an array of bytes in which each element represented eight pixels, byte aligned to the width of the code. Apart from that, the only other noteworthy part of the code is that it loads fortunes from a toml file saved in an s3 bucked on start up. The idea here is that I could install the pyramid in some location and keep adding fortunes from home.

![qr]({{ '/images/aftm/qr.jpg' | relative_url}})
*Getting QR codes to print*

![innards]({{ '/images/aftm/innards.jpg' | relative_url}})
*The innards of the machine. The umbilical cord is also visible.*

## The Party

All in all, everything went pretty well and I was very satisfied with the results. The fortune telling machine was a big hit and from what I could tell almost every guest ended up playing with it during the course of the evening. After I had showed and explained it to the first few guest, very quickly people started showing other guests they had only just met, offering the QR codes they had gotten with their fortunes. The idea of encouraging social interaction through the chain of codes worked just as I had imagined and was the most fun for me to observe. The exponential explosion of codes that I had anticipated did not happen as codes kept disappearing. I had hardcoded a special QR code I carried on me that never expired to allow me to generate more codes as required. I used this code a few times during the course of the evening but I assume that better explanations on the printed artefacts would lead to fewer codes going unused.

![ready-to-go]({{ '/images/aftm/ready-to-go.jpg' | relative_url}})
*Everything set up and ready to tell*

The hardware held together surprisingly well. I had placed a pair of scissors in front of the pyramid since tearing off fortunes was quite hard and required just the right amount of force. A few times, I had to lift the shell and reset the printer either by closing it (pulling on the paper caused the printer cover to open up) or re-inserting the paper into the slit in the cardboard. I still haven’t decided what to do about this but it would be nice to devise of some way to make printing and tearing off fortunes more robust and reliable. The part that worked least well was recognising the QR codes. This was a combination of a bad detection package, a very narrow angle on the camera I was using and wrong focus setting. I only learned after the party that pi cameras come with manual focus controls. I bought a wide angle lens that looks great and will add to the look of the machine once it’s been integrated which, in combination with adjusted focus and better detection code, will hopefully solve this issue.

![in-action]({{ '/images/aftm/in-action.jpg' | relative_url}})
*The machine in action*

Generally, the machine could probably do with slightly more instructions. I don’t want to overdo it since people introducing others to it and explaining how they could get their own fortunes is a big part of what I wanted to build but some of the shyer guests seemed to have been intimidated by the lack of guidance. The fact that QR codes could only be used once was documented nowhere and so had to be explained by me. This, in combination with the fact that scanning codes sometimes took up to a minute because of the problems with detection so, made for a frustrating experience when things didn’t work. I was surprised and encouraged by how much persistence people showed in getting their fortune. This was at least partly due to the fact that the fortunes from the corpus made for a great combination of cheesiness, shared laughter and traditional horoscope experience.

![aftermath]({{ '/images/aftm/aftermath.jpg' | relative_url}})
*The aftermath*

I had considered putting a speaker inside the machine and giving feedback and instructions that way, however that definitely would not work for a noisy party setting. Right now, I am leaning towards adding a small screen above the slit for the printer. This would make the machine somewhat less impersonal, since it would be communicating through the screen but if done right, could also add a cool dimension.
