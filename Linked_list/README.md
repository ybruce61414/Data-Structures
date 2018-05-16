 ## What is a Linked List?

  Linked list is a dynamic linear data structure where each element (node) is a separate object with its own memory allocation connected to the other objects via pointers.. 


 The basic building block for the linked list implementation is the node. Each node object must hold at least two pieces of information. First, the node must contain the list item itself. We will call this the data field of the node. In addition, each node must hold the reference to the next node. The starting node of a linked list is referred to as the **head**.
 
 ![Alt text](pic/linkedlist.png)

## Advantages of Linked Lists
- They are a dynamic in nature which allocates the memory when required.
- They have efficient memory utilization.
- They can grow and shrink during run time.
- Insertion and deletion operations can be easily implemented (time complexity: **O(1)**).

## Disadvantages of linked lists
- Extra memory is required for a pointer holding the reference to the next node.
- No element can be accessed randomly; it has to access each node sequentially (time complexity: **O(n)**).
- Reverse traversing is difficult in linked list.

## Types of Linked Lists

 1.   singly linked list          
 2.   circular linked list 
 3.   doubly linked list
 
 ## Basic Operations on Linked Lists 
 - append & prepend
 - add before & after node
 - swap two nodes
 - search
 - remove
 - reverse
 - rotate
 
### Additional Resources
---
- <https://www.studytonight.com/data-structures/linked-list-vs-array>
- [Problem Solving with Algorithms and Data Structures using Python](http://interactivepython.org/runestone/static/pythonds/BasicDS/ImplementinganUnorderedListLinkedLists.html)
- <https://www.quora.com/What-is-linked-list-1>
- [Linked lists non-contiguous memory](https://stackoverflow.com/questions/23571432/linked-lists-non-contiguous-memory)
 
  
     