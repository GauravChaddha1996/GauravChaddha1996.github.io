---
layout: post
title: Weekly update 2
menu: false
categories: [personal]
tags: [weeklyUpdate]
comments: true
permalink: weeklyUpdate2
excerpt: Week of implementing security, library development, installing Ubuntu again and the "Moonshield".
--- 

This week at work I had to secure the keys we were creating. We know that perfect **security** isn't achievable. But we can make it a lot 
harder for the hacker to crack our app.

There are quite a lot of ways of storing things. If you want nobody else can read your data like keys, storing them in internal storage 
makes sense, but it doesn't give you much space. The next logical way is to encrypt the files in external storage while keeping the keys 
in internal storage. Sure, works fine until the phone is rooted. For preventing from this type of access and attacks by process hijacking 
(I don't know how people do that - but it's mentioned in the android KeyStore docs) I needed to find ways to ensure that even my internal 
storage data is secured. 

*Android KeyStore* can be used to securely store your keys. Using it we can stop the keys being exported even after your process has been 
hijacked as the cryptography actions are done in system process. But I feel that KeyStore API can be improved, the docs can be 
updated and should give some good examples. Another interesting way of storing keys or secrets, is to store them  in '.so' files and 
compile them in your APK file. This way, it becomes very hard for the hacker to extract them.

I also came across implementing a worker thread where multiple instances of an object would request work/tasks to the same worker 
background thread. It was nice to actually use *Handler* and *Looper*. [Post1](https://blog.mindorks.com/android-core-looper-handler-and-
handlerthread-bd54d69fe91a) and [Post2](https://blog.nikitaog.me/2014/10/11/android-looper-handler-handlerthread-i/) are great posts to 
understand Handler and Looper. 

A dev.to [post](https://dev.to/amangautam/softer-skills-that-make-you-a-better-programmer--2g3e) by *Aman Gautam* taught me on important 
thing - Explain the **"Why?"** in your comments and not only "What?" the code does. It will help the developer who is going to use or 
maintain your code a lot.

In other parts of my life - the OS problem persists. In my opinion, the best way to learn **Arch linux** is to install it the hard way and 
not use any installer. But doing that means my system will remain a bust if I only rely on Arch Linux. I tried to install arch linux but 
couldn't get the internet connection to work so didn't even go through the first step. My grub surrendered and stopped showing Antergos at 
all. So I finally decided to do the long overdue cleanup of my messy disk (about 15 partitions on a 1TB HDD for triple boot Ubuntu, 
Windows and Antergos). 

I erased everything and installed **Ubuntu 17.10**. Although it's slow for a new install - it'll work for now. I'm almost done configuring 
it to my liking. I tried configuring *Rofi* but failed so perhaps next week I'll post a good running Rofi pic. As of now my system looks 
like this.
![Ubuntu 17.10 with Gnome Wayland](/assets/postImages/weekly_update_2.png)*Ubuntu 17.10 with Gnome Wayland*

I watched **Black mirror** season 4 first two episodes - they were softer in tone than the previous seasons. 
They made me wonder but the twist that shocked me in the previous seasons was absent.

Artist wise - I was still stuck on *Pink Floyd* in the start of week. Then the guitar solos in **The Jester Race** by *In Flames*, 
specially *Moonshield* and *Artefacts of the black sun. I went back to Muse and Radiohead again. On the weekend I listened to *Fiction* 
and *Atoma* albums by **Dark Tranquility**. Their solos are epic, specially the one in *When the world screams*, it's introduction 
complements the whole song very well.
