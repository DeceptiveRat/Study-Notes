1. word embeddings
- dense vector representations of text
- uses distributional hypothesis; words that appear in similar contexts have similar meaning
- captures word's meanings
- central technique in NLP
- methods for training:
   - Word2Vec
   - GloVe (Global Vectors for word representation)

2. GloVe
- focuses on creating word co-occurrence matrix over whole corpus
- embeddings relate to probabilities that two words appear together
- e.g.
![unnamed_ac0a4555de794a6d8445c64ac479ab4a](unnamed_ac0a4555de794a6d8445c64ac479ab4a.png)

3. comparing word embeddings
![unnamed_d4614c8b974143d894687c7176b906d0](unnamed_d4614c8b974143d894687c7176b906d0.png)
- related words have similar embeddings
- addition and subtraction can be done to word embeddings
![unnamed_9e3cfa5ee18947d09fbddd6d3c2c4286](unnamed_9e3cfa5ee18947d09fbddd6d3c2c4286.png)

4. generating training dataset
- determine context window size n
- group words in window (context words) as sample

![unnamed_8b7dc6550d5f49fb86976b34b3ee2c62](unnamed_8b7dc6550d5f49fb86976b34b3ee2c62.png)![unnamed_f6388402d7124d288acd45d900d8bd5d](unnamed_f6388402d7124d288acd45d900d8bd5d.png)

5. context word perspectives
- Continuous Bag of Words (CBoW):
   - given context words, predict target word
- SkipGram:
   - given target word, predict context words
	![unnamed_bc96daf3d4f94d95ab14c7f5a50c80d6](unnamed_bc96daf3d4f94d95ab14c7f5a50c80d6.png)

6. training model
- feed input word
![unnamed_5ebb9bb661744963ac0e2e2475c4eae8](unnamed_5ebb9bb661744963ac0e2e2475c4eae8.png)
- get error vector
![unnamed_4c6fe80d845340949b1aeeb9c3e610c1](unnamed_4c6fe80d845340949b1aeeb9c3e610c1.png)
- update model parameters

7. speeding up training process - negative sampling
- to train embedding matrix, change "neighboring word prediction" task into "determine if two given words are neighbors or not" task:
![unnamed_5dcff6df219449e2b94f1c2658be83ed](unnamed_5dcff6df219449e2b94f1c2658be83ed.png)
   - this changes the model from neural network to binary classifier, making it much more simple
   - requires dataset structure to be changed
	 => ![unnamed_33583ab9b9cc45388af0682368429bbf](unnamed_33583ab9b9cc45388af0682368429bbf.png)![unnamed_ad66cf1027454c56814419be91f20c5d](unnamed_ad66cf1027454c56814419be91f20c5d.png)
   - negative target values are required (chosen randomly from vocabulary)
![unnamed_59244f157fab4d3691bdecfa57a4dd36](unnamed_59244f157fab4d3691bdecfa57a4dd36.png)

8. speeding up training process - hierarchical softmax
- use binary tree to store dictionary; reduces search time
- huffman tree; common words toward top of tree
- reduces computation time from linear to logarithmic time
![unnamed_b5cf09e3635a415db6a1ddcd9d261439](unnamed_b5cf09e3635a415db6a1ddcd9d261439.png)

reference:
- Gachon University - Machine learning lecture
- 가천대 인공지능입문 Lecture 5 강의 자료 