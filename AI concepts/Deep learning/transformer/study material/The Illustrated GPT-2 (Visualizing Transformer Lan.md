1. language modeling
- only has one stack of transformer blocks

2. auto regression
- after each token is produced, that token is added to sequence of inputs

3. generating unconditional samples
3.1. input encoding
- look up embedding of word in embedding matrix
- use positional encoding matrix to get input vector
![unnamed_e72d9eb828194930bdce6bff467aeeb7](unnamed_e72d9eb828194930bdce6bff467aeeb7.png)

3.2. move up stack
![unnamed_a509c679fc3444cda1eeb293fedfc3dd](unnamed_a509c679fc3444cda1eeb293fedfc3dd.png)
- self-attention
- FFNN

3.3. model output
- output of top block is multiplied with embedding matrix
![unnamed_b974f435ffb147d5aecc86b69bf59f00](unnamed_b974f435ffb147d5aecc86b69bf59f00.png)




sources:
<https://jalammar.github.io/illustrated-gpt2/>