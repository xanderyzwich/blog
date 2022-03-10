---
title: Perfection vs Completion
description: Is it better to be right or done?
date: 2022-03-10
tags:
- development
- programming
- craftsmanship
- journey
layout: layouts/post.njk
---

It's extremely common in tech that we find ourselves debating the best way to do something. You can find arguments about anything from text editor selection to number of lines in a function. All of these arguments come from a good place. We want to learn what is best in order to build the best thing that we can. But, what if I told you that a vast majority of these debates have no right or wrong answers?

When it comes to tools for writing code there is certainly no shortage. Some people use bare-bones Vim or have it decked out with 100 plugins. There are similar groups of people using VSCode, Atom, Sublime Text, Emacs, JetBrains products, Eclipse, Visual Studio or anything else. Not a single one of these tools is going to do you any good if you don't know how to use it. The biggest part of tool selection is using something that you are familiar with and taking the time to learn how to use it well. Nearly every code editor out there can be configured to function in very similar ways. The thing that determines how much it helps you is whether you know how to use it.

Due to this, there is value in making a decision and sticking with it. At some point you may decide that what you've decided isn't working and choose something else. That's okay. Too often I see people that are early in their development career stressing over what the best programming language or text editor is, and I'm here to tell you that none is the best at everything. These are just tools. You can turn screws with a manual screwdriver, power screwdriver, drill, or impact driver, and there is a certain amount of overlap in functionality, but purchasing an impact driver for changing the batteries in your kids toys is entirely unnecessary, and may actually present more difficulty than using a small manual screwdriver. The most important questions that you can ask when choosing a tool are centered around "does it do what I need?" and "at what cost?". Is it best to build front-end and back-end separately? Many times the answer is yes, but if the project is small enough then doing so may actually bring about more difficulty than there is benefit in doing so.

Currently, I'm working on modernizing an old website that uses Java Server Pages. The replacement has separated front-end and back-end systems. The front-end is sharp. It's built with NodeJS, Nuxt, Vue, Vuex, Tailwind, Eslint, and Stylelint. The back-end is built with Java, Spring Boot, Lombok, Hibernate, and several Saas systems that make our life easier. Any one of the tools in our front-end and back-end systems could eat away a week of your time if you wanted to explore all the configuration options. If they don't get in your way, there it's usually more helpful to just use the default configuration. Once that configuration is found to not fit some part of your needs, only then should you add whatever configuration is necessary to overcome that limitation. Let the tools enable you to do work. If you spend too much time considering what is possible then you won't get around to the task at hand. When it comes to code style and linting, I've seen people argue both ways on most of the things that can be checked or configured, but in the end you will actually get used to whatever code style is being used. Having all the code match in style allows your brain to look past unnecessary things and read the important bits. At the end of the day, it's how much you are able to build that matters, not what hammer you used.

> In his writings, a wise Italian says that the best is the enemy of the good
> ~Voltaire
