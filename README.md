# Documentation


## Generation
This is a class called `Generation`, which represents a generation of neural networks.

The class has the following properties:

*   `networkList`: An array that stores instances of the `Network` class.
*   `generationSize`: A number that represents the number of networks in the generation.
*   `id`: A string that represents the ID of the generation.
*   `io`: An object that contains two properties: `inputCount` and `outputCount`, which represent the number of inputs and outputs of the neural networks in the generation.

The class has the following methods:

*   `constructor`: A method that initializes the `Generation` object. If `buildData` is provided, it is used to build a new generation. Otherwise, a new generation is created by creating new instances of the `Network` class and adding them to the `networkList` array.
*   `json`: A getter method that returns a JSON representation of the `Generation` object.
*   `fromJSON`: A static method that takes a JSON object and returns a new `Generation` object.
*   `saveJSON`: A static method that saves a `Generation` object to a JSON file. It takes the `Generation` object, the line spacing of the file (optional), and the file path (optional) as parameters.


## Network
This is a JavaScript class called `Network` which represents a neural network. It contains several methods for building, modifying, and using a neural network.

The class has the following properties:

*   `#parentGeneration`: a private property that stores a reference to the `Generation` object that this network belongs to.
*   `layerList`: an array of `Layer` objects, representing the layers in the network.
*   `id`: a getter method that returns a unique identifier for the network.
*   `location`: a getter method that returns the position of the network within its parent generation.
*   `json`: a getter method that returns a JSON representation of the network.

The class has the following methods:

*   `constructor(io, parentGeneration, buildData, pushToGeneration)`: the constructor method, which initializes a new `Network` object with the specified input/output node counts, parent generation, and build data.
*   `calculate(inputList)`: calculates the output of the network for the given input array.
*   `clone()`: returns a copy of the network.
*   `insertLayer(index, layer)`: inserts a new layer into the network at the specified index.
*   `mutate(mutationChance, flag)`: randomly mutates the network based on the specified mutation chance and flag.
*   `removeLayer(position)`: removes the layer at the specified position from the network.
*   `static fromJSON(buildData, parentGeneration, pushToGeneration)`: creates a new `Network` object from the specified JSON build data, with the specified parent generation and push flag.


## Layer
The `Layer` class represents a layer of nodes in a neural network.

It has the following properties and methods:

Properties:

*   `#parentNetwork`: A private property that holds a reference to the parent `Network` object.
*   `nodeList`: An array that holds the `Node` objects in the layer.

Methods:

*   `constructor(nodeCount, parentNetwork, buildData = null, pushToNetwork = true)`: Creates a new `Layer` object. `nodeCount` is the number of nodes in the layer, `parentNetwork` is a reference to the parent `Network` object, `buildData` is an optional parameter that can be used to build a layer from a JSON object, and `pushToNetwork` is a boolean flag that determines whether the layer should be added to the parent network's `layerList` array.
*   `id`: A getter method that returns a unique identifier for the layer based on its position in the network.
*   `json`: A getter method that returns a JSON representation of the layer.
*   `location`: A getter method that returns the layer's position in the network.
*   `nextLayer`: A getter method that returns the next layer in the network.
*   `parentNetwork`: A getter method that returns the parent `Network` object.
*   `previousLayer`: A getter method that returns the previous layer in the network.
*   `calculate()`: Calculates the output value for each node in the layer.
*   `insertNode(index, node)`: Inserts a new node at the specified index in the layer's `nodeList`, and adds a connection from the new node to each node in the next layer.
*   `removeNode(index)`: Removes the node at the specified index in the layer's `nodeList`, and removes the connection from the removed node to each node in the next layer.
*   `static fromJSON(buildData, parentNetwork)`: A static method that creates a new `Layer` object from a JSON object. `buildData` is the JSON object, and `parentNetwork` is a reference to the parent `Network` object.


## Node
This is a module that defines a neural network and its components, including `Generation`, `Network`, `Layer`, and `Node`.

`Generation` represents a group of networks that are trained together, and it includes an array of `Network` instances.

`Network` is a collection of `Layer` instances that are connected to each other. The first layer is an input layer, and the last layer is an output layer. The `Network` class has methods for feeding input to the network and obtaining its output, as well as for training the network using backpropagation.

`Layer` represents a layer of nodes in the network. It includes an array of `Node` instances, and each node in the layer is connected to all nodes in the previous layer.

`Node` represents a node in the network. It includes a weight value, a list of connection weights to the nodes in the previous layer, and a reference to its parent `Layer` instance. It has a `calculate` method that computes its output based on the output of the nodes in the previous layer and their connection weights to the current node.
