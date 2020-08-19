---  
title: Uncle Bob - Lesson One  
description: My summary of the video.  
date: 2020-08-18  
tags:  
    - career  
    - codequality  
    - cleancode
    - development
    - "uncle bob"
layout: layouts/post.njk  
---  

This material is a summary of a [talk by Uncle Bob that I watched on YouTube](https://www.youtube.com/watch?v=7EmboKQH8lM)

> Regardless of age, race, gender as developers we share a passion for something, and can communicate about it in a way that most other people can't.

## Introduction to Clean Code

![The only valid measurement of code quality: wtf's per minute](/img/wtfpm.jpg)

In this comic the door on the right must contain some pretty terrible code with five simultaneous WTF's, but how do we move from that to the left with only two? How do we avoid driving coworkers mad trying to understand our code?

In the lecture room there are thousands of processors. Your smartphone alone contains more computing power than the the planet Earth in 1980. Computers/processors are in a huge amount of things around us. Airbuds, cameras, lights, speakers, smoke detectors, and even exit signs contain small processors. In speakers and microphones, a small audio processor is used for removing audio hum. It's become less expensive than using a traditional capacitor and inductor. Trickle charge in emergency exit signs is probably being monitored by a processor. Any given person in our society interacts with a software system at least once every minute. There is software running in your refrigerator, dishwasher, stove, tv, remote, and even your car. Modern cars run over a hundred million lines of code running in the entertainment system, gps, and even in the engine controller. When you push on the brake pedal there are if statements that decide whether or not to slow/stop the car. This means that there are likely dozens of people that have died because software controlling the brake and accelerator failed for some stupid reason.

## Why? 

You and I are killing people. We didn't get into this business to kill people. We became programmers because we had some experience with a cool machine somewhere that we were able to make do something fun, and we decided that we wanted to do that for the rest of our life. Now you can kill people with software, or lose 450 million of dollars in 45 minutes. There is nothing that you can do in our society without software. Society doesn't realize just how dependent everything is on software. And developers control that. The people that believe that they rule the world bring their rules to us and we write the software that governs the machines that actually run the world. Society doesn't yet comprehend how dependent they are upon developers. They won't until some dumb programmer does one dumb thing and kills 10,000 people at once. When that occurs the politicians of the world will rise up and point a finger at US.

The CEO of Volkswagen North America testified before the American congress about why [their software was cheating EPA regulations in California](https://www.epa.gov/enforcement/volkswagen-clean-air-act-civil-settlement). He said "It was just a couple of software developers that did this for whatever reason." It ***was*** a couple of developers that did it. They are now in jail. But when the politicians of the world come to hold us accountable for our actions they will ask "How could you let this happen?" and if our answer is "*Boss said that it had to get done by Tuesday*" then they will be forced to regulate us and tell us what languages we can use, what courses we must take, what books we must read, what process we must follow, and what signatures that we must get to do anything.

How do we avoid this? We avoid it by getting there first. We have to establish an ethics of software development. We are not a profession as there is nothing that we profess. We have to build our own set of standards so that when the politicians of the world come to hold us accountable we can respond with proof that it is not neglegence because we have standards, morals, and ethics that have been maintained. They will come to us to looking for those standards that they can enforce, and we had better have a good definition of what it is that we hold dear as a profession. One of those had better be cleanliness of code.

## Why are Programmers so slow?

[Kent Beck](https://en.wikipedia.org/wiki/Kent_Beck) wrote a book called [Implementation Patterns](https://en.wikipedia.org/wiki/Special:BookSources/978-0321413093). In its introduction it stated that the book was based on a '***fragile premise***' that '***good code matters***.' This seems pretty solid. If we work on a green field project with no existing code then we can get features completed extremely fast. By the time a year has past, a request for similarly sized feature may take six months. The speed at the beginning is done at the cost of a bit of mess. Over time this slows progress down to around 1% of the original rate. 

You have to figure out how to go faster. Adding more people to the team makes the team slower. The experienced people have to slow down to train the new people, and you have to hope that the new peole come up to speed in time to become helpful. The new people then wind up being trained by the old code, and they emulate it. The problem of messy code becomes worse. 

If programmers didn't make a mess then they'd be faster. You could add new features in a reasonable amount of time as long as the code was able to be maintained in an orderly way. We make the mess so that we can go fast. Then once the code finally works there can be a fear of breaking it that prevents it being touched again. Having gotten it work is only first part. Nobody writes clean code. Once it works it will be a mess. Once it works, it should then be cleaned. That should take roughly the same amount of time that it took to write it. Nobody wants to put that time in, and that's the problem. You aren't done when it works, you're done when it's right. With that attitude it would always stay clean and you'd never experience the slow down. 

## What is Clean Code?

Uncle Bob says:  
> The only way to go fast is to go well.


### [Bjarne Stroustrup](https://en.wikipedia.org/wiki/Bjarne_Stroustrup) - creator of C++ 
> I like my code to be elegant and efficient ... clean code does one thing well.  

But, what does "one thing" mean? Uncle Bob has a theory.

### [Grady Booch](https://en.wikipedia.org/wiki/Grady_Booch) - writer of Object Oriented Software Design with Applications
> Clean code is simple and direct. It reads like well-written prose...  

What does it mean for code to resemble well-written prose? Uncle Bob's theory on this will be shared as we go forward.  

### [Michael Feathers](https://michaelfeathers.silvrback.com) 
> Clean code always looks like it was written by someone who cares.  

When's the last time that you read a module and thought that the author cared about you and everyone that would be reading that code?

Your job is only half to get code to work. *The more important half of your job is to write code that other people can understand and maintain*. Understandable code that doesn't work can be made to work, but working code that can't be understood will become useless as soon as the requirements change. It is more important to communicate with your peers using a programming language than it is for the computer to understand you.

### [Ward Cunningham](https://en.wikipedia.org/wiki/Ward_Cunningham) - inventor of wiki
> You know you are working on clean code when each routine you read turns out to be pretty much what you expected.  

Very first wiki is still alive at [c2.com](http://c2.com) and was built in 19 lines of Perl in 1990. It's full of desing patterns, extreme programming and agile stuff.

Everything is pretty much what you expect or **ZERO** WTF per second.

## Analyzing some lines of code

Uncle Bob gives a few minutes to read and understand some example code that stretches across three slides and is far from being easily understood. The code is explained for handling his testing tool called Fitness which has tests defined on wiki pages. The code fetches setup and teardown pages for a test and creates html. `TestableHTML` is the function name which he calls horrible as functions should have verbs for names because they do something.

The first line of the function is creating a wiki page and the next is creating a string buffer which takes you crashing immediately from the highest level of abstraction into the lowest. Every line of a function should be at the same level of abstraction, which is one level below the name. We write code in a very rude way. We oscillate from high level to very low level as we think about things. There is nothing wrong with writing things this way, but you must come back and clean it up so that it can be easily understood. 

The function follows four repetitions of the form: null check, page crawler, and three appends with one of the blocks having an extra append for a new line. Getting something done and then using copy and paste is common enough of a technique to follow for getting code to work, but not something that should be left.

### Long code is not Good Code
A cursory cleanup of this code brings it into a single page where it becomes visible that the entire function body is enclosed in a single `if` statement. The control of that `if` statment has been moved into a boolean variable whose only purpose is to explain the state that it contains. `if(isTestPage)` reads more like well-written prose. The four similar blocks have been brought into one single block. This is much easier to understand by the simple fact that it's smaller. 

### Good Code / Refactored Function
If smaller is better then let's go a step further.

+ functions should not be 100 lines long
+ functions should hardly ever be 20 lines long
+ prior refactor was too long even in one screenful

```java
public static String renderPageWithSetupsAndTeardowns(
    PageData pageData, boolean isSuite) throws Exception {
        if (isTestPage(pageData))
            includedSetupAndTeardownPages(pageData, isSuite);
        return pageData.getHtml();
    }
)
```

This function takes no time to understand. It is very polite.

## Polite Code / Rules for writing a news paper article

If you read the news there is an expected format.

1. Start with a headline
2. Synopsis/abstract paragraph that describes the entire content
3. ...more detailed...
4. ...even more detailed ...
5. so on
6. so forth

The most detailed bit is at the very end. This allows you to read a bit and decide whether you are still interested, and that is polite. It allows for early exit as soon as you get bored of the detail. In code this allows you to read through what is going on without getting into unneccessary detail. 

Having short functions with a single level of abstraction allows *politely* for you to dig as deep as you need to and to understand the purpose from each level.

## Shrunk Code / The Rules of Functions
What's the proces of refactoring the long code into something shorter?

The rules of functions are as follows:
1. Functions should be small.
2. They should be smaller than that.

How many lines should a funciton be? It should fit on your screen. Originally a screen (once they were available in the 80's) would have been 24 lines by 72 columns. this follows from the fact that punch card had 80 holes per line and 8 were used for sequence numbers. This led to functions of 20 lines or less. But Uncle Bob's rule is that a function should do one thing.  

In IntelliJ you can use the refactoring menu with an entry called extract method. If you cannot meaningfully extract another function then your function does exactly one thing. This means that you should extract methods as far as you can to have tiny little functions.

Before you say that this would lead to your drowning in thousands of little, tiny functions, you will not drown because you will have to give them names. As they are named they should be moved into appropriately named classes in appropriately names packages. 


## Shrunk Code / Drawing a Function
Long ago Uncle Bob wrote this function called gi. GI stood for graphic interpreter. It was 3000 lines long, but this was the general shape of it:

![Code form with an inconsistent sawtooth shape with many varying depths of nesting](/img/uncle_bob_code_shape.png)

If some part of your brain relaxes when you see this shape then it's because you've come to know similar code it by it's landmarks. If rotated 90 degrees then it would resemble the horizon. This is something our brains became accustomed to over time. It certainly isn't because nested code is enjoyable to read or maintain.

If you have a couple of variables `int i,j;` that are manipulated in the first indent section. Extract method on this section. If `i` and `j` are both local variables then you can make them global for the time being. Now you can extract method on all of the funcionality that manipulates `i` and `j`, and you now have a bit of data and a set of functions that operate on that data. This is what we call a class. This refactoring method can help you to discover the true object oriented structure of the system that you are trying to design.

## When and why was Java invented?

[James Gosling](https://en.wikipedia.org/wiki/James_Gosling) in 1991 invented Java at Sun Microsystems in the Contract Programming division and there was a contract for a cable television set top box. Sun was dedicated to C++ at the time, but he hated the language so he made his own. He called it Oak, and he used it for the project and it worked and the contract ended which cast Oak to the garbage bin.

Sun Microsystems was a hardware company and their marketing scheme was selling hardware. They realized that if they wanted to be successful then they should win over programmers due to their feedback provided for buying systems. It would be really great if they could provide "the language of the internet" (whatever that might be). As they looked around found James Gosling had Oak. They took Oak and renamed it something more stimulating like coffee. 

## Prose Code 

Indenting
+ Smallness also implies:
  + functions should not be large enough to hold nested structures.
  + 1-4lines would be ideal, 6 might happen occasionally
  + therefore, the indent level of a function should not be greater than one or two
+ This, of course, makes the functions easier to read and understand

If you  keep refactoring out chunk by chunk then you can make the body of if statements into function calls.

```java
if(cupIsEmpty){
    fillCup();
}
```
This reads like well-written prose.

## Arguments

### Count
The best case for argument count to a function is zero as that is the easiest to understand. One is very straight forward as well. Two arguments can only be arranged two ways, but with three then there are 6 possibilities for ordering your arguments as it follows by N-Factorial. With 4 there are 24 options. Uncle Bob's personal rule is that a function shouldn't include more than 3 argments out of politeness to the reader. If you have a function and you want to pass six things into it, then if those six things are so cohesive that they should be passed in together why aren't they already collected into an object?

### Booleans
If you are passing a boolean into a function then there is likely an if-else in that function. Pull that out and have a function of the if and a function for the else. `doThis(4, 5, 6, true)` is rude. What does that `true` mean? If it is really important then you would benefit from a method name that denoted what was being done if it is `true`. The exception to this rule is something like `setFlag(true)`.

```java
if(boolIsTrue)
    doFirstThing();
else
    doSecondThing();
```
Isn't that easy to read?

### Output Control
Arguments passed into a function for the purpose of collecting the output. It doesn't make sense when you are reading it. Your vertical momentum leads you to try to pass it over, but it demands that you come back and understand that out of place argument. It's a double take. It demands that you return to figure it out. If code causes you to do a double take that is rude. It forces you to stop what you are reading and go back. 

> Make sure that your code is not surprising.

## Avoid Switch Statements 
Switch statements are bad. If you have a switch statement that is on the type of a shape, then there must be an `ENUM` somewhere that defines those types. Switch statements will need to surround similar usages throughout your code. If you add a new type to the `ENUM` then you need to find all of the switch statements and make a change. Don't forget the if/else statements. When you need to add a new type, THEN you must go through and find all of the right places to add your new shape. This is overly complex. 

Instead you should use polymorphism (inheritance) with a base class that contains the definition of the common functionality. Then each child class implements its own functionality and when you need to add a new shape then you only need to make changes in the new class for that shape, and it can be used by all of the other code that manipulates the different types of shapes. All of the draw, rotate, area, and other functions are wrapped inside the class and it manipulates its own data.

> **Open/Close Principle**  
> A module should be open for extension,  
> but closed to modification

Switch statements cluster together dependency. There is a single module that has dependency on all of these outside modules. The switch statement is then used by some other modules. If there is a change in one of these dependencies of the switch statement then the switch code and everything dependent ON the switch code must be recompiled and redeployed. This breaks the ability to independently deploy parts of the system. Keeping interdependency minimal allows for independent deployment such as being able to deploy your GUI separate from your business logic. One really nice way to do this is to avoid switch statements.

## Side Effects
A side effect is a change to the state of the system. The function `open()` has a side effect as it leaves an open file. Another such is `new` that allocates some memory. These side effect functions come in pairs, and we are really bad at remembering to call the second part of the pair. Garbage collection is a hack that allows us to forget about cleaning up the memory that we use. We still have to deal with opening and closing files and some other such pairs. Forgetting to let go of the resources that you allocate will eventually result in a system failure once the resources are depleted. 

### Using Lambdas To
A lambda is basically a class with one function called execute. We can use it to make `open()` safe. 

```java
void open(String fn, Lambda proc){
    File f = File.open(fn);
    proc.(f);
    File.close(f);
    return;
}
```
We now have a function that has no side effect. You pass a lambda into the function and the open and close are paired to prevent unintended side effects.


### Command and Query Separation
A function that returns `void` must have a side effect, otherwise it is useless. A function that returns something shouldn't have any side effect. This is a convention called **Command and Query Separation**

### Prefer Exceptions to returning error codes
Exceptions provide the opportunity to handle expliticly expected breakage states. Error codes are considerably easier to overlook.

If you are going to have a `try` block inside of a function then it is best to have **ONLY** the `try`/`catch`/`finally` and no pre or post blocks.

## DRY Principle (Don't Repeat Yourself)
We want to avoid duplication as much as possible because it's sloppy. Move the duplicated code into a function, and if it is slightly different then you need to include an argument that allows you to know when to execute the different part. That works great for code that is duplicated. 

Sometimes you find the manipulation of a complex data structure requires duplication of a looping structure. If you have lambdas then you can use them here, as you create a looping method that can be passed in a lambda for what to execute inside that looping structure.

## Structured Programming 

### Edsger Dijkstra's Vision 
[Edsger Dijkstra](https://en.wikipedia.org/wiki/Edsger_W._Dijkstra) was the first programmer in the Netherlands, and one of the first in the world. He survived Nazi occupation. He went into school and wanted to become a nuclear physicist. He saw the very first computer in the Netherlands, and went to his adviser and complained that there was no body of knowledge, formalism, or discipline in computers. He didn't think that his peers would take him seriously if he studied computers. The adviser suggested that he might be one of the ones that helps to define that formalism and body of knowledge. Dijkstra took this as a challenge and became the first programmer in the Netherlands. When he was married in the 1950's he had to list his profession. He tried to list that he was a programmer, but they denied him because that wasn't a known profession. He changed it to nuclear physicist. He said that he made the more difficult choice of programming over nuclear physics.

He [wrote a letter in 1968](https://www.cs.utexas.edu/users/EWD/ewd02xx/EWD215.PDF) saying that `goto` was considered harmful which was extremely disruptive. This was rejected for years, and people wrote scathing letters in professional publications debating his argument. All these years later we don't have `goto`. His argument was that software should be like mathematics. There should be postulates and theorems that have been proven. These would be proven software that would be adapted by simple lemmas utilizing these proven pieces. He built up a mathematical structure of proof around if statements, loops, and many things. He discovered that certain algorithms cannot be proven correct because they have unrestricted `goto`'s. This is basically [Alan Turing](https://en.wikipedia.org/wiki/Alan_Turing)'s [Halting Problem](https://en.wikipedia.org/wiki/Halting_problem). Every algorithm can be composed of from three structures: Sequence, Selection, and Iteration.

### Reality of Programming
We don't prove anything. Dijkstra's vision failed. We do lean on and risk our lives everyday on something else that cannot be proven. That thing is science. Science is made up of things that cannot be proven correct, but can be proven incorrect. We can surround something with enough tests that it's assumed correct. We can do similarly and demonstrate the non-failing qualities of software with tests. We may not be able to prove our software correct, but we can provide that it isn't incorrect by surrounding it with sufficient tests.

