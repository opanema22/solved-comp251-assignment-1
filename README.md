Download Link: https://assignmentchef.com/product/solved-comp251-assignment-1
<br>
<strong>Exercise 1 <em>Building a Hash Table </em></strong>We want to compare the performance of hash tables implemented using chaining and open addressing. In this assignment, we will consider hash tables implemented using the multiplication and linear probing methods. We will (respectively) call the hash functions <em>h </em>and <em>g </em>and describe them below. Note that we are using the hash function <em>h </em>to define <em>g</em>.

Collisions solved by chaining (multiplication method): <em>h</em>(<em>k</em>) = ((<em>A · k</em>) mod 2<em><sup>w</sup></em>) <em>&gt;&gt; </em>(<em>w − r</em>)

Open addressing (linear probing):        <em>g</em>(<em>k,i</em>) = (<em>h</em>(<em>k</em>) + <em>i</em>) mod 2<em><sup>r</sup></em>

In the formula above, <em>r </em>and <em>w </em>are two integers such that <em>w &gt; r</em>, and <em>A </em>is a random number such that 2<em><sup>w−</sup></em><sup>1 </sup><em>&lt; A &lt; </em>2<em><sup>w</sup></em>. In addition, let <em>n </em>be the number of keys inserted, and <em>m </em>the number of slots in the hash tables. Here, we set <em>m </em>= 2<em><sup>r </sup></em>and <em>r </em>= <em>dw/</em>2<em>e</em>. The <em>load factor α </em>is equal to <em><sub>m</sub><u><sup>n </sup></u></em>.

We want to estimate the number of collisions when inserting keys with respect to keys and the choice of values for <em>A</em>.

We provide you a set of three template files within COMP251HW1.zip that you will complete. This file contains three classes, a main class and one for each hash function. Those contain several helper functions, namely generateRandom that enables you to generate a random number within a specified range. Details on which functions are included, how to use them, and where to add in your code can be found as comments in the java files. Please read them with attention.

Your first task is to complete the two java methods Open_Addressing.probe and Chaining.chain. These methods must implement the hash functions for (respectively) the linear probing and multiplication methods. They take as input a key <em>k</em>, as well as an integer 0 <em>≤ i &lt; m </em>for the linear probing method, and return a hash value in [0<em>,m</em>[.

Next, you will implement the method insertKey in both classes, which inserts a key <em>k </em>into the hash table and returns the number of collisions encountered before insertion, or the number of collisions encountered before giving up on inserting, if applicable. Note that for this exercise as well as for the rest of the homework, we define the number of collisions in open addressing as the number of keys encountered, or “jumped over” before inserting or removing a key. For chaining, we simply consider the number of other keys in the same bin at the time of insertion as the number collisions. You can assume the key is not negative.

You will also implement a method removeKey, this one only in Open_Addressing. This method should take as input a key <em>k</em>, and remove it from the hash table while visiting the minimum number of slots possible. Like insertKey, it should output the number of collisions. If the key is not in the hash table, the method should simply not change the hash table, and output the number of slots visited. You will notice from the code and comments that empty slots are given a value of <em>−</em>1. If applicable, you are allowed to use a different notation of your choice for slots containing a deleted element.

You can then implement tests in the main class. Make sure to test your assignment thoroughly by thinking about all the different situations that can occur when dealing with hash tables.

For this assignment, you will need to submit a zip file containing the completed version of the three provided java files on codePost.

<strong>Exercise 2 <em>Least common multiple </em></strong>This problem aims to study an algorithm that computes, for an integer <em>n ∈ </em>N, the least common multiple (LCM) of integers <em>≤ n</em>.

For a given integer <em>n ∈ </em>N, let <em>P<sub>n </sub></em><em>p<sup>x</sup><sub>k</sub></em><em><sup>k</sup></em>, where <em>p</em><sub>1</sub><em>,p</em><sub>2</sub><em>,··· ,p<sub>k </sub></em>is a strictly increasing sequence of prime numbers between 2 and <em>n </em>and for each <em>i ∈ {</em>1<em>,···k}</em>, <em>x<sub>i </sub></em>is the integer such that <em>p<sup>x</sup><sub>i </sub></em><em><sup>i </sup>≤ n &lt; p<sup>x</sup><sub>i </sub></em><em><sup>i</sup></em><sup>+1</sup>. For example, <em>P</em><sub>9 </sub>= 2<sup>3 </sup><em>· </em>3<sup>2 </sup><em>· </em>5 <em>· </em>7.

More precisely, we’re going to compute all <em>P<sub>j</sub></em>, <em>j ∈ {</em>1<em>,··· ,n} </em>and store pairs of integers (<em>p<sup>α</sup>,p</em>) in a heap, a binary tree where the element stored in the parent node is <strong>strictly smaller </strong>than those stored in children nodes. For two given pairs of integers (<em>a,b</em>) and (<em>a<sup>0</sup>,b<sup>0</sup></em>), (<em>a,b</em>) <em>&lt; </em>(<em>a<sup>0</sup>,b<sup>0</sup></em>) if and only if <em>a &lt; a<sup>0</sup></em>. Let <em>h </em>denotes the tree height, we admit that <em>h </em>= Θ(log<em>n</em>). All levels of the binary tree are filled with data except for the level <em>h</em>, where elements are stored from the left to the right. After computing <em>P<sub>j</sub></em>, all pairs (<em>p<sup>α</sup>,p</em>) are stored in the heap such that <em>p </em>is a prime number smaller or equal to <em>j </em>and <em>α </em>is the <strong>smallest </strong>integer such that <strong>j </strong><em>&lt; </em><strong>p</strong><em><sup>α</sup></em>. For instance, after

computing <em>P</em><sub>9</sub>, we store (16<em>,</em>2), (27<em>,</em>3), (25<em>,</em>5), and (49<em>,</em>7) in the heap.

The algorithm is iterative. We store in the variable <strong>LCM </strong>the least common multiple computed so far. At first, <strong>LCM</strong>= 2 is the LCM of integers smaller than 2 and the heap is constructed with only one node with value (4<em>,</em>2). After finish the (<em>j −</em>1)-th step, we compute the <em>j</em>-th step as follows:

<ol>

 <li>If <em>j </em>is a prime number, multiply <strong>LCM </strong>by <em>j </em>and insert a new node (<em>j</em><sup>2</sup><em>,j</em>) in the heap.</li>

 <li>Otherwise, if the root (<em>p<sup>α</sup>,p</em>) satisfies <em>j </em>= <em>p<sup>α</sup></em>, then we multiply <strong>LCM </strong>by <em>p</em>, change the root’s value by (<em>p<sup>α</sup></em><sup>+1</sup><em>,p</em>), and reconstruct the heap.</li>

</ol>

<em>√</em>

We’re going to prove, step by step, that the time complexity of this algorithm is <em>O</em>(<em>n                                                                               n</em>).

<ul>

 <li><strong>– </strong></li>

</ul>

In operation 1, a new node is inserted. What is the complexity of this operation?

<ul>

 <li><strong>– </strong></li>

</ul>

In operation 2, the heap is reconstructed. What is the time complexity of this operation?

<h2>3.3 –</h2>

<em>√</em>

The number of prime numbers smaller than <em>n </em>concerned in the operation 2 is less than <em>n</em>. Prove that the number of times <em>N </em>we need to execute operation 2 to compute <em>P<sub>n </sub></em>is asymptotically negligible compared to <em>n</em>. Tip: you can prove this by proving N is <em>o</em>(<em>n</em>), where <em>o </em>(little o) denotes a strict upper bound.

<h2>3.4 –</h2>

<em>√</em>

Assume the complexity of assessing whether an integer is a prime number is     <em>n </em>and suppose

<em>√ </em>multiplication has a time complexity of 1. Prove that the algorithm’s complexity is <em>O</em>(<em>n n</em>).

<h2>3.5 –</h2>

Prove that, for a given heap of height <em>h </em>with <em>n </em>nodes, we have <em>h </em>= Θ(log<em>n</em>). No partial credit will be awarded.