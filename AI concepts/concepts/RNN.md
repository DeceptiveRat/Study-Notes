1. Recurrent Neural Network(RNN)
- input 1 token at a time to preserve order
- has hidden state as memory space; used to remember previous context
![unnamed_21921e990564444fb962b5a495a95d69](unnamed_21921e990564444fb962b5a495a95d69.png)

2. core concept - memory
- previous tokens are "remembered"

![unnamed_3e17ef7ce47e48d09a996eee52188df6](unnamed_3e17ef7ce47e48d09a996eee52188df6.png)![unnamed_120575fb0a7944c4bb790f0ca527d3fe](unnamed_120575fb0a7944c4bb790f0ca527d3fe.png)

3. limits
- long-term dependency: as the sentence gets longer the first tokens "fade away" from memory
- performance: no parallelization

reference:
- 가천대 인공지능입문 Lecture 5 강의 자료 