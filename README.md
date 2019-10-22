# Catch-The-Cat-Game

### Description:
It's a simple puzzle based game made by me in C++.
- You can find the main game file in this Repository by the name **CATCH THE CAT GAME.cpp**.
- Run this code on any compiler and enjoy the simple puzzle.

### Solution of this puzzle:
Watch this video: https://www.youtube.com/watch?time_continue=5&v=yZyx9gHhRXM

#### Answer:

You might approach the puzzle by solving a simpler version: imagine the cat is hiding in one of 3 boxes in a row.

Imagine you check box 2 on day 1. If you do not find the cat, then you know the cat must have started in box 1 or 3. In that case, the cat must move to box 2 at night. So check box 2 on day 2 and you will find the cat for sure!

The key to the puzzle is you learn information after you open a box. If you choose wisely, you can eliminate boxes until you can deduce where the cat has to be.

The 5 box version is slightly more complicated as there are more possibilities. But the same kind of logic holds: the cat’s movements are limited. A cat in box 1 has to move to box 2 the next day; a cat in box 5 has to move to box 4 the next day. Furthermore, the box number the cat occupies alternates between even and odd numbers.

We first devise a strategy to catch a cat that starts in an even numbered box. Then we can apply that strategy again, which will catch a cat that started in an odd numbered box.

Here is a strategy that will work for sure. Inspect box 2, then box 3, then box 4. If you have not found the cat, then repeat: inspect 2, 3, then 4. You will certainly find the cat by the 6th time you check.

Why is that?

Let’s assume the cat starts in an even box, 2 or 4.

Day 1: you check box 2. If the cat is in 2, you find the cat. Otherwise, the cat must be in box 4.

Day 2: you check box 3. You will catch the cat if it moved from 4 to 3. But you will miss it if the cat moved from 4 to 5.

Day 3: you check box 4. As the cat was previously in 5, it must have moved to 4. So you will catch the cat.

The above strategy works if the cat started in an even numbered box. But the cat might have been in an odd numbered box 1, 3, or 5.

In that case, after 3 days of checking, you know the cat is now in an even numbered box. If the cat started in 1, 3, or 5, then on night 1 the cat would move to an even box (2 or 4); on night 2 the cat would move to an odd box (1, 3, or 5); and on night 3 the cat would move to an even box (2 or 4).

Thus, on the morning of day 4, you know the cat is in an even numbered box. So now you can repeat the strategy outlined above: check the boxes 2, 3, 4. You will find the cat for sure!

The strategy 2, 3, 4 is sure to catch a cat in an even box. An equivalent strategy is to check 4, then 3, then 2. This works for exactly the same reason due to the symmetry of the boxes in a line.

Both strategies 2, 3, 4 and 4, 3, 2 will catch a cat in an even box. And if either fails after 3 days, then you can repeat either strategy. Thus there are 4 equivalent ways to catch the cat:

2, 3, 4, 2, 3, 4
2, 3, 4, 4, 3, 2
4, 3, 2, 4, 3, 2
4, 3, 2, 2, 3, 4

It will be convenient to visualize the strategy 2, 3, 4, 4, 3, 2, so let us use that for the continuing discussion.

Furthermore, the idea of checking boxes from 2 to n – 1 and then checking the reverse will also work when n is an even number.

Another explanation: process of elimination

Here is another way to understand the strategy of checking 2, 3, 4, 4, 3, 2.

On day 1, you check box 2. If the cat is not in box 2, then there is no way the cat could be in box 1 the next day.

On day 2, you check box 3. You already know the cat is not in box 1 on this day, and if the cat is not in box 3, then there is no way for the cat to be in box 2 the next day.

On day 3, you check box 4. Since the cat is also not in box 2, there is no way it can move to either box 1 or box 3 the next day. Furthermore, if the cat is not in box 4, it also cannot move to box 5 the next day.

Therefore, you know the cat cannot be in box 1, 3, or 5 for the start of day 4. It must be in 2 or 4 to start day 4. In other words, you know the cat is in an even numbered box.

On day 4, you check box 4. If the cat is not there, then you know the cat must have been in box 2, and it can move to box 1 or 3.

On day 5, you check box 3. If the cat is not there, you know the cat must have moved to box 1 the night before, so now the cat has to move to box 2 the next day.

On day 6, you check box 2 and the cat has to be there.

Visualization

Here is a grid that shows the possible cat positions for each day.


You eventually eliminate possible positions for the cat until you find its location on the 6th day.

Solving for 4 boxes

Suppose cat starts in an even box (2 or 4).

First you check box 2. If the cat is there you win. If not, then you know the cat is in box 4 and it will move to box 3.

On day 2, you check box 3. You will catch the cat.

However, the cat might have started in box 1 or 3. After day 1, the cat would move to 2 or 4. After day 2, the cat would move to box 1 or 3. Now there is a twist: the cat is in an odd-numbered box. In order to catch it, you have to guess an odd number box.

So you cannot repeat checking box 2 then box 3. You have to check box 3 on day 3. If you catch the cat, you are done. Otherwise, you know the cat is in box 1 and it will move to box 2. So you check box 2 on day 4.

Thus, the strategy is 2, 3, 3, 2. Alternately you could have checked 3, 2, 2, 3.

In either case, you need to reverse the sequence on the second half of the search.

The key to the solution is that you need to guess an even box when the cat is in an even box. This will makes (your guess – cat box) an even number every single day–this means you never miss the cat bu just one box.

Equivalently, you need to guess an odd box when the cat is in an odd box. This makes (your guess – cat box) an even number every single day, so you again never miss the cat by just one box.

Generalization

The strategy can be generalized to any number of boxes.

Step 1: Check the boxes 2, 3, 4, …, n – 1 (the strategy surely finds a cat that started in an even numbered box on day 1).

Step 2: If that does not work, do search n – 1, n – 2, …, 4, 3, 2 (the strategy surely finds a cat that started in an odd numbered box on day 1).

You can also reverse steps 1 and 2 to find the cat.

And if n is odd, you can also perform the search in step 1 twice, or the search in step 2 twice, to find the cat.

/*Source: https://mindyourdecisions.com/blog/2017/07/09/can-you-solve-the-hiding-cat-puzzle-tech-interview-question/
Credits: __Presh Talwalkar__*/
