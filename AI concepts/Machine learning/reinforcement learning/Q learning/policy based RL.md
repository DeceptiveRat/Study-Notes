1. policy based RL
- DQN is limited to finite and discrete action space
- uses policy network that inputs state and outputs probability distribution of action
   - 𝜋~𝜃~(a|s): probability of a given s
![unnamed_110392678838470eb93552d2fde57217](unnamed_110392678838470eb93552d2fde57217.png)

2. output format
- continuous: print mean and standard deviation and sample action from resulting distribution
- discrete: use Softmax to get probability distribution of actions
![unnamed_b7b5d78fb9ac4e07b1e0841dc525c8af](unnamed_b7b5d78fb9ac4e07b1e0841dc525c8af.png)

3. policy gradient learning
- unlike cross entropy, try action, see reward, then fix probability
- objective function should maximize reward, not minimize loss
![unnamed_3e0171d3f9b04ebb9bc3f41de1d3fb66](unnamed_3e0171d3f9b04ebb9bc3f41de1d3fb66.png)

using log-derivative trick 

![unnamed_4d7fd9e2a60e46efbabf4478245a9ff6](unnamed_4d7fd9e2a60e46efbabf4478245a9ff6.png)![unnamed_1829893a028d4afa9bdf588b7a909e34](unnamed_1829893a028d4afa9bdf588b7a909e34.png)

- single episode is used to collect sample data, which is used to approximate ideal gradient update
![unnamed_9e02b4a11bed4ab9aaa2c05dc3899676](unnamed_9e02b4a11bed4ab9aaa2c05dc3899676.png)

4. limits
- update delay: episode must finish for update to be applied
- high variance: learning is highly unstable and convergence is slow

5. solution - actor-critic structure
- actor(policy network): inputs current state and outputs action probability distribution (PG)
- critic(Q value network): evaluates what current action is worth (DQN)

reference:
- 가천대 인공지능입문 Lecture 6 강의 자료 