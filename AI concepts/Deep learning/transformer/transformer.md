1. transformer

2. core concept - self attention
- attention compares target word to translate with input sentence
- compares words within input sentence to see how they relate
![unnamed_4169c4a185394d44bae02cd1fcb88c04](unnamed_4169c4a185394d44bae02cd1fcb88c04.png)

3. core concept - parallelization 
- unlike RNN, can process all words in sentence in parallel
- allows model to be much quicker

4. core concept - positional encoding
- used to keep order between words
- using simple indices means values can increase indefinitely, causing confusion in model
- normalizing to values between 0 and N changes distance between words, not allowing it to learn absolute distances 
- using sin and cos:
   - keeps values between -1 and 1 (bounded)
   - due to the cyclic nature, even a new position is not confusing for the model (extrapolation)
   - x + k encoding is a linear transformation of x encoding; allows model to learn relationship easily 
   - combining different frequencies in a single vector allows each position to have a unique "fingerprint"


![unnamed_d73961c3123c407c9f567bdd97a25818](unnamed_d73961c3123c407c9f567bdd97a25818.png)![unnamed_4683e2d4968a4c6b99ac605eeed8a98e](unnamed_4683e2d4968a4c6b99ac605eeed8a98e.png)


reference:
- 가천대 인공지능입문 Lecture 5 강의 자료 