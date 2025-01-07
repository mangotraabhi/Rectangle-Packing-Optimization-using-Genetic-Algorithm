# Rectangle Packing Optimization using Genetic Algorithm

This project solves a rectangle packing problem using a **Genetic Algorithm (GA)**. The goal is to place 8 rectangles of random sizes into a bin of fixed dimensions (80x40) without overlaps and with specific constraints. The solution is optimized to minimize unused space while satisfying all constraints.

---

## Problem Statement

### Bin and Rectangles
- **Bin Dimensions:** Width = 80 units, Height = 40 units.
- **Rectangles:** 8 rectangles with random widths and heights (between 5 and 20 units).

### Constraints
1. **Placement Constraints:**
   - Rectangle 1 must be placed on the **top side** of the bin.
   - Rectangle 2 must be placed on the **bottom side** of the bin.
   - Rectangle 3 must be placed **close to rectangles 4, 5, and 8**.
   - Rectangle 7 must be placed **close to rectangles 6 and 2**.
2. **Separation Constraint:**
   - All rectangles must have at least **one unit of separation** between them.
3. **No Overlaps:**
   - Rectangles cannot overlap with each other or go outside the bin boundaries.

---

## Approach

### Genetic Algorithm (GA)
The Genetic Algorithm is used to solve this problem because it is well-suited for combinatorial optimization problems with constraints. The key steps are:

1. **Representation:**
   - Each solution is represented as a list of rectangle placements: `[(x1, y1, w1, h1), (x2, y2, w2, h2), ..., (x8, y8, w8, h8)]`.
   - `(x, y)` = bottom-left corner of the rectangle.
   - `(w, h)` = width and height of the rectangle.

2. **Population Initialization:**
   - Generate random placements for rectangles, ensuring rectangles 1 and 2 are on the top and bottom sides, respectively.
   - Validate placements to ensure no overlaps and one-unit separation.

3. **Fitness Function:**
   - Minimize the unused area in the bin.
   - Add penalties for violating proximity constraints (e.g., rectangles 3, 4, 5, and 8 must be close).

4. **Selection, Crossover, and Mutation:**
   - **Selection:** Choose the best solutions (based on fitness) for reproduction.
   - **Crossover:** Combine two parents to create a child.
   - **Mutation:** Randomly modify a rectangle's position in the child.

5. **Evolution:**
   - Evolve the population over generations, retaining the best solutions and creating new ones through crossover and mutation.

---

## Code Structure

The code is organized into **Google Colab cells** for easy execution. Below is a breakdown of the cells:

### 1. Install Required Libraries
Installs `networkx` and `matplotlib` for graph visualization and plotting.

### 2. Import Libraries
Imports necessary libraries: `random`, `numpy`, `matplotlib`, and `networkx`.

### 3. Define Bin and Rectangles
- Defines bin dimensions and randomly generates rectangle sizes.

### 4. Define Constraint Graph
- Creates a graph to represent proximity constraints (e.g., rectangle 3 must be close to rectangles 4, 5, and 8).

### 5. Constraints Handling
- Defines a function to check if a placement is valid (no overlaps, one-unit separation, within bin boundaries).

### 6. Distance Penalty
- Calculates penalties for violating proximity constraints.

### 7. Objective Function
- Combines unused area and penalty into a single fitness value.

### 8. Genetic Algorithm
- Implements the Genetic Algorithm to evolve solutions over generations.

### 9. Run Genetic Algorithm
- Runs the GA and prints the best placement.

### 10. Plot Final Placement
- Visualizes the final placement of rectangles in the bin.

---

## How to Run the Code

1. Open the project in **Google Colab**.
2. Run each cell sequentially.
3. The output will include:
   - The constraint graph.
   - Training progress plot (fitness vs. generations).
   - Best placement coordinates.
   - Visualization of the final rectangle placement.

---

## Key Features

1. **Constraint Handling:**
   - Ensures rectangles do not overlap and have one-unit separation.
   - Enforces proximity constraints using a penalty in the fitness function.

2. **Visualization:**
   - Plots the constraint graph to show relationships between rectangles.
   - Displays the final placement of rectangles in the bin.

3. **Optimization:**
   - Minimizes unused area while satisfying all constraints.

---

## Rectangles Used
- Rectangles are numbered from **1 to 8**.
- Rectangle 9 is **not used**; instead, rectangle 8 is used in the proximity constraints.

---

## Future Improvements
1. **Dynamic Rectangle Sizes:**
   - Allow rectangles to have dynamic sizes based on user input.
2. **Additional Constraints:**
   - Add more complex constraints (e.g., alignment, orientation).
3. **Performance Optimization:**
   - Improve the efficiency of the Genetic Algorithm for larger problems.

---

## Dependencies
- Python 3.x
- Libraries: `networkx`, `matplotlib`, `numpy`

---

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---
