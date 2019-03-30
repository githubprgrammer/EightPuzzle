# EightPuzzle
Solving the 8-puzzle problem first by using depth-first-search and then by using a heuristic function.

## Problem Description
The 8-puzzle is a sliding puzzle that consists of a frame of 8 numbered square tiles in random order with one tile missing. The object of the puzzle is to place the tiles in order by making sliding moves that use the empty space. 
For more information: https://en.wikipedia.org/wiki/15_puzzle

In our program, we do not care where the empty space ends. What matters is that the numbered tiles are sorted in ascending manner from left to right, top to bottom. It is important to note that this problem is not solvable for half of the possible initial configurations. So first we have to check if the puzzle is solveable. Therefore we check if the number of inversions in the initial puzzle is even. A pair of tiles form an inversion if the values on tiles are in reverse order of their appearance in goal state. For more information about the solvability of 8-puzzle see here: https://www.geeksforgeeks.org/check-instance-8-puzzle-solvable/

## Examples 

The following puzzle for example is unsolvable because it has 11 inversions:

![alt text](https://github.com/githubprgrammer/EightPuzzle/blob/master/unsolvable%20puzzle.PNG)

So if we try the following:

```
val puzzle_1 = List(Eight, One, Two, Empty, Four, Three, Seven, Six, Five)
heuristic(puzzle_1)
```

We get the following output: 

```
(Not solvable,List(),List(),0)
```
