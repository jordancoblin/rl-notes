## Dynamic Programming

Collection of algos that can compute optimal policies given a perfect model of the env. Disadvantages: require perfect model and sometimes computationally expensive.
Useful as a foundation for more sophisticated methods.

Continuous states/action spaces -> quantize/bin into finite spaces.

Key idea: use value function to structure policy search -> DP can be used to compute value functions, by splitting into sub-problems (recursive definition).

### 4.1 Policy Evaluation
Prediction problem -> computing the value function.

Can do this iteratively, by updating $v_{k+1}$ to be the result of the bellman equation over $v_k$:

$$ v_{k+1}(s) = \mathbb{E_\pi} R $$
