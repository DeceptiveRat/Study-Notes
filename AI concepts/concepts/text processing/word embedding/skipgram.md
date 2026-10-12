1. skipgram
- uses centre word to predict surrounding words
![unnamed_718d9d8e71cc4df1a8659c6223dc4567](unnamed_718d9d8e71cc4df1a8659c6223dc4567.png)

2. process
- one-hot encoding
- multiply one-hot input vector with W
- input result into hidden layer
- multiply hidden layer output with W'
- Softmax resulting vector
- compare vector with one-hot vectors of answer to get loss
- backpropagation and gradient descent to minimize loss
![unnamed_0ddba38ee2684a48a62ba6a37a6041ba](unnamed_0ddba38ee2684a48a62ba6a37a6041ba.png)

reference:
- 가천대 인공지능입문 Lecture 5 강의 자료 