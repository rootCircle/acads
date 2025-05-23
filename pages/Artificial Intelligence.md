- ![image.png](../assets/image_1740239847606_0.png){:height 186, :width 536}
- ![image.png](../assets/image_1740240121740_0.png){:height 261, :width 470}
- ### BFS
	- Uninformed, Complete(searches all even in infinite)
	- Uses FIFO (Queue) to traverse
	- O(V+E) O($b^d$)
	- Optimal (cost is min)
- ### DFS
	- Incomplete (infinite/cycle)
	- Stack (LIFO)
	- Non-optimal (cost may not be min)
	- O(V+E) O($b^d$)
- ### Bidirectional Search
	- ![image.png](../assets/image_1740241455698_0.png){:height 265, :width 469}
- ### 8 bit Puzzle
	- ![image.png](../assets/image_1740241883697_0.png){:height 274, :width 436}
	- #### Heuristic(Informed Search)
		- No. of misplaced tiles
- ### Heuristic
	- Use euclidean, manhattan(|x1-x2| + |y1-y2|), misplaced tiles in 8 bit puzzle
	- Good solution, reduce time complexity, not always optimal
- ### Generate and test
	- Heuristic, DFS with backtracking
	- Good generator: Complete, Non-redundant, Informed Search
	- Generate all state with heuristics and remove state which aren't the solutions
- ### Best First Search
	- ![image.png](../assets/image_1740432836468_0.png){:height 361, :width 588}
	- f-values are not related to cost, but heuristics
	- sort after each insertion in queue
- ### Beam Search Algorithm
	- Care of space complexity by only account for best $\beta$ (beam width) branch node, instead of all
	- Not complete
- ### Hill Climbing Algo
	- $\beta$ = 1
	- ![image.png](../assets/image_1740435246307_0.png){:height 336, :width 565}
- ### A* algorithm
	- ![image.png](../assets/image_1740435794625_0.png){:height 269, :width 520}
	- ![image.png](../assets/image_1740438266856_0.png){:height 306, :width 594}
- ### AO*
	- Update heuristic values based on lower values and update it till root level
	- f(n) is for current node, not path when updating values
	- ![image.png](../assets/image_1740441626799_0.png){:height 403, :width 403}
	- It doesn't explore all solution path once it got the solution
- ### Minimax Algorithm
	- ![image.png](../assets/image_1740444270401_0.png){:height 308, :width 615}
	- ![image.png](../assets/image_1740444332377_0.png){:height 387, :width 453}
- ### Alpha beta pruning
	- ![image.png](../assets/image_1740445236566_0.png){:height 243, :width 551}
	- a >= b else pruning
- ### Knowledge Representation
	- ![image.png](../assets/image_1740446813565_0.png){:height 291, :width 453}
	- ![image.png](../assets/image_1740447270926_0.png)
- ### AI Agents
	- ![image.png](../assets/image_1740447791265_0.png){:height 372, :width 659}
		- P: Performance measure
		- E: Environment
		- A: Actuators
		- S: Sensors
	- ![image.png](../assets/image_1740448745058_0.png){:height 315, :width 527}
	- ![image.png](../assets/image_1740449088845_0.png){:height 342, :width 576}
	- ![image.png](../assets/image_1740450848954_0.png){:height 303, :width 542}
	- ![image.png](../assets/image_1740451084820_0.png){:height 318, :width 559}