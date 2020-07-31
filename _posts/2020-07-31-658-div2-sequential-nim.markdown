---
layout: post
title:  "Codeforces 658-Div2-B Sequential Nim"
date:   2020-07-31 21:03:36 +0530
---
Here is my explanation for Codeforces Round 658 Div2-B-Sequential Nim.

The problem statement: [problem][ques]

So there are a bunch of ways the stones can be put into heaps. It is clear from the beginning that the person whose turn it is should take either all the stones of a heap or all stones except 1 from the heap (the obvious exception is if the heap has only one stone, something I will address later in the post.)

Any given state of piles is either losing or winning. 

Let us take an example of the following state of piles given as the problem: 
  	
```
3 4 1 2 5...
```
	
Now, let’s talk about the state of piles except the first one:
	
```
4 1 2 5...
```
	
If this state is losing, First wants this to be the state of piles at Second’s turn, so he takes all the three stones from the first pile, ensuring that he wins.

Now, assume this state is winning. Now, First wants it to be the state of piles at his turn. So he takes 2 stones from the original pile, thereby forcing Second to take the leftover 1 stone, making sure he gets the winning pile.
	
```
1 4 1 2 5…
0 4 1 2 5…
```
	
So the person whose turn it is at the original state is the winner.

One exception case occurs when the first or first few heaps all have 1 stone in them like:

```
1 1 1 2 3 1…
```
	
Now, this can be reduced to the following state, removing all starting piles with 1 stone :
	
```
2 3 1…
```
	
Again, it becomes like the original case, the person whose turn it is at this state wins. This can be found out easily by counting the number of leading 1-stone heaps. 

If all the heaps have only one stone, finding the loser is pretty straight forward, by finding whose turn it was at the end position.

This is my first blog, any suggestion or feedback is welcome. Send a [mail][email]!

[ques]: https://codeforces.com/contest/1382/problem/B
[email]: shirin.kaul11@gmail.com
