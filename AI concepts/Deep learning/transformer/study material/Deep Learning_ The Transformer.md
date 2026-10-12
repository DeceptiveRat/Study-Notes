1. RNN to attention
- signals from early input gets diluted in RNN
=> performance drops
- can use skip-connections that feed every hidden state to every input of decoder
=> need to combine multiple hidden states to single context vector
- sum, average, max, min, etc to turn into a single vector 
=> assumes each hidden state and corresponding input word is equally important
- use weighted sum (e.g. tf-idf weighted sum) to pay more attention to relatively rarer words
=> assumes same hidden states will be of same importance to each output identically
- use dynamic weighting via attention



reference:
<https://medium.com/@b.terryjack/deep-learning-the-transformer-9ae5e9c5a190>