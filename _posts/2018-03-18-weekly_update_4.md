---
layout: post
title: Weekly update 4
menu: false
categories: [personal]
tags: [weeklyUpdate]
comments: true
permalink: weeklyUpdate4
excerpt: Rediscovering power of java generics, using android profiler to Mr. Robot soundtrack, this last month was amazing.   
---

I have been getting lazy lately and skipped on a lot of tasks. From now on I'll be starting a daily discipline daemon. Let's hope it goes well. 

I had a chance to research on different cryptography algorithms. I found that while **AES** is a balanced algorithm (fast and appropriately secure), **Twofish** (A finalist in the competetion in which AES algorithm was decided) is faster, and **Serpent** (A finalist too) is more secure owing to more number of rounds. But only AES is supported in android by default. I find it a bit unsettling that google didn't even gave implementations for the other too.  

Also while doing some UI smoothing work, I found that mathematical equations work miracles. Calculations done using them produce smooth results which look natural and very eye-pleasing.  

In java related learnings, one day my code was about 1000 lines and a lot of it was repeated due to having different types. So I introduced **generics**, and my code reduced to 300 lines. The logic is now clear, code is more maintainable, easy to explain and expendable. I would recommend java/android devs to use it at appropriate places where logic is repeated for different types of data. Here is a good [resource](https://www.journaldev.com/1663/java-generics-example-method-class-interface) to learn about generics. 

Memory usage is a pretty important thing too. I used **android profiler** to analyze the java heap dump, then filtered the classes via package name to check memory footprint of my app and library. The *retained size* shows the amount of memory that will get free if this particular object is garbage collected.

## Tech articles and discovery
1. Awesome use of machine learning - [Compressing and enhancing hand-written notes](https://mzucker.github.io/2016/09/20/noteshrink.html)
2. Git messages are important, very important - [How to Write a Git Commit Message](https://chris.beams.io/posts/git-commit/)
3. Who doesn't want to look cool - [Hackertyper](http://hackertyper.com/)
4. Understanding zygote in android - [What the Zygote!?](https://medium.com/@voodoomio/what-the-zygote-76f852d887d9)
5. Who doesn't love this - [Linus Torvalds slams CTS Labs over AMD vulnerability report](http://www.zdnet.com/article/linus-torvalds-slams-cts-labs-over-amd-vulnerability-report/)
6. People at google are amazing - [Making music using new sounds generated with machine learning](https://www.blog.google/topics/machine-learning/making-music-using-new-sounds-generated-machine-learning/)
7. Google strikes again - [Making amazing games like Pokemon Go with Maps](https://www.theverge.com/2018/3/14/17114494/google-maps-location-games-jurassic-world-walking-dead)
8. ML again - [Implementing IphoneX faceId using deep learning](https://towardsdatascience.com/how-i-implemented-iphone-xs-faceid-using-deep-learning-in-python-d5dbaa128e1d)
9. [Stack Overflow developer survey 2018](https://insights.stackoverflow.com/survey/2018/)
10. [Block compressor in Java, Go and C++. ](https://github.com/flanglet/kanzi/wiki)

## Mr. Robot soundtrack
Mr. Robot soundtrack is a great piece of music - specially while you are coding. Highly recommended to put you into the flow quickly. 
Oh and quick fact - *Sam esmail*, the creator of *Mr. Robot* was himself a hacker (a pretty bad one but still) - that explains why the show is so good and close to actual hacking or computer culture.

