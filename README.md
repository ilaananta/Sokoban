# Sokoban
 
This repository contains a Python program designed to solve Sokoban puzzles efficiently using various heuristics. The game Sokoban is a transportation puzzle where the playing arena is composed of a grid of squares. Some of the squares are marked as boxes where the player has to push to a goal on the board. Some of the squares are marked as walls which act as constraints where the player as well as the boxes cannot enter. The initial state consists of a player at a certain x,y location on the grid and certain locations marked boxes and target stores. The player can move horizontally or vertically (in four directions - Up, Down, Left, and Right). The player can push, at most a single box into an empty space that is not a wall or another box. The player is not allowed to pull the boxes too. There are an equal number of boxes and target goals, and the player succeeds once all boxes are in goal locations. The player fails if a box gets locked up in a corner or with another box with the goal being unoccupied. One of the things that makes the Sokoban problem so difficult to solve is the large branching factor and the significant length of the average solution, resulting in a search space too big for even an informed search agent with good heuristics to solve in a practical amount of time. We attempted to overcome this by trying different approaches.

## Approach
We tried to solve the Sokoban problem using A* algorithm. Under the right conditions i.e., heuristics, this algorithm can minimize the cost and provide the solution in optimal time.

## Heuristics Explored

1. **Number of Blocks Out of Place**: The initial attempt was to assess the number of blocks out of place. However, this approach was highly inefficient and failed to solve any cases.

2. **Manhattan Distance with Modifications**: A more efficient heuristic was developed by modifying the Manhattan distance calculation. This heuristic enabled us to solve problems from real Sokoban games available online. However, it still faced challenges with complex problems, often taking extended hours to compute.

3. **Hungarian Algorithm**: Another heuristic explored was the Hungarian algorithm. We utilized an implementation of this algorithm to find the lowest cost for perfect matching of boxes to goals in the initial state. This matching was then used to determine which box to move onto which goal tile, considering the distance between a box and its target goal in computing the score of any heuristic.

### Program Workflow

The program's workflow can be summarized as follows:

1. **Loading Test Cases**: Test cases are loaded into a matrix using the `getmatrix()` function defined within the game class.
   
2. **State Representation**: The state of the game is stored as a tuple, obtained by flattening the matrix.
   
3. **Open Nodes Maintenance**: Open nodes are maintained using a dictionary data structure, where the key represents the state of the game (as a tuple), and the value represents the heuristic used.
   
4. **Node Expansion**: Each node, including the root node (start state), is expanded by evaluating the possible moves of the player. Each child obtained is added to the open dictionary, which is then sorted based on its heuristic value.

Feel free to explore the code!

 
