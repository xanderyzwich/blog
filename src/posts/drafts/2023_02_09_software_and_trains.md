---  
title: Software like trains  
description: Analogies can be really helpful  
date: 2023-02-09  
tags:  
    - devops   
    - planning  
    - teamwork  
    - craftsmanship  
layout: layouts/post.njk  
---  

A new analogy that's been going through my mind lately is one that likens software to trains, in particular subway trains.

# Monolith v Modules

A monolith is like a train that has to be built all at once, but trains are usually made of cars that can be added, removed, or replaced individually. You can even have multiple trains each with a different version of a particular module for comparison testing under the same load volume. 

# Deployment/Repair Windows

Many traditional deployment practices involve taking down a server in off hours, deploying changes, and then bringing the server up. This has many excess costs and drawbacks. If this were a subway train it would be akin to stopping service on a given train line and repairing the train while it remains on that line. You cannot serve customers through that line while it happens. There's pressure to do so in hours with least volume, and those tend to be while everyone is asleep. This means that you are running a smaller crew, they are working during sleep hours, and any delay/problems risk excessive downtime to the service. 

More modern deployment strategies would involve not only having multiple trains running on the same line but also a station where the down train can be moved to allow the other trains to continue serving users. Once this capability exists, you can do repairs during operational hours. When repairing things during normal business hours you will have more people on hand to troubleshoot and discuss possible causes, and they can be more rested and more mentally sharp. It also allows you to take more time to ensure work is completed with higher quality. 

# Configuration Management

If your configuration is baked into the build or the code then everytime that it needs to be changed it's like removing a train from service (even if others are still running), and reconfiguring (building) it before returning it to service. What type of things could need configuration on a train? Maybe the speed limiter or brake force are requiring configuration. More mild configuration can provide better user experience (no jerking) while more extreme configuration allows for faster total service time. There could also be a difference of wear and tear on the machine. It quickly becomes apparent that it is desireable to change configuration at different points in the day. Highest volume windows would be better to serve in faster service time, while lower volume windows could preserve wear and tear along with more comfortable user experience. On the train this would likely just be a lever and how the controller moves the lever, but in software we need something like a configuration server or feature flag service. With these things we can change the operation of the system without taking the train out of service or even waiting for it to return to the maintenance station. 

