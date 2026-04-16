# Constraint Satisfaction Problems

Learning goals:
- Define possible worlds in term of variables and their domains
- Compute number of possible worlds on real examples
- Specify constraints to represent real world problems differentiating between
    - Unary and k-ary constraints
    - List vs function format
- Verify whether a possible world satisfies a set of constraints
- CSP as search problems
- Local search
- Hill climbing vs greedy descent
- Implement stochastic local search with random steps and random restart
- Compare different SLS algorithms using runtime distributions

## Variables/features, domains, possible worlds

Variables are denoted using capital letters and have a domain $dom(V)$ of possible values. Variables can be boolean, finite, infinite but discrete, or continuous. A possible world is a complete assignment of values to a set of variables. 

### Number of possible worlds

- Product of cardinality of each domain
- Exponential in the number of variables

## Constraints

Restrictions on the values that variables can take. 

- Unary constraint: restriction on a single variable
- k-ary constraint: restriction on the domains of k different variables
    - Can be represented as binary constraints
- Constraints can be specified
    - As a function that returns true when conditions are satisfied
    - As a list of valid domain values

## CSP

A constraint satisfaction problem consists of a set of variables, a domain for each variable, and a set of constraints. 

### Model

A model of a CSP is a possible world that **satisfies** all of the constraints. 

### Objectives of CSP

- Does a model exist
- Find a model
- Find all models
- How many models are there
- Optimal model

### Generate and test

This is a brute-force method to solve CSPs. Generate possible worlds one at a time and test if they violate constraints. Problem with this method is its speed. 

### Search

We can represent CSPs as search problems. 

- States: assignments of values to a subset of variables
- Start state: the empty assignment
- Neighbors of a state (successor function): values are assigned to one additional variable
- Goal state: any state that is a model

**The path to a goal node is not important**

#### DFS with pruning

We can use DFS with pruning by removing a path that violates some constraint, because there won't be a solution past this point. 

The efficiency depends on the order in which variables are assigned values. Degree heuristics are helpful here. (Consider assigning values to variables that are most constrained)

### Local search

1. Start from a possible world
2. Generate some neighbors
3. Move from current node to a neighbor selected with a strategy (scoring function)
4. Repeat 2 and 3

#### Iterative best improvement

How do we generate neighbors? We can generate by changing one assignment or multiple assignments of values, etc. 

Iterative best selects the neighbor that optimizes some evaluation function. It is a greedy approach. For example, we can select the neighbor that has the least number of constraint violations. 

### Constrained optimization

Sometimes solutions have different values/costs. We may want to find an optimal solution that maximizes value or minimizes cost. 

- Hill climbing: select a neighbor that maximizes value and constraints satisfied
- Greedy descent: select a neighbor that minimizes cost and constraints violated

#### Problems

Hill climbing and greedy descent are greedy algorithms. They may get stuck at local maxima or minima. 

### Stochastic local search

This addresses the problem with hill climbing and greedy descent. We can alternate between using:
- Hill climbing or greedy descent
- Random steps: move to a random neighbor
- Random restart: reassign random values to all variables

#### Random steps

Treat neighbors as (variable, value) pairs. Given $n$ variables with domains of $d$ values, there are $n(d-1)$ neighbors. Use the greedy approach with scoring function, but sometimes choose a neighbor randomly. 

Another strategy (two-stage selection)
- Select a variable that
    - has the most conflicts
    - has at least one conflict
    - or randomly
- Then select a value that
    - minimizes conflicts
    - or randomly

**Advantage**: anytime algorithm. When you want a good result in a short time

**Downside**: it may never stop (stagnate). It also can't prove that no solution exists. 

#### Comparing SLS algorithms

Using a runtime distribution plot, where x-axis is the number of steps, and y-axis is the number of runs that are solved within that many steps, we can see which algorithm is faster, and which algorithm will likely stagnate. 

### Tabu list

Keep a tabu list of size $k$ of the recently visited nodes, so that the algorithm doesn't get trapped in cycles

### Simulated annealing

Annealing: metals are heated and then slowly cooled. Similarly, allow more random steps at the start, and then slowly follow greedy approach. 

### Beam search

Keep a memory of tabu list and best node so far. Or run multiple "beams" of SLS searches in parallel. 

### Genetic algorithms

Select $k$ individuals randomly. Each individual is represented as a string. Fitness function decides the "fitness" of an individual and the probability of getting selected as parents.
- Selection
- Crossover
- Mutation

This is very slow