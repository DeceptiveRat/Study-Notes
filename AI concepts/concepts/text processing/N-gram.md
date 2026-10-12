1. n-gram
- sequence of n words
- use:
   - predict next word
   - correct spelling
- needs a very large sample of sentences (corpus)
- N-gram model:
P(w~1~)*P(w~2~|w~1~)*P(w~3~|w~2~, w~1~)*...*P(w~n~|w~n-1~, w~n-2~, ..., w~n-N~)
- uses the chain rule:
   - joint probability can be expressed in terms of conditional probability: P(X,Y) = P(X|Y)*P(Y)
   - e.g. P("Today is a sunny day") = P("Today")*P("is" | "Today")*P("a" | "is","Today")*...*P("day" | "sunny","a")
- using Markov assumption, the probability of a sentence is reduced to the probabilities of bi-grams

reference:
- Gachon University - Machine learning lecture