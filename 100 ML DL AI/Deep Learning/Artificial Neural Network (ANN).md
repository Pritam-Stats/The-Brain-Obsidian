**Parent Topic** : [[]]
**Created** : June 17, 2025 | 10:32 AM
**Platform** : #KrishNaik #udemy 

---
# Multi Layered Perceptron/NN [[MLPs]]
#### Main topics
- [[Forward Propagation]]
	- Input > Assign weights and bias > First Layer (With multiple neurons) connected with weights > output of the neurons form L1 gets new weights and given as input to the neurons of L2 then Calculate Loss > update the weights in *Backward* to Optimize the Loss Function.
- [[Backward Propagation]]
	- Main research area of [[Geoffrey Hinton]]
- Loss Function
	- Difference b/w loss and cost, loss in for every value $(y_i - \hat{y_i})^2$ and loss the total as $\sum_i{(y_i - \hat{y_i})^2}$
- Optimizers
	- In DL we keep optimize the Loss function by updating the weights *similar process how we optimize the gradient descent  for linear regression*
	- $$W_{new} = W_{old} - \eta \frac{dL}{dw} \quad; \eta \text{ is the learning rate and {L} is the Loss}$$
	- Now we update the weights from the *backward* and we expand the derivative based with the output of each neuron
	- And the process is same as when the slope is negative we will increase the weight and vice-versa
- [[Activation Functions]]

##### Recall
- Each neuron has the same mechanisms which is Calculating `Z` then applying the activation function according to the dataset or problem
So here in MLPs we have multiple neurons. Also called the hidden layers

---
## **Step-by-Step Breakdown of Multi-Layer Neural Networks** - 17th June

## 1. **Forward Pass**

- **Input Layer:** Raw data (e.g., images, text) is fed into the input layer.
    
- **Weights and Bias:** Each connection between neurons in adjacent layers has a **weight** (strength of the connection), and each neuron (except input neurons) has a **bias** (an offset term).
    
- **Layer Computations (L1, L2, etc.):**
    
    - For each neuron in a hidden/output layer:
        
        - Compute the **weighted sum**: $z=(inputs×weights)+biasz = (\text{inputs} \times \text{weights}) + \text{bias}$$z=(inputs×weights)+bias.$
            
        - Apply an **activation function** (e.g., ReLU, sigmoid) to zzz to introduce non-linearity: a=ϕ(z)a = \phi(z)a=ϕ(z).
            
    - Outputs of one layer become inputs to the next layer.
        
- **Final Output:** The last layer produces predictions (e.g., class probabilities).
    

## 2. **Loss Calculation**

- Compare the network’s output to the true target values using a **loss function** (e.g., mean squared error, cross-entropy).
    
- Example: Loss=1N∑(ytrue−ypred)2\text{Loss} = \frac{1}{N} \sum (y_{\text{true}} - y_{\text{pred}})^2Loss=N1∑(ytrue−ypred)2.
    

## 3. **Backward Pass (Backpropagation)**

- **Gradient Calculation:** Use the chain rule to compute gradients of the loss with respect to **all weights and biases** (starting from the output layer backward).
    
    - This identifies how much each weight/bias contributed to the error.
        
- **Weight Update:** Adjust weights and biases using an **optimization algorithm** (e.g., stochastic gradient descent) to minimize the loss:
    
    - New Weight=Old Weight−η⋅∂Loss∂Weight\text{New Weight} = \text{Old Weight} - \eta \cdot \frac{\partial \text{Loss}}{\partial \text{Weight}}New Weight=Old Weight−η⋅∂Weight∂Loss, where η\etaη is the learning rate.
        

---

## **Key Clarifications**

- **Activation Functions:** Essential for modeling non-linear relationships (e.g., ReLU in hidden layers, softmax/sigmoid in output layers).
    
- **Backpropagation ≠ Weight Update:** Backpropagation computes gradients; optimization algorithms (e.g., Adam, SGD) use these gradients to update weights.
    
- **Batch vs. Stochastic Training:** Modern networks often process data in **batches** (subsets of data) for efficiency.
    

---

## **Example Architecture (Simplified)**

|Layer Type|Neurons|Activation|Parameters|
|---|---|---|---|
|Input|3|None|Weights: 3×4|
|Hidden (L1)|4|ReLU|Weights: 4×2, Bias: 4|
|Output (L2)|2|Softmax|Weights: 2×2, Bias: 2|

---

## **Conclusion**

Yes, your summary captures the core process! The critical additions are:

1. **Non-linear activation functions** between layers.
    
2. **Explicit gradient calculation** (not just "updating weights in backward").
    
3. The role of **optimization algorithms** in weight updates.
    

This process allows neural networks to learn complex patterns in data[1](https://www.mathworks.com/help/deeplearning/ug/train-and-apply-multilayer-neural-networks.html)[2](http://d2l.ai/chapter_multilayer-perceptrons/backprop.html)[5](https://www.datacamp.com/tutorial/multilayer-perceptrons-in-machine-learning).

1. [https://www.mathworks.com/help/deeplearning/ug/train-and-apply-multilayer-neural-networks.html](https://www.mathworks.com/help/deeplearning/ug/train-and-apply-multilayer-neural-networks.html)
2. [http://d2l.ai/chapter_multilayer-perceptrons/backprop.html](http://d2l.ai/chapter_multilayer-perceptrons/backprop.html)
3. [https://www.ibm.com/think/topics/backpropagation](https://www.ibm.com/think/topics/backpropagation)
4. [https://scikit-learn.org/stable/modules/neural_networks_supervised.html](https://scikit-learn.org/stable/modules/neural_networks_supervised.html)
5. [https://www.datacamp.com/tutorial/multilayer-perceptrons-in-machine-learning](https://www.datacamp.com/tutorial/multilayer-perceptrons-in-machine-learning)
6. [http://deeplearning.stanford.edu/tutorial/supervised/MultiLayerNeuralNetworks/](http://deeplearning.stanford.edu/tutorial/supervised/MultiLayerNeuralNetworks/)
7. [https://www.shiksha.com/online-courses/articles/understanding-multilayer-perceptron-mlp-neural-networks/](https://www.shiksha.com/online-courses/articles/understanding-multilayer-perceptron-mlp-neural-networks/)
8. [https://en.wikipedia.org/wiki/Multilayer_perceptron](https://en.wikipedia.org/wiki/Multilayer_perceptron)
9. [https://drgupopeengg.org/wp-content/uploads/2023/09/Unit-5-AIML.pdf](https://drgupopeengg.org/wp-content/uploads/2023/09/Unit-5-AIML.pdf)
10. [https://h2o.ai/wiki/weights-and-biases/](https://h2o.ai/wiki/weights-and-biases/)

