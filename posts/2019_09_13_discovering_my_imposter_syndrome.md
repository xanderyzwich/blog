---  
title: Discovering My Impostor Syndrome  
description: Coming to better understanding of my skill level  
date: 2019-09-13  
tags:  
  - impostor syndrome  
  - mental health
  - meta  
layout: layouts/post.njk    
---  

I've now been working as a developer for five years, but along the way I never felt like my skill level had improved. During that time I had spent four solid years working on the same application with a number of very talented developers who knew a great deal more than I. It was great as I was able to learn so many different things about our application and all of the technology and systems directly around us. 

## A Bit About Our Application ##
We owned and maintained a data storage solution that served CRUD operations as a Java web service over SOAP requests. We deployed into a Tomcat instance that we also owned and managed using a 'pipeline' that consisted of a build server where we checked out code from SVN repository, compiled, and then pushed out into our application servers (RedHat VM's that were ours alone); all of which was being done with our custom written bash scripts which were highly interdependent. Our data storage was a mix of Oracle SQL Server and Datastax/Cassandra NoSQL clusters. We utilize Java Messaging Services (JMS) to publish messages out to people interested in updates to the data, and Java Management Extensions (JMX) to trigger various processes in our application from outside the already running Java. 

## Back to the Meta ## 
So, along the many years of supporting and managing this application I became deeply intimate with it's inner workings (some of my peers would refer to ME as the Subject Matter Expert).  During the majority of this time my primary duties did NOT include writing changes to the Java code itself.  The program is 'wired' via some controlling tables in the database that tell it where data is and how to handle it. Due the the nature of this application, there were design choices made that meant that it was not a good fit for pulling out large data set, but should be queried as specifically as possible. As such, clients had to be advised as to how they might fit their logic flow into our data access methodologies.  There was a great deal of working with these client teams to model their data and the ways that they would access it so that neither their application nor ours was negatively affected.  **I became a specialist in this application.**  That implied a great deal of knowledge in how our environment functioned.  I thought that this was just how everyone worked.  

## Time for a New Team ##
After the four years that I spent with that team, I was granted a transfer into another team for an adjacent application.  In the early months with this team I have had the privilege to go into a cloud training and redesigning one of the applications to adopt a new tool set and environment.  We are moving from WebLogic deployed XML configured Java (still SOAP) web service into Springboot with a Pivotal Cloud Foundry deployment.  Most of our developers were VERY excited about attending these sessions for eight weeks.

As we work through moving files over from the old project into the new, there is a lot of finding and string replacing, and the like.  After having become pretty fluent in SED, GREP, FIND, and use of IntelliJ, these tasks were pretty simple and I would rattle off Bash commands to make it happen.  This is when I started getting the comments about being a 'bash wizard' or 'command line guru' as apparently nobody else on the team is as comfortable with these things.  When it comes time to find occurrences of things and usages throughout the entirety of our project Eclipse proved to be a poor tool for the job as it was very slow and cumbersome to deal with.  IntelliJ on the other hand offers quick tools for these things.  Again, I hear sighs and comments about 'we know, IntelliJ is better' as everyone around me continues using Eclipse and Spring Tool Suite.  Many of the developers on this team have been coding for more than a decade, and are respecting of my seemingly well formed opinion on things.  ** **MIND BLOWN** **   

## Am I a Senior? ##
Now I'm forced to evaluate whether my previous thoughts of being a junior to --maybe-- mid level developer could be largely mistaken.  After having gotten a deep knowledge around some subjects (even beyond the engineering classes in college) I somehow managed to **completely** overlook the value of my skill set.  I have done all that I know how in terms of assisting anyone that I know with high level troubleshooting of issues that they may be facing in whatever development work that they might have as well as working with some online communities to help people learn programming and overcome issues that they may be facing.  Looking back, I do realize that most of the times I can help them at least find the direction to look in for finding the cause of their problem.  

## Impostor Syndrome ##
It dawns on me only after this realization that the standard explanation of "believing that someone will discover you as a phony" might not encompass all of what entails impostor syndrome.  My belief wasn't that I'd be found as a phony, but instead that the position that I held was of little importance and skill; especially as most of my work didn't involve writing 'code'.  I'm just now coming to realize that having been so far junior to the peers in my old team led me to a *very* skewed view of what is junior.  I had been given tasks thought to be below the rest of my team and just believed that these were super easy, and not that my skills were sufficient that I was getting bigger work than a fresh graduate would be given.  Complex data manipulation with hand written scripts and giant Bash one-liners isn't something that someone exactly understands right out of school, but it would be something that I did as a 'menial' task.  

## Conclusion ##
With so much material already out there on impostor syndrome, I still never understood it to be quite what I've experienced.  These random thoughts might be a bit off on the definition of what most people would consider the syndrome to be, but overall I feel like the intention comes down very much to the same thing.  I really hope that this helps somebody else along their journey. 
