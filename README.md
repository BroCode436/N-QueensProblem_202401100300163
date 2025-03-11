# N-QueensProblem_202401100300163

# N-Queens Problem Solver

## Problem Description

The N-Queens problem is a classic combinatorial puzzle that asks: How can N chess queens be placed on an N×N chessboard so that no two queens threaten each other?

In chess, a queen can attack any piece that lies in the same row, column, or diagonal. Therefore, to solve the N-Queens problem, we must place N queens on the board such that:
- No two queens share the same row
- No two queens share the same column 
- No two queens share the same diagonal

This problem:
- Has no solutions for N=2 and N=3
- Has 2 solutions for N=4
- Has 10 solutions for N=5
- Has 92 solutions for N=8
- Generally becomes more complex as N increases

## Solution Approach: Hill Climbing with Random Restarts

This repository implements a solution to the N-Queens problem using the Hill Climbing algorithm with Random Restarts, which is a local search optimization technique.

### Key Components

1. **State Representation**:
   - The board state is represented as a one-dimensional array of length N
   - Each index represents a column, and the value represents the row where a queen is placed
   - This representation automatically ensures no two queens share the same column

2. **Conflict Detection**:
   - The `calculate_conflicts()` function counts how many pairs of queens are attacking each other
   - Queens conflict if they share the same row or diagonal

3. **Hill Climbing Algorithm**:
   - Start with a random initial state (queens randomly placed in each column)
   - Evaluate all possible moves (moving each queen to different positions within its column)
   - Choose the move that minimizes the number of conflicts
   - Continue until no better move can be found (local minimum)

4. **Random Restart Strategy**:
   - If a local minimum is reached without finding a solution, restart with a new random state
   - This helps escape local minima to find a global solution
   - The implementation allows for a configurable number of restarts (default: 50)

### Time and Space Complexity

- **Time Complexity**: O(N³) for each hill climbing attempt
  - O(N²) to calculate conflicts
  - O(N²) possible moves to evaluate
  - Combined with restarts: O(R × N³) where R is the number of restarts

- **Space Complexity**: O(N) to store the state (position of queens)

## Usage

Run the script and enter the board size (N) when prompted:

```
python n_queens_solver.py
Enter board size (N >= 4): 8
```

The program will display a visual representation of the solution, with 'Q' indicating queen positions and '.' indicating empty spaces.

## Example Output

For N=8, a possible output might be:
```
. . Q . . . . . 
. . . . . Q . . 
. Q . . . . . . 
. . . . . . Q . 
. . . Q . . . . 
. . . . . . . Q 
Q . . . . . . . 
. . . . Q . . . 
```

## Limitations

- For very large values of N, the algorithm may take a significant amount of time
- The random restart approach does not guarantee finding a solution within a fixed number of attempts
- There is no built-in visualization beyond the text-based board representation

## Future Improvements

- Implement alternative algorithms like Min-Conflicts or Genetic Algorithms
- Add a graphical user interface to visualize the solution
- Optimize the conflict calculation for better performance
- Add functionality to enumerate all possible solutions for a given N
