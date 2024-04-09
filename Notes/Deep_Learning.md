# Deep Learning 🧠

"Universal Function Approximator"

---

## 1) Prepare Input Data 🌊

#### Preparing Training Data

- Pre-Processing: Missing Values, Categorical Values, Feature Selection, Scaling

- Splitting the Data

  1. Training Data --> For training the network
  2. Validation Data --> As feedback during training
  3. Test Data --> For the final test

- [Cross-validation](https://www.youtube.com/watch?v=fSytzGwwBVw) --> Shuffling the training data

#### Modifying Input Data

- Rotation of images, Grayscale, etc.

---

## 2) Choose Network Architecture 🏛

_When starting a new project, try to reuse a model that already works._

#### Model Type

- Machine Learning --> Few input data
- Deep Learning --> Lots of input data

#### Deep Learning Models

- ANN --> Numbers, Pattern Recognition
- LSTM --> Time-Series, Natural Language Processing (NLP)
- CNN --> Images, Time-Series Data
- Recurrent Neural Network --> Sequences, Temporal Data
- Generative Adversarial Network --> Synthetic Data, Image Generation
- Autoencoder --> Data Reconstruction, Dimensionality Reduction

#### Layer Architecture

_Number of nodes based on the complexity of the problem to solve._

##### Input Layer

- Convolutional Layer --> Feature extraction from images
- Fully connected Layer (Dense) --> Completely connected

##### Hidden Layer

- The actual learning takes place in the hidden layer

##### Output Layer:

- **Softmax** --> At the end, normalizes output range to "0-1" (-> "percentages")
  - **Logits** --> Input data for Softmax, current weights of the network

#### Special Features

- [Long Short Term Memory](https://de.wikipedia.org/wiki/Long_short-term_memory) --> Store information over long time intervals, sequence data
- [Attention](<https://en.wikipedia.org/wiki/Attention_(machine_learning)>) --> Focus on individual features

---

## 3) Adjust Hyperparameters 🔗

#### Initial weights (w)

- Small, random values (without symmetry)
- [Xavier initialization](https://kuenstliche-intelligenz-in-a-nutshell.at/2020/04/04/xavier-initialization-neural-nets.html) —> Adjusting weights

#### Batch-Size

- [Mini-Batches](https://towardsdatascience.com/batch-mini-batch-stochastic-gradient-descent-7a62ecba642a) --> Faster learning
- **Batch normalization** --> Normalizing values before each batch

#### Learning Rate

- Too large: Pendulum effects and overshooting during gradient descent
- Too small: Limits the speed of gradient descent, too small steps

#### Activation Function

- **Sigmoid** --> Binary Classification (0,1)
- **Leaky Relu**--> Better choice for deep networks

#### Loss-Function

_How strong does the predictedvalue deviate from the truth?_

- **Mean Squared Error** --> For linear models
- **Logarithmic Loss** --> For smoothing sigmoid functions
- **Cross Entropy** —> For classification, works well with Softmax

#### Regularization (of the Loss Function)

- L1-Norm
- L2-Norm

---

## 4) Training the Network 🏋🏽‍♂️

#### Updating Weights

- Feedforward --> Information is passed through the network
- Backpropagation --> Adjusting weights with the loss function

#### Choosing an Optimizer

_Start with the most popular optimizer for the type of problem at hand._

- Gradient Descent: Convex, Continuous, Differentiable
  - Always goes against zero, step size proportional
  - Use squared error because it is more derivable and has a steeper rise
- Momentum
- RMSprop
- SGD
- ADAM
- NADAM

#### Hyperparameter Tuning

- AutoGrad
- Bayes
- Optuna

---

## 5) Testing Predictions 🔍

- Check prediction of the test data set
  - Accuracy, F1-Score, Mean Squared Error
- Cross-validation --> k training datasets, estimating robustness and generalizability
- Analysis of misclassifications

---

## 6) Optimizing the Network 🏎️

- Adjusting the learning rate
- Adjusting the shape of the network (Layers, Nodes, etc.)
- Number of training runs
- Changing the Batch-Sizes
- Adjust preprocessing + distribution of training data

---

## Phenomenons 🌀

- Overfitting ⬆️
- Underfitting ⬇️
- Vanishing Gradients 🌬
- Exploding Gradients 💥
- Numerical Instability 🌪
- Dead Neurons 💀
- Degradation 🍂

---

# Additional Information

### Batch-Size

```text
The batch size governs the training speed
- Shouldn't be used to directly tune the validation set performance.
- Often, the ideal batch size will be the largest batch size supported by the available hardware
- Smaller batch sizes introduce more noise into the training algorithm due to sample variance, and this noise can have a regularizing effect.
- Larger batch sizes can be more prone to overfitting and may require stronger regularization and/or additional regularization techniques.
```

### Learning Rate

```
We need it so that the algorithm doesn't always adjust completely to the last training example, thus obtaining a tendency in the right direction

- With several epochs, one can possibly afford smaller learning rates
```

### Regularization

```
To prevent overfitting and improve the generalization capability of the network
```

### Backpropagation

```
- The error is divided proportionally according to the size of the weights of the preceding nodes
    - High weights contribute more to the error
- Deeper layers also get a proportional share of the error

Why do we need calculus here?
- To determine the change factor for the weights using the error per node
- Only the nodes connected are decisive for the gradient

How do we use the divided errors for the weights?
- The errors are divided, and then gradient descent is performed for each node
```

### Activation Function

```text
Essential nonlinearity, allows a neural optimization process to assume different optimal parameter configurations

- To avoid vanishingly small or excessively high gradients during backpropagation, activation functions are usually continuously differentiable
- There are several types to counteract problems like vanishing gradients
- Scaling / Normalization: Input data in the effective range of the activation functions
- Avoid saturation in neurons: Extreme values like `0` and `1` --> Loss of gradient information

With some activation functions, not all values can be reached
- Thus, the gradients continuously shift if the target values are significantly higher than the activation function can reach. Solution: Normalize input data!
```

### Loss Function

```text
The loss function takes the output of the entire neural network with all "Weights and Biases" as input and determines the deviation from the ground truth

The function must be:
- Convex --> No local minima
- Continuous --> No jumps
- Differentiable --> No peaks, etc., that have no derivative
```

### Overfitting ⬆️

```
Too much training is bad as the network becomes too adapted to the data and adapts poorly to new ones.
- Regularization —> L1, L2, Dropout
- Remove Layers in Network
```

### Underfitting ⬇️

```
- Train Longer, giving gradient descent more opportunities to navigate the paths.
- The learning rate can be adjusted (reduced) accordingly.
- Change the network's structure
    - Too few nodes: Not enough space/capacity to learn
    - Too many nodes: Too many possibilities for creating learning structures, takes longer
- Manipulate Training Data (E.g., rotate images by 10°)
    - At too large angles, the images distort the results too much
```

### Numerical Stability

```
- When the network is numerically stable, there's no overflow due to inflation
- Standardization → Smaller inputs make the network more stable
```

---

### Random Questions ❓

#### Why are there different gradient methods?

```
Different gradient methods are used for different loss functions to make the gradient surfaces smoother and more derivable.
```

#### What's the purpose of the Dot-Product in NN?

```
To sum up the values of all connected nodes to a single node!
- Matrix multiplication (Dot-Product) occurs between x and w in the forward propagation, the values are then added up and subtracted from the Ground-Truth
- The Dot-Product of matrices is used to combine the weight vector w with the inner nodes so that each node receives the summed signals of the previous layer
```

#### Why should you never initialize with 0 or identical numbers?

```
Zeros block the learning process
- Too large numbers saturate the neurons and prevent learning
- With identical numbers, the error is equally distributed among all nodes, making differentiation impossible
- Better to use random values between -1 and 1, or 0.01 and 0.0
```

---

## 💻 Webpages

- [Checklist for debugging neural networks](https://towardsdatascience.com/checklist-for-debugging-neural-networks-d8b2a9434f21)
- [A playbook for systematically maximizing the performance of deep learning models.](https://github.com/google-research/tuning_playbook#guide-for-starting-a-new-project)
- [A Neural Network Playground](https://playground.tensorflow.org/#activation=tanh&batchSize=10&dataset=circle&regDataset=reg-plane&learningRate=0.03&regularizationRate=0&noise=0&networkShape=4,2&seed=0.42697&showTestData=false&discretize=false&percTrainData=50&x=true&y=true&xTimesY=false&xSquared=false&ySquared=false&cosX=false&sinX=false&cosY=false&sinY=false&collectStats=false&problem=classification&initZero=false&hideText=false)

---
