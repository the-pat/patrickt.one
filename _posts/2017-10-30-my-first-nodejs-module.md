---
layout: post
title: "My First Node.js Module(s)"
date: 2017-10-30 18:42 -0600
---

Over the past few weeks I have really started to enjoy [Node.js](https://nodejs.org).

For those unfamilar, Node.js provides
> an asynchronous event driven JavaScript runtime...to build scalable network applications.

What I have really loved while dipping my toe into the water is the simplicity of simple publishing Node.js modules (or packages).
To begin learning about Node.js, I decided to write a simple wallpaper changer. This was my [reddit-node-wallpaper](https://github.com/the-pat/reddit-node-wallpaper) application.
The goal was to create a simple application to:
1. Pull posts from [reddit](https://www.reddit.com/),
1. Filter by a given criteria,
1. Grab the image URL from a random filtered post,
1. Download the image, and
1. Set the image as the desktop wallpaper.

But if we think about the [single responsibility principle](https://en.wikipedia.org/wiki/Single_responsibility_principle), this application does _way_ more than one thing.
Working on a new project (use [Lorem Picsum](https://picsum.photos/) to provide the image), I broke the functionality into multiple modules.

1. Pull an image from the given URL into memory ([image-download](https://github.com/the-pat/image-download)),
1. Download the image on to the file system,
1. Set the image as a wallpaper,
1. Orchestrate all the functionality ([lorem-picsum-wallpaper](https://github.com/the-pat/lorem-picsum-wallpaper) -- also does the previous 2 functions...), and
1. Expose a CLI ([lorem-picsum-wallpaper-cli](https://github.com/the-pat/lorem-picsum-wallpaper-cli)).

This journey to release my first Node.js few modules was an extremely enjoyable experience. I cannot wait to take on larger projects in the future.

For those wanting to get into Node.js, here are a few resources I used:
- [Fun Fun Function](https://www.youtube.com/c/mpjmevideos),
- [NodeSchool](https://nodeschool.io/),
- [Eloquent JavaScript](http://eloquentjavascript.net/),
- [Mostly adequate guide to FP (in javascript)](https://drboolean.gitbooks.io/mostly-adequate-guide/content/)
- [Sindre Sorhus](https://github.com/sindresorhus) (_bytes_ of awesome code), and
- [jreina/Superlatives](https://github.com/jreina/Superlatives)