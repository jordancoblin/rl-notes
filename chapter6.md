# Temporal-Difference Learning

## 6.1 TD Prediction

MC methods need to wait to end of episode to make updates to value function, TD methods need only wait 1 (or n) steps. Combines sampling of MC with bootstrapping of DP.

TD(0)/one-step TD:

$$ V(S_t) \leftarrow V(S_t) + \alpha (R_{t+1} + \gamma V(S_{t+1}) - V(S_t)) $$

TD Error:

$$ \delta_t = R_{t+1} + \gamma V(S_{t+1}) - V(S_t) $$

## 6.2 TD Prediction

TD over DP:
- Do not require model of environment

TD over MC: 
- Can make updates online/incrementally during episode, rather than only at end.
- Can use for continuing case.

Convergence: TD(0) has been proved to converge to $v_\pi$ for any fixed policy $\pi$ - for tabular and linear FA cases at least.

Speed of convergence/learning: not theoretically proven yet. However, empirically we usually see faster learning in TD(0) methods vs. constant-$\alpha$ MC methods.

## 6.3 Optimality of TD(0)

TD(0) and constant-$\alpha$ MC converge to different values.

For batch methods:

MC: minimizes MSE of V(s) from actual returns during training.
TD: estimates the MLE result of the Markov process -> converges to the **certainty-equivalence estimate**.

Plot shows that TD outperforms MC in terms of RMSE on a random walk task. Given that MC minimizes MSE, this is surprising. This can be explained due to TD approximating the certainty-equivalence estimate: TD V(s) estimates encapsulate a model of the MDP (and transition probabilities) based on experience. Given this model, we compute an estimate of the value function if the model were _exactly correct_ - hence the "certainty-equivalence" naming. Another way of thinking of this is that TD can be considered to produce lower error on _future data_, whereas MC produces lower error on _existing data_.

## 6.4 Sarsa: On-policy TD Control

GPI + TD methods.

$$ Q(S_t, A_t) \leftarrow Q(S_t, A_t) + \alpha (R_{t+1} + \gamma Q(S_{t+1}, A_{t+1}) - Q(S_t, A_t)) $$
