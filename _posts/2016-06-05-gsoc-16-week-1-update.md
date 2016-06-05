---
layout: post
title: [GSoC16] Week 1 update
date: 2016-06-05 15:00:00
category: gsoc16
---

It's been a week since the coding period of Google Summer of Code started and so far it's been great.
After some discussion with my mentor during the community bonding period I started coding my project which is an [Eclipse plugin for coala](http://sheikharaf.me/gsoc16/gsoc-16-with-coala.html).

In the first few days I setup `maven` to build my project and `Travis-Ci` for continuous integration.
Many developers underestimate the importance of test-driven development. Although initially it seems as if writing tests would slow you down, but instead I found the opposite to be true.

This is especially the case if you're dealing with GUI interactions. After writing code in lieu of launching a new Eclipse workspace to test the plug-in manually, you can just write tests and run them in headless mode.
This in my opinion is substantially quicker.

So, after the foundation was laid further development was a breeze. I did some clean-up of the existing prototype of the plug-in and re-organized the project structure.
The next task was to run the code analysis on a separate thread to avoid freezing the main UI thread. Although this was possible using built-in Java libraries, I used the Apache commons' [`exec`](https://commons.apache.org/exec/) library to run the `coala-json` command. This was necessary because whilst dealing with multiple processes and supporting many operating systems a lot of things can go wrong.

In the coming weeks I plan on adding options to select the bear to use for running the analysis and handle bears that require user interaction. If everything goes according to the plan I'll have a usable static code analysis plug-in by mid-term evaluation.

Cheers!
