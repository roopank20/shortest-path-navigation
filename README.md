# shortest-path-navigation
Write a program that finds the shortest path between an initial state and the final state. The agent can move one square at a time in any of the four principal compass directions, and the program should find the shortest distance between the two points and then output a string of letters (L, R, D, and U for left, right, down, and up) indicating that solution.

In the part one of assignment 0, we were provided with a setup where we had a grid of dimensions N*M
cells. Each cell was marked with one of the 4 symbols :

P (Agent's current location)

X (a barrier or a wall to restrict agent's movement)

. (open spaces where agent can take place or traverse over)

@ (the goal state or desired final position of the agent)

Our objective of this problem was to find the shortest path between P and @ keeping in mind that the agent can traverse 
only one step at a time. If we are not able to find a path, then our code should return -1.

## Assumptions:

Here, we assume that there is only one agent and one target destination (@).

## Solution

In the given scenario, our code is stuck in an infinite loop as the code is initialized using a stratergy where the 
agent is traversing non stop between two points. This can also be explained syntactically where the fringe is appending 
the same element that it is popping out (Stack implementation). So my first step was to end the infinite loop and it was 
achieved by implementing approach used in queue data structure. Here the first element was popping out in place of the 
last element.

After that, I implemented the Breadth First Search technique in order to fulfil the objective, that was to reach the 
goal(@). In this technique, starting from the initial position (p), our agent started traversing the path it obtained 
further and reached the goal in the fewest steps taken or reached the destination in the most optimal manner.
This implementation works in such a manner that the agent keeps on traversing till it obtains the goal node. 


## Abstractions

State Space - It is the collection of all possible states available to an agent or where an agent can move while 
traversing the path. It is not necessary that an agent will traverse that node, but it will always be available in the agents universe.

Initial State - Initial state is the initial configuration or map provided to us where the  agent is placed in its 
position. With respect to this question, the house_map variable is the initial state. It is the state which is available 
before the agent starts traversing and which we feed to the search method.

Goal State - It is the final state or the output configuration of the agent when the agent reaches the goal state 
(marked with @) without any error. The coordinates of the @ position is our goal state.

Successor Function - Successor Function is the set of successful operations performed on the existing state so that the
agent can reach the next valid state. In this case, the final string of directions returned when the agent reaches the 
goal state, that successful direction is reached with the help of a successor function.

Cost Function - Cost function is nothing but the sum of moves performed by the agent to reach its goal state from the 
initial state. Here, the final cost returned after reaching the goal state is the cost function.

## Design Decisions

Other than implementing the BFS approach, some other data structures were used to fulfil the requirements.
* A list named visitedList was used to store the nodes or coordinates that were visited or traversed by the agent. This 
was also done to ensure that the agent does not traverse the same node more than once otherwise the solution will not be 
optimal in nature.
* A string named dirc was used to store the direction (U,D,L,R) that our agent was taking. This was important in order 
to display the final output.
* A new function getDirections() was constructed and its goal was to return the direcion (U,D,L,R) being taken by the 
agent.


## Input and Output

Input - The map or grid that represents the state space

Output - The number of steps taken by the agent in order to reach the goal state and the string representing the 
direction the agent took after every step.

