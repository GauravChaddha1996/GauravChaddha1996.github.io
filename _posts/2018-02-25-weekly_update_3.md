---
layout: post
title: Weekly update 3
menu: false
categories: [personal]
tags: [weeklyUpdate]
comments: true
permalink: weeklyUpdate3
excerpt: From generating random IV, to groovy lava lamps, fixing race conditions on database and feel good playlist, this week was pretty good.  
---

Generating a **random IV** is important to protect cryptography operations. In 2013 Bitcoin theft occurred owing to generation of non-random IV's. Reading up on many resources, I found out that there was a bug in generation of random numbers in JCA (Java cryptography architecture) until API version 4.1 which lead to bitcoins being stolen from android wallets. The bug has since been patched. Above API 21 we use **SecureRandom** to generate IV. It uses a NativePRNG technique with true random seed from **/dev/random** and uses **/dev/urandom** to generate cryptographically strong random number for IV.

Also I learned one more thing in practice, increasing security comes at a cost of more operation time. Race conditions are a tricky thing while doing concurrency. I investigated some attacks via reflection and internal android API's on static variables defined. I'll report the things I find next week or whenever I'm able to easily attack on this.

I found [this](https://techcrunch.com/2018/02/16/cloudflare-is-protecting-the-internet-using-groovy-lava-lamps/) on Techcrunch - generating entropy from randomly moving lava lamps and ensuring security of internet traffic - incredible geek points to Cloudflare. I love the [stuff](https://techcrunch.com/2018/02/21/watch-spacex-launch-a-falcon-9-carrying-its-first-internet-demo-satellites-live-here/) that SpaceX do. They launched a satellite to provide Internet from it. That is the type of stuff every engineer wants to work on.
Also wireless charging might come sooner now - they made charging using laser beams ([link](https://phys.org/news/2018-02-laser-wirelessly-smartphone-safely-room.html)).

In entertainment part of my life, I binged **Black mirror** season 4, it has some happy endings but I liked previous seasons better.
Mr robot has ended. It was not as spectacular as the previous season but hey i didn't leave it in 3rd season - I'll consider that a win. (Most of my friends and me have left many countless series in season 3 like Suits, Flash, Arrow etc. aka the 3rd season curse). **Atoma** is a great album by **Dark tranquility**. The way guitar solos blend is a pleasure to hear. A **MGMT** song called *Little dark age* is awesome. I was facing coder's block when I
heard it, it relaxed my mind and my block was gone. On the weekend I found a good playlist called [**Transistor**](https://open.spotify.com/user/spotify/playlist/37i9dQZF1DXa0pRxO3JAC0) on spotify. It's pretty good and kept me upbeat throughout the day.  

I also riced my Ubuntu 17.10 configuration a bit. It's a bit hard to do as Gnome isn't exactly as configurable as i3WM. But it looks pretty sleak now. Here are some current screenshots.
![Desktop and dock](/assets/postImages/weekly_update_3_1.png)
![Terminator](/assets/postImages/weekly_update_3_2.png)
![Nautilus](/assets/postImages/weekly_update_3_3.png)
![Rofi](/assets/postImages/weekly_update_3_4.png)
![Htop](/assets/postImages/weekly_update_3_5.png)
![Firefox and Vi](/assets/postImages/weekly_update_3_6.png)

## Read box:
Articles and blog posts that I read this week.

 * Secure random box
 1. [Some securerandom thoughts](https://android-developers.googleblog.com/2013/08/some-securerandom-thoughts.html)
 2. [Android secure random not even nonce](http://blog.lxgr.net/posts/2013/08/15/android-securerandom-not-even-nonce/)
 3. [Helpful stack overflow question](https://stackoverflow.com/questions/25817133/does-the-android-implementation-of-securerandom-produce-true-random-numbers)
 4. [Myths about urandom](https://www.2uo.de/myths-about-urandom/)
 5. [SecureRandom reference](https://developer.android.com/reference/java/security/SecureRandom.html)
 6. [Right way to use secure random](https://tersesystems.com/blog/2015/12/17/the-right-way-to-use-securerandom/)

* Random Dev read box
 1. [What is graphQl](https://medium.com/mindorks/what-is-graphql-and-using-it-on-android-ab8e493abdd7)
 2. [How to do technical blogging](https://dev.to/yelluw/how-to-do-technical-blogging)
 3. [conversational bots](https://www.nytimes.com/interactive/2018/02/21/technology/conversational-bots.html)
 4. [Handling alarms](https://medium.com/@sauge16/how-to-handle-alarm-in-all-android-version-e7aca16ae885)
 5. [What's new in android nougat](https://blog.aritraroy.in/whats-new-in-android-nougat-from-a-developer-s-point-of-view-ed41b77d6458)
 6. [Android O notification badges](https://medium.com/exploring-android/exploring-android-o-notification-badges-32e1152eb1a0)
 7. [Background execution limits on android O](https://medium.com/exploring-android/exploring-background-execution-limits-on-android-oreo-ab384762a66c)
 8. [Adaptive icons](https://medium.com/google-developers/implementing-adaptive-icons-1e4d1795470e)
 9. [Notification channels](https://medium.com/cr8resume/notification-in-android-8-0-oreo-implementing-notification-channels-d65b0f81ca50)
