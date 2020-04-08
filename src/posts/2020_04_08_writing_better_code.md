---  
title: Writing Better Code  
description: Even bad code runs, how do we make our code better?  
date: 2020-04-09  
tags:  
  - development  
  - codequality   
  - cleancode  
  - craftsmanship  
layout: layouts/post.njk  
---  

What are ways that we can write better code? As clean code is something that I really strive for, I read alot of thoughts on the subject. There are so many debates out there surrounding every miniscule decision that can be made. It is a bit crazy when you think about it. It always seems that the discussions come back to some of the same points, which I'll do my best to explain here

## Consistent formatting and layout
I'm not going to engage in what format and layout decisions are right and what ones are wrong here. For the most part, whatever decisions you make, you will become accustomed to them and you will become better at reading code that follows your style guide. Linters are celebrated as being one of the greatest things for readability, and rightfully so. If you aren't a large company or don't have lots of different teams and code repositories to manage, then custom configuration of a linter can be quite cumbersome work that isn't really necessary. Whatever style decisions that your linter of choice is preconfigured with is likely fine, or at least a good start.

## Meaningful names are really important
Variables, classes, and function names can be quite helpful if handled well. Just consider `carOne.startEngine()` vs `c1.go()` where one reads like a spoken sentence, and the other could be anything (especially in a dynamic typed language). This extends to tests as well. `scenario27()` is much more difficult to understand than `addingTwoPositiveIntegers()`. It can be a bit of a pain, but overall it is the central tenet of the mythical 'self documenting code'. 

## Single thought per line.
I heard Python core dev, Raymond Hettinger, say this during a keynote and it has become a guiding principle for me. It is the determining factor in the prolific 'Are ternary statements evil?' debate. Tools have their place. Sometimes clever tricks are the only way that you can do make something work. When you find yourself writing clever code, I suggest you consider whether the clever code is really making anything shorter when you need a bunch of comments to explain what's happening. Again, ff there are more than two thoughts on a line then you should probably break it up.  

## Read other peoples' code.
Code reviews are a wonderful thing. Unfortunately, they aren't always a priority or possibility due to various factors. I personally have a split onsite and offshore development team where we are forced to handoff work between the two, and we can't have all of the developers on hand-off meetings morning and night. Without official code reviews, a few of us still ask one another for a quick look over our code if we are doing something complex and quick. Pair programming is another great way to be reading other peoples' code, and you get the added benefit of following along in their writing process.

Added bonus for pair/group programming is that it gives you the opportunity to share productivity tricks, and ways to better use your toolset to get work done more quickly, easily, and consistently
