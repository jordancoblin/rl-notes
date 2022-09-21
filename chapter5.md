# Monte Carlo Methods

Does not require full model of environment - only experience. Solve RL problems by averaging sample returns (no boostrapping).

Limited to episodic tasks.

Advantages of MC over DP:
- Ability to learn from real experience
- Ability to learn from simulated experience
- Computational cost of estimating value of single state does not depend on number of states

## 5.1 MC Prediction

First-visit vs. every-visit MC -> both converge to $v_\pi(s)$ as the number of visits to s goes to infinity.

## 5.2 MC Estimation of Action-Values

Without a model, need to estimate _action-values_ and not just _state_values_ in order to determine an optimal policy. I.e. want to estimate $q_\pi(s, a)$.

**Exploration Problem**: if a policy only ever takes action a from state s, then we will not be able to improve action-value estimates for other actions.

Solution 1: **Exploring Starts**, which makes every state-action pair have a non-zero probability of being selected as start state.
Solution 2: Can't always control start state. Instead, use stochastic policies that have non-zero probability of selecting each action from all states.

## 5.3 MC Control



