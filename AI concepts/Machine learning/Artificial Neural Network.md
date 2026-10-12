1. Perceptron
![unnamed_76fecd484634484c995660bae0a944ef](unnamed_76fecd484634484c995660bae0a944ef.png)
- simplest first-gen neural network
- algorithm:
   - multiply each input by its weight
   - sum weighted input
   - apply activation function to get output

2. modified Perceptron
![unnamed_02641a994ee24adbaeaa397d8e8866c0](unnamed_02641a994ee24adbaeaa397d8e8866c0.png)
- bias input is added
- can solve OR

![unnamed_5a33111bc7ed4e4799bc19c067d46fca](unnamed_5a33111bc7ed4e4799bc19c067d46fca.png)![unnamed_8523700682ed4c3a8ef273515643a063](unnamed_8523700682ed4c3a8ef273515643a063.png)
- can solve AND
![unnamed_53c408a2c0cb4ef59ba2d7cc47917a34](unnamed_53c408a2c0cb4ef59ba2d7cc47917a34.png)

3. training Perceptrons
- compute error and adjust weights according to error (gradient descent)

4. Perceptron limitations
- can only solve linearly separable problems
![unnamed_acdbaade99b84815acd6902945961f1e](unnamed_acdbaade99b84815acd6902945961f1e.png)

5. Artificial Neural Network (ANN)
- network of perceptrons
![unnamed_d10b0fcc027147d6b891dbf98700e6c1](unnamed_d10b0fcc027147d6b891dbf98700e6c1.png)
- solves problems perceptrons can't - [1]

6. common activation functions
- unit step function
![unnamed_3940ace8bfd249fb975d383880ace40f](unnamed_3940ace8bfd249fb975d383880ace40f.png)
- piecewise linear
![unnamed_8b996902bd15408f804a89420bf5c5ea](unnamed_8b996902bd15408f804a89420bf5c5ea.png)
- Rectified Linear Unit
![unnamed_eb6a745252d44c70b90f2623d4dd36e8](unnamed_eb6a745252d44c70b90f2623d4dd36e8.png)
- Sigmoid
![unnamed_270c00e9eb8b4a87b84dd87121efd3c6](unnamed_270c00e9eb8b4a87b84dd87121efd3c6.png)
- Softmax (hyper-tangent)
![unnamed_fa84181546044638bc0f5474d8ab9b04](unnamed_fa84181546044638bc0f5474d8ab9b04.png)
- Gaussian Function
![unnamed_48d9874169fa48dd9a0bff96923d6f70](unnamed_48d9874169fa48dd9a0bff96923d6f70.png)

7. ANN problems
- not appropriate for precise calculations
- training takes time and data
- determining network architecture is difficult (node count, layer count)
- no explanation for results

8. backpropagation
- calculate error for each neuron in the output layer
- using error, calculate changes to the weights in each neuron in hidden layer
- errors cannot be directly calculated for hidden neurons since they don't have target output => errors are backpropagated

   - Error~B~![unnamed_f8d47073b4584e918440909f92fcc0db](unnamed_f8d47073b4584e918440909f92fcc0db.png) = Output~B~*(1-Output~B~)(Target~B~ - Output~B~)
      - output(1-output) is derivative of sigmoid function
   - W~AB~ := W~AB~ + (Error~B~ * Output~A~)
   - ErrorA = Output~A~ (1 - Output~A~)(Error~B~ W~AB~ + Error~C~ W~AC~)

9. backpropagation demonstration
![unnamed_dcc5f0ee141444a584797379eed03bb4](unnamed_dcc5f0ee141444a584797379eed03bb4.png)
- new weights for output layer:
   - w1+ = w1+(δ x input) = 0.3 + (-0.0406x0.68) = 0.272392
   - w2+ = w2+(δ x input) = 0.9 + (-0.0406x0.6637) = 0.87305
- Errors for the hidden layer:
   - δ1 = δ x w1 = -0.0406 x 0.272392 x (1-o)o = -2.406x10-3
   - δ2= δ x w2 = -0.0406 x 0.87305 x (1-o)o = -7.916x10-3
- New hidden layer weights:
   - w3+=0.1 + (-2.406 x 10-3 x 0.35) = 0.09916
   - w4+ = 0.8 + (-2.406 x 10-3 x 0.9) = 0.7978
   - w5+ = 0.4 + (-7.916 x 10-3 x 0.35) = 0.3972
   - w6+ = 0.6 + (-7.916 x 10-3 x 0.9) = 0.5928
- new error becomes -0.18205

10. types of neural networks
- Perceptron
- feed forward
- deep feed forward
- Radial Basis Function (RBF) network
- Recurrent Neural Network (RNN)
- Long/Short term memory (LSTM)
- Auto-Encoder (AE)
- Convolutional Neural Network (CNN)
- Generative Adversarial Network (GAN)
- Transformer

reference:
- Gachon University - Machine learning lecture

notes
[1]: combine 3 AND perceptrons
![unnamed_4d351d7ad43b48429a7306e17a2df671](unnamed_4d351d7ad43b48429a7306e17a2df671.png)