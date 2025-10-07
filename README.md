# 🧩 Former Goat Puzzle – Monty Hall Simulation  
**Author:** Karthika Ramasamy  

[![Python](https://img.shields.io/badge/Python-3.10-blue.svg)]() [![NumPy](https://img.shields.io/badge/NumPy-1.26-blue.svg)]() [![Matplotlib](https://img.shields.io/badge/Matplotlib-3.8-orange.svg)]() [![Status](https://img.shields.io/badge/Simulation-Monty%20Hall%20Problem-green.svg)]()

---

## 🚀 Overview  

This notebook simulates the **Monty Hall (Former Goat) Puzzle** using **classical search algorithms** —  
**Breadth-First Search (BFS)**, **Depth-First Search (DFS)**, and **Uniform Cost Search (UCS)** —  
to explore decision paths in the door-selection problem.

Rather than relying solely on random simulation, each algorithm systematically explores all possible states and outcomes to determine the optimal strategy for maximizing the chance of winning the car.

You can open and run the notebook directly:  
```bash
jupyter notebook "CAP_5636_HW3.ipynb"
```
---

## Problem Description

In the Monty Hall problem, a player faces three doors:

Behind one door is a car (the prize).

Behind the other two doors are goats.

**Game Rules:**

1. The player selects one door at random.

2. The host (who knows what’s behind each door) opens another door that has a goat.

3. The player then chooses whether to stay with the original door or switch to the other unopened door.

Question: Should the player stay or switch to maximize the chance of winning?

---

## ⚙️ Setup
```bash
git clone https://github.com/<your_username>/<your_repo>.git
cd <your_repo>
jupyter notebook "CAP_5636_HW3.ipynb"
```

# Dependencies:

Python ≥ 3.9

NumPy ≥ 1.26

Matplotlib ≥ 3.8

Jupyter Notebook

---
# 🔍 State Representation

Each state in the search tree represents a unique configuration of:

Player’s choice – which door is currently selected

Host’s revealed door – which door is opened to show a goat

Remaining unopened doors

Decision outcome – whether the player wins or loses by staying or switching

Example State:
'''(player_door=1, car_door=3, host_door=2, action="switch") '''

Each algorithm explores transitions between these states differently, depending on the search policy.

# 🧩 Algorithms Implemented

**1. Breadth-First Search (BFS)
**
Explores all states level by level.

Ensures the shortest path to a goal (winning configuration) is found first.

Each node represents a possible combination of player/host actions.

BFS Workflow:

Initialize queue with root node (initial door selection).

Expand all states by revealing one goat door.

Generate next possible moves (stay or switch).

Stop when a terminal state (win/lose) is reached.

✅ Pros: Guarantees the optimal (shortest) solution path.
⚠️ Cons: High memory usage for branching states.

**2. Depth-First Search (DFS)
**
Explores a single branch of the state tree deeply before backtracking.

Useful for exhaustively exploring all decision combinations.

DFS Workflow:

Start from root node (initial choice).

Recurse through door reveal → switch/stay transitions.

Track visited states to prevent cycles.

✅ Pros: Memory efficient, simple recursive structure.
⚠️ Cons: May find a non-optimal solution earlier (depends on tree depth).

**3. Uniform Cost Search (UCS)
**
Expands the lowest cumulative cost node first.

Each transition (door reveal, switch/stay) is assigned a cost (e.g., probability or action weight).

Finds the least-cost path to the winning state.

UCS Workflow:

Use a priority queue ordered by path cost.

Expand the state with the smallest total cost.

Continue until the goal state (win) is reached.

✅ Pros: Guarantees the least-cost (optimal) solution.
⚠️ Cons: Requires consistent cost metrics for fair comparison.

---
# Algorithm Comparison
| Algorithm | Search Strategy            | Optimal Solution | Memory Usage | Execution Time | Notes                             |
| :-------- | :------------------------- | :--------------: | :----------: | :------------: | :-------------------------------- |
| BFS       | Level-by-level exploration |       ✅ Yes      |    🔺 High   |    Moderate    | Finds shortest win path first     |
| DFS       | Deep recursive search      | ❌ Not guaranteed |     ✅ Low    |      Fast      | May explore unnecessary states    |
| UCS       | Cost-based priority search |       ✅ Yes      |  ⚠️ Moderate |    Moderate    | Finds least-cost winning strategy |

---

# Algorithm Outcomes

BFS consistently finds the shortest sequence of actions leading to a win.

DFS covers the full search space but can get stuck in non-winning branches before backtracking.

UCS adapts to varying costs, identifying the lowest cumulative cost route to the goal.

Across all algorithms, the winning probability aligns with the theoretical 2/3 success rate for switching versus 1/3 for staying.
