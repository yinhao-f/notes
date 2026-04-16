# Representational Dimensions

Learning goals:

- Discuss different representational dimensions of problems in AI
- Assess the size of the state space of a given problem

## What needs to be represented

We need to represent the different configurations (states/possible worlds), e.g. chessboards. We also need to represent how the world works using constraints, causal relationships, and actions with preconditions and effects. 

## Types of problems

- Static
    - Constraint satisfaction (scheduling problem)
    - Answering queries (probability of an event)
- Sequential
    - Planning (walking through a maze)

## Types of environments

- Deterministic
    - Agent can fully observe current state
    - Agent knows for sure the direct effects of actions
- Stochastic
    - Agent not certain about either of those two

## Representation & Reasoning (R&R)

Besides a representation, we also need reasoning techniques to compute a solution. The choice of techniques depend on the type of problem and environment. 

## Modeling the environment

### Explicit states, features/propositions, and relations

- A natural approach would be enumerating all possible states.
- We can also use features to describe states. Each feature is a variable and has a domain. The number of possible states will be the product of the domains.
- Another way is to describe using objects and relationships. 
    - Relationship: $\text{Registered}(S,C)=\{T,F\}$
    - Objects: $\text{Students}=\{s1, s2, s3\}, \text{Courses}=\{c1, c2\}$ 
    - Number of inputs is $3 \times 2=6$
    - Number of states is $2^6$

### Goals vs preferences

- Goals
    - An agent wants to be in some state(s)
    - An agent wants to make some proposition(s) true
- Preferences
    - Some function that describes how "happy" the agent is in each state
    - Try to reach a state that maximizes "happiness"

### Other dimensions of representational complexity (not testable)

- Flat vs hierarchical
- Knowledge given vs knowledge learned
- Single agent vs multi agent