# Intro

One could imagine a world where different agents have different objective functions, leading to broadly different behavior. In such a world, building AI with a human-aligned objective function could be a fruitful endeavor.

However, different objective functions may also lead to broadly similar instrumental behavior, a possibility known as *instrumental convergence*.

Here we explore, with mathematical rigor, the conditions that lead to instrumental convergence. These conditions may be quite broad.

# Math

We model the universe with a Markov game, $(I, S, A, P, R, \gamma)$, where:

- $I$ is the finite set of agents.
- $S$ is the set of states (assumed finite here).
- $A_i$ is the finite set of actions available to agent $i$ in any state, and $A = \prod_{i \in I} A_i$ is the joint action space.
- $P(s' \mid s, a)$ is the probability of transitioning to state $s'$ from state $s$ under the joint action $a = (a_i)_{i \in I} \in A$.
- $R_i(s)$ is the reward for agent $i$ in state $s$.
- $\gamma \in [0, 1)$ is the discount factor.

A joint policy profile $\pi$ specifies a policy for each agent. $\pi_i(a_i \mid s)$ is the probability of agent $i$ choosing action $a_i$ in state $s$.

When a policy profile $\pi$ is fixed, averaging over the action choices reduces the Markov game to a Markov chain with transition matrix $P^\pi$. Assuming agents choose their actions independently conditional on the current state,

$$
P^\pi(s' \mid s) = \sum_{a \in A} P(s' \mid s, a) \prod_{i \in I} \pi_i(a_i \mid s),
$$

where $\prod_{i \in I} \pi_i(a_i \mid s)$ is the probability of the joint action $a$ under $\pi$.

The value $V_i^\pi(s)$ is the expected cumulative discounted return to agent $i$, starting in state $s$ and following policy profile $\pi$ over an infinite time horizon:

$$
V_i^\pi(s) = R_i(s) + \gamma \sum_{s' \in S} P^\pi(s' \mid s) V_i^\pi(s').
$$

# Thoughts

One interesting observation: let's say you're a society that wants to create one billion happy people and then chill. By itself, the society can do that. But if another society pursues unbounded growth, the former may predict that, to survive and build its chill society, it will also have to be unboundedly competitive. It seems possible that almost everyone converges on the same behavior. Let's call it power-seeking. There certainly are objectives that don't require competing with anyone, like "my goal is to enforce the laws of physics," but objectives that require resources might all lead to a similar power-seeking strategy.

We're concerned about the long term: an infinite time horizon with a discount factor $\gamma$ close to $1$ (a low discount rate).

The answer could be that there are many different goals to optimize for, so evolution will lead to a billion different things, each being good in its own orthogonal niche. To be fair, that is to some extent what we see in the animal world. But then again, maybe all interesting objective functions ultimately depend on the same resources (atoms, etc.). Agents pursuing them may end up competing when they become powerful enough and may not care much about the form those atoms are currently assembled in. Humans are probably already at that point.

I'm not sure of the correct terminology, but maybe power-seeking is an attractor in a Markov game under certain realistic assumptions?

# Related Work

- Stephen M. Omohundro (2008). [The Basic AI Drives](https://selfawaresystems.com/2007/11/30/paper-on-the-basic-ai-drives/).

- Alex Turner, Logan Smith, Rohin Shah, Andrew Critch, and Prasad Tadepalli (2021). [Optimal Policies Tend To Seek Power](https://papers.nips.cc/paper/2021/hash/c26820b8a4c1b3c2aa868d6d57e14a79-Abstract.html). 