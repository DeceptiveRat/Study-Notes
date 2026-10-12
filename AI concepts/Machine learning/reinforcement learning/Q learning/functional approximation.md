1. functional approximation
- Q learning limits:
   - curse of dimensionality: as state and actions increase, number of probable outcomes explodes
   - memory limit
   - sample inefficiency: most states are not visited and thus, empty
- defines function that outputs Q(action value) given state
![unnamed_404c7f1c0f7d426f907e23f6399d5aa6](unnamed_404c7f1c0f7d426f907e23f6399d5aa6.png)
- can infer values of unseen states from surrounding data; similar input gets similar output
- uses deep neural networks to approximate Q learning table

![unnamed_6d4fb392b5c44ebab8155c50b37dbf28](unnamed_6d4fb392b5c44ebab8155c50b37dbf28.png)![unnamed_0ec2441b82f542088748ae37e417610f](unnamed_0ec2441b82f542088748ae37e417610f.png)

reference:
- 가천대 인공지능입문 Lecture 6 강의 자료 