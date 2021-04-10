---
layout: post
tags: self compsci
title: "Running Jekyll Inside a Docker Container"
---
Like I mentioned in [a recent post]({% post_url 2020-08-06-and-we-re-back %}), I was working on a custom blogging for a while. That project has been put on the back burner because I'm workin on something else that's more important but I would like to get back to it eventually, maybe as a way to learn a new programming language.

The reason I started working on an alternative to what I'm using now, Jekyll, is that I was having some trouble running it. I solved these issues by running it in a docker container. It took combining a few Google results to get it to work so I thought I'd post the command that works for my on this blog since I'm likely not the only one having trouble running jekyll directly on OSX:

<script src="https://gist.github.com/jsoendermann/1571311e4bc5d5c947f1145047621743.js"></script>