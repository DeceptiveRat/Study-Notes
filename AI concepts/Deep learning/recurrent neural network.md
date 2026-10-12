1. recurrent neural network
- used when using time-series data to make predictions
- take information from prior inputs to influence current input and output
- shares parameters across each layer of the network
- shares same weight parameter within each layer of the network
- uses backpropagation through time (BPTT) algorithm to determine gradients
=> sums errors at each time step

2. advantages
- uses both binary data processing and memory
- can produce one-to-many, many-to-one, or many-to-many outputs

3. disadvantages
- exploding gradient
   - gradient too large
   - creates unstable model
   - weights grow too large
   - solutions:
      - reduce number of hidden layers
- vanishing gradient
   - gradient too small
   - weight becomes 0 => model no longer learning
- long training time
- difficult to use on large datasets