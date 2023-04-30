Download Link: https://assignmentchef.com/product/solved-cs261-assignment-4-binary-search-trees
<br>
For this assignment, you will implement a binary search tree that can store any arbitrary struct in its nodes. You will start by completing the <em>recursive implementation</em> of the binary search tree (BST) in Worksheet 29. You will then modify it to so it can store arbitrary structures at each node, provided you have a an implementation of a <strong>compare</strong> and <strong>print_type</strong> function for that structure.

We are providing you with the following files:

bst.c – This is the file in which you’ll finish implementing the unfinished BSTree implementation. There is

a main function in this file that you should modify to exercise your BST. The file contains several test cases such as <strong>testAddNode</strong>, <strong>testContainsBSTree</strong>, <strong>testLeftMost</strong>, <strong>testRemoveLeftMost</strong>, and <strong>testRemoveNode</strong>. Your implementation must pass all these test cases, and you are strongly encouraged to add your own tests as well. bst.h – This file should not be changed. structs.h – This file can be extended to test your code with different data types. compare.c- Put your compare and print functions in here. makefile.txt – Remember to rename this file to <strong>makefile</strong> (without the .txt extension).

Worksheet 29 will get you started on your implementation. However, there is one function not mentioned in the worksheet. You will be using the <strong>compare</strong> function to test two values of a node to determine if one is less than, greater than, or equal to the other. This function is similar to the <strong>compareTo</strong> function in the <strong>Comparable</strong> interface in Java. Rather than embedding it into the data structure, as you would do in Java, we will declare it and assume that the user has provided an implementation of <strong>compare</strong> in the file <strong>compare.c</strong>. That way, the user can substitute an appropriate compare function for any data type that they plan to store in the tree.

For example, if you want to store doubles in your tree, you might define the following struct to store at each node.

struct data {  double num;

}

And then define your <strong>compare</strong> function to simply compare the two structs based on the <strong>num</strong> field. However, a user of your data structure could also do the following:

struct pizza {

double cost;  int numToppings;  char *name;

}

And define a <strong>compare</strong> function that compares pizzas based on their name, cost, or number of toppings.

In this assignment, the <strong>TYPE</strong> macro is set to <strong>void*</strong>. This means that the type of value stored in a node is a <em>void pointer</em>, which means it can be a “pointer to anything”. Whenever you dereference a void pointer, you <em>must</em> cast it to a specific type. For example, you can cast a void pointer to <strong>struct data*</strong> (see the definition in <strong>structs.h</strong>), then dereference it to get the <strong>struct data</strong> value the pointer points to. It is the programmer’s responsibility to ensure that they cast the void pointer to the same type of value that was actually stored at that location. You should read up on void pointers in your C reference or on the internet.

The <strong>compare</strong> function is needed because we need some way to compare the values stored in the tree nodes. Note that we can’t just compare the pointers with the <strong>&gt;</strong>, <strong>&lt;</strong>, or <strong>==</strong> operations since this would just compare the memory addresses the pointers point to. Instead, we want to compare some field of the struct that the pointer points to (e.g. <strong>val-&gt;number &lt; otherVal-&gt;number</strong>). The <strong>compare</strong> function will make changing this function for different structs much easier.

Finally, we strongly recommend that you add to the <strong>main</strong> function to exercise your binary search tree by adding, removing, and testing for elements.

<h2>QUESTIONS</h2>

<h3>Question 1</h3>

Show the binary search tree built by adding numbers in this specific order, assuming the graph is empty to start with: 50, 10, 90, 14, 62, 71, 42, 6. ( You may need to add more boxes to the diagram)

<h3>Question 2</h3>

The trouble with binary search trees is that they can become unbalanced depending on the order that you insert values. Give an order for inserting the numbers 1 through 7 such that the resulting tree is a full binary search tree. This problem does not require you to fill in a tree, just write down the order in which you would insert the values. (Hint: it might be helpful to first draw the full tree to figure out how the values must be arranged, then you can determine the order to add them!)

<h3>Question 3</h3>

Part A: Given the following tree, question3.pdf, show the tree after removing the value 42.

Part B: Using the tree produced by Part A, show the tree after removing the value 19.

<h3>Question 4</h3>

The computer has built the following decision tree for the Guess the Animal Game, question4.pdf. The player has an animal in mind and will answer the questions shown in the tree. Each of the players responses is used to determine the next question to ask. For example, if the player is thinking of a sea turtle, she would answer Yes to the first (top) question, “does it live in the water?”, which leads to the second question “is it a mammal?”, to which she would answer No.

Show the decision tree that the computer should build after adding a Zergling and a question to differentiate it, “Does it eat space marines?”, to the tree. The question and the animal should be added below existing questions in the tree. Note that Zerglings <em>do</em> eat space marines , <em>do not</em> live in the water, <em>do not</em> climb trees, and <em>are not</em> mammals (just in case you didn’t know :-))