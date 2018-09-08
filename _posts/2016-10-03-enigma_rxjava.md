---
layout: post
title: Understanding the enigma of RxJava (Part 1)
categories: [android]
tags: [rxjava,frp]
comments: true
permalink: enigmaOfRxJava
excerpt: This post is about RxJava. First objective is to convince you that you need RxJava. Then the objective is to break down RxJava paradigm or Functional Reactive programming into it's two parts - Functional programming and Reactive programming and try to explain what they are using examples. Then finally we will put them together and try to understand Functional Reactive Programming(FRP).
---

This [post](https://hackernoon.com/understanding-the-enigma-of-rxjava-part-1-8e04a456d9de) was originally written for Hackernoon publication on Medium. The first thing that came to my mind when I first heard about Functional Reactive Programming (FRP) and RxJava was why?!

Why switch from my comfortable Imperative programming and AsyncTask world? The answer was not clear at that time but after 
recent experiences I felt the need for it. In this part I will try to convince you, honestly myself as well a little bit,
to learn RxJava and then we will discuss what it is we are trying to achieve using RxJava (Psst… Hint, it is a paradigm).
In later parts, we will cover the basics of RxJava and it’s implementation in real life based android applications.

## Why should I use RxJava?

*If you are asking this question, good then. Let’s begin!*
I started this project called [Pokify](https://github.com/GauravChaddha1996/Pokify), which was based on Pokémons. In that
project I made a simple SQLlite Helper class and used Executor Service for threading and AsyncTask for other asynchronous 
operations. It was a pain to manage all of these and after numerous incidents of cursing and fixing my stupid bugs, 
I realized the need of *RxJava* for my threading and asynchronous operations. Without even a waste of second, 
I committed myself to *RxJava* because that is *what devs do, they learn new stuff when they aren’t satisfied with
what they have on their plate.*
> *If you have also cursed AsyncTask, it is time to stop cursing and start moving on.*

Oh and I’ve got ample reasons which will be enough to convince you to move on!
Here are some **advantages** of using *RxJava*:

1. **Avoid the [Callback Hell](https://www.quora.com/What-is-callback-hell).**
If you have ever made nested network calls you know what I’m talking about. It is a very common problem and a dreaded one too,
which is easily solved by RxJava.

2. **Threading is a hundred times easier.**
No more worrying of updating the views and getting the dreadful ‘~UI Thread crash’.

3. **Asynchronous operations becomes way easier using RxJava.**
Using AsyncTasks you have a large set of problems. The code is not clean, testing it is a pain, or if you are trying to cache
the download of an AsyncTask on rotation of the device, well Good Luck! Also, be it handling of activity life-cycle, or multiple
network calls, or even error handling of nested AsyncTasks…I could go on but I guess you see the problem, right? With RxJava
all these can be tackled with fairly easily.

4. **UI and View-Handling.**
Ever made a network call when the user searches for something in an EditView? We don’t want to make a network call for every 
‘R’ ,‘Rx’, ‘RxJa’ or ‘Rxjava’. We only want to do so when the user has stopped typing for at least 250ms. If you start thinking
about the solution with imperative coding, you see the flaw there, right? With RxJava we will solve this pretty easily using 
the [debounce](http://reactivex.io/documentation/operators/debounce.html) operator.
Other View-Handling stuff like listening for double tap or triple taps is a piece of cake with RxJava. Listening to EditView text changes is 
infinite times easier. Want to create multiple listeners for button click? No problemo! With RxJava, you can do it all with many other cool 
advantages as well.

5. **A standard error handling mechanism.**
Ever made a simple weather app? You have to first fetch the location and then its weather. If using AsyncTasks, it will have nested tasks 
and a nested error handling mechanism which is not very clean. With RxJava you get a standard way of handling all these errors. Neat, right?

6. **RxJava has a lot, literally, a lot of operators for your use.**
Anything you can think of will most likely have an operator already. That too all tested!

7. Using the *FRP* paradigm (The paradigm whose library is RxJava) you will be able to easily add code or remove it. If you followed FRP correctly, most of the times your structure will tell you where the bug is coming from and then we can squash it!

**Have I convinced you yet? Good.**

Now let me break the truth to you. The idea that we want to implement using **RxJava** is actually **Functional Reactive Programming(FRP)**. It is
a paradigm on how we should write our program or project. In fact, it is one of the many others like OOPS paradigm etc. The way to easily follow
it in Android is through RxJava, which is an extension library of [Reactive](http://reactivex.io/)X for Java that can also be used in android
for programming in FRP. FRP paradigm can also be implemented without using RxJava in some places which will get clear in the breakdown of FRP.  

## The Breakdown of Functional Reactive Programming

OK, Now that I have you on my side of the table, we are going to break down *Functional Reactive Programming* to understand clearly all it’s
aspects; what it is and how will we implement this in our project using RxJava. It is made of two parts: **Functional Programming** and **Reactive
programming**.

### What is Functional Programming?

Typically, most of us have an imperative mindset. We see things as objects which bring together two things: data and functions that act on that
data. In OOPS paradigm data can be changed or mutated. But in **Functional Programming** we code the program as such that we try to avoid data
mutation. Instead we create a new set of data every time we need to mutate the data. This helps in the way that a function that transforms the
data set will always return the same value as the original data set is never mutated. Thus this function is easily unit-testable.

### Difference Between Imperative and Functional Approach

OK, I know, I know, you want an example. Suppose you have a generic thing called Figure. Square, circle, triangle are all Figures.Now you have a
box containing 3 squares.You need to convert them all to circles applying some operations. The imperative approach to solve this is iterate
through the list and convert each item from a square to a triangle and then to a circle one by one.

![Imperative approach to problem: Given a data set( list) of 3 squares convert it to data set of circles using operators.](/assets/postImages/enigma_rxjava_1.jpeg)*Imperative approach to problem: Given a data set( list) of 3 squares convert it to data set of circles using operators.*

However the functional approach differs as such that we put our 3 items in a stream. Then we convert this stream of squares into a stream of triangles and then this stream into a stream of circles.

![Functional approach to problem: Given a data set( list) of 3 squares convert it to data set of circles using operators.](/assets/postImages/enigma_rxjava_2.jpeg)*Functional approach to problem: Given a data set( list) of 3 squares convert it to data set of circles using operators.*

Both of the paradigm are achieving the same result, it is just a matter of how it is done. For Asynchronous and some other operations an imperative approach has many problems and that is why we are switching to a functional approach.

### Pure functions

*Functional Programming* introduces a very cool concept of **Pure functions**. This blog [post](http://blog.jenkster.com/2015/12/what-is-functional-programming.html) explains this beautifully. This is the implementation of FRP without using RxJava and is very powerful. The summary of the post is this;
Consider the function:

    function a()
    {
        item = queue.getItem();
        process(item);
        print(item.name);
    }

The function has a hidden input: ‘queue.getItem( )’. It is called hidden because looking at the function signature one cannot determine that it is required by the function. This is known as *a **Side cause**.* Similarly it is printing the item name. This also cannot be predicted by the signature and hence is a hidden output called as **Side effect.**

As you can imagine Side effects and Side causes lead to numerous problems and bugs that can’t be easily tracked as they are hidden. They also lead to testing problems.

Any function which doesn’t have a hidden input or output is known as a Pure function. For pure functions, looking at the function signature, we can determine what it’s inputs and outputs are. Example:

    function int add ( Integer a, Integer b) 
    {
        c = a+b;
        return c;
    }

**Functional Programming** is programming using pure functions and removing side effects are much as possible. Functional languages are languages which encourages and provides easy way to do functional programming.

### When to use Functional Approach?

My view is that Functional programming is better to deal with the data of people while OOPS is better when we deal with people. In a MVP pattern the model classes should use the OOP paradigm while the funtions inside these classes should use Functional approach. Transformation or manager classes (Like presenter or views in MVP) should also use pure functions to operate on model objects having pure functions. The benefits of both world! Using functional approach we can gain the advantages listed above.

### What is Reactive Programming?

**Reactive Programming** is the paradigm that says that our code should be as such that we react to changes. A very good explanation of reactive programming is given in this medium [post](https://edgecoders.com/how-to-explain-reactive-programming-to-a-5-year-old-e802c5385aee#.iqzs91ibd). A good example from this post is: Suppose you order a coffee and while waiting you focus shifts and you start reading a medium article. Now as soon as your order comes up and your name is called you react to this change and your focus changes from the article to coffee.This is reactive programming.

### What is Functional Reactive Programming?

A mixture of Functional and Reactive Programming is called **Functional Reactive Programming.** In this case we code our project as such that we react to changes using the functional paradigm. A very good resource for understanding FRP is this [gist](https://gist.github.com/staltz/868e7e9bc2a7b8c1f754) by Andre Stalz. To understand FRP lets see the mixing of Functional Programming and Reactive Programming using an example:

![Button click stream example for FRP](/assets/postImages/enigma_rxjava_3.jpeg)*Button click stream example for FRP*

Suppose we have to listen for double or more taps on a button. We can see in the marble diagram that we first have the event stream of user clicking the button. This event stream is a functional programming data set. First we use *RxJava*’s operator called buffer and throttle the click stream.This operator will merge/accumulate all the events for the given parameter time (250ms) and adds them as one. To make it very clear in terms of *FRP*, we used pure functions from *RxJava* to have a new data set which has mutated from the original one. Next we map these click events as number of clicks to the data set. Again we have a new mutated data set which we have created using *RxJava*’s functional approach . Then we filter our data set for items greater than or equal to 2. Now we react to these clicks data set using the reactive paradigm.
To summarize this example, we used pure function operators of *RxJava* to mutate our button click stream (from click stream to accumulated stream to number of click stream and then filtered it) and then we reacted to the mutated button click stream. This paradigm is *FRP* as we used functional approach to do reactive programming.

## Conclusion

I hope I have convinced you to try coding in **Functional Reactive Programming** and using **RxJava**. In the next post I will discuss some basics of RxJava. 

## Further reading
1. [Why you should be doing functional reactive programming](https://medium.com/@cesarmcferreira/why-you-should-be-doing-functional-reactive-programming-858bd9bb8001#.y8p1je1o5) 
2. [Grokking RxJava Series](http://blog.danlew.net/2014/09/15/grokking-rxjava-part-1/)
3. [The introduction to Reactive Programming you've been missing](https://gist.github.com/staltz/868e7e9bc2a7b8c1f754)
4. [Crunching RxAndroid Series](https://medium.com/crunching-rxandroid/crunching-rxandroid-part-1-4ac7b7123238#.svvpyf3a2)
5. [Exploring RxJava 2 for Android by Jake Wharton](https://academy.realm.io/posts/gotocph-jake-wharton-exploring-rxjava2-android/)

## Links and resources
1. [Pokify](https://github.com/GauravChaddha1996/Pokify)
2. [What is functional programming](http://blog.jenkster.com/2015/12/what-is-functional-programming.html)
3. [How to explain reactive programming to a 5 year old](https://edgecoders.com/how-to-explain-reactive-programming-to-a-5-year-old-e802c5385aee#.iqzs91ibd)

