1. Q learning
- R matrix: reward matrix
- Q matrix:
   - represents memory of what agent learned
   - rows: current state of agent
   - columns: possible actions

2. Q matrix update process
- initialized to 0
- Q(state, action) = (1-Gamma)*Q(state, action) + R(state, action) + Gamma * Max[Q(next state, all actions)]

3. Q learning
- agent explores state reaching goal => episode
- each episode serves to train Q matrix

4. Gamma
- discounting factor
- between 0 and 1
- closer to 0 => consider immediate rewards
- closer to 1 => consider future rewards

5. Q learning walkthrough
![unnamed_f097899c83e3472c9b2d3cdbd6b30139](unnamed_f097899c83e3472c9b2d3cdbd6b30139.png)
- R matrix
![unnamed_7b1c228fe4234e3493879c918084b2a0](unnamed_7b1c228fe4234e3493879c918084b2a0.png)
- initial Q matrix
![unnamed_67c65b621d054a22bbb98fdb675cbc9d](unnamed_67c65b621d054a22bbb98fdb675cbc9d.png)
- gamma = 0.8, initial state is 1
- randomly choose next state (3 or 5)
- choose 5 and calculate Q values
Q(1, 5) = R(1, 5) + 0.8 * Max[Q(5, 1), Q(5, 4), Q(5, 5)] = 100 + 0.8 * 0 = 100
- state 5 becomes current state and episode finishes:
![unnamed_4bf4ec2f0a1e4d1e886216c023b4f138](unnamed_4bf4ec2f0a1e4d1e886216c023b4f138.png)
- 3 is chosen as initial state
- randomly choose next state (1, 2, 4)
- choose 1 and calculate Q values 
Q(3, 1) = R(3, 1) + 0.8 * Max[Q(1, 3), Q(1, 5)] = 0 + 0.8 *   Max(0, 100) = 80
- state 1 becomes current state
![unnamed_1342ccab1c6548b8b82178e63e828d01](unnamed_1342ccab1c6548b8b82178e63e828d01.png)
- randomly choose next state (3 or 5)
- choose 5 and calculate Q values
Q(1, 5) = R(1, 5) + 0.8 * Max[Q(5, 1), Q(5, 4), Q(5, 5)] = 100 + 0.8 * 0 = 100
- state 5 becomes current state and episode finishes (Q matrix doesn't change)
- repeat until converge:
![unnamed_2a173600c4c74152bf5211ca6517fc85](unnamed_2a173600c4c74152bf5211ca6517fc85.png)
- normalize Q matrix
![unnamed_eb54d95db8954ed19c1bc33c8ae04c74](unnamed_eb54d95db8954ed19c1bc33c8ae04c74.png)
- following highest value is the best sequence of events

reference:
- Gachon University - Machine learning lecture
- wikipedia - Q learning: <https://en.wikipedia.org/wiki/Q-learning>