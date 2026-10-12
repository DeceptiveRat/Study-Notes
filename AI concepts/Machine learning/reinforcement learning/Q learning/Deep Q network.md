1. deep Q network(DQN)
- state(image pixel, etc) is input to Q values for each action
- uses CNN
![unnamed_4d20aa42125a487baba1508c98a6d5e6](unnamed_4d20aa42125a487baba1508c98a6d5e6.png)

2. limits
- correlation between data: experience data is strongly linked, violating deep learning assumption of i.i.d.
- moving target: target value comes from same model, changes during learning process
![unnamed_f5e021f6391f4fcd8c1d78f8d036c25a](unnamed_f5e021f6391f4fcd8c1d78f8d036c25a.png)

3. solutions
- experience replay:
   - store experiences and randomly extract from them
   - breaks chronological link between data
![unnamed_88e63cf1b45d4e7098c8e7e2350feea5](unnamed_88e63cf1b45d4e7098c8e7e2350feea5.png)

- target network:
   - separate main network that calculates Q and target network that calculates target
   - target network is updated periodically to suppress volatility
![unnamed_97b78272d121443583ba6ca414d493fb](unnamed_97b78272d121443583ba6ca414d493fb.png)

reference:
- 가천대 인공지능입문 Lecture 6 강의 자료 