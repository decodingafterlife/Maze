BFS vs Q-Learning for Maze Path Finding
1. Introduction
The project's aim is to develop and compare Breadth-First Search (BFS) and Q-Learning on finding the shortest path in a maze. The objective is to develop the algorithms and compare them based on various factors such as execution time, steps taken and nodes expanded.
2. Methodology
Maze Representation:
The mazes used are represented using a 2D NumPy array with binary representation (0,1). '0' represents an open path whereas '1' represents an obstacle/wall. Initially for developing the algorithms images of mazes having singular solutions were collected online and then they were converted into arrays. Both the algorithms were developed, fine-tuned and tested on these mazes. After ensuring that the algorithms were working as intended and giving the desired outputs custom mazes were created using the 'create_maze' function in file 'BFS_vs_QLearning'.
BFS Implementation:
BFS is an uninformed search algorithm that explores all possible nodes breadth wise (level-by-level). A queue is used to store the paths as well as an array to store the visited nodes. BFS is usually used to find the shortest path in data structures such as graphs.
In case of the given problem statement each node was expanded to search its neighbouring nodes. These nodes were checked in the 'visited' array and if not present they were added in the queue. Four actions are possible from every node 'move left', 'move right', 'move up' and 'move down'.
Q-Learning Implementation:
Q-Learning is a Reinforcement Learning technique where the model learns through trial and error. The agent interacts with the environment through different actions and based on the change in the environment, it determines the reward for that particular action. Over time the same action is repeated and the reward for that action is averaged out. This reward is called Q-value. A Q-table is maintained which stores all the Q-values. Q-Table is updated after each action.
Some essential parameters are need for the implementation of the Q-Learning algorithm:

Alpha (α) - Learning Rate: Controls by how much the Q-values are updated in each iteration. (value used = 0.1)
Gamma (γ) - Discount Factor: Determines the importance of future rewards. (value used = 0.99)
Epsilon (ε) - Exploration Rate: Controls the balance between exploration (trying new actions) and exploitation (using known good actions). (value used = 0.1)

For the given problem statement, I have used an Epsilon-Greedy Strategy where the epsilon value balances the exploitation and exploration. An episode value of 10,000 was used for each maze. The final Q-Table along with Q-Values are stored in 'json' files. Numba library and Just-in-Time compilation is used to make the algorithm more efficient and faster.
File Description:

Q-Learning.ipynb: This notebook contains the implementation of the Q-learning algorithm. It includes the functions for setting up the maze environment, training the Q-learning agent, and visualizing the results.
BFS.ipynb: This notebook contains the implementation of the BFS algorithm. It includes the functions for executing BFS on a maze, tracking the path from start to goal, and visualizing the maze with the solution path.
BFS_vs_QLearning.ipynb: This is the final notebook which contains the comparison of both the algorithms on custom mazes. The mazes are created in such a way that they can have multiple solutions, this is done so to see which methods returns the most optimal path.

3. Results and Discussion
Three different custom mazes were used for testing
Performance Metrics:

Total Execution Time: Time taken to find the solution.
Steps Taken: Number of steps from the start to the goal.
Nodes Expanded: Number of nodes explored during the search process.

BFS vs. Q-learning:

Execution Time: BFS was much faster than Q-learning in all test cases, even after using Numba to optimize the Q-learning code.
Steps Taken: BFS consistently found the shortest path. Q-learning, depending on the exploration rate and learning parameters, sometimes found suboptimal paths.
Nodes Expanded: BFS explored fewer nodes than Q-learning, which often explored many unnecessary nodes during its learning phase.

4. Challenges:
The primary challenge was to optimize the Q-Learning algorithm, which involved a large number of iterations. Optimal values for alpha, gamma and epsilon had to be found through trial and error. Numba and Just-in-Time compilation had to be used to optimize the code and reduce the time complexity.
5. Conclusion:
The approach to first test both the algorithm so as to refine them and then using them on custom mazes was important to achieve optimal results. While BFS proved to be faster and more efficient, the process of fine-tuning Q-learning highlighted its potential flexibility in solving and providing better results to more complex problems.
6. Professional Concerns:
Q-learning is a powerful algorithm in reinforcement learning, but its application in this problem statement shows its limitations in comparison to traditional algorithms like BFS. When implementing such algorithms, it is important to consider the trade-offs between flexibility and efficiency. Proper optimization techniques, like those provided by the Numba library, helped in increasing the performance but even after that BFS proved to be more optimised and faster.
