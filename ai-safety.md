# Intro

One could imagine a world, where different agents can have different objective functions, and this leads to broadly different behavior among these agents. In such a world,  building AI with a human aligned objective function could be a fruitfuil endevour.

It has been observed however, that different objective functions may lead to broadly similar behavior, which is called *instrumental convergence*.

Here we explore with mathematical rigor, the conditions which lead to instrumental convergence. They appear to be quite broad. 

# Math

We model the universe with a Markov Game, $(I,S,A,P, R, γ)$, where:
- $I$ is the set of agents
- $S$ is the set of states
- $A_i$ is the set of actions available to agent $i$ (in any state)
- $P(s,a,s')$ is the probability to transition to state $s'$ when in $s$, with the joint action by all players $a:A_0 \times A_1 \times A_2 \times ...$, also written as $P(s'|s,a)$.
- $R_i(s)$ is the reward for agent $i$ in state $s$.
- $γ \in [0,1)$ is the dicount.

A joint policy profile (or strategy profile)  defines policies for each agent, so i(s,ai) is the probability of agent i choosing action ai in state s, also written as i(ai|s).
When a policy profile  is fixed, the action choices are eliminated, reducing Markov Game to a Markov Chain with transition matrix P.
P(s'|s)=aP(s'|s,a) ii(ai|s) 
where ii(ai|s) is the probability that the joint action a is being used.

The value V,i(s) is the cumulative return (discounted over time) that agent i in state s is expected to receive in the future (up to infinity) given the policy profile .

V,i(s)=Ri(s)+s'P(s'|s) V,i(s')


# Thoughts

One interesting observation. Let's say your society that want to just create 1B happy people and then chill. By itself they can do that, but if there is another strategy that's going something unbounded, the former strategy will predict that to survive and build their chill society, they'll have to also be unboundedly competitive. It really seems to basically everyone converges on the same behavior. Let's maybe call it power seeking, as you were talking about convergence before. I mean, there certainly are strategies that don't compete with anything, like "my goal is to enforce the laws of physics", but any objective that actually requires resources, seems like it might all collapse into a single "power seeking" strategy.

We're concerned about the long term, i.e. infinite time horizon, tiny discount rate.

The answer could be, well there are many different goals you can optimize for and so evolution will just lead to a billion different things all being good in their own orthogonal nieche. And to be fair, that is to some extend what we see in the animal world. But then again, maybe all interesting objective functions ultimate depend on the same resources (atoms etc) and end up competing when you get powerful enough, and don't care that much about the form that the atoms are currently assembled in. Humans are probably already at that point.

I'm not sure of the correct terminology, but maybe power seeking is an attractor in a Markov Game, under certain realistic assumptions?

# Related Work

(expand to real citations)

- Instrumental Convergence paper
- Those guys that used math to prove that agents want to go to spaces with more potential actions.
