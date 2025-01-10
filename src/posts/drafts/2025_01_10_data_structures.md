---
title: Intro to Data Structures
description: A commonly overlooked super power
date: 2025-01-10
tags:  
    - craftsmanship  
    - data
    - second  
    - interview  
layout: layouts/post.njk
---
# Introduction to Data Structures

One of the most frequently discussed topics in software development is the validitiy of studying data structures. I personally believe that you can work your entire career without a solid understanding of data structures; however, you will be amazed at how often this foundational information will help you to reach a more robust solution more quickly. 

## Structures

- Arrays
  
- Lists
  - Linked List
  - Doubly Linked List
- Stack
- Queue
- Graph
  - Tree
    - Balancing
    - Recursion
    - Depth/Breadth first 
    - Binary/Ternary/Trie

### Array
A collection of elements where the size of those elements and the length of the collection is fixed. Arrays can have more than one dimension, but those can effectively be considered similarly to if you were storing arrays in arrays. Their key feature is the allocation of a solid memory block which can be addressed internally by the index. Can randomly access any index in constant time. 

### List
Collection with data nodes that are interconnected. The length is dynamic and can grow. Insertion and removal of data can occur anywhere within the list without leaving gaps. Standard linked list does this with each node pointing at the next one, but links/references can also go backwards in a doubly-linked list. Accessing any non-flagged position within the list requires traveling to that position first. 

#### Usage of Lists
The two most common usages of lists are called a queue and a stack. 

A queue works in the same way that standing in line at a store might function. You put thing in (enqueue) by adding after the last position, and you remove things (dequeue) by removing things from the head of the queue. In this format you would have two flagged positions in the list, one for head and the other for tail. 

A stack is the other primary usage. It functions kind of like those plate dispensers that you find at some buffets. Plates are stacked on top and the rest of the stack is not acessible. You pull things out of the stack from the same end that you put them in. In business this is often referred to as Last In First Out (LIFO), whereas a queue is said to be First In First Out (FIFO). 

### Graphs

It turns out that if you have a collection of nodes and connections that they can be arranged in infinitely many different ways, and generically this is called a graph. You've interacted with a more free form graph anytime that you've driven or navigated between landmarks in the world. There are connections between different landmarks. The landmarks or intersections are the nodes of this graph and the connections are the paths or roads. There are also ways that we can store a weight/cost on these connections and leverage this for determining the shortest path. One of the best examples of this was an algorithm devised by Edsger W Dijkstra in 1956. You can find lots of information online about Dijkstra's Algorithm, but it honestly deserves its own lecture. 

#### Trees

So technically a list is a graph with a specific layout, but another common layout for a graph is called a tree. In a tree you have a root node with a fixed number of connections. You can think of this like the root of a tree. There will be very few branches at the root/trunk of the tree. Then each node in a tree has children. 

If you've ever looked at a computer's filesystem then you've interacted with a tree. Every file is contained by a folder (its parent), and the folders are also contained by folders. 

##### Binary Trees and Binary Search Trees

A tree node can generically have any number of children. But if there is a rule to the number of children that are had by a given node then that will give the tree a more specific type. One very important type of tree is defined as having two children per node. This is called a binary tree. And that's technically all that we know about a binary tree, that each node has at most two children. 

BUT, there are much more specific types of tree like a binary search tree. With that one we know that for any node that there will be one child that contains only values less than the current node, and there will be one child that contains only values greater than the current node. 

Does anybody know how to use a phone book? The typical way is to go into the middle and determine whether what you need is left or right, then you repeat this process splitting a new section in half each time. We refer to this process as Binary Search, and it is very much the way that a Binary search tree is designed to be used. The root of a balanced binary search tree will be the middle-most value. If you want something smaller then go that direction (typically left) or if you need a higher value then you go the other direction. Continue on until you find your value (or exhaust the depth of the tree).


##### Tree terms

A tree is said to be balanced if both sides of the tree have the same number of nodes. Additionally we typically would expect a balanced tree to contain a minimum number of generations/tiers. 




    
