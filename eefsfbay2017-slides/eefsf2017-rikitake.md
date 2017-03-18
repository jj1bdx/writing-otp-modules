footer: Kenji Rikitake / Erlang and Elixir Factory SF Bay 2017
slidenumbers: true

![](davide-ragusa-5417.jpg)

# Writing A New Erlang/OTP Module for Beginners

<!-- Use Deckset 1.6.0, Next theme, 16:9 aspect ratio -->
<!-- target: 25 slides -->

^ Good afternoon!

---

# Kenji Rikitake

23-MAR-2017
Erlang and Elixir Factory SF Bay 2017
San Francisco, CA, USA
@jj1bdx

![right, fit](kenjiface-20150328-2.jpg)

^ Hi, my name is Kenji Rikitake. I'm very glad to come back here again. This is my eighth presentation at the San Francisco Erlang Factory since 2010.

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

Photo credits:

* Title slide: Davide Ragusa

---

# [fit] Thank you

# [fit] Questions?

^ Thank you!
