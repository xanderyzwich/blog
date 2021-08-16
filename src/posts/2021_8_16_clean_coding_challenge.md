---  
title: Coding Challenge with Clean Code  
description: What benefits are there to clean coding?  
date: 2021-08-16  
tags:  
    - codequality  
    - programming  
    - cleancode  
    - productivity  
layout: layouts/post.njk  
---  

After studying Uncle Bob's Clean Code and trying to practice it as much as possible, I find that it can make a huge improvement to the maintainability or even just readability of a piece of code. 

This coding challenge came up in one of my favorite coding communitites:

> Length of the Last Word  
> Given a string s consisting of some words separated by some number of spaces, return the length of the last word in the string.  
> A word is a maximal substring consisting of non-space characters only.  

So, because I like to do challeneges with tests, I put together this bit of unit test using Python's built in unittest package based on the three examples that were given with the challenge. 

```python
from unittest import TestCase

def last_word_length(input_str):
    pass

class TestLastWordLength(TestCase):

    def test_one(self):
        assert(last_word_length_golf('Hello World')) == 5

    def test_two(self):
        assert(last_word_length_golf('   fly me   to   the moon  ')) == 4

    def test_three(self):
        assert(last_word_length_golf('luffy is still joyboy')) == 6

```

Now, I knew that I could pull this off with a single line of Python. I quickly wrote this:

```python
import re

def last_word_length(input_str):
    return len(re.split(r'[\W]+', input_str.strip())[-1])
```

This does everything that the challenge asks for, but part of the goal of doing these challenges in my community is that we use several different languages and it allows everyone to get more familiar with the language that you used, whether they have ever written it before or not. One liners like this are not usually a good idea for long term maintenance OR teaching. So, I took a minute to clean it up a bit. Having tests laid out made it really easy to know that I'd not introduced any errors.

```python
import re

def last_word_length(input_str):
    indefinite_whitespace = r'[\W]+'
    clean_input = input_str.strip()
    words = re.split(indefinite_whitespace, clean_input)
    return len(words[-1])
```

Now, it's pretty easy for anyone with a moderate amount of coding ability to understand what's going on. We have a regex that matches any clustering of whitespace. We have an input string that gets trimmed/stripped of it's surrounding whitespace. That string gets split according to the regex. And then we return the length of the last word. 

There are two main things that this technique improves. Breaking the pieces apart reduces the mental overhead of undestanding each piece. Naming the variable helps to document the intention of that line. It also makes the later lines significantly easier to understand by offering those names. That benefit will help you both with the reading and the writing of your code. The other major benefit comes long after this code has been put into version control. The history of this code allows you to tell which part of this was changed when. Instead of a diff showing that something in this block was changed at a, b, c, and d commits, you can see that the regex changed in commit a, the input cleaning changed in b and d and maybe the split call changed in c. This is especially helpful if you have IDE/editor functionality that helps you to see the git blame info for each line. 

