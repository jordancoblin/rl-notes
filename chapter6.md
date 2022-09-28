# Temporal-Difference Learning

## 6.1 TD Prediction

MC methods need to wait to end of episode to make updates to value function, TD methods need only wait 1 (or n) steps. Combines sampling of MC with bootstrapping of DP.

TD(0)/one-step TD:

$$ V(S_t) \leftarrow V(S_t) + \alpha (R_{t+1} + \gamma V(S_{t+1} - V(S_t)) $$

TD Error:

$$ \delta_t = R_{t+1} + \gamma V(S_{t+1} - V(S_t) $$
