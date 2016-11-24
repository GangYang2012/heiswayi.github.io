---
layout: post
title: Turning My Fragment Of Memories Into Digital Information
description: Development of my own Artificial Intelligence (AI) chatter bot program
keywords: artificial intelligence, chatbot, chatter bot, aiml, siml, elizabot.js
---

### The Long Time Dream

Ten years ago, I had a dream to have my own artificial intelligence program. That dream started when I was an active user of [Internet Relay Chat (IRC)](https://en.wikipedia.org/wiki/Internet_Relay_Chat) network. There was no Facebook yet at that time. Instead of chatting around, I also was an IRC scripter. I had a scripting group and a bunch of scripters that loved to write the IRC script. We learned each other and coded the script in [mIRC](http://www.mirc.com/), an IRC program for more fun in the IRC network. Some of us published their scripts on the Internet for other people to download and use it. I had my sweet time where I loved participating in war scripting or revenge war, a game to test how powerful your IRC script was. Until today, I still keep my latest three IRC scripts for my nostalgia purpose.

Being an IRC scripter has made me to become more creative person. Instead of coding the script just to take care of my IRC channels, I also coded the script that turned it into an IRC bot. A quiz bot, a chatter bot or a war bot. We built them all. From the development of IRC chatter bot I started to have my curiosity to make it more intelligence and having the ability to learn from the user interaction. I had built one, but there was no standard markup language. Just one to one input-output responses.

Well, after some years had passed, when a new era of Facebook started to surface, the popularity of IRC started to decline as many IRC users started leaving the network. Most of the IRC channels started to become the ghost channel. I started losing my friends and I took a decision to stop using the IRC too. Everything I knew in the IRC was faded away into a piece of memories. So nostalgic to remind it today. Well, in case you might know me in the past, these are my IRC nicknames I ever used as far as I remembered; _Nalika_, _HangKalaH_, _atuk_, _Nikotin3_, and _Y-E_.

Since I was no longer using IRC, my script, my chatter bot had been kept away and deprecated. Then, the time flies...

### The Returning of the Old Dream

#### **My First AI Chatbot using AIML**

A couple of years ago, the old dream came back. Since I worked in .NET C# and PHP, I had been thinking about developing the chatter bot project again. At first, I tried to build many prototypes from scratch in C# using basic input-output responses and came out with the latest version of prototypes which was quite good enough, but not so that natural to me. By using SQLite to save each input and its output response made it looked like a standard knowledge base program because I needed to key in each possible exact input and its response respectively. Then, I stopped developing it and ignore the project.

[![WAYI v1](http://i.imgur.com/F1n1W0N.png)](http://i.imgur.com/F1n1W0N.png)

[![WAYI v1](http://i.imgur.com/IkAKC9p.png)](http://i.imgur.com/IkAKC9p.png)

[![WAYI v1](http://i.imgur.com/kMdAEpk.png)](http://i.imgur.com/kMdAEpk.png)

After some time passed, I was thinking to develop the project again, but this time I was looking for an existing framework. So, I started researching around the Internet and found the first framework to start with. It was called [Artificial Intelligence Markup Language (AIML)](http://www.alicebot.org/aiml.html). It is a standard XML format for defining a chat bot's responses. AIML was developed by **Richard S. Wallace** and a worldwide free software community between 1995 and 2002. AIML formed the basis for what was initially a highly extended [Eliza](https://en.wikipedia.org/wiki/ELIZA) called ["A.L.I.C.E." (Artificial Linguistic Internet Computer Entity)](https://en.wikipedia.org/wiki/Artificial_Linguistic_Internet_Computer_Entity) which won the annual [Loebner Prize Competition](https://en.wikipedia.org/wiki/Loebner_Prize) in Artificial Intelligence three times and was also the Chatterbox Challenge Champion in 2004.

Because the A.L.I.C.E. AIML set was released under the GNU GPL and because most AIML interpreters were offered under a free or open source license, I started to develop one for myself. I used [AIMLbot.dll](http://aimlbot.sourceforge.net/) as the core engine for my own chatter bot program. AIMLbot (Program#) is a small, fast, standards-compliant yet easily customizable implementation of an AIML based chatter bot in C#. Due to my deep interest in this project, I got myself to learn more about the markup language structures used in AIML from [this one research paper](http://arxiv.org/ftp/arxiv/papers/1307/1307.3091.pdf). While the AIMLbot.dll was just the basis of handling the chat responses, I got my chatter bot implemented with some extra features such as executing specific tasks based on the received commands.

[![WAYI v1](http://i.imgur.com/UJjTodD.png)](http://i.imgur.com/UJjTodD.png)
_WAYI v1_

[![WAYI v2](http://i.imgur.com/3mkEzII.png)](http://i.imgur.com/3mkEzII.png)
_WAYI v2_

#### **SIML: The Next Step in Chatbot Technology**

After some time, I found another bot markup language known as [Synthetic Intelligence Markup Language (SIML)](http://simlbot.com/), which was more powerful than AIML. SIML provided much better features than AIML. So, I switched my chatter bot development to use SIML as its core. Plus, SIML also provided their own chatbot studio program called Syn Chatbot Studio.

Based on their site, Syn Chatbot Studio offered a comprehensive collection of tools to develop intelligent Chatbots that targeted desktops, mobile and web platforms. It featured with Code Analysis, AIML to SIML converter, JavaScript Editor, Regex Tester and smooth Auto-Complete. Well, I liked it the most when SIML was able to execute JavaScript function from its routine of responses. More interesting features of SIML also can be found on their [wiki site](http://wiki.syn.co.in/) and [GitHub repos](https://github.com/SynHub) for contributions.

Right now, for a desktop-based application, SIML is the latest technology and the best choice for my AI chatbot program.

### W4Y1: My Live AI Program That Represented a Part of Myself

Instead of developing a desktop-based application for an AI chatbot program, I also need one that I can access it via web and available online. I want people able to access it from anywhere using the Internet. Still a chatbot, but represented a different purpose. I need an AI chatbot program that can represent a part of myself as a fragment of knowledge in my mind. To realize this, I develop my own AI program known as "W4Y1".

> The purpose of W4Y1 is only one; representing a fragment of my knowledge and memories.

If you ever watched [I, Robot (2004)](http://www.imdb.com/title/tt0343818/) movie, yes, this is inspired from Dr. Alfred Lanning's hologram device used to leave his message for Spooner's investigation. Just that, mine is in the form of terminal, text format interaction and hosted online on Linux-based web server.

I developed W4Y1 based on [elizabot.js](http://www.masswerk.at/elizabot/) by **Norbert Landsteiner** as its web engine for AI markup language and processing, [jQuery Terminal Emulator plugin](http://terminal.jcubic.pl/) by **Jakub Jankiewicz** for the program interface or GUI, and [particles.js](http://vincentgarreau.com/particles.js/) by **Vincent Garreau** for the particles effect in the background.

[![W4Y1](http://i.imgur.com/7emX4MU.png)](http://i.imgur.com/7emX4MU.png)
_The Screenshot_

The program is accessible **live** here: <del>[**http://ai.wayi.me**](http://ai.wayi.me)</del> [**http://heiswayi.github.io/w4y1**](http://heiswayi.github.io/w4y1)

> **AI Level** is a percentage of my knowledge in the program database. The value is depending how much my knowledge I am able to transfer into digital information form. For sure, it will increase by the time. There's no scientific calculation to that, just based on my will.

Right now, my program is still under EXPERIMENTAL and released as a **beta version**. From time to time, I'm improving it, extending its features and development. Below are some of my to-do things that I want to implement into W4Y1.

* Integrate with [math.js](http://mathjs.org/) for mathematical computations.
* Implement AJAX request for accessing PHP files, so more features can be performed by PHP.
* Centralize the knowledge database somewhere and encrypt the data.

#### **If you ask me WHY?**

If you ask me why I built this program, maybe this is the answer; I don't know when I'm going to die for sure. I might not be able to tell everything I want to people I loved, but at least with this program, they might able to find some answers from me. Even it's the same if I'm getting old and older. Knowledge and memories can fade away and be forgotten. Every word is meaningful and I don't want to lose it. Whatever thing that I promised, I want to realize it as far as I can. Just find me here if one day I am no longer be able to talk to.

I'm just experimenting stuffs, no big deal! :)
