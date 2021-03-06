# Deep Neural Network for MNIST classification dataset.

This code is an improved version of the Nielsen's implementation from 'http://neuralnetworksanddeeplearning.com/chap1.html'



Requirements :
- the activation function from the last layer must take positive values
- the activation functions and loss function must be given with the name from 'Activations_Module.py', 'Loss_Module.py'
- the optimizer must be chosen with the name from 'Optimizers_Module.py'



Activation functions : 
- identity
- sigmoid
- tanh
- atan
- softplus



Loss functions :
- quadratic
- cross entropy
- Kullback
- Kullback Leibler
- Hellinger



Optimizers :
- SGD
- Momentum (Polyak)
- Nesterov
- RMSprop
- Adam
- Adadelta



Remarks :
- the weights are generated with the Truncated Normal Distribution as in :
'https://www.python-course.eu/neural_networks_with_python_numpy.php'
- a list of activation functions (and the derivates) is given in :
'https://towardsdatascience.com/activation-functions-neural-networks-1cbd9f8d91d6'
- a list of loss functions (and the gradient with respec to the activation function from the last layer) can be found in : 'https://stats.stackexchange.com/questions/154879/a-list-of-cost-functions-used-in-neural-networks-alongside-applications'
- for the understanding of the optimizers, follow :
'https://github.com/HIPS/autograd/blob/master/autograd/misc/optimizers.py'
- the weights are part of the 'params' list, i.e. the weights are self.params[0] and the biases are self.params[1]
- the gradient and error parameters are local variables, and are not inherent parameters of the DNN class
- each optimizer has its own parameters ... see the function 'initialize_optimizer'
- in the current implementation, the 0 index is for the weights and the 1 index is for the biases (for the 'params'-type variables)
- the NaG backpropagation is different from other optimizers, since we use updated values of the weights and biases under the gradient
- one can use different activation functions between layers
- the velocity for the 'Momentum' and 'NaG' optimizers is kept during the epochs. This means that the velocity is not set to zero at the start of each epoch
- since I made each optimizer to be simple enough, the parameters are lists of weights numpy array and biases numpy array. Each of them contain numpy arrays (weights and biases, respectively) for each layer. For adaptive optimizers like RMSprop the energy that is defined iteratively must take the value 0 for each weight and each bias of a given layer



Future implementation :
- learning rate decay (as in Keras)
- L2 regularization
- modifying NaG (Nesterov) and Momentum (Polyak) so that they depend on the current iteration, i.e. gamma is a function of iterations or epochs
- implement cross-validation
- implement dropout technique
