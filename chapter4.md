## Dynamic Programming

Collection of algos that can compute optimal policies given a perfect model of the env. Disadvantages: require perfect model and sometimes computationally expensive.
Useful as a foundation for more sophisticated methods.

Continuous states/action spaces -> quantize/bin into finite spaces.

Key idea: use value function to structure policy search -> DP can be used to compute value functions, by splitting into sub-problems (recursive definition).

### 4.1 Policy Evaluation
Prediction problem -> computing the value function.

**Iterative Policy Evaluation**:
Can do this iteratively, by updating $v_{k+1}$ to be the result of the bellman equation over $v_k$:

$$ v_{k+1}(s) = \mathbb{E_\pi} [R_{t+1} + \gamma v_k(S_{t+1}) | S_t = s] $$

$v_k$ can be shown to converge to $v_\pi$ as $k \rightarrow \infty$.

One iteration -> update value of _every state_ once.

### 4.2 Policy Improvement

Question: is it better or worse to change to a new policy? One way to answer is to consider selecting action $a$ in state $s$ and following the existing policy $\pi$ thereafter. Value would be:

$$ q_{\pi}(s, a) = \mathbb{E} [R_{t+1} + \gamma v_{\pi}(S_{t+1}) | S_t = s, A_t = a] $$
