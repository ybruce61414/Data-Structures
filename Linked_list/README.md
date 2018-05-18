## Demonstration
 In this section, we will demonstrate how to construct three types of linked lists and how to implement the methods of basic operations on linked lists. To come close to daily application, we let the basic element for the linked list, the **node** object, be the class `student` as shown below.
 
 
 ## What is a Linked List?

  Linked list is a dynamic linear data structure where each element (node) is a separate object with its own memory allocation connected to the other objects via pointers.


 The basic building block for the linked list implementation is the node. Each node object must hold at least two pieces of information. First, the node must contain the list item itself. We will call this the data field of the node. In addition, each node must hold the reference to the next node. The starting node of a linked list is referred to as the **head**.
 
 
 The basic operations that we will implement are all based on a technique known as **linked list traversal**. Traversal refers to the process of visiting each node. To do this we use an external reference (called `current` and is initialized to the head of the list) that starts at the first node in the list. As we visit each node, we move the reference to the next node by **traversing** the next reference.
  
 ![Alt singly linked list](pic/linkedlist.png)

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
 - size
 - remove
 - reverse
 - rotate
 
### Additional Resources & Reference
---
- <https://www.studytonight.com/data-structures/linked-list-vs-array>
- [Problem Solving with Algorithms and Data Structures using Python](http://interactivepython.org/runestone/static/pythonds/BasicDS/ImplementinganUnorderedListLinkedLists.html)
- <https://www.quora.com/What-is-linked-list-1>
- [Linked lists non-contiguous memory](https://stackoverflow.com/questions/23571432/linked-lists-non-contiguous-memory)
 
  
     