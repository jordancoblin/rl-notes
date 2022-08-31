## Bandits

Mostly standard stuff here, a basic intro to the multi-armed bandit problem and basic approaches to solving.

As opposed to other RL problems, the bandits problem involves taking action from a _single_ state (i.e. they call this non-associative).

**Incremental average reward**: Can transform the standard expression for average reward into one that supports incremental updates (this is a theme for DP techniques in general).
I.e. $(Q_{n+1} = 1/n)$
