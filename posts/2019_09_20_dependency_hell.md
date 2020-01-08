---  
title: Dependency Hell    
description: Best practices must evolve    
date: 2019-09-20  
tags:  
  - java  
  - gradle  
  - technicaldebt
  - codequality
layout: layouts/post.njk    
---  
## Traditional Best Practices ##
It is typically accepted that any code that is needed in more than one place should be abstracted away somewhere.  Classes with repeated logic get methods, packages with repeated logic get classes, projects with repeated logic get dependency projects.  It makes sense.  You don't want to update the code in many places, just do it once and let it trickle through the code base, and when you moved jar files manually from output of one project into another for usage then you could be pretty confident that things would remain stable.

## To the Cloud! ##
Once you move a legacy java web service into the modern era then a few things happen. SOAP becomes REST (I wish), XML becomes annotations and Java configuration classes, and you move from a traditional servlet container (Tomcat, WebLogic, etc) into Springboot jars (typically with Tomcat baked in). Something that should also happen between Y2K and cloud native application deployment would be a modern build tool with an artifact repository.  We're moving from Ant to Gradle, and utilizing a Nexus artifact repository for our dependencies.  

This is all great, and I'm thoroughly enjoying the learning that I'm getting in this position. But, our application has a spiderweb of 6 'common' dependency jars that we own.  The application that we are currently upgrading uses 4 of them.  There is one for each of two databases (logical) and then there is a SUPER DEPENDENCY that all of the others inherit EVERYTHING from.  To make things even more difficult, the application that we are working on depends directly on the SUPER jar as well as three jars that then depend on the SUPER jar.    

**ENTER HEARTACHE**  
Gradle is a wonderful tool. After our having gotten it working, I realized that local environment setup means being on the right git branch and having some environment variables setup for running the application so that we don't accidentally commit passwords while working around things that are done by our CI/CD.  Along the way however, there were many pain points.  Logging dependencies are apparently buried in every single thing that we use, and apparently SLF4J was being pulled down by the dozens.   

We are told that the original architect and developer of our application was an absolute genius.  We are not.  This thing implemented it's own hibernate, property handler, application context, and many other things that are gotten for free with modern build tools, frameworks, and dependency injection; and many of these features are implemented deep within our dependency jars.  Particularly the application context and property handler were implemented all the way down in the SUPER jar.  They required access to a particular property file on the filesystem where the application resides.  I can see where that would have made the management of some dozen applications more uniform and easily understood.  When you deploy into a Cloud Foundry environment then the file system isn't exactly something that is at your disposal.  We have overcome this by adopting a configuration server to serve property files from git through a web server that makes them immediately available to any server making request for it.  SUPER jar doesn't like that.  FILE NOT FOUND meets NULL POINTER and everything breaks. Refactoring the four dependencies has been deemed outside the scope of our seven week engagement with the cloud foundry team that is helping us.  

## Solutions ##
We eventually managed some quick fixes to make things work, and were given the confidence by our business team that we will be working on a complete ground up redesign of our applications in the future where we would have the opportunity to make corrections to the things that caused us so many problems.    

Java configuration classes replaced each of our XML files that were used previously, and we were able to force feed the home baked application context with properties from the configuration server, and overcome some issues.    

Later we found an issue with our Junit design that meant that initialization was attempting to read that same property file, and we were able to overcome this by a quick fix to the SUPER jar to make direct use of `"${foo}"` notation and commenting away the file read.  

The gradle build file required a **TON** of excluding to prevent duplication of dependencies (which may or may not have been based in different groups).  We have decided that these common jars should not be so interdependent because we currently require touching of six projects in order to make one work.


If you have any stories, recommendations, or solutions that you've come across for such thing then I ask that you please comment.
