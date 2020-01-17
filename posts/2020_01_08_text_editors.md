---  
title: What Text Editors Do You Use?  
description: However many it may be, what editors do you find helpful in your workflow?  
date: 2020-01-17  
tags:  
  - watercooler
  - discuss  
  - tools
  - editor
layout: layouts/post.njk  
---  

When your work involves typing and manipulating data files with many different sources then you wind up with different tasks that can be accomplished in many ways. What are your favorite text editors or ways of manipulating text for different tasks?

## VSCode
This is the newest editor in my toolbox. It has really good support for markdown and you can use it to open a regular file folder and access all of the contents. Lots of plugins and themes available.

## Notepad++
I've used this for years and gotten a lot of enjoyment out of it. The code highlighting is entirely customizable in addition to the themes that are available online. There are plugins, but I've personally had issues with using them on my work laptop with user policies. One great feature is that when you close Notepad++ it will actually keep any unsaved work that you have without your explicitly saving the file anywhere. I used this for years ;keeping text files for ongoing tasks where the information wasn't relevant long term. VSCode is actually starting to replace this for me, especially with my adoption of markdown for notes that might include several different languages.

## Programmer's Notepad
While very similar to Notepad++, Programmer's Notepad has a find/replace functionality that can use mixed backslash characters (\n, \r, \t, etc.) and simple regular expressions. While the finding could be done with regular expression in another editor, Programmer's notepad will let you replace the new line characters easily, which I found to be usefule when dealing with reformatting of data extracts and programmatically formed queries.

## JetBrains IDEA & PyCharm
Anytime that I need to run Python code, or run Java projects (including Maven, Gradle, and Springboot tasks) then I greatly prefer the JetBrains editors. Also, the tooling for interaction with version control systems is top shelf! The merge tool, diff, and local history are very helpful. I also find that the global find tools are better than the rest. There are separate tools for finding a file name that contains your string or finding the string in a file. The global string replace tool has assisted me with package restructuring of java projects without effort.

## Oracle SQL Developer
Writing queries with code completion with your actual database information is great. It helps that you can execute queries and export result data in multiple file formats.

## Excel
While it seems a bit out of place in a discussion of code editors, when you have comma separated data that needs to be reformatted adhoc then Excel can be a really good tool, especially when coupled with another pure text editor. We had a playbook that clients would fill out that I would translate into sql for the database insertion (it actually controlled the functionality of our application), and I would use Excel for moving the columns around, clear out unnecessary data, auto incrementing some values, and then I could paste the first and last parts of the insert statement into the first and last columns of the spreadsheet.

## Microsoft Word
This is the only tool that I've found that will quickly and easily make everything lowercase. That's really all that I use it for. Well, that and writing documentation that will be for someone who isn't a programmer.

## grep/sed/awk
Grep helps pull out the data that does/doesn't match a given pattern/string.

Sed helps replace a given pattern/string (even several at a time).

Awk is really helpful for pulling out certain pieces of column formatted data.

It's also of important note that with these tools that you really get the most power out of them when you start chaining them together with linux command line pipes ("|") and output redirects (">" or ">>") to write files or `wc -l` to count the lines.

Altogether these things can be used almost like sql from the linux command line.

## Python Scripts
Python is really quick and powerful for writing text manipulation scripts. Opening a file, iterating through it's lines, splitting the line into variables and checking for given values can be achieved in 5 lines of code.

```python
with open('file.csv', 'r') as input_data:
    for line in input_data:
	    a, b, c, d = line.split(',')
		if b = 'fubar':
		    do(thing)
```