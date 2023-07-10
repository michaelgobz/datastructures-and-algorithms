# Exiting the Maze

This challenge it inspired by the mouse trapped in a maze and find the exit door.
The mouse hopes to escape from the maze by systematically trying all
the routes. If it reaches a dead end, it retraces its steps to the last position and begins at
least one more untried path. For each position, the mouse can go in one of four directions: right, left, down, up. Regardless of how close it is to the exit, it always tries the
open paths in this order, which may lead to some unnecessary detours. By retaining
information that allows for resuming the search after a dead end is reached, the mouse
uses a method called backtracking. This method is discussed further in the next chapter.
The maze is implemented as a two-dimensional character array in which passages are marked with 0s, walls by 1s, exit position by the letter e, and the initial position of the mouse by the letter m (Figure 4.22b). In this program, the maze problem
is slightly generalized by allowing the exit to be in any position of the maze (picture
the exit position as having an elevator that takes the mouse out of the trap) and allowing passages to be on the borderline. To protect itself from falling off the array by
trying to continue its path when an open cell is reached on one of the borderlines, the
mouse also has to constantly check whether it is in such a borderline position or not.
To avoid it, the program automatically puts a frame of 1s around the maze entered
by the user.
The program uses two stacks: one to initialize the maze and another to implement backtracking.
The user enters a maze one line at a time. The maze entered by the user can have
any number of rows and any number of columns. The only assumption the program
makes is that all rows are of the same length and that it uses only these characters:
any number of 1s, any number of 0s, one e, and one m. The rows are pushed on the
stack mazeRows in the order they are entered after attaching one 1 at the beginning
and one 1 at the end. After all rows are entered, the size of the array store can be determined, and then the rows from the stack are transferred to the array.
A second stack, mazeStack, is used in the process of escaping the maze. To remember untried paths for subsequent tries, the positions of the untried neighbors of
the current position (if any) are stored on a stack and always in the same order, first
upper neighbor, then lower, then left, and finally right. After stacking the open avenues on the stack, the mouse takes the topmost position and tries to follow it by first
storing untried neighbors and then trying the topmost position, and so forth, until it
reaches the exit or exhausts all possibilities and finds itself trapped. To avoid falling
into an infinite loop of trying paths that have already been investigated, each visited
position of the maze is marked with a period.
Here is a pseudocode of an algorithm for escaping a maze:

```c++
exitMaze()
 initialize stack, exitCell, entryCell, currentCell = entryCell;
 while currentCell is not exitCell
 mark currentCell as visited;
 push onto the stack the unvisited neighbors of currentCell;
 if stack is empty
 failure;
 else pop off a cell from the stack and make it currentCell;
 success;
```
