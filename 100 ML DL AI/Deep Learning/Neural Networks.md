**Parent Topic** : [[Deep Learning]]
**Created** : June 15, 2025 | 10:23 AM
**Platform** : #KrishNaik #udemy 

---
- Our main aim in [[Deep Learning]] is to mimic the Human Brain.
- In the whole network, each node are called as *Neurons*
- NN consists multiple layers on interconnected nodes that collab together to process the input data , in the full network data travels through layers where each node performs some non-linear transformation allowing the model to learn 
- all hidden layers processes the data

## [[Perceptron]]
- Artificial Neuron or Single Neural Network Unit
	- having only one node
- *Single Layered* NN
	- Can solve Binary Classification problem
	- Linear Classifier
- Steps / Structure:
	1. Input Layer
	2. Initialize *Weights*
	3. We add Bias
	4. The main Hidden Layer (Also Called [[Neuron]]) 
		1. Step 1. $Z = \sum{X_i W_i} + b$
		2. Step 2. **Activation Function** $Act(Z)$ to apply some transformation
	5. Then according to the output we calculate Error / Loss
	6. According to the Loss we keep updating the *Weights* to optimize the model
	- 
## [[Types of Neural Networks]]

# ANN is the General term for NNs
***Yes,*** Feedforward Neural Networks (FNN), Convolutional Neural Networks (CNN), Recurrent Neural Networks (RNN), and perceptron are all types of Artificial Neural Networks (ANNs) in general[1](https://www.coursera.org/in/articles/types-of-neural-networks)[2](https://en.wikipedia.org/wiki/Types_of_artificial_neural_networks)[4](https://www.techtarget.com/searchenterpriseai/definition/neural-network)[6](https://www.linkedin.com/pulse/types-artificial-neural-networks-ann-sayed-qasim).

**Explanation:**

- **Artificial Neural Network (ANN)** is the broad term for computational models inspired by the human brain, consisting of interconnected nodes (neurons) organized in layers[2](https://en.wikipedia.org/wiki/Types_of_artificial_neural_networks)[4](https://www.techtarget.com/searchenterpriseai/definition/neural-network).
    
- **Perceptron** is the simplest form of ANN, designed for binary classification[4](https://www.techtarget.com/searchenterpriseai/definition/neural-network).
    
- **Feedforward Neural Network (FNN)** is a basic ANN where data flows in one direction from input to output, possibly through hidden layers[5](https://www.spiceworks.com/tech/artificial-intelligence/articles/what-is-a-neural-network/)[6](https://www.linkedin.com/pulse/types-artificial-neural-networks-ann-sayed-qasim).
    
- **Convolutional Neural Network (CNN)** is a specialized ANN for processing data with a grid-like topology, such as images[1](https://www.coursera.org/in/articles/types-of-neural-networks)[4](https://www.techtarget.com/searchenterpriseai/definition/neural-network)[5](https://www.spiceworks.com/tech/artificial-intelligence/articles/what-is-a-neural-network/).
    
- **Recurrent Neural Network (RNN)** is an ANN designed for sequential data, with connections that form cycles to allow information persistence[1](https://www.coursera.org/in/articles/types-of-neural-networks)[2](https://en.wikipedia.org/wiki/Types_of_artificial_neural_networks).
    

All these are considered subtypes or architectures under the umbrella of ANNs[2](https://en.wikipedia.org/wiki/Types_of_artificial_neural_networks)[4](https://www.techtarget.com/searchenterpriseai/definition/neural-network)[6](https://www.linkedin.com/pulse/types-artificial-neural-networks-ann-sayed-qasim).

1. [https://www.coursera.org/in/articles/types-of-neural-networks](https://www.coursera.org/in/articles/types-of-neural-networks)
2. [https://en.wikipedia.org/wiki/Types_of_artificial_neural_networks](https://en.wikipedia.org/wiki/Types_of_artificial_neural_networks)
3. [https://vajiramandravi.com/upsc-exam/artificial-neural-network/](https://vajiramandravi.com/upsc-exam/artificial-neural-network/)
4. [https://www.techtarget.com/searchenterpriseai/definition/neural-network](https://www.techtarget.com/searchenterpriseai/definition/neural-network)
5. [https://www.spiceworks.com/tech/artificial-intelligence/articles/what-is-a-neural-network/](https://www.spiceworks.com/tech/artificial-intelligence/articles/what-is-a-neural-network/)
6. [https://www.linkedin.com/pulse/types-artificial-neural-networks-ann-sayed-qasim](https://www.linkedin.com/pulse/types-artificial-neural-networks-ann-sayed-qasim)
7. [http://uc-r.github.io/ann_classification](http://uc-r.github.io/ann_classification)