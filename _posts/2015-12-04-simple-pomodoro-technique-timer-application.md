---
layout: post
title: Simple Pomodoro Technique Timer Application
description: A very simple C# WPF application for Time Management and Productivity.
keywords: pomodoro technique, time management, timer application, wpf
---

Talking about Time Management at work, there is one of the more popular time management life hacks used today, it's called [Pomodoro Technique](https://en.wikipedia.org/wiki/Pomodoro_Technique) created in the 1980s by Francesco Cirillo. The Pomodoro Technique is a time management philosophy that aims to provide the user with maximum focus and creative freshness, thereby allowing them to complete projects faster with less mental fatique.

The technique uses a timer to break down work into intervals traditionally 25 minutes in length, separated by short breaks (e.g. 5 minutes). Each 25-minute work period is called a "pomodoro", named after the Italian word for tomato. Francesco Cirillo used a kitchen timer shaped like a tomato as his personal timer, and thus the method's name.

Well, you can [google](https://www.google.com/search?q=pomodoro+technique) around if you want to know or learn more about this Pomodoro Technique.

Inspired from an [open source Pomodoro Technique Timer application](http://github.com/Mellen/Pomodoro) originally developed by [Matthew Ellen](http://www.matthewellen.co.uk/) in 2010, so I take the source code, [update it](https://github.com/heiswayi/Pomodoro) for my own use by making a little change and adding new features to it.

**Let the pictures speak for themselves.**

This is the normal look of the application on startup or before pressing "START WORKING" button:

![Screenshot1](http://i.imgur.com/JPmbbLb.png)

When the user pressed "START WORKING" button, the application will start the Pomodoro timer and minimize into the tray panel:

![Screenshot2](http://i.imgur.com/d2Uqbvs.png)

After 25-minute period has passed, the application will beep once and show up with a "Take a break!" message:

![Screenshot3](http://i.imgur.com/1vh1MjD.png)

If the user finished his/her break time, he/she can continue the Pomodoro timer again by pressing "START WORKING" button. Just repeat the process.

**TIPS:** After four "pomodoros" has passed (100 minutes of work time with 15 minutes of break time), you then can take a 15-30 minute break.

This application is a very simple Pomodoro timer application, but a quite helpful to me since my official job is working with PC all the time. At least, it gives me better focus completing my job tasks.

### Downloads

If you want to try, go ahead, download the latest binary package (`Pomodoro.exe` file) on the [**release page**](https://github.com/heiswayi/Pomodoro/releases). No installation required. The application's source code are also available on [**GitHub repo**](https://github.com/heiswayi/Pomodoro). Freeware and open source. This application is built in C# WPF with .NET Framework 3.5 SP1.
