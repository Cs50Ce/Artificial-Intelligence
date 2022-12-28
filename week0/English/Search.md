## Search

### Search Problems

### agent
entity that perceives its environment and acts upon that environment.

### state
a configuration of the agent and its environment.

### initial state
the state in which the agent begins.

### actions
choices that can be made in a state.

### actions
ACTIONS(s) returns the set of actions that can be executed in state s.

### transition model
a description of what state results from performing any applicable action in any state.

### transition model
RESULT(s, a) returns the state resulting from performing action a in state s.

### state space
the set of all states reachable from the initial state by any sequence of actions.

### goal test
way to determine whether a given state is a goal state.

### path cost
numerical cost associated with a given path.


## Search Problems

  - **initial state**
  - **actions**
  - **transition model**
  - **goal test**
  - **path cost function**


### solution
a sequence of actions that **leads from the initial state** to a goal state.

### optimal solution
a solution that has the **lowest path cost** among all solutions.

### node
a data structure that keeps track of
  - **a state**
  - **a parent** (node that generated this node)
  - **an action** (action applied to parent to get node)
  - **a path cost** (from initial state to node)


## Approach

Start with a **frontier** that contains the **initial state**.\
Repeat:
  - If the frontier is empty, then **no solution**.
  - Remove a node from the frontier.
  - If node contains goal state, return the **solution**.
  - Expand node, add resulting nodes to the frontier.


## Revised Approach

Start with a **frontier** that contains the **initial state**.\
Start with an **empty explored set**.\
Repeat:
  - If the frontier is **empty**, then **no solution**.
  - Remove a node from the frontier.
  - If node contains **goal state**, return the **solution**.
  - Add the node to the explored set.
  - Expand node, add resulting nodes to the frontier if they aren't already in the frontier or the explored set.

### stack
**last-in first-out**(LIFO) data type.

### depth-first search (DFS)
search algorithm that always expands the **deepest node** in the frontier.

### breadth-first search (BFS)
search algorithm that always expands the **shallowest node** in the frontier.

### queue
**first-in first-out**(FIFO) data type.


### uninformed search
search strategy that **uses no problemspecific knowledge**.

### informed search
search strategy that **uses problem-specific knowledge to find solutions more efficiently**.

### greedy best-first search
search algorithm that **expands the node that is closest to the goal**, as estimated by a heuristic function h(n).

## A* search
search algorithm that expands node with lowest value of **g(n) + h(n)**:
  - **g(n)** = cost to reach node
  - **h(n)** = estimated cost to goal

### A* search
optimal if
  - **h(n)** is **admissible** (never overestimates the true cost)
  - **h(n)** is **consistent** (for every node n and successor n' with step cost c, **h(n) ≤ h(n') + c**)


## Adversarial Search

### Minimax
  - MAX (X) aims to maximize score.
  - MIN (O) aims to minimize score.

### Game
  - S0 : initial state
  - PLAYER(s) : returns which player to move in state s
  - ACTIONS(s) : returns legal moves in state s
  - RESULT(s, a) : returns state after action a taken in state s
  - TERMINAL(s) : checks if state s is a terminal state
  - UTILITY(s) : final numerical value for terminal state s

### Minimax
  - Given a state s:
  - MAX picks action a in ACTIONS(s) that produces highest value of MIN-VALUE(RESULT(s, a))
  - MIN picks action a in ACTIONS(s) that produces smallest value of MAX-VALUE(RESULT(s, a))

### Minimax
```java
function MAX-VALUE(state):
if TERMINAL(state):
return UTILITY(state)
v = -∞
for action in ACTIONS(state):
v = MAX(v, MIN-VALUE(RESULT(state, action)))
return v
```

```java
function MIN-VALUE(state):
if TERMINAL(state):
return UTILITY(state)
v = ∞
for action in ACTIONS(state):
v = MIN(v, MAX-VALUE(RESULT(state, action)))
return v
```

### Alpha-Beta Pruning

### Depth-Limited Minimax

### evaluation function
function that estimates the expected utility of the game from a given state.



- ***last update: 2022 Dec 29***
- ***State: complete***
