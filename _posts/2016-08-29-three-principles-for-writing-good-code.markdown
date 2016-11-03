---
layout: post
title:  "Three principles for writing good code"
date:   2016-09-15 13:12:38 +0100
categories:
---

![Code](/assets/code.jpg){:class="post-img" :margin-bottom="30px"}

Granted, there is no magic trinity of ideas that can capture the art of writing 'good' code. Yet, of all the lessons I've learned about code craftsmanship at Makers Academy, these principles are among the most fundamental:


#### Good code is readable.
{: class="subheading"}

Nearly every project will at some point require the involvement of another developer; their actions will be the judge of your work. It doesn't matter how ingenious the approach to a particular problem may be, if the code cannot speak clearly enough for the next developer to understand, it will be misused or discarded.  

#### Good code is test driven.
{: class="subheading"}

Comprehensive testing is the only way to be sure your code behaves the way you expect. It is surprising how often a small change can cause ruptures in other parts of your program, for reasons you might never have anticipated. Writing tests beforehand forces you to think carefully about each line of the code you intend to write, along with the consequences and edge cases that could arise. Well organised tests expose the design story of your project; they make it easy to spot the responsibilities and relationships between different areas of the code, the challenges that were anticipated and any gaps that were missed.  

#### Good code is well encapsulated.
{: class="subheading"}

This is one of the core paradigms of object oriented programming, and fits comfortably with our own cognitive limitations. Files that run many hundreds of lines long, functions that encompass too much complexity and objects that know too much about their environment make a codebase harder to extend and maintain. No time is more valuable than your own, and finding the right abstractions can save many hours lost debugging the code further down the line.
