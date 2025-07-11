**Parent Topic** : [[01. Deep Learning]]
**Created** : June 17, 2025 | 10:32 AM
**Platform** : #KrishNaik #udemy 

---
# Multi Layered Perceptron/NN [[03.11 MLPs]]
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
- [[04.1 Activation Functions]]

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
        - Apply an **activation function** (e.g., ReLU, sigmoid) to `z` to introduce non-linearity: a=ϕ(z)a = \phi(z)a=ϕ(z).
        
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

# Vanishing Gradient Problem
- This problem is the case when weights not get updated and doesn't move much towards convergence. $W_{old} \approx  W_{new}$  
	- This happens for **Sigmoid** [[04.1 Activation Functions]] since the derivative of sigmoid ranges between (0 , 0.25)

### Perplexity
>just learned about Vanishing Gradient problem, is the problem only for the sigmoid activation function? and check my understading
vanishing gradient is the case when the weighted is not get updated further that is when the w_new is approximately equals to w_old, this happens in case of applying the sigmoid function as the activation function since the derivative of the sigmoid ranges between 0 to 0.25 so this doesn't move the weight much towards convergence in general that's why sigmoid function are generally not useful for deep Neural networks

The vanishing gradient problem is not exclusive to the sigmoid activation function, though sigmoid is particularly prone to it. Your understanding captures the core issue: when gradients become extremely small during backpropagation, weight updates (w_new ≈ w_old) stagnate, hindering convergence. Below is a detailed breakdown:

#### 🔍 Vanishing Gradient Problem: Key Insights

1. **Mechanism**:
    
    - During backpropagation, gradients are computed via the chain rule: $$\frac{\partial \mathcal{L}}{\partial w} = \frac{\partial \mathcal{L}}{\partial a^{(L)}} \cdot \frac{\partial a^{(L)}}{\partial a^{(L-1)}} \cdots \frac{\partial a^{(1)}}{\partial w}$$
        
    - If each partial derivative $$\frac{\partial a^{(i)}}{\partial a^{(i-1)}} \lt 1$$their product shrinks exponentially with depth, causing gradients to "vanish"[1](https://www.kdnuggets.com/2022/02/vanishing-gradient-problem.html)[2](https://www.goml.io/vanishing-gradients-how-activation-functions-can-help-or-hurt/)[8](https://en.wikipedia.org/wiki/Vanishing_gradient_problem).
        
2. **Sigmoid’s Role**:
    
    - The sigmoid derivative σ′(x)=σ(x)(1−σ(x))\sigma'(x) = \sigma(x)(1-\sigma(x))σ′(x)=σ(x)(1−σ(x)) has a **maximum value of 0.25** (at x=0x=0x=0) and approaches 0 for large ∣x∣|x|∣x∣[1](https://www.kdnuggets.com/2022/02/vanishing-gradient-problem.html)[4](https://dev.to/shrsv/a-friendly-step-by-step-tutorial-on-the-vanishing-gradient-problem-5aj0)[7](https://kikaben.com/vanishing-gradient-problem/).
    - Derivative of sigmoid is a special case where the derivative Range is (0, 0.25), this not general for all differentiable function with range [0, 1]  [[11. Sigmoid Differentiation]]
        
    - Example: In a 15-layer network with weights initialized to 0.6, the gradient becomes 0.615≈0.000470.6^{15} \approx 0.000470.615≈0.00047[3](https://www.linkedin.com/pulse/understanding-vanishing-gradient-problem-sigmoid-guide-beach-mba-coctf).
        
    - This small derivative range directly causes weight updates to stall in deep networks[1](https://www.kdnuggets.com/2022/02/vanishing-gradient-problem.html)[3](https://www.linkedin.com/pulse/understanding-vanishing-gradient-problem-sigmoid-guide-beach-mba-coctf)[6](https://datascience.stackexchange.com/questions/113313/if-sigmoid-activation-function-is-prone-to-vanishing-and-exploding-gradients-can).
        
3. **Other Activation Functions**:
    
    - **Tanh**: Derivative peaks at 1.0 (better than sigmoid) but still <1<1<1, leading to vanishing gradients in very deep networks[7](https://kikaben.com/vanishing-gradient-problem/)[8](https://en.wikipedia.org/wiki/Vanishing_gradient_problem).
        
    - **ReLU**: Derivative is 1 for x>0x>0x>0 and 0 for x<0x<0x<0. Avoids vanishing gradients for positive inputs but risks "dead neurons" (zero gradients)[1](https://www.kdnuggets.com/2022/02/vanishing-gradient-problem.html)[3](https://www.linkedin.com/pulse/understanding-vanishing-gradient-problem-sigmoid-guide-beach-mba-coctf).
        
    - **Leaky ReLU**: Fixes dead neurons by allowing a small gradient for x<0x<0x<0 (e.g., 0.01)[1](https://www.kdnuggets.com/2022/02/vanishing-gradient-problem.html)[3](https://www.linkedin.com/pulse/understanding-vanishing-gradient-problem-sigmoid-guide-beach-mba-coctf).
        

## ✅ Your Understanding: Correct with Nuance

- **Correct**: Sigmoid’s small derivative range (0–0.25) is a primary cause of vanishing gradients in deep networks[1](https://www.kdnuggets.com/2022/02/vanishing-gradient-problem.html)[3](https://www.linkedin.com/pulse/understanding-vanishing-gradient-problem-sigmoid-guide-beach-mba-coctf)[4](https://dev.to/shrsv/a-friendly-step-by-step-tutorial-on-the-vanishing-gradient-problem-5aj0).
    
- **Nuance**: The problem isn’t _exclusive_ to sigmoid. Any activation with derivatives <1<1<1 (e.g., tanh) can cause it, but sigmoid is the worst offender[2](https://www.goml.io/vanishing-gradients-how-activation-functions-can-help-or-hurt/)[7](https://kikaben.com/vanishing-gradient-problem/)[8](https://en.wikipedia.org/wiki/Vanishing_gradient_problem).
    
- **Exception**: Using sigmoid **only in the final layer** (e.g., for binary classification) is safe because no further backpropagation occurs[6](https://datascience.stackexchange.com/questions/113313/if-sigmoid-activation-function-is-prone-to-vanishing-and-exploding-gradients-can).
    

## 💡 Solutions

1. **Activation Replacement**:
    
    - Use **ReLU** or **Leaky ReLU** in hidden layers to avoid small derivatives[1](https://www.kdnuggets.com/2022/02/vanishing-gradient-problem.html)[3](https://www.linkedin.com/pulse/understanding-vanishing-gradient-problem-sigmoid-guide-beach-mba-coctf)[4](https://dev.to/shrsv/a-friendly-step-by-step-tutorial-on-the-vanishing-gradient-problem-5aj0).
        
2. **Weight Initialization**:
    
    - Techniques like **Xavier/Glorot** initialization scale weights to preserve gradient magnitudes[1](https://www.kdnuggets.com/2022/02/vanishing-gradient-problem.html)[5](https://studylib.net/doc/27130694/understanding-the-difficulty-of-training-deep-feedforward...).
        
3. **Architectural Adjustments**:
    
    - **Skip connections** (e.g., ResNet) allow gradients to bypass layers[8](https://en.wikipedia.org/wiki/Vanishing_gradient_problem).
        

## 📊 Comparison of Activation Functions

|**Function**|**Derivative Range**|**Vanishing Risk**|
|---|---|---|
|Sigmoid|[0, 0.25]|High|
|Tanh|[0, 1.0]|Moderate|
|ReLU|{0, 1}|Low (for x>0x>0x>0)|
|Leaky ReLU|{α, 1} (α≈0.01)|Very Low|

## 💎 Conclusion

Your understanding aligns with the core issue: sigmoid’s limited derivative range causes gradients to vanish in deep networks, stalling learning[1](https://www.kdnuggets.com/2022/02/vanishing-gradient-problem.html)[3](https://www.linkedin.com/pulse/understanding-vanishing-gradient-problem-sigmoid-guide-beach-mba-coctf)[4](https://dev.to/shrsv/a-friendly-step-by-step-tutorial-on-the-vanishing-gradient-problem-5aj0). However, alternatives like ReLU and weight initialization mitigate this. For shallow networks or final-layer use, sigmoid remains viable[6](https://datascience.stackexchange.com/questions/113313/if-sigmoid-activation-function-is-prone-to-vanishing-and-exploding-gradients-can)[7](https://kikaben.com/vanishing-gradient-problem/).

**Sources**: [1](https://www.kdnuggets.com/2022/02/vanishing-gradient-problem.html)[2](https://www.goml.io/vanishing-gradients-how-activation-functions-can-help-or-hurt/)[3](https://www.linkedin.com/pulse/understanding-vanishing-gradient-problem-sigmoid-guide-beach-mba-coctf)[4](https://dev.to/shrsv/a-friendly-step-by-step-tutorial-on-the-vanishing-gradient-problem-5aj0)[5](https://studylib.net/doc/27130694/understanding-the-difficulty-of-training-deep-feedforward...)[6](https://datascience.stackexchange.com/questions/113313/if-sigmoid-activation-function-is-prone-to-vanishing-and-exploding-gradients-can)[7](https://kikaben.com/vanishing-gradient-problem/)[8](https://en.wikipedia.org/wiki/Vanishing_gradient_problem)

1. [https://www.kdnuggets.com/2022/02/vanishing-gradient-problem.html](https://www.kdnuggets.com/2022/02/vanishing-gradient-problem.html)
2. [https://www.goml.io/vanishing-gradients-how-activation-functions-can-help-or-hurt/](https://www.goml.io/vanishing-gradients-how-activation-functions-can-help-or-hurt/)
3. [https://www.linkedin.com/pulse/understanding-vanishing-gradient-problem-sigmoid-guide-beach-mba-coctf](https://www.linkedin.com/pulse/understanding-vanishing-gradient-problem-sigmoid-guide-beach-mba-coctf)
4. [https://dev.to/shrsv/a-friendly-step-by-step-tutorial-on-the-vanishing-gradient-problem-5aj0](https://dev.to/shrsv/a-friendly-step-by-step-tutorial-on-the-vanishing-gradient-problem-5aj0)
5. [https://studylib.net/doc/27130694/understanding-the-difficulty-of-training-deep-feedforward...](https://studylib.net/doc/27130694/understanding-the-difficulty-of-training-deep-feedforward...)
6. [https://datascience.stackexchange.com/questions/113313/if-sigmoid-activation-function-is-prone-to-vanishing-and-exploding-gradients-can](https://datascience.stackexchange.com/questions/113313/if-sigmoid-activation-function-is-prone-to-vanishing-and-exploding-gradients-can)
7. [https://kikaben.com/vanishing-gradient-problem/](https://kikaben.com/vanishing-gradient-problem/)
8. [https://en.wikipedia.org/wiki/Vanishing_gradient_problem](https://en.wikipedia.org/wiki/Vanishing_gradient_problem)
9. [https://neptune.ai/blog/vanishing-and-exploding-gradients-debugging-monitoring-fixing](https://neptune.ai/blog/vanishing-and-exploding-gradients-debugging-monitoring-fixing)
10. [https://zephyrnet.com/vanishing-gradient-problem-explained/](https://zephyrnet.com/vanishing-gradient-problem-explained/)
11. [https://deepai.org/machine-learning-glossary-and-terms/vanishing-gradient-problem](https://deepai.org/machine-learning-glossary-and-terms/vanishing-gradient-problem)
12. [https://xenoss.io/ai-and-data-glossary/vanishing-gradient](https://xenoss.io/ai-and-data-glossary/vanishing-gradient)
13. [https://www.youtube.com/watch?v=8z3DFk4VxRo](https://www.youtube.com/watch?v=8z3DFk4VxRo)
14. [https://www.kaggle.com/discussions/getting-started/460328](https://www.kaggle.com/discussions/getting-started/460328)
15. [https://stats.stackexchange.com/questions/176794/how-does-rectilinear-activation-function-solve-the-vanishing-gradient-problem-in](https://stats.stackexchange.com/questions/176794/how-does-rectilinear-activation-function-solve-the-vanishing-gradient-problem-in)
16. [https://www.youtube.com/watch?v=QjSnmP9EYlI](https://www.youtube.com/watch?v=QjSnmP9EYlI)
17. [https://www.mathworks.com/help/deeplearning/ug/train-and-apply-multilayer-neural-networks.html](https://www.mathworks.com/help/deeplearning/ug/train-and-apply-multilayer-neural-networks.html)
18. [http://d2l.ai/chapter_multilayer-perceptrons/backprop.html](http://d2l.ai/chapter_multilayer-perceptrons/backprop.html)
19. [https://www.ibm.com/think/topics/backpropagation](https://www.ibm.com/think/topics/backpropagation)
20. [https://scikit-learn.org/stable/modules/neural_networks_supervised.html](https://scikit-learn.org/stable/modules/neural_networks_supervised.html)
21. [https://www.datacamp.com/tutorial/multilayer-perceptrons-in-machine-learning](https://www.datacamp.com/tutorial/multilayer-perceptrons-in-machine-learning)
22. [http://deeplearning.stanford.edu/tutorial/supervised/MultiLayerNeuralNetworks/](http://deeplearning.stanford.edu/tutorial/supervised/MultiLayerNeuralNetworks/)
23. [https://www.shiksha.com/online-courses/articles/understanding-multilayer-perceptron-mlp-neural-networks/](https://www.shiksha.com/online-courses/articles/understanding-multilayer-perceptron-mlp-neural-networks/)
24. [https://en.wikipedia.org/wiki/Multilayer_perceptron](https://en.wikipedia.org/wiki/Multilayer_perceptron)
25. [https://drgupopeengg.org/wp-content/uploads/2023/09/Unit-5-AIML.pdf](https://drgupopeengg.org/wp-content/uploads/2023/09/Unit-5-AIML.pdf)
26. [https://h2o.ai/wiki/weights-and-biases/](https://h2o.ai/wiki/weights-and-biases/)

