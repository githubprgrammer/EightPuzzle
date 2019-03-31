# EightPuzzle
Solving the 8-puzzle problem first by using **depth-first-search** and then by using a **heuristic function with Manhattan Distance**.

## Problem Description
The 8-puzzle is a sliding puzzle that consists of a frame of 8 numbered square tiles in random order with one tile missing. The object of the puzzle is to place the tiles in order by making sliding moves that use the empty space. 
For more information: https://en.wikipedia.org/wiki/15_puzzle

In our program, we do not care where the empty space ends. What matters is that the numbered tiles are sorted in ascending manner from left to right, top to bottom. It is important to note that this problem is not solvable for half of the possible initial configurations. So first we have to check if the puzzle is solveable. Therefore we check if the number of inversions in the initial puzzle is even. A pair of tiles form an inversion if the values on tiles are in reverse order of their appearance in goal state. For more information about the solvability of 8-puzzle see here: https://www.geeksforgeeks.org/check-instance-8-puzzle-solvable/

## Examples 

### Solvable Puzzle
Let's try to find a solution for this puzzle:

![alt text](https://github.com/githubprgrammer/EightPuzzle/blob/master/Solvable%20puzzle.PNG)

This one is solvable because it has with its two inversions (7,6) and (8,6) an even number of inversions.

Let's **compare the performance** of the depth-first-search and our heuristic algorithm:

```
val puzzle_1 = List(One, Two, Three, Four, Five, Empty,  Seven, Eight, Six)
depthfirstsearch(puzzle_1)
heuristic(puzzle_1)
```


For the DFS algorithm we get the output:
```
(Solution found:,List(One, Two, Three, Four, Five, Six, Empty, Seven, Eight),List(List(One, Two, Three, Four, Five, Empty, Seven, Eight, Six), List(One, Two, Empty, Four, Five, Three, Seven, Eight, Six), List(One, Empty, Two, Four, Five, Three, Seven, Eight, Six), List(One, Five, Two, Four, Empty, Three, Seven, Eight, Six), List(One, Five, Two, Four, Eight, Three, Seven, Empty, Six), List(One, Five, Two, Four, Eight, Three, Empty, Seven, Six), List(One, Five, Two, Empty, Eight, Three, Four, Seven, Six), List(Empty, Five, Two, One, Eight, Three, Four, Seven, Six), List(Five, Empty, Two, One, Eight, Three, Four, Seven, Six), List(Five, Eight, Two, One, Empty, Three, Four, Seven, Six), List(Five, Eight, Two, One, Seven, Three, Four, Empty, Six), List(Five, Eight, Two, One, Seven, Three, Empty, Four, Six), List(Five, Eight, Two, Empty, Seven, Three, One, Four, Six), List(Empty, Eight, Two, Five, Seven, Three, One, Four, Six), List(Eight, Empty, Two, Five, Seven, Three, One, Four, Six), List(Eight, Seven, Two, Five, Empty, Three, One, Four, Six), List(Eight, Seven, Two, Five, Four, Three, One, Empty, Six), List(Eight, Seven, Two, Five, Four, Three, Empty, One, Six), List(Eight, Seven, Two, Empty, Four, Three, Five, One, Six), List(Empty, Seven, Two, Eight, Four, Three, Five, One, Six), List(Seven, Empty, Two, Eight, Four, Three, Five, One, Six), List(Seven, Four, Two, Eight, Empty, Three, Five, One, Six), List(Seven, Four, Two, Eight, One, Three, Five, Empty, Six), List(Seven, Four, Two, Eight, One, Three, Empty, Five, Six), List(Seven, Four, Two, Empty, One, Three, Eight, Five, Six), List(Empty, Four, Two, Seven, One, Three, Eight, Five, Six), List(Four, Empty, Two, Seven, One, Three, Eight, Five, Six), List(Four, One, Two, Seven, Empty, Three, Eight, Five, Six), List(Four, One, Two, Seven, Five, Three, Eight, Empty, Six), List(Four, One, Two, Seven, Five, Three, Empty, Eight, Six), List(Four, One, Two, Empty, Five, Three, Seven, Eight, Six), List(Empty, One, Two, Four, Five, Three, Seven, Eight, Six), List(Four, One, Two, Five, Empty, Three, Seven, Eight, Six), List(Four, Empty, Two, Five, One, Three, Seven, Eight, Six), List(Empty, Four, Two, Five, One, Three, Seven, Eight, Six), List(Five, Four, Two, Empty, One, Three, Seven, Eight, Six), List(Five, Four, Two, Seven, One, Three, Empty, Eight, Six), List(Five, Four, Two, Seven, One, Three, Eight, Empty, Six), List(Five, Four, Two, Seven, Empty, Three, Eight, One, Six), List(Five, Empty, Two, Seven, Four, Three, Eight, One, Six), List(Empty, Five, Two, Seven, Four, Three, Eight, One, Six), List(Seven, Five, Two, Empty, Four, Three, Eight, One, Six), List(Seven, Five, Two, Eight, Four, Three, Empty, One, Six), List(Seven, Five, Two, Eight, Four, Three, One, Empty, Six), List(Seven, Five, Two, Eight, Empty, Three, One, Four, Six), List(Seven, Empty, Two, Eight, Five, Three, One, Four, Six), List(Empty, Seven, Two, Eight, Five, Three, One, Four, Six), List(Eight, Seven, Two, Empty, Five, Three, One, Four, Six), List(Eight, Seven, Two, One, Five, Three, Empty, Four, Six), List(Eight, Seven, Two, One, Five, Three, Four, Empty, Six), List(Eight, Seven, Two, One, Empty, Three, Four, Five, Six), List(Eight, Empty, Two, One, Seven, Three, Four, Five, Six), List(Empty, Eight, Two, One, Seven, Three, Four, Five, Six), List(One, Eight, Two, Empty, Seven, Three, Four, Five, Six), List(One, Eight, Two, Four, Seven, Three, Empty, Five, Six), List(One, Eight, Two, Four, Seven, Three, Five, Empty, Six), List(One, Eight, Two, Four, Empty, Three, Five, Seven, Six), List(One, Empty, Two, Four, Eight, Three, Five, Seven, Six), List(Empty, One, Two, Four, Eight, Three, Five, Seven, Six), List(Four, One, Two, Empty, Eight, Three, Five, Seven, Six), List(Four, One, Two, Five, Eight, Three, Empty, Seven, Six), List(Four, One, Two, Five, Eight, Three, Seven, Empty, Six), List(Four, One, Two, Five, Eight, Three, Seven, Six, Empty), List(Four, One, Two, Five, Eight, Empty, Seven, Six, Three), List(Four, One, Empty, Five, Eight, Two, Seven, Six, Three), List(Four, Empty, One, Five, Eight, Two, Seven, Six, Three), List(Four, Eight, One, Five, Empty, Two, Seven, Six, Three), List(Four, Eight, One, Five, Six, Two, Seven, Empty, Three), List(Four, Eight, One, Five, Six, Two, Empty, Seven, Three), List(Four, Eight, One, Empty, Six, Two, Five, Seven, Three), List(Empty, Eight, One, Four, Six, Two, Five, Seven, Three), List(Eight, Empty, One, Four, Six, Two, Five, Seven, Three), List(Eight, Six, One, Four, Empty, Two, Five, Seven, Three), List(Eight, Six, One, Four, Seven, Two, Five, Empty, Three), List(Eight, Six, One, Four, Seven, Two, Empty, Five, Three), List(Eight, Six, One, Empty, Seven, Two, Four, Five, Three), List(Empty, Six, One, Eight, Seven, Two, Four, Five, Three), List(Six, Empty, One, Eight, Seven, Two, Four, Five, Three), List(Six, Seven, One, Eight, Empty, Two, Four, Five, Three), List(Six, Seven, One, Eight, Five, Two, Four, Empty, Three), List(Six, Seven, One, Eight, Five, Two, Empty, Four, Three), List(Six, Seven, One, Empty, Five, Two, Eight, Four, Three), List(Empty, Seven, One, Six, Five, Two, Eight, Four, Three), List(Seven, Empty, One, Six, Five, Two, Eight, Four, Three), List(Seven, Five, One, Six, Empty, Two, Eight, Four, Three), List(Seven, Five, One, Six, Four, Two, Eight, Empty, Three), List(Seven, Five, One, Six, Four, Two, Empty, Eight, Three), List(Seven, Five, One, Empty, Four, Two, Six, Eight, Three), List(Empty, Five, One, Seven, Four, Two, Six, Eight, Three), List(Five, Empty, One, Seven, Four, Two, Six, Eight, Three), List(Five, Four, One, Seven, Empty, Two, Six, Eight, Three), List(Five, Four, One, Seven, Eight, Two, Six, Empty, Three), List(Five, Four, One, Seven, Eight, Two, Empty, Six, Three), List(Five, Four, One, Empty, Eight, Two, Seven, Six, Three), List(Empty, Four, One, Five, Eight, Two, Seven, Six, Three), List(Five, Four, One, Eight, Empty, Two, Seven, Six, Three), List(Five, Empty, One, Eight, Four, Two, Seven, Six, Three), List(Empty, Five, One, Eight, Four, Two, Seven, Six, Three), List(Eight, Five, One, Empty, Four, Two, Seven, Six, Three), List(Eight, Five, One, Seven, Four, Two, Empty, Six, Three), List(Eight, Five, One, Seven, Four, Two, Six, Empty, Three), List(Eight, Five, One, Seven, Empty, Two, Six, Four, Three), List(Eight, Empty, One, Seven, Five, Two, Six, Four, Three), List(Empty, Eight, One, Seven, Five, Two, Six, Four, Three), List(Seven, Eight, One, Empty, Five, Two, Six, Four, Three), List(Seven, Eight, One, Six, Five, Two, Empty, Four, Three), List(Seven, Eight, One, Six, Five, Two, Four, Empty, Three), List(Seven, Eight, One, Six, Empty, Two, Four, Five, Three), List(Seven, Empty, One, Six, Eight, Two, Four, Five, Three), List(Empty, Seven, One, Six, Eight, Two, Four, Five, Three), List(Six, Seven, One, Empty, Eight, Two, Four, Five, Three), List(Six, Seven, One, Four, Eight, Two, Empty, Five, Three), List(Six, Seven, One, Four, Eight, Two, Five, Empty, Three), List(Six, Seven, One, Four, Empty, Two, Five, Eight, Three), List(Six, Empty, One, Four, Seven, Two, Five, Eight, Three), List(Empty, Six, One, Four, Seven, Two, Five, Eight, Three), List(Four, Six, One, Empty, Seven, Two, Five, Eight, Three), List(Four, Six, One, Five, Seven, Two, Empty, Eight, Three), List(Four, Six, One, Five, Seven, Two, Eight, Empty, Three), List(Four, Six, One, Five, Empty, Two, Eight, Seven, Three), List(Four, Empty, One, Five, Six, Two, Eight, Seven, Three), List(Empty, Four, One, Five, Six, Two, Eight, Seven, Three), List(Five, Four, One, Empty, Six, Two, Eight, Seven, Three), List(Five, Four, One, Eight, Six, Two, Empty, Seven, Three), List(Five, Four, One, Eight, Six, Two, Seven, Empty, Three), List(Five, Four, One, Eight, Six, Two, Seven, Three, Empty), List(Five, Four, One, Eight, Six, Empty, Seven, Three, Two), List(Five, Four, Empty, Eight, Six, One, Seven, Three, Two), List(Five, Empty, Four, Eight, Six, One, Seven, Three, Two), List(Five, Six, Four, Eight, Empty, One, Seven, Three, Two), List(Five, Six, Four, Eight, Three, One, Seven, Empty, Two), List(Five, Six, Four, Eight, Three, One, Empty, Seven, Two), List(Five, Six, Four, Empty, Three, One, Eight, Seven, Two), List(Empty, Six, Four, Five, Three, One, Eight, Seven, Two), List(Six, Empty, Four, Five, Three, One, Eight, Seven, Two), List(Six, Three, Four, Five, Empty, One, Eight, Seven, Two), List(Six, Three, Four, Five, Seven, One, Eight, Empty, Two), List(Six, Three, Four, Five, Seven, One, Empty, Eight, Two), List(Six, Three, Four, Empty, Seven, One, Five, Eight, Two), List(Empty, Three, Four, Six, Seven, One, Five, Eight, Two), List(Three, Empty, Four, Six, Seven, One, Five, Eight, Two), List(Three, Seven, Four, Six, Empty, One, Five, Eight, Two), List(Three, Seven, Four, Six, Eight, One, Five, Empty, Two), List(Three, Seven, Four, Six, Eight, One, Empty, Five, Two), List(Three, Seven, Four, Empty, Eight, One, Six, Five, Two), List(Empty, Seven, Four, Three, Eight, One, Six, Five, Two), List(Seven, Empty, Four, Three, Eight, One, Six, Five, Two), List(Seven, Eight, Four, Three, Empty, One, Six, Five, Two), List(Seven, Eight, Four, Three, Five, One, Six, Empty, Two), List(Seven, Eight, Four, Three, Five, One, Empty, Six, Two), List(Seven, Eight, Four, Empty, Five, One, Three, Six, Two), List(Empty, Eight, Four, Seven, Five, One, Three, Six, Two), List(Eight, Empty, Four, Seven, Five, One, Three, Six, Two), List(Eight, Five, Four, Seven, Empty, One, Three, Six, Two), List(Eight, Five, Four, Seven, Six, One, Three, Empty, Two), List(Eight, Five, Four, Seven, Six, One, Empty, Three, Two), List(Eight, Five, Four, Empty, Six, One, Seven, Three, Two), List(Empty, Five, Four, Eight, Six, One, Seven, Three, Two), List(Eight, Five, Four, Six, Empty, One, Seven, Three, Two), List(Eight, Empty, Four, Six, Five, One, Seven, Three, Two), List(Empty, Eight, Four, Six, Five, One, Seven, Three, Two), List(Six, Eight, Four, Empty, Five, One, Seven, Three, Two), List(Six, Eight, Four, Seven, Five, One, Empty, Three, Two), List(Six, Eight, Four, Seven, Five, One, Three, Empty, Two), List(Six, Eight, Four, Seven, Empty, One, Three, Five, Two), List(Six, Empty, Four, Seven, Eight, One, Three, Five, Two), List(Empty, Six, Four, Seven, Eight, One, Three, Five, Two), List(Seven, Six, Four, Empty, Eight, One, Three, Five, Two), List(Seven, Six, Four, Three, Eight, One, Empty, Five, Two), List(Seven, Six, Four, Three, Eight, One, Five, Empty, Two), List(Seven, Six, Four, Three, Empty, One, Five, Eight, Two), List(Seven, Empty, Four, Three, Six, One, Five, Eight, Two), List(Empty, Seven, Four, Three, Six, One, Five, Eight, Two), List(Three, Seven, Four, Empty, Six, One, Five, Eight, Two), List(Three, Seven, Four, Five, Six, One, Empty, Eight, Two), List(Three, Seven, Four, Five, Six, One, Eight, Empty, Two), List(Three, Seven, Four, Five, Empty, One, Eight, Six, Two), List(Three, Empty, Four, Five, Seven, One, Eight, Six, Two), List(Empty, Three, Four, Five, Seven, One, Eight, Six, Two), List(Five, Three, Four, Empty, Seven, One, Eight, Six, Two), List(Five, Three, Four, Eight, Seven, One, Empty, Six, Two), List(Five, Three, Four, Eight, Seven, One, Six, Empty, Two), List(Five, Three, Four, Eight, Empty, One, Six, Seven, Two), List(Five, Empty, Four, Eight, Three, One, Six, Seven, Two), List(Empty, Five, Four, Eight, Three, One, Six, Seven, Two), List(Eight, Five, Four, Empty, Three, One, Six, Seven, Two), List(Eight, Five, Four, Six, Three, One, Empty, Seven, Two), List(Eight, Five, Four, Six, Three, One, Seven, Empty, Two), List(Eight, Five, Four, Six, Three, One, Seven, Two, Empty), List(Eight, Five, Four, Six, Three, Empty, Seven, Two, One), List(Eight, Five, Empty, Six, Three, Four, Seven, Two, One), List(Eight, Empty, Five, Six, Three, Four, Seven, Two, One), List(Eight, Three, Five, Six, Empty, Four, Seven, Two, One), List(Eight, Three, Five, Six, Two, Four, Seven, Empty, One), List(Eight, Three, Five, Six, Two, Four, Empty, Seven, One), List(Eight, Three, Five, Empty, Two, Four, Six, Seven, One), List(Empty, Three, Five, Eight, Two, Four, Six, Seven, One), List(Three, Empty, Five, Eight, Two, Four, Six, Seven, One), List(Three, Two, Five, Eight, Empty, Four, Six, Seven, One), List(Three, Two, Five, Eight, Seven, Four, Six, Empty, One), List(Three, Two, Five, Eight, Seven, Four, Empty, Six, One), List(Three, Two, Five, Empty, Seven, Four, Eight, Six, One), List(Empty, Two, Five, Three, Seven, Four, Eight, Six, One), List(Two, Empty, Five, Three, Seven, Four, Eight, Six, One), List(Two, Seven, Five, Three, Empty, Four, Eight, Six, One), List(Two, Seven, Five, Three, Six, Four, Eight, Empty, One), List(Two, Seven, Five, Three, Six, Four, Empty, Eight, One), List(Two, Seven, Five, Empty, Six, Four, Three, Eight, One), List(Empty, Seven, Five, Two, Six, Four, Three, Eight, One), List(Seven, Empty, Five, Two, Six, Four, Three, Eight, One), List(Seven, Six, Five, Two, Empty, Four, Three, Eight, One), List(Seven, Six, Five, Two, Eight, Four, Three, Empty, One), List(Seven, Six, Five, Two, Eight, Four, Empty, Three, One), List(Seven, Six, Five, Empty, Eight, Four, Two, Three, One), List(Empty, Six, Five, Seven, Eight, Four, Two, Three, One), List(Six, Empty, Five, Seven, Eight, Four, Two, Three, One), List(Six, Eight, Five, Seven, Empty, Four, Two, Three, One), List(Six, Eight, Five, Seven, Three, Four, Two, Empty, One), List(Six, Eight, Five, Seven, Three, Four, Empty, Two, One), List(Six, Eight, Five, Empty, Three, Four, Seven, Two, One), List(Empty, Eight, Five, Six, Three, Four, Seven, Two, One), List(Six, Eight, Five, Three, Empty, Four, Seven, Two, One), List(Six, Empty, Five, Three, Eight, Four, Seven, Two, One), List(Empty, Six, Five, Three, Eight, Four, Seven, Two, One), List(Three, Six, Five, Empty, Eight, Four, Seven, Two, One), List(Three, Six, Five, Seven, Eight, Four, Empty, Two, One), List(Three, Six, Five, Seven, Eight, Four, Two, Empty, One), List(Three, Six, Five, Seven, Empty, Four, Two, Eight, One), List(Three, Empty, Five, Seven, Six, Four, Two, Eight, One), List(Empty, Three, Five, Seven, Six, Four, Two, Eight, One), List(Seven, Three, Five, Empty, Six, Four, Two, Eight, One), List(Seven, Three, Five, Two, Six, Four, Empty, Eight, One), List(Seven, Three, Five, Two, Six, Four, Eight, Empty, One), List(Seven, Three, Five, Two, Empty, Four, Eight, Six, One), List(Seven, Empty, Five, Two, Three, Four, Eight, Six, One), List(Empty, Seven, Five, Two, Three, Four, Eight, Six, One), List(Two, Seven, Five, Empty, Three, Four, Eight, Six, One), List(Two, Seven, Five, Eight, Three, Four, Empty, Six, One), List(Two, Seven, Five, Eight, Three, Four, Six, Empty, One), List(Two, Seven, Five, Eight, Empty, Four, Six, Three, One), List(Two, Empty, Five, Eight, Seven, Four, Six, Three, One), List(Empty, Two, Five, Eight, Seven, Four, Six, Three, One), List(Eight, Two, Five, Empty, Seven, Four, Six, Three, One), List(Eight, Two, Five, Six, Seven, Four, Empty, Three, One), List(Eight, Two, Five, Six, Seven, Four, Three, Empty, One), List(Eight, Two, Five, Six, Empty, Four, Three, Seven, One), List(Eight, Empty, Five, Six, Two, Four, Three, Seven, One), List(Empty, Eight, Five, Six, Two, Four, Three, Seven, One), List(Six, Eight, Five, Empty, Two, Four, Three, Seven, One), List(Six, Eight, Five, Three, Two, Four, Empty, Seven, One), List(Six, Eight, Five, Three, Two, Four, Seven, Empty, One), List(Six, Eight, Five, Three, Two, Four, Seven, One, Empty), List(Six, Eight, Five, Three, Two, Empty, Seven, One, Four), List(Six, Eight, Empty, Three, Two, Five, Seven, One, Four), List(Six, Empty, Eight, Three, Two, Five, Seven, One, Four), List(Six, Two, Eight, Three, Empty, Five, Seven, One, Four), List(Six, Two, Eight, Three, One, Five, Seven, Empty, Four), List(Six, Two, Eight, Three, One, Five, Empty, Seven, Four), List(Six, Two, Eight, Empty, One, Five, Three, Seven, Four), List(Empty, Two, Eight, Six, One, Five, Three, Seven, Four), List(Two, Empty, Eight, Six, One, Five, Three, Seven, Four), List(Two, One, Eight, Six, Empty, Five, Three, Seven, Four), List(Two, One, Eight, Six, Seven, Five, Three, Empty, Four), List(Two, One, Eight, Six, Seven, Five, Empty, Three, Four), List(Two, One, Eight, Empty, Seven, Five, Six, Three, Four), List(Empty, One, Eight, Two, Seven, Five, Six, Three, Four), List(One, Empty, Eight, Two, Seven, Five, Six, Three, Four), List(One, Seven, Eight, Two, Empty, Five, Six, Three, Four), List(One, Seven, Eight, Two, Three, Five, Six, Empty, Four), List(One, Seven, Eight, Two, Three, Five, Empty, Six, Four), List(One, Seven, Eight, Empty, Three, Five, Two, Six, Four), List(Empty, Seven, Eight, One, Three, Five, Two, Six, Four), List(Seven, Empty, Eight, One, Three, Five, Two, Six, Four), List(Seven, Three, Eight, One, Empty, Five, Two, Six, Four), List(Seven, Three, Eight, One, Six, Five, Two, Empty, Four), List(Seven, Three, Eight, One, Six, Five, Empty, Two, Four), List(Seven, Three, Eight, Empty, Six, Five, One, Two, Four), List(Empty, Three, Eight, Seven, Six, Five, One, Two, Four), List(Three, Empty, Eight, Seven, Six, Five, One, Two, Four), List(Three, Six, Eight, Seven, Empty, Five, One, Two, Four), List(Three, Six, Eight, Seven, Two, Five, One, Empty, Four), List(Three, Six, Eight, Seven, Two, Five, Empty, One, Four), List(Three, Six, Eight, Empty, Two, Five, Seven, One, Four), List(Empty, Six, Eight, Three, Two, Five, Seven, One, Four), List(Three, Six, Eight, Two, Empty, Five, Seven, One, Four), List(Three, Empty, Eight, Two, Six, Five, Seven, One, Four), List(Empty, Three, Eight, Two, Six, Five, Seven, One, Four), List(Two, Three, Eight, Empty, Six, Five, Seven, One, Four), List(Two, Three, Eight, Seven, Six, Five, Empty, One, Four), List(Two, Three, Eight, Seven, Six, Five, One, Empty, Four), List(Two, Three, Eight, Seven, Empty, Five, One, Six, Four), List(Two, Empty, Eight, Seven, Three, Five, One, Six, Four), List(Empty, Two, Eight, Seven, Three, Five, One, Six, Four), List(Seven, Two, Eight, Empty, Three, Five, One, Six, Four), List(Seven, Two, Eight, One, Three, Five, Empty, Six, Four), List(Seven, Two, Eight, One, Three, Five, Six, Empty, Four), List(Seven, Two, Eight, One, Empty, Five, Six, Three, Four), List(Seven, Empty, Eight, One, Two, Five, Six, Three, Four), List(Empty, Seven, Eight, One, Two, Five, Six, Three, Four), List(One, Seven, Eight, Empty, Two, Five, Six, Three, Four), List(One, Seven, Eight, Six, Two, Five, Empty, Three, Four), List(One, Seven, Eight, Six, Two, Five, Three, Empty, Four), List(One, Seven, Eight, Six, Empty, Five, Three, Two, Four), List(One, Empty, Eight, Six, Seven, Five, Three, Two, Four), List(Empty, One, Eight, Six, Seven, Five, Three, Two, Four), List(Six, One, Eight, Empty, Seven, Five, Three, Two, Four), List(Six, One, Eight, Three, Seven, Five, Empty, Two, Four), List(Six, One, Eight, Three, Seven, Five, Two, Empty, Four), List(Six, One, Eight, Three, Empty, Five, Two, Seven, Four), List(Six, Empty, Eight, Three, One, Five, Two, Seven, Four), List(Empty, Six, Eight, Three, One, Five, Two, Seven, Four), List(Three, Six, Eight, Empty, One, Five, Two, Seven, Four), List(Three, Six, Eight, Two, One, Five, Empty, Seven, Four), List(Three, Six, Eight, Two, One, Five, Seven, Empty, Four), List(Three, Six, Eight, Two, One, Five, Seven, Four, Empty), List(Three, Six, Eight, Two, One, Empty, Seven, Four, Five), List(Three, Six, Empty, Two, One, Eight, Seven, Four, Five), List(Three, Empty, Six, Two, One, Eight, Seven, Four, Five), List(Three, One, Six, Two, Empty, Eight, Seven, Four, Five), List(Three, One, Six, Two, Four, Eight, Seven, Empty, Five), List(Three, One, Six, Two, Four, Eight, Empty, Seven, Five), List(Three, One, Six, Empty, Four, Eight, Two, Seven, Five), List(Empty, One, Six, Three, Four, Eight, Two, Seven, Five), List(One, Empty, Six, Three, Four, Eight, Two, Seven, Five), List(One, Four, Six, Three, Empty, Eight, Two, Seven, Five), List(One, Four, Six, Three, Seven, Eight, Two, Empty, Five), List(One, Four, Six, Three, Seven, Eight, Empty, Two, Five), List(One, Four, Six, Empty, Seven, Eight, Three, Two, Five), List(Empty, Four, Six, One, Seven, Eight, Three, Two, Five), List(Four, Empty, Six, One, Seven, Eight, Three, Two, Five), List(Four, Seven, Six, One, Empty, Eight, Three, Two, Five), List(Four, Seven, Six, One, Two, Eight, Three, Empty, Five), List(Four, Seven, Six, One, Two, Eight, Empty, Three, Five), List(Four, Seven, Six, Empty, Two, Eight, One, Three, Five), List(Empty, Seven, Six, Four, Two, Eight, One, Three, Five), List(Seven, Empty, Six, Four, Two, Eight, One, Three, Five), List(Seven, Two, Six, Four, Empty, Eight, One, Three, Five), List(Seven, Two, Six, Four, Three, Eight, One, Empty, Five), List(Seven, Two, Six, Four, Three, Eight, Empty, One, Five), List(Seven, Two, Six, Empty, Three, Eight, Four, One, Five), List(Empty, Two, Six, Seven, Three, Eight, Four, One, Five), List(Two, Empty, Six, Seven, Three, Eight, Four, One, Five), List(Two, Three, Six, Seven, Empty, Eight, Four, One, Five), List(Two, Three, Six, Seven, One, Eight, Four, Empty, Five), List(Two, Three, Six, Seven, One, Eight, Empty, Four, Five), List(Two, Three, Six, Empty, One, Eight, Seven, Four, Five), List(Empty, Three, Six, Two, One, Eight, Seven, Four, Five), List(Two, Three, Six, One, Empty, Eight, Seven, Four, Five), List(Two, Empty, Six, One, Three, Eight, Seven, Four, Five), List(Empty, Two, Six, One, Three, Eight, Seven, Four, Five), List(One, Two, Six, Empty, Three, Eight, Seven, Four, Five), List(One, Two, Six, Seven, Three, Eight, Empty, Four, Five), List(One, Two, Six, Seven, Three, Eight, Four, Empty, Five), List(One, Two, Six, Seven, Empty, Eight, Four, Three, Five), List(One, Empty, Six, Seven, Two, Eight, Four, Three, Five), List(Empty, One, Six, Seven, Two, Eight, Four, Three, Five), List(Seven, One, Six, Empty, Two, Eight, Four, Three, Five), List(Seven, One, Six, Four, Two, Eight, Empty, Three, Five), List(Seven, One, Six, Four, Two, Eight, Three, Empty, Five), List(Seven, One, Six, Four, Empty, Eight, Three, Two, Five), List(Seven, Empty, Six, Four, One, Eight, Three, Two, Five), List(Empty, Seven, Six, Four, One, Eight, Three, Two, Five), List(Four, Seven, Six, Empty, One, Eight, Three, Two, Five), List(Four, Seven, Six, Three, One, Eight, Empty, Two, Five), List(Four, Seven, Six, Three, One, Eight, Two, Empty, Five), List(Four, Seven, Six, Three, Empty, Eight, Two, One, Five), List(Four, Empty, Six, Three, Seven, Eight, Two, One, Five), List(Empty, Four, Six, Three, Seven, Eight, Two, One, Five), List(Three, Four, Six, Empty, Seven, Eight, Two, One, Five), List(Three, Four, Six, Two, Seven, Eight, Empty, One, Five), List(Three, Four, Six, Two, Seven, Eight, One, Empty, Five), List(Three, Four, Six, Two, Empty, Eight, One, Seven, Five), List(Three, Empty, Six, Two, Four, Eight, One, Seven, Five), List(Empty, Three, Six, Two, Four, Eight, One, Seven, Five), List(Two, Three, Six, Empty, Four, Eight, One, Seven, Five), List(Two, Three, Six, One, Four, Eight, Empty, Seven, Five), List(Two, Three, Six, One, Four, Eight, Seven, Empty, Five), List(Two, Three, Six, One, Four, Eight, Seven, Five, Empty), List(Two, Three, Six, One, Four, Empty, Seven, Five, Eight), List(Two, Three, Empty, One, Four, Six, Seven, Five, Eight), List(Two, Empty, Three, One, Four, Six, Seven, Five, Eight), List(Two, Four, Three, One, Empty, Six, Seven, Five, Eight), List(Two, Four, Three, One, Five, Six, Seven, Empty, Eight), List(Two, Four, Three, One, Five, Six, Empty, Seven, Eight), List(Two, Four, Three, Empty, Five, Six, One, Seven, Eight), List(Empty, Four, Three, Two, Five, Six, One, Seven, Eight), List(Four, Empty, Three, Two, Five, Six, One, Seven, Eight), List(Four, Five, Three, Two, Empty, Six, One, Seven, Eight), List(Four, Five, Three, Two, Seven, Six, One, Empty, Eight), List(Four, Five, Three, Two, Seven, Six, Empty, One, Eight), List(Four, Five, Three, Empty, Seven, Six, Two, One, Eight), List(Empty, Five, Three, Four, Seven, Six, Two, One, Eight), List(Five, Empty, Three, Four, Seven, Six, Two, One, Eight), List(Five, Seven, Three, Four, Empty, Six, Two, One, Eight), List(Five, Seven, Three, Four, One, Six, Two, Empty, Eight), List(Five, Seven, Three, Four, One, Six, Empty, Two, Eight), List(Five, Seven, Three, Empty, One, Six, Four, Two, Eight), List(Empty, Seven, Three, Five, One, Six, Four, Two, Eight), List(Seven, Empty, Three, Five, One, Six, Four, Two, Eight), List(Seven, One, Three, Five, Empty, Six, Four, Two, Eight), List(Seven, One, Three, Five, Two, Six, Four, Empty, Eight), List(Seven, One, Three, Five, Two, Six, Empty, Four, Eight), List(Seven, One, Three, Empty, Two, Six, Five, Four, Eight), List(Empty, One, Three, Seven, Two, Six, Five, Four, Eight), List(One, Empty, Three, Seven, Two, Six, Five, Four, Eight), List(One, Two, Three, Seven, Empty, Six, Five, Four, Eight), List(One, Two, Three, Seven, Four, Six, Five, Empty, Eight), List(One, Two, Three, Seven, Four, Six, Empty, Five, Eight), List(One, Two, Three, Empty, Four, Six, Seven, Five, Eight), List(Empty, Two, Three, One, Four, Six, Seven, Five, Eight), List(One, Two, Three, Four, Empty, Six, Seven, Five, Eight), List(One, Empty, Three, Four, Two, Six, Seven, Five, Eight), List(Empty, One, Three, Four, Two, Six, Seven, Five, Eight), List(Four, One, Three, Empty, Two, Six, Seven, Five, Eight), List(Four, One, Three, Seven, Two, Six, Empty, Five, Eight), List(Four, One, Three, Seven, Two, Six, Five, Empty, Eight), List(Four, One, Three, Seven, Empty, Six, Five, Two, Eight), List(Four, Empty, Three, Seven, One, Six, Five, Two, Eight), List(Empty, Four, Three, Seven, One, Six, Five, Two, Eight), List(Seven, Four, Three, Empty, One, Six, Five, Two, Eight), List(Seven, Four, Three, Five, One, Six, Empty, Two, Eight), List(Seven, Four, Three, Five, One, Six, Two, Empty, Eight), List(Seven, Four, Three, Five, Empty, Six, Two, One, Eight), List(Seven, Empty, Three, Five, Four, Six, Two, One, Eight), List(Empty, Seven, Three, Five, Four, Six, Two, One, Eight), List(Five, Seven, Three, Empty, Four, Six, Two, One, Eight), List(Five, Seven, Three, Two, Four, Six, Empty, One, Eight), List(Five, Seven, Three, Two, Four, Six, One, Empty, Eight), List(Five, Seven, Three, Two, Empty, Six, One, Four, Eight), List(Five, Empty, Three, Two, Seven, Six, One, Four, Eight), List(Empty, Five, Three, Two, Seven, Six, One, Four, Eight), List(Two, Five, Three, Empty, Seven, Six, One, Four, Eight), List(Two, Five, Three, One, Seven, Six, Empty, Four, Eight), List(Two, Five, Three, One, Seven, Six, Four, Empty, Eight), List(Two, Five, Three, One, Empty, Six, Four, Seven, Eight), List(Two, Empty, Three, One, Five, Six, Four, Seven, Eight), List(Empty, Two, Three, One, Five, Six, Four, Seven, Eight), List(One, Two, Three, Empty, Five, Six, Four, Seven, Eight), List(One, Two, Three, Four, Five, Six, Empty, Seven, Eight)),439)
```

And for the **heuristic search algorithm using Mahattan-Distance**:

```
(Solution found:,List(One, Two, Three, Four, Five, Six, Seven, Eight, Empty),List(List(One, Two, Three, Four, Five, Six, Seven, Eight, Empty)),1)
```
The output of the programm consists of a tuple with 4 elements:
- The first tuple element of the output is a String which tells us whether a solution was found.
- The second element is the final state of the puzzle that represents the solution.
- The third element represents a list of those states ("moves") which were tried.
- And the last element states number of moves to the solution state.

It is obvious that the heuristic search algorithm is much faster than the DFS-algorithm since it needs just one move to solve the puzzle whereas the DFS needs 439 moves.

### Nonsolvable Puzzle
The following puzzle for example is unsolvable because it has an odd number of inversions (it has only the inversion (2,1)):

![alt text](https://github.com/githubprgrammer/EightPuzzle/blob/master/unsolvable%20puzzle.PNG)

So if we try the following:

```
val puzzle_2 = List(Two, One, Three, Four, Five, Six, Seven, Eight, Empty)
heuristic(puzzle_2)
```

We get the following output: 

```
(Not solvable,List(),List(),0)
```
