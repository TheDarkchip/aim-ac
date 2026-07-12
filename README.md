# AIM-AC

**AIM-AC (Action-Independent Magnitude Control for Fully Streaming Actor–Critic)**
is a research proposal for stabilizing policy updates in fully streaming
reinforcement learning.

Streaming actor–critic methods update immediately after each transition, with
no replay buffer or minibatch. Recent intentional-update methods control an
update using the score norm of the action that happened to be sampled. Because
that normalizer changes with the sampled action, it can reweight the policy
gradient—and, in simple cases, reverse its expected direction.

AIM-AC instead computes one state-local sensitivity scale from the policy
scores of **all discrete actions**. Every possible sampled action therefore
shares the same normalizer. The proposed update aims to:

- preserve the conditional expected policy-gradient direction;
- bound or normalize the local change in action log-probabilities;
- retain the strict streaming protocol of one actor and one critic update per
  transition; and
- require no additional environment interactions or stored experience.

The proposal studies two variants: **AIM-RMS**, which uses a policy-weighted
root-mean-square sensitivity, and **AIM-Max**, which uses the largest
cross-action sensitivity for a more conservative local bound. Exact bandit
diagnostics and discrete-action classic-control experiments are proposed to
compare their direction preservation, stability, learning speed, and overhead.

See the compiled [`proposal.pdf`](output/pdf/proposal.pdf) for the complete
formulation, analysis, experimental plan, and references.
