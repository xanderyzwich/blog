---  
title: Logging Improves Quality of Life  
description: If you care then you will work to improve the logging in everything you write.  
date: 2020-02-25  
tags:  
  - logging  
  - development 
  - programming 
  - beginner
layout: layouts/post.njk  
---  

[Here](https://dev.to/theodormanolescu/comment/1b5o) I found a pretty good explanation of logging. 

The questions posed were:
  1. When should I be logging information?  
  2. What information should a log message always contain and what is optional?  
  3. How do you decide what level this log should be set to there's many info, trace, debug, error, warn and even "verbose".  


The answer given: 
>Consider your application a human.  
>Depends how much info do you want to get from it.  
Example:  
+ **6 months baby** -> App with no logs and no error handling either works or doesn't, baby is ok or crying.  
+ **1.5 years** -> app with small error handling and 1-5 word logged like error save or error buy, baby has a vocabulary of 50 words  
+ **2.5 years** - app has some error handling and logs that express an action like could not save order, baby can make simple sentences like i fell down  
+ **5 years** - app logs that express intention with some context and can provide info about what's wrong with it, for baby while eating some candy i got sick and my stomach hurts  
+ **18 years** - app handles errors correctly and logs with full relevant context and can provide info for most of the problems, human drank allot of beer now is drunk and he knows he needs to sleep it off or eat something  

---

Knowing that there was some terrible event is a good start, but knowing what happened is far better, and even better still is knowing the cause.  Moving even further still,  you will figure out that it is really good to know if anything good has happened, or when was the last time that X thing didn't fail.

I spent some years performing support activities for an application before having the opportunity to upgrade the logging framework (we went from log4j to log4j2) and while I was in there making changes in every single class that performed logging, I increased the logging functionality. Log4j2 has a thread context hashmap that can hold whatever you like, and those variables can be referenced in the configured logging pattern. I was really excited. For the most part I didn't create any entries in the logs that didn't previously exist, but I did make several enhancements.
 
So many times when you are debugging something you find yourself looking for a little more context. Logging should give you an idea of where you should look for when something is going wrong. Debug logging should capture notable data. If your sql is being generated in a completely different place than the original flow of the logic then you should really log the sql. If you don't log enough information then you will find yourself struggling to debug issues, but if you have the right information being logged then you should find that debugging sessions are less intensive.

---

## Basic Improvements

1. Generate a transaction id for every request, return it in the response header, and add it to the logging context. This allows for a transaction to be traced as long as the client can provide the transaction id. 

2. Log the class where the message was generated

3. and the method/function

4. Debug level logs AND Error logs should both contain the request and response.

5. Database queries should be logged in debug (even if not needed elsewhere).

6. Log as much as possible of the following
   + timestamp
   + requesting system identification
   + database table/schema/ being accessed
   + entry point
   + response time

Overall you want to know as much as possible about who or what system is making the call to the applicaiton, what that transaction looks like, what generated calls look like, and what particular exceptions are occurring (even if being captured). You will learn over time what things are helpful for debugging your applications and you can add or remove from this list for your own usage. Make sure that each logging level has a purpose and that the messages generated for that level apply to that purpose. 

## My Personal Beliefs
+ **ERROR** is when something goes wrong
  + i.e. "This thing went wrong"
+ **WARN** should illuminate any potentially harmful situations
  + i.e. "This odd thing happened and could be relevant if something is going wrong"
+ **INFO** should show how the application is progressing from a little higher of a level; Incomming calls, outgoing calls, anything substantial on an external unit of work level.
  + i.e. "Received request of type X, called Y database,"
+ **DEBUG** should help me track the exact process that is going on when I am researching issues and help me to find the source of a problem fairly quickly.
  + i.e. "Entering/exiting X method call with input/output data that looks like Y"

