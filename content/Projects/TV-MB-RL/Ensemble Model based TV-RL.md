# Ensemble Model based TV-RL
## Motivation
In non stationary environment RL approaches need to adapt to new plant parameters. The  context can be inferred by the past transitions. Given discrete system changes we can use Baysian context length inference to compute a probability distribution over the context length. We need a model to compute this distribution.
MBRL also uses a model to generate new data. The first question is if we can combine Dyna Style MBRL with nonstationary RL. The second question is if we use simmilar ideas as in MACURA to stop model unrolls not only for different state spaces areas but also for different model believes. 

## Details
### Problem setup
Normal RL setup (like mujoco halfcheetah) but the env (or later reward function) can change at any point in time (also while training)

Env ideas:
- halfcheetah with changing ground
- halfcheetah with changing target velocity and direction
### Main idea
- Combine Dyna style MBRL with non stationary environments with picewise stationary context $c_t$.
	- First: generate context vector based on past transitions $p(c_t| \tau_{t-G_t:t})$ to condition model $p(s_{t+1}|s_t, a_t, c_t)$, value network and policy.
	- Use the model (used in dyna style MBRL) to generate context length believe $p(G_t| \tau_{1:t})$
- Keep track of a distribution of possible context vectors $p(c_t)$. Sample from this  adapt the policy to unseen plant parameter.
- Use MACURA style ideas to stop unrolls for context believes that the model is uncertain about.


### Open questions
- When we use sampled context encodings to generate data to train e.g. SAC, how can we make sure that we get this encoding if we encounter it in the real world aka this transitions.
- Which context encoding ist best? For markov assumption or without.
	- CNP like
	- Graph based
	- RNN
		- e.g. with autoencoding like in [[chenAdaptiveDeepRL2022]]
	- 
## Related work
- Continuous Meta-Learning without tasks
- An Adaptive Deep RL Method for Non-Stationary Environments with Piecewise Stable context
- Trust the Model Where It Trusts Itself -- Model-Based Actor-Critic with Uncertainty-Aware Rollout Adaption
- 

## Project Outline

1. Implement MBRL
2. Implement non stationary enviroments
3. Combine MBRL with baysian context length belive
	1. Sample already visited contexts
4. Find way to sample new contexts
5. Combine with MACURA
6. Evaluation
	1. Compare impact of context extrapolation
	2. Compare impact of stoping if uncertain

## References
