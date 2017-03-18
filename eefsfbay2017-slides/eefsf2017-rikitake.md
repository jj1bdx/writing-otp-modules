footer: Kenji Rikitake / Erlang and Elixir Factory SF Bay 2017
slidenumbers: true

![](davide-ragusa-5417-slide.jpg)

# Writing A New Erlang/OTP Module for Beginners

<!-- Use Deckset 1.6.0, Next theme, 16:9 aspect ratio -->
<!-- target: 25 slides -->

^ Good morning!

---

# Kenji Rikitake

23-MAR-2017
Erlang and Elixir Factory SF Bay 2017
San Francisco, CA, USA
@jj1bdx

* Erlang Factory SF Bay 2010-2016 speaker for seven times, and...
* Erlang and Elixir Factory SF Bay 2017 speaker (8th year!)
* Erlang `rand` module co-creator

![right, fit](kenjiface-20150328-2.jpg)

^ My name is Kenji Rikitake. I'm very glad to come back here again. This is my eighth presentation at the San Francisco Erlang and Elixir Factory since 2010.

---

# What I did for OTP

## Wrote Erlang PRNG code
## Tested and published the results
## Put the code into OTP

^ I've written six implementations of random number code for Erlang since July 2010. They're all on GitHub. I've tested and published the results at many places, including past years of this conference, and at ACM Erlang Workshops. After doing this for nearly 5 years, the code is now a part of OTP, and the first major revision will be available at OTP 20.

---

![](markus-spiske-221494-slide.jpg)

# This talk is *not* about

## Algorithms
## Random numbers
## Other implementation details

^ I have already given multiple talks at Erlang Factory on the details of pseudo random number generators, their algorithms, and the implementation details. I'll be glad to answer those questions during the conference, but I will not go into the details in this presentation.

---

# This talk is about

## Development for Erlang/OTP
## Working with OTP Team
## How to gain support of your code

^ In this talk, I will explain what I've learned from writing an Erlang module for the OTP. I will include three major topics: developing software for OTP, working with the OTP Team, and how to gain the community support of your code.

---

# Development for Erlang/OTP

^ I'd like to talk about software development for Erlang/OTP.

---

# WARNING

## Don't try commiting code only for nurturing your ego or just for your own fame, please

^ There's one thing I need to mention before getting into the details. I've observed that quite a lot of people write software for their psycological need for approval, and for their own fame. It is a bad approach for writing open source software, and often becomes destructive to the project. So don't do it.

---

# Why new code?

## Bugfix/security
## New features
## "Fix what I don't like"

^ There are many reasons for writing a new piece of code. The most critical one is for fixing a bug and closing the security holes. And people want new features, or invent some cool stuff. Some people want to change what they don't like.

---

# Do you have to change OTP?

## OTP is for *all* Erlang users
## Who needs new code?
## Once committed, removal is hard

^ You need to think carefully before trying to change the OTP. OTP is for all Erlang users, including the Elixir and other language users, so changing it may affect many people. You also need to think about who needs the code. If the code is a critical security fix it'll be accepted in short time, but if it's a new feature more design discussion will be needed. And you need to remember, once code is committed, removing it is a very difficult task.

---

# [fit] Rationale for `rand` module

* **`random` module period is too short and exploitable within <10 hours with a modern desktop computer, so it's basically a security fix**
* **Fixing API: eliminating the need for initialization**
* **New features: selecting multiple algorithms, normal distribution generator, jump functions from OTP 20**

^ The rational for including rand module was mainly to fix the security issues of random module. The random module is exploitable within less than 10 hours. Eliminating the need for initialization is an improvement for the API. Selecting multiple algorithms and providing normal distribution generator are already available as the new features. From OTP 20 you will be able to use the jump functions too. The important point is that you need to have a rationale that can convince all users of Erlang.

---

# Prototyping

## Independent repository
## Common Test and Dialyzer
## Learn erl_docgen

^ When you decide to write your own Erlang module, the first thing you need to do is to make an independent repository. Isolating code under development from existing systems will make the testing easier. You also need to learn Common Test, which is the default testing framework for OTP, and Dialyzer, to provide function and data type specifications. You also need to be fluent in erl_docgen, which is an XML-based documentation system.

---

# Working with OTP Team

---

# How to gain support of your code

---

[Tweet from Loïc Hoguin (@lhoguin at Twitter)](https://twitter.com/lhoguin/status/834869334174466048)

![inline](tweet-lhoguin-834869334174466048.png)

^ I'm going to show you a couple of tweets from Loïc Hoguin, the author of Cowboy, telling tips on getting your patches or pull requests merged. The first one tells that sending a large patch abruptly without a thorough discussion beforehard will always be rejected.

---

[Tweet from Loïc Hoguin (@lhoguin at Twitter)](https://twitter.com/lhoguin/status/834869569382715394)

![inline](tweet-lhoguin-834869569382715394.png)

^ The second tweet tells that having a discussion of the broader goals with the maintainer beforehand and sending patches in small steps one at a time is a key to successfully merge your patches.


---

[Tweet from Loïc Hoguin (@lhoguin at Twitter)](https://twitter.com/lhoguin/status/834869820042645504)

![inline](tweet-lhoguin-834869820042645504.png)

^ And this last tweet tells that constantly discussing around the changes is the key for a successful communication on software development.

---

# [fit] Support for this presentation is provided by

![inline, fit](gmo_pepabo_logo_en_ja.png)

# [fit] Pepabo R&D Institute, GMO Pepabo, Inc.

^ I'd like to thank GMO Pepabo for supporting this presentation as a research activity of Pepabo R&D Institute, where I'm working as a guest researcher.

---

# Acknowledgment

* Dan Gudmundsson - rand module principal developer
* Sebastiano Vigna - [Xorshift\*/+](http://xoroshiro.di.unimi.it/) inventor
* Erlang Solutions

^ I'd like to thank Dan Gudmundsson as the OTP Team maintainer of the rand module. Sebastiano Vigna provided the Xorshift+ algorithm optimized for Erlang VM. Erlang Solutions has given me many chances of talking about this topic. 

---

![](chris-brignola-392-slide.jpg)

# [fit] Thank you

# [fit] Questions?

^ Thank you!

---

Photo credits:

* Title slide: Davide Ragusa, from Unsplash.com
* My face: Yutaka Sakurai, Naoki Sakurai
* "This talk is not about" slide: Markus Spiske, from Unsplash.com
* "Thank you" slide: Chris Brignola, from Unsplash.com

<!-- Local Variables: -->
<!-- coding: utf-8 -->
<!-- End: -->
