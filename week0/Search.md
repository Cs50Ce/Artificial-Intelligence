## Search

### 🔴Search Problems

### 🟡agent
entity that perceives its environment and acts upon that environment.

### 🟡state
a configuration of the agent and its environment.

### 🟡initial state
the state in which the agent begins.

### 🟡actions
choices that can be made in a state.

### 🟡actions
ACTIONS(s) returns the set of actions that can be executed in state s.

### 🟡transition model
a description of what state results from performing any applicable action in any state.

### 🟡transition model
RESULT(s, a) returns the state resulting from performing action a in state s.

### 🟡state space
the set of all states reachable from the initial state by any sequence of actions.

### 🟡goal test
way to determine whether a given state is a goal state.

### 🟡path cost
numerical cost associated with a given path.


## Search Problems

  - **initial state**
  - **actions**
  - **transition model**
  - **goal test**
  - **path cost function**


### 🟡solution
a sequence of actions that **leads from the initial state** to a goal state.

### 🟡optimal solution
a solution that has the **lowest path cost** among all solutions.

### 🟡node
a data structure that keeps track of
  - **a state**
  - **a parent** (node that generated this node)
  - **an action** (action applied to parent to get node)
  - **a path cost** (from initial state to node)


## 🔴Approach

Start with a **frontier** that contains the **initial state**.\
Repeat:
  - If the frontier is empty, then **no solution**.
  - Remove a node from the frontier.
  - If node contains goal state, return the **solution**.
  - Expand node, add resulting nodes to the frontier.


## 🔴Revised Approach

Start with a **frontier** that contains the **initial state**.\
Start with an **empty explored set**.\
Repeat:
  - If the frontier is **empty**, then **no solution**.
  - Remove a node from the frontier.
  - If node contains **goal state**, return the **solution**.
  - Add the node to the explored set.
  - Expand node, add resulting nodes to the frontier if they aren't already in the frontier or the explored set.

### 🟡stack
**last-in first-out**(LIFO) data type.

### 🟡depth-first search (DFS)
search algorithm that always expands the **deepest node** in the frontier.

### 🟡breadth-first search (BFS)
search algorithm that always expands the **shallowest node** in the frontier.

### 🟡queue
**first-in first-out**(FIFO) data type.
