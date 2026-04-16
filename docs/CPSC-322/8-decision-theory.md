# Decision Theory

Learning goals:

- Compare and contrast stochastic single-stage (one-off) decisions vs multi-stage decisions
- Define a Utility Function on possible worlds​
- Define and compute optimal one-off decisions (max expected utility)
- Represent one-off decisions as sinigle stage decision networks and compute optimal decisions by variable elimination

## Planning under uncertainty

- Deterministic goal: a possible world in which some propositions are true
- Planning: how to select and organize a sequence of actions/decisions to achieve a given goal

Under uncertainty:

- Goal: move from all-or-nothing goals to a richer notion: rating how satisfied the agent is in different possible worlds
- Planning: how to select and organize a sequence of actions/decisions to maximize expected agent satisfaction

## Single vs sequence of actions

- Single or one-off: set of one or more primitive decisions that can be treated as a single macro decision to be made before acting, with no prior observations
- Sequential: set of one or more decisions, each of which depends on observations. Agent:
    - Makes observations
    - Decides on an action
    - Carries out the action
    - Repeats with future decisions

## One-off decision

Example: a delivery robot can choose to take a short but risky way, or a longer but safer way. It can also choose to wear pads to mitigate the risk, but will add weight. 

- Macro decision: the decisions the robot makes (wear pads = True, which way = short)
- Decision variables: (wear pads, which way)
- Random variables: (accident)

## Utility

Utility is a measure of desirability of possible world to an agent. ("How happy the robot will be") The utility of achieving certain probability distribution over possible worlds is the expected utility weighting possible worlds by their probabiliy. I.e. sum of probability of each possible world times utility. 

Expected utility of decision $D=d_i$ is

$$E(U|D=d_i) = \sum_{w \models D=d_i}{P(w|D=d_i)U(w)}$$

The optimal decision is the decision $D=d_{max}$

## Single stage decision networks

Extended BNets with decision nodes (rectangles) and utility nodes (diamonds). This network shows explicitly which decision nodes affect random variables. 

### Optimal decision

To find the optimal decision, use variable elimination:
1. Create a factor for each conditional probability and for the utility (but not for the decisions)
2. Multiply factors and sum out all of the random variables, which gives the expected utility for each decision
3. Choose the decision with the maximum value in the factor

## Sequential decision problems

It consists of a sequence of decision variables $D_1,...,D_n$. Each $D_i$ has an information set of variables $pD_i$ whose value will be known at the time decision $D_i$ is made. 

### Policy

A policy specifies what an agent should do under each circumstance. For each decision, consider the parents of the decision node. 

The number of policies is $|D_i|^{|pD_i|}$

### Value of information

The value of information of a random variable $X$ for decision $D$ is  
$$maxEU(\text{knowning } X)-maxEU(\text{not knowing } X)$$

I.e. the expected utility of best decision with an edge from $X$ to $D$ minus without the edge. It is always non-negative. It is positive only if the angent changes its decision. 

### Value of control

The utility of the network when you make $X$ a decision variable minus the utility when $X$ is a random variable. 

### No-forgetting decision network

Decisions are totally ordered. If $D_b$ comes before $D_a$, then $D_b$ is a parent of $D_a$, and parents of $D_b$ are parents of $D_a$. 

### Satisfying a policy

Possible world $w$ satisfies policy $\delta$, written as $w \models \delta$, if the value of each decision variable is the value selected by its decision function in the policy. 

### Expected value of a policy

Each possible world $w$ has a probability $P(w)$ and a utility $U(w)$. The optimal policy is the one with the maximum expected utility of policy $\delta$:

$$\argmax_\delta{\sum_{w \models \delta}{P(w)U(w)}}$$