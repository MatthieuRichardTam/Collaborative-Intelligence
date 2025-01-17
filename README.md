# ICO - Intelligence Collaborative Optimization

## Description
This project focuses on collaborative optimization for the **Vehicle Routing Problem (VRP)**, an NP-hard problem where the goal is to minimize costs associated with vehicle routes (travel distances, number of vehicles used). We started with the application of three classic metaheuristics (tabu search, simulated annealing, genetic algorithm) to solve this problem. Subsequently, we explored more collaborative approaches using multi-agent protocols (friend/enemy) and enhanced the performance with reinforcement learning methods (Q-learning).

## Details of the Algorithms Used

### 1. Metaheuristic Solutions
We first implemented three metaheuristic algorithms to solve the vehicle routing scheduling problem:

- **Tabu Search**:
  - This algorithm iteratively explores neighboring solutions and maintains a tabu list to avoid revisiting the same solutions.
  - Neighbors are generated by random permutations of clients, such as swapping two clients or moving a client to a different position.
  - Notable results: progressive reduction of route costs with each iteration.  
  ![Figure 3 - Progressive cost reduction](graphs/tabu_algo.png)

- **Simulated Annealing**:
  - Inspired by the metal cooling process, this algorithm alternates between exploration and exploitation through a decreasing temperature parameter.
  - Neighbors are generated by modifying existing routes using strategies like inter-route swaps or intra-route moves.
  - Results: a better balance between global exploration and rapid convergence.  
  ![Figure 6 - Comparison of neighborhood methods](graphs/annealing_algo.png)

- **Genetic Algorithm**:
  - This algorithm mimics biological evolution mechanisms (selection, crossover, mutation).
  - An initial population of solutions is generated randomly and refined over iterations to improve solution quality.
  - Key parameters: population size, crossover, and mutation probabilities.  
  ![Figure 14 - Cost evolution](graphs/genetic_algo.png)

### 2. Multi-Agent Protocols
To leverage the advantages of metaheuristics, we developed two collaborative agent protocols:

- **Friend Protocol**:
  - Agents share their best solutions through a collaborative pool.
  - This enables faster convergence to optimal solutions through guided exploration.  
  ![Figure 38 - Best solution with Friend Protocol](images/figure38.png)

- **Enemy Protocol**:
  - Agents operate in competition, with each team striving to outperform the other’s solutions.
  - This protocol encourages continuous improvement in agent performance.  
  ![Figure 40 - Results of Enemy Protocol](images/figure40.png)

### 3. Reinforcement Learning with Q-learning
To further optimize the solution, we integrated reinforcement learning (Q-learning) into our metaheuristics:

- Neighbors are evaluated based on their cost, and the best solutions are favored to guide exploration.
- An E-greedy strategy balances exploitation of optimal solutions with exploration of new options.
- Results: significant improvement in solutions with notable reductions in total travel distances.  
  ![Figure 43 - Influence of E-greedy on solutions](images/figure43.png)

## Key Results

### Metaheuristic Comparisons
- Metaheuristics were tested on datasets of varying sizes. For instance, with a dataset of 20 clients:
  - Tabu: optimal cost ≈ 260.
  - Simulated Annealing: optimal cost ≈ 255.
  - Genetic: optimal cost ≈ 250.  
  ![Figure 3 - Metaheuristic comparison](images/figure3.png)

- For a complete dataset of 107 clients, the genetic algorithm converged faster and yielded better solutions.  
  ![Figure 36 - Algorithm comparison](images/figure36.png)

### Friend Protocol
- The Friend Protocol improved solutions by 180 points compared to standalone metaheuristics.  
  ![Figure 38 - Best solution with Friend Protocol](images/figure38.png)

### Enemy Protocol
- With the Enemy Protocol, agent teams converged toward an optimal solution where both teams reached a plateau.  
  ![Figure 40 - Results of Enemy Protocol](images/figure40.png)

### Reinforcement Learning
- Using Q-learning, the best solution achieved was ≈ 379 km (E-greedy = 0.02), compared to 530 km without Q-learning.  
  ![Figure 43 - Influence of E-greedy on solutions](images/figure43.png)

### Final Results
- Standalone metaheuristics achieved a final cost of approximately 560.
- Combining SMA and Q-learning reduced the final cost to ≈ 350.  
  ![Figure 44 - Final results](images/figure44.png)

## Authors
- Matthieu Richard, Ilyasse Chaouki, Antoine Deschamps, Virgile Devillers, Antoine Greaume



