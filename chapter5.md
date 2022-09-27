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

- Solution 1: **Exploring Starts**, which makes every state-action pair have a non-zero probability of being selected as start state.
- Solution 2: Can't always control start state. Instead, use stochastic policies that have non-zero probability of selecting each action from all states.

## 5.3 MC Control

Policy evaluation is done as outlined in 5.1.

Policy improvement is done by making the policy greedy w.r.t. the current value function:

$$ \pi_{k+1}(s) = \arg \max_a q_{\pi_k}(s, a) $$

Can show that policy improvement theorem holds in MC case.

Monte Carlo with Exploring Starts: at the end of each episode, alternate between policy evaluation (averaged discounted returns) and policy improvement (greedy action selection) when processing each timestep.

<img width="790" alt="image" src="https://user-images.githubusercontent.com/7538750/192599820-eef4ca4b-d074-4302-95de-c3f90d2713a3.png">

## 5.4 MC Control w/o Exploring Starts

Can use $\epsilon-greedy$ policy to ensure all actions get selected infinitely.

<img width="804" alt="image" src="https://user-images.githubusercontent.com/7538750/192602315-bb86cc2b-aba4-48aa-9a38-944a14022413.png">

Can show that policy improvement holds in this case (however only achieve the best policy among $\epsilon-soft$ policies.

## 5.5. Off-policy Prediction via Importance Sampling

Off-policy allows us to separate the notion of behaviour policy from target policy. Off-policy methods are more powerful and more general (on-policy can be thought of as a special case of off-policy), but are of greater variance and slower to converge.

Prediction -> behaviour and target policies are fixed.

Assumption of **coverage**: every action taken under $\pi$ gets taken at least occasionally under b.

**Importance sampling**: technique for estimating expected values under one distribution given samples from another -> weigh returns based on the relative probability of their trajectories occurring under the target and behaviour policies.

$$ \rho_{t:T-1} = \prod_{k=t}^{T-1} \frac{\pi(A_k | S_k)}{b(A_k | S_k)} $$

Note that the importance sampling ration $\rho$ only depends on the policies, and not the MDP transition probabilities.

$$ v_b(s) = \mathbb{E}[G_t | S_t=s] $$

$$ v_\pi(s) = \mathbb{E}[\rho_{t:T-1} G_t | S_t=s] $$
