
# Mashtiksh Neural Network Library

Mashtiksh is a lightweight JavaScript library for creating and training neural networks. It provides a simple and intuitive interface to implement various neural network architectures, making it suitable for both beginners and experienced developers in the field of machine learning.

## Table of Contents

- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
  - [Creating a Neural Network](#creating-a-neural-network)
  - [Training the Network](#training-the-network)
  - [Making Predictions](#making-predictions)
  - [Saving and Loading the Network](#saving-and-loading-the-network)
- [API Documentation](#api-documentation)
  - [Classes](#classes)
  - [Activation Functions](#activation-functions)
- [Example](#example)
- [Contributing](#contributing)
- [License](#license)

## Features

- **Matrix Operations**: Supports essential matrix operations such as addition, subtraction, multiplication, and transposition.
- **Activation Functions**: Implements multiple activation functions including Sigmoid, Tanh, ReLU, and Softmax.
- **Feedforward Neural Network**: Facilitates feedforward propagation through layers.
- **Backpropagation**: Utilizes backpropagation for training the network.
- **Flexible Architecture**: Customize the number of input, hidden, and output nodes.
- **Early Stopping**: Implements early stopping based on expected error during training.
- **Logging**: Option to log training progress and error metrics.

## Installation

You can clone the repository or download the library directly from GitHub. To include the library in your project, use the following HTML script tag:

```html
<script src="mashtiksh.js"></script>
```

## Usage

### Creating a Neural Network

To create a new neural network instance, you can use the following code snippet:

```javascript
const nn = new NeuralNetwork({
  inputs: 2,
  hiddenLayers: 3,
  outputs: 1,
  learningrate: 0.1,
  log: true,
  steps: 10,
  iterations: 1000,
  errors: 0.01
});
```

### Training the Network

You can train the network using the `trainNetwork` method with a dataset:

```javascript
const trainingData = [
  { input: [0, 0], output: [0] },
  { input: [0, 1], output: [1] },
  { input: [1, 0], output: [1] },
  { input: [1, 1], output: [0] }
];

nn.trainNetwork(trainingData);
```

### Making Predictions

After training the network, you can make predictions using the `feedforward` method:

```javascript
const output = nn.feedforward([1, 0]);
console.log(output); // Outputs the prediction
```

### Saving and Loading the Network

You can save the neural network's architecture and parameters to JSON format:

```javascript
const json = JSON.stringify(nn);
console.log(json);
```

To load the network from JSON, you will need to parse the JSON string and set the properties accordingly.

## API Documentation

### Classes

#### Matrix

- **Constructor**: `new Matrix(rows, cols)`
  - Initializes a new matrix with specified rows and columns.

- **Static Methods**:
  - `Matrix.fromArray(arr)`: Converts a 1D array to a Matrix object.
  - `Matrix.subtract(a, b)`: Subtracts matrix `b` from matrix `a`.
  - `Matrix.multiply(a, b)`: Multiplies two matrices.
  - `Matrix.randomize(rows, cols)`: Creates a matrix with random values.

- **Instance Methods**:
  - `add(n)`: Adds a number or another matrix to the current matrix.
  - `multiply(n)`: Multiplies the current matrix by a number or another matrix.
  - `map(func)`: Applies a function to each element in the matrix.
  - `transpose()`: Transposes the matrix.

#### NeuralNetwork

- **Constructor**: `new NeuralNetwork(params)`
  - Initializes a neural network with given parameters.

- **Methods**:
  - `feedforward(inputArray)`: Feeds input through the network and returns the output.
  - `train(inputArray, targetArray, iteration)`: Trains the network using provided input and target data.
  - `trainNetwork(trainingData)`: Trains the network on an array of training data.
  - `toJSON()`: Converts the neural network parameters to JSON format.

### Activation Functions

- **sigmoid(x)**: Sigmoid activation function.
- **sigmoidDerivative(y)**: Derivative of the sigmoid function.
- **tanh(x)**: Hyperbolic tangent activation function.
- **tanhDerivative(y)**: Derivative of the tanh function.
- **relu(x)**: ReLU activation function.
- **reluDerivative(y)**: Derivative of the ReLU function.
- **softmax(x)**: Softmax activation function.
- **softmaxDerivative(y)**: Simplified derivative of the softmax function.

## Example

Here is a simple example of how to use the Mashtiksh library to create a neural network and train it to learn the XOR function:

```javascript
// Create a new neural network
const nn = new NeuralNetwork({
  inputs: 2,
  hiddenLayers: 3,
  outputs: 1,
  learningrate: 0.1,
  log: true,
  steps: 10,
  iterations: 1000,
  errors: 0.01
});

// Training data for XOR
const trainingData = [
  { input: [0, 0], output: [0] },
  { input: [0, 1], output: [1] },
  { input: [1, 0], output: [1] },
  { input: [1, 1], output: [0] }
];

// Train the network
nn.trainNetwork(trainingData);

// Test the network
console.log(nn.feedforward([1, 0])); // Output close to 1
console.log(nn.feedforward([0, 0])); // Output close to 0
```

## Contributing

Contributions are welcome! Please feel free to submit a pull request or open an issue to discuss improvements.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
```

