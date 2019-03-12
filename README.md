# EightPuzzle
Solving the 8-puzzle problem first by using depth-first-search and then by using a heuristic function.

The 8-puzzle is a sliding puzzle that consists of a frame of 8 numbered square tiles in random order with one tile missing. The object of the puzzle is to place the tiles in order by making sliding moves that use the empty space. 
For more information: https://en.wikipedia.org/wiki/15_puzzle

In our program, we do not care where the empty space ends. What matters is that the numbered tiles are sorted in ascending manner from left to right, top to bottom. It is important to note that this problem is not solvable for half of the possible initial configurations. So first we have to prove if the puzzle is solveable.
