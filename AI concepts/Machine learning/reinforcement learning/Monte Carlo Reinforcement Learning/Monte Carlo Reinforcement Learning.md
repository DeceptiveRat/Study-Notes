1. Monte Carlo (MC) method
- apply repeated random sampling to obtain numerical results for difficult/impossible problems
- general approach:
   - define domain of possible inputs
   - generate inputs randomly from a probability distribution over domain
   - perform deterministic computation on inputs
   - aggregate results
![unnamed_99c19e2c563f472ba9f385d7d0408c94](unnamed_99c19e2c563f472ba9f385d7d0408c94.png)

2. MC RL
- learns from episode of experience
- model-free (no knowledge of MDP transitions/rewards)
- learns from complete episodes 
- uses simple idea: value function = empirical mean return

3. MC RL definition
- sample episodes from experience under π
- when visiting state, increase visit counter and calculate mean
![unnamed_f5a3499e4b474a4e971b997d7551e1a0](unnamed_f5a3499e4b474a4e971b997d7551e1a0.png) - [1]
- also possible to use exponential moving average
![unnamed_0ce7f49916644a8e8bfb2a8979b5cd12](unnamed_0ce7f49916644a8e8bfb2a8979b5cd12.png)
- can balance exploration and exploitation

4. MC RL policy iteration
- greedily improving policy over V(s) requires model:
![unnamed_32da9f6ddeae41958768eb3b1d89022b](unnamed_32da9f6ddeae41958768eb3b1d89022b.png)
- greedy policy improvement over Q(s, a) is model-free: - [2]
![unnamed_7875439d7e184cc3a85e0ecabc201707](unnamed_7875439d7e184cc3a85e0ecabc201707.png)

5. Q learning
![unnamed_efc499d127e542f0bc4ef13d4ddb8b85](unnamed_efc499d127e542f0bc4ef13d4ddb8b85.png)
stuck at local minima

6. ε-greedy exploration
- simple idea to avoid local minima:
   - choose random action with probability ε (epsilon)
   - choose action greedily with probability 1-ε
- gives updated policy:
![unnamed_358e9f0d02cc4fe6b8e2130c4dfd1cd4](unnamed_358e9f0d02cc4fe6b8e2130c4dfd1cd4.png)

7. Greedy at the Limit with Infinite Exploration (GLIE)
- define schedule for exploration so two conditions are met:
   - continue to explore everything
	![unnamed_a6b80f3206864f0f84d71bb6be60787c](unnamed_a6b80f3206864f0f84d71bb6be60787c.png)
   - policy converges on a greedy policy
	![unnamed_66a3f953c53944cd9de82d565aaf7619](unnamed_66a3f953c53944cd9de82d565aaf7619.png)

reference:
- <https://www.google.com/url?sa=t&source=web&rct=j&opi=89978449&url=https://cwkx.github.io/data/teaching/dl-and-rl/rl-lecture5.pdf&ved=2ahUKEwi99cWsoaiQAxWCsVYBHQtuNhwQFnoECB4QAQ&usg=AOvVaw1OS2PUtCnzYGNTCOr3Ecks>

notes:
[1]: 

x~k~ = G~t~![unnamed_5c9eb766ff4546fca1276e18863a78c9](unnamed_5c9eb766ff4546fca1276e18863a78c9.png): return
μ~k-1~ = V(S~t~): average(expected value) of returns

[2]:
V(s) only tells you how good it is to be in s following π
=> to decide which action to take, you need to look ahead: 
![unnamed_02d3d4f5e5844c79ae75b9237501a048](unnamed_02d3d4f5e5844c79ae75b9237501a048.png)
model of environment, p(s', r|s, a) is needed

Q(s, a) tells you how good it is to take a in s then follow π
=> already has expected future return of a in s: 
![unnamed_4aa480c97dd24524b65053c7a2ded38a](unnamed_4aa480c97dd24524b65053c7a2ded38a.png)
you already know how good each action is (on average), because it is implicitly encoded
despite environment model being in Bellman equation, it is not needed - [3]

[3]: 
instead of the model, samples are used to approximate expectation