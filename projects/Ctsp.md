---
layout: project
type: project
image: img/tsp/logo.png
title: "Traveling Salesman Problem Solver"
date: "Nov 2022 - Dec 2022"
position: 3
published: true
labels:
  - C++
  - Artificial Intelligence
  - Algorithms
  - Heuristics
summary: "Implemented Branch and Bound Depth First Search (heuristic) and Simulated Annealing Stochastic Local Search algorithms to find optimal path."
---

## Problem Statement
Traveling salesman's problem is to find the optimal path for visiting the given locations and their
distances. The optimal path is the path with minimum cost. The salesman comes back to the city from
where he started the path. For our project, we have following assumptions:
1. Each city is connected to every other city.
2. Distance or cost of going from one city to another is the same as coming back from that city to
the initial city i.e., the cost of going from city A to B is the same as going from city B to city A.

## Solution Approach
For the solution, I am using three algorithms:

#### Branch and Bound Depth First Search algorithm
This algorithm performs exhaustive search on the given cities, and finds the optimal path. The algorithm selects a starting city and iterates over other cities using DFS technique and an initial best cost is provided to the algorithm. In each iteration it moves to the city only if adding it to the path does not increase the given cost. If it does, that city is not included in the current path and the path if that city was included is pruned meaning is ignored and not processed. If a path with less cost is found then the best cost is updated to this value.

#### Simulated Annealing Stochastic Local Search
This algorithm creates a random path initially and then swaps two cities at a time to get an optimal path. Each time a path is found, its cost is compared with the previously found path. If the cost is reduced, then that path is kept and used in later iterations for cost comparison.

#### Dynamic Programming based naive approach
In this approach, an intial city is chosen and then next city with mininum cost is added to the path, and then next city with minimum cost is chosen and so on.

**Heuristic Logic**: 
In all the these algorithms, I used minimum spanning tree logic to estimate the path cost whenever required. For this, I used Kruskul's algorithm.

## Observations

- If ran to completion (without any time limits), bnb finds the optimal path. Solution with dynamic programming also gives the optimal path but the catch is it is alot slower than bnb where number of cities goes beyond 23.

- The Simulated Annealing algorithm, deviates from the optimal path in some cases and returns the sub-optimal path because of randomness and no exhaustive search. The benefit is that it returns the good sub-optimal solution in very little time as compared to the time taken by the BnB algorithm for getting the optimal path.

Click [here](https://github.com/pallavi-garg/Travelling-Salesman-Problem#observations-and-results) for detailed comparisons.

[Source Code](https://github.com/pallavi-garg/Travelling-Salesman-Problem).
