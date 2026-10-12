1. word2vec training process
- preprocess text corpus
- generate training dataset
- train embedding matrix
- train language model 
- detailed:
   - tokenize corpus
   - set hidden layer size (embedding dimension)
   - use sliding window to create dataset
   - one-hot encode all tokens
   - input one-hot vectors are multiplied with W
   - CBOW uses average of resulting vectors as input of hidden layer
   - output of hidden layer is multiplied with W' and put through Softmax
   - using resulting probability vector, get loss
   - backpropagation and gradient descent to train
   - discard W' and use W as word embedding matrix
![unnamed_d18436822d984421b5ef642dcfa43c6b](unnamed_d18436822d984421b5ef642dcfa43c6b.png)

2. train embedding matrix
- initialize embedding and context matrix with random values
![unnamed_dc2437d219f14df69d50a45865003781](unnamed_dc2437d219f14df69d50a45865003781.png)
- choose one positive sample and it's associated negative samples
![unnamed_20c15ecf1e1047978e1d04a5ed0b6b41](unnamed_20c15ecf1e1047978e1d04a5ed0b6b41.png)
- for input word, look up embedding in embedding matrix
- for context word, look up context matrix
![unnamed_48f38be19f81455c9233ee9c79a71aac](unnamed_48f38be19f81455c9233ee9c79a71aac.png)
- dot product input embedding with each context embedding to calculate similarity
![unnamed_b31a7dc4b2994740822533a698b9a0dc](unnamed_b31a7dc4b2994740822533a698b9a0dc.png)
- map values to 0~1
![unnamed_25a4c320d8f740688cd75c58208882ee](unnamed_25a4c320d8f740688cd75c58208882ee.png)
- subtract from target value to get error
![unnamed_078ec5f8107a47a08a3be9a812b5e797](unnamed_078ec5f8107a47a08a3be9a812b5e797.png)
- adjust embeddings to make errors smaller
- after multiple iterations and training finishes, discard context matrix

3. word2vec hyperparameters
- embedding size:
   - gpt-3 uses about 50000
- context window size:
   - 2~15: high similarity indicates interchangeable words
   - 15~50: high similarity indicates relatedness of words
   - 5 is default for Gensim
- number of negative samples:
   - 5~20 suggested

reference:
- Gachon University - Machine learning lecture
- 가천대 인공지능입문 Lecture 5 강의 자료 