### Improve data Quality

##### Attributes related to data quality

- Accuracy
	- if data values are correct 
- Consistency 
	- correlative with different representations of the same info across multiple datasets
- Timeliness
	- time between when information is expected and when it can be used
- Completeness
	- if all intended data being produced in the dataset is complete or is any data missing

#### Ways to improve data quality
1. Resolve missing values
2. Convert Date features column to Datetime format
3. Parse date/time features
4. Remove unwanted values
5. Convert categorical columns to "one-hot encodings"


## Machine Learning in practice

#### Linear Regression
- regression is used for prediction of continuous label values (eg, time factor)
- minimize errors between our labeled value vs our predicted values usually using  Mean squared error (MSE)


#### Logistic Regression
![[Pasted image 20250506160831.png]]
- calibrated probability estimate
- useful to cat  binary classification problems into probabilistic problems
	- yes or no -> predict probability that x will happen

![[Pasted image 20250508143801.png]]
- regularization is important as driving the loss of info to zero is dangerous and difficult

- regularization and early stopping is done to counteract overfitting

![[Pasted image 20250508144030.png]]

- choice of threshold is also important and can be tuned to allow for the binary decision (yes or no)
-  use ROC curve to choose the decision threshold based on decision criteria

![[Pasted image 20250508144141.png]]

- Area under curve (AUC) provides aggregate  measure of performance across all possible classification thresholds
- helps choose between models when u dk which decision threshold will be used
- all logistic regression predictions should be unbiased where the average of predictions == average of observations

## Optimizations

#### Defining ML Models
- ML models are mathematical functions with parameters (changed during training) and hyperparameters (set before training)
- linear models have 2 types of params 
	- Bias 
	- Weight

![[Pasted image 20250508144737.png]]


#### Loss function
- by calculating errors
	- Error = actual - predicted

- Root Mean Squared Error (RMSE)
	- ![[Pasted image 20250508145250.png]]
	- Lower RMSE = better performing model
	- Problem : doesn't work as well for classification
	- Used for regression

-  Cross entropy
	- ![[Pasted image 20250508213642.png]]
	-  used for classification


#### Gradient Descent
- turn loss function into search strategy
- small step size can take very long to train and cover 
- big step size may overshoot and leave the valley
- step size is a hyper-parameter set before training
- 1 step size may not fit for every model
- ![[Pasted image 20250508214247.png]]
- gradient will provide a sense of direction and step size 
	- if gradient = -5, step size Big and to the right
	- if gradient = 2 step size small and to the left

#### Troubleshooting loss curves
- for standard loss curve, as training goes on, loss will drop big step early on and smaller steps as approaching minima
- for abnormal loss curve, big jumps = too big step size. little to no decrease = too small step size
- to fix this we need a scaling parameter, learning rate

#### ML model pitfalls
- problem : model changes every time it's retrained
	- problem might be due to >1 minima (non-convex)
-  problem : model training is still too slow
	- factors that may affect training time
	- ![[Pasted image 20250508215300.png]]
	- do mini-batches instead of entire sample
	- use reduced frequency 



#### Performance metrics
- Inappropriate minima
	- not true reflection of relationship between features and label
- Skewed data can make inappropriate strategies seductive

![[Pasted image 20250508221942.png]]

	- Precision = True Positive / total positive 
	- Recall = True Positive/ all positive
	- Accuracy = True Positive / total


## Generalization and Sampling

#### Generalization and ML models
- the most accurate ML model is not always the best choice
- 

#### When to stop model training
- split experimental dataset into training and validation 
	- use the validation dataset to experiment with model complexity
![[Pasted image 20250508223300.png]]
- evaluate final model with independent test data
- if lots of data, use held-out test dataset
- if little data, use cross-validation




# Computer Vision Fundamentals

## What is Computer Vision
- Subset of ML and AI
-  Focus on how computers see
-  understanding of images and videos

- cloud computing with specialized computer vision equipment allows for this to be utilized at scale
- computer vision generates large amounts of data

![[Pasted image 20250630164455.png]]

## Different Types of Computer Vision Problems
### image classification
- used with image with 1 object
- key to assign label to entire image 

### semantic segmentation
- partition image into multiple regions
- segments all pixels into different categories
- then labels each pixel including background, with different colors based on category class or class label

### instance segmentation
- identifies boundaries of object in an image
- labels pixels with different colors 
- the exact outline of an object is provided by the image segmentation

### image classification with localization
- more complex version of image classification
- assigns class label to an image
- creates a bounding box around a single object 


### object recognition
- identifies the object in the image by outputting class labels and class probabilities of the objects 
- cannot detect where the object is located


### object detection
- detects specific object
- similar to image classification with localization
- useful when multiple types of objects within 1 single image
- bounding boxes used for detection and localization of objects
- tells you which objects are in the image and output bounding boxes about the width and height to indicate the location of the objects

### pattern recognition
- detects and identifies repeated shapes, colors, and other visual indicators
- includes:
	- facial recognition
	- movement recognition
	- OCR
	- medical image recognition

### facial recognition
- advanced type of object detection
- can detect multiple faces
- detect key facial attributes:
	- emotion
	- headwear
- some models can also confirm identity

### edge detection
- used to extract edges from an image
- by identifying boundaries of object within
- initial step of object detection
- main principle is detected changes in brightness and intensity levels

### feature matching
-  type of pattern detection 
- compares features of images 
- such as :
	  - orientation
	  - perspective
	  - lighting  sizes
	  - colors
- Applications:
	- auto object tracking
	- 3D object reconstruction
	- robot navigations
	- image retrieval 
	- indexing

## Computer Vision Use Cases
- classify images into categories of similar images
- analyze content based on user requests
- return results and score of confidence in analysis
-  generate captions based on image


## Custom Training with Linear, Neural Network and Deep Neural Network Models

## Introduction to linear models
- popular in ML and statistics
-  work well on binary and multiclass classification
- linear models assume linear relationship between input variable and output variable by introducing softmax or sigmoid layer
- parameters of linear models are assumed as linear functions of the input
- simplest version, linear model with 1 input and 1 output model takes weighted sum of inputs and 1 addition sum (bias) 
![[Pasted image 20250630173654.png]]

![[Pasted image 20250630173728.png]]

- in linear models, every input is connected to every output


### Reading the data
- to create input pipelines, must start with a data source
- eg, to construct dataset from data in memory we can use tf.io and tf.image in code
	- they consists of modules like image processing functions and encoding/decoding functions
- Reading and decoding image data in standard forms like PNG or JPEG consists the following steps:
	- Read
	- Decode
	- Convert
	- Resize


#### Read
- first need to read file into your program
- tf.io.read_file reads contents of the file
- it returns a tensor that contains an array of bytes with entire contents of the input
- tensors are mathematical objects just like scalars and vectors
- rank of tensor is defined by no. of directions; therefore its directionality of array is required to describe it
	- eg, scalar is zero-rank tensor and vector is first-rank tensor
- important that tf.io.read_file does not do any parsing
- it only returns the contents as they are

#### Decode
- decoding data is done with tf.image.decode_jpeg 
- it converts the input bytes strings into uint8 tensor
- encoded images are represented with scalar string tensors
- decoded images are represented by 4-D uint8 tensors of shape (height, width, channels)
- available channels depend on the file itself
	- eg, a grayscale image might only have 1 channel
	- in 5 flower dataset, flower images have 3 channels (RGB)

#### Convert
- computers dont see images like humans do
- all color intensities of each pixels are expected in float numbers
- pixels consisting of RGB values are integer data types with values of range (0 , max)
	- max is largest positive representable number for the data type
- convert will max the pixels consisting of RGB and convert into floats and scaled in the range of 0 to 1 

#### Resize
- might need to crop data to desired size or pad the data with zeros
- other cases, resize while keeping aspect ratio then pad the remaining 


### Visualizing Image Data
- data exploration is needed in many ML processes
- Visualizing image data is important use of increasingly large and complex image data resources
- use matplotlib
- to display image, first need to use read_and_decode function to read the image
- imshow() function creates an image from 2d numpy array
- use numpy() function to convert tensor format image into numpy array

### Reading entire image dataset
- more efficient if we work with large number of data
- use tf.data.Dataset API
- API supports writing of descriptive and efficient input pipelines :
	- lets you create a source dataset from your input data
	- apply dataset transformations to preprocess the data
	- iterate over entire dataset and process the elements
		- as iteration happens in streaming fashion, entire dataset does not ened to fit into memory 

- API supports multiple ways to create a dataset:
	- process lines from files : tf.data.TextLineDataset
	- process records written in TFRecord format : tf.data.TFRecordDataset
	- dataset of all files that match a pattern : tf.data.Dataset.list_files
	- read fixed length records from binary files and create dataset where each record is an element: tf.data.FixedLengthRecordDataset


## Implementing Linear Models for linear Classification
- best to start with simpler model and gradually introduce complexity until criteria are met
- simpler models are less likely to overfit and are easier to interpret and maintain
- another method is to choose a large enough model to interpolate the data and increase regularization as needed

- simplest type of model is sequential model with groups linear stack of layers into a tf.keras.Model
- sequential model is a simple list of layers that are connected so that the output of one later is the input of the next
- this means that if you have multiple outputs such as regression and classification outputs at the same time, you cannot use sequential model
- use functional API to handle those non-linear topology, or shared layers

- to use sequential keras model, follow :
	- defined and create the model
	- compile model to configure for training
	- display model with model.summary() dunction to print a string summary of the network (Optional)
	- call model.fit() with training dataset to train model for fixed number of epochs
	- plot history of loss and error metrics (Optional)
	- generate output predictions for input samples with model.predict() using each image you want to classify
	- plot predictions of model by defining custom plot_predictions function (Optional)

### Creating a Model
- model = tf.keras.Sequential([ tf.keras.layers.Flatten(input_shape=(IMG_HEIGHT,IMG_WIDTH, 3)),tf.keras.layers.Dense(len(CLASS_NAMES))]) 
- In the linear model, each image is flattened by unstacking its pixels
- then the model produces 5 outputs
- each output values is a weighted sum of the input pixel values
- generally, all keras needs to know is the shape of their inputs to create their weights
- so when a new sequential model is created, it initally has no weights
- when you instantiated a sequential model without an input shape, it isnt built and thus has no weights
- weights are created when model is first exposed to input data
- simple alternatives is to pass input_shape argument to ur first later
- thats why input layer expects a 3D image tensor is implicit in your code snippets

- Second layer, flatten layer takes 3D image tensor as input and flattens it with same number of values
- it transforsm image format from 3d array of 224 x 224 x 3 to 1D array of 224*224*3 = 150528 pixels
- similar to unstacking rows of pixels and lining them up
- this layer has no params to learn and onlky reformats the data

- Last later, dense later implements dense operation to calculate output as activation of weighted average of flattened input pixel values added by bias
- activation function is used to determin output of equation
- activation function maps resulting values between 0 to 1 or -1 to 1 or other ranges depending on the function
- this converts logits into probabilities
- depending on binary or multiclass problem, u can apply sigmoid or softmax to obtain probability


- softmax function converts vector of values to probability distribution
- it exponentiates its inputs and then normalize them
- exponentiation means that 1 more unit of evidence multiplicatively increases the weight
- conversely 1 less unit of evidence will make the weight a factor of the earlier weight
- softmax will normalize weight so they all add up to 1
- forming a valid probability distribution
- output will be softmax of the weighted average of the flattened input pixel values

- dense layer has 1 output node for each class 

### Compiling a model
- before its ready for training, it must be first compiled with a few more settings
- 3 settings:
	- Optimizer
		- how the model is updated based on data seen and loss function
	- Loss Function
		- measures how accurate the model is during training
		- minimized so that model is more accurate
	- Metrics
		- monitor training and testing steps
		- eg accuracy


#### Optimizer
- methods to update your model weights
- to reduce losses
- adjust learning rate to get results faster
- eg, Adam optimization, popular stochastic gradient descent methods

#### Loss Function
- optimization needs a number to represent quality of ur solution
- it tells optimizer if its moving in the right direction or not
- in keras its used to compute quantity that model should seek to minimize during training
- use SparseCategorialCrossentropy loss for classification with 2 or more labels. it will expect labels to be provided as integers
-  if you want one-hot representation to provide labels, use CategorialCrossentropy loss

#### Metrics
- Keras has accuracy class, to calculate how often predictions = labels



### Displaying the Model
![[Pasted image 20250706112405.png]]
- after its built, call the model summary to display contents


#### Model Plotting Utilities
- keras api has model plotting utils to convert keras model to dot format
- tf.keras.utils.plot_model returns Jupyter Notebook image that enables in-line display of model in the notebook

### Training the Model
![[Pasted image 20250706112719.png]]
- training sequential models need feeding of training data to the model
- use model.fit and pass in training and validation datasets to train the model
- training dataset is passed in to train the model 
- validation dataset is passed in to report accuracy metrics

### Evaluating the Model
- evaluation is needed to understand whether number of epochs are enough for loss to converge
- callback is object that perform actions at various stages of training
- keras registers callbacks during training including history callback which records training metrics for each epoch such as loss, accuracy, validation loss or validation accuracy
- by comparing learning data with validation data, plot provides insights for the slope - speed of convergence over epochs, status of convergence, and also insight if there is overtraining

### Generating the prediction
- call model.predict() on a few images in the evaluation dataset
- reason for reshape is that model.predict() expects a batch of images
- so we have to reshape the image tensor as a batch consisting of only 1 image
- the predicted confidence values are called logits and are in range of -infinity to +infinity
- predicted label from model is the label which has the highest confidence
- you can convert logits to probabilities using softmax

#### Error metrics
- SparseCategorialCrossentropy loss used to minimize loss function on training dataset
- business users expect more meaningful error metrics
- most common is accuracy - fraction of instances that are classified correctly
- however, accuracy fails when 1 class in dataset is represented by a very rare example


### Plotting Predictions
- looking at what model has learned, you can plot predictions of model on a few images from evalution dataset by defining custom plot_predictions() function



## Neural Networks and Deep Neural Networks for Image Classification

### Neural Networks
- made of:
	- Input layer
	- Hidden Layer(s)
	- Output Layer
- each layer contains nodes (neurons) which are connected to nodes in next layer with weights (fully connected)
- each node performs a linear computation (such as linear regression) and passes result to next layer

### Roles of Activation Functions
- Activation functions introduce non-linearity making neural networks different from simple linear models
- Popular activations:
	- ReLU (Rectified Linear Unit) : f(x) = max(0,x)
	- Others: Sigmoid, Tanh, ELU
- Without non-Linear activations, stacking layers will just result in another linear function

### Building Neural Networks in Keras
- use sequential model to stack layers
- add dense (full connected) layers
- compile the model with loss function and optimizers
- train with model.fit(), evaluate with model.evaluate(), and predict with model.predict()

### Training Neural Networks
- training is similar to linear models
- use model.compile() with metrics like accuracy
- use model.fit() to train model on data
- Monitor loss and validation loss to detect overfitting and poor optimization
- Tuning tips:
	- Adjust learning rate, loss function, batch size
	- use more data or validation techniques

### Deep Neural Networks
- DNN has more than 1 hidden layer
- More layers = more modeling power, but need more data
- DNN are trained same way as NN (Compile, Fit, Predict)
- Downsides:
	- May perform worse with small datasets
	- Prone to overfitting

### Improving DNN performance
- Techniques to boost performance:
	- Dropout layers: prevents overfitting
	- Batch normalization: Stabilizes learning
	- Regularization, Early stopping, learning rate tuning

### Key Concept: Feature Hierarchy
- Neural Networks can learn their own features through layers (less need for manual feature engineering)
- Each layer learns increasingly abstract representations of the data
- This hierarchy is critical in more advanced models like Convolutional Neural Networks  (CNNs)


## Deep Neural Networks with Dropout and Batch Normalization

### Why not make the Neural Network bigger?
- Universal Approximation Theorem: A single hidden layer (if large enough) can approximate any function
	- But it needs to be infinitely large which is'nt practical
- More layers = more parameters, which increases memory and risk of overfitting
- Large models:
	- need longer time to train
	- need smaller batch size (slower optimization)
	- Risk overfitting, especially on small datasets

### Overfitting and Regularization
- Overfitting: When the model memorizes training data but fails to generalize
- Regularization techniques help prevent this:
	- L1/L2 regularization: Adds a penalty for large weights
	- Dropout: (Only used in neural networks)
		- Randomly drops out nodes during training
		- Each training step sees a different subset of the model
		- results in an ensemble effect of many smaller networks
		- implements in keras via tf.keras.layers.Dropout(rate)

### Dropout
- Only applied during training, not during evaluation
- keras handles dropout automatically
- makes the model less likely to overfit by reducing reliance on specific nodes

### Batch Normalization (BatchNorm)
- Problem: Internal Covariate Shift
	- Changing parameters in earlier layers alters input distribution in later layers
- Batch Normalization:
	- Normalizes input in each mini-batch to mean = 0 and std = 1
	- Stabilizes and speeds up training
	- Improves model accuracy
- Implemented using tf.keras.layers.BatchNormalization()

#### How BatchNorm works
- During training:
	- Normalizes based on current batch's mean and std
- During inference:
	- Uses moving average of training batches for normalization
- Introduces learnable scale and center parameters

### Best Practices with Dropout & BatchNorm
- Use Dropout after activation layers to reduce overfitting
- Use BatchNorm between Dense Layers and their activations
- flow eg,
	- ``` Dense -> BatchNorm -> Activation -> Dropout```


## Convolutional Neural Networks


### Origin and Inspiration of CNNs

#### Neocognitron 
- Hierarchical Network with simple cells (local feature extraction)  and complex cells (tolerance to local shift/deformation)
- learns object shapes and inspired later CNNs
-  Complex cells provide position (translation) tolerance via local pooling-like aggregation

#### Direct Influence on CNNs
- LeCun et al, explicitly drew on simply/complex cell like concepts to design convolution and pooling layers
- "Pooling" in early CNNs correspond to complex-cell-like spatial aggregation

#### LeNet
- early CN architecture demonstrates end-to-end learning for handwriting recognition by composing simple to complex features
- Trained on Digit images using conv -> subsampling stacks then full connected layers


### Breakthroughs in CNN performance

#### AlexNet (2012 ImageNet)
- Deep CNN that beat runner-up by 10.9% points 
- catalyzing fields shift to CNNs as default for vision
-  key innovations such as ReLu activations, heavy data augmentation, dropout, GPU training, local response normalization used


### Why CNNs > DNNs
- Dense layers on megapixel images imply biullions of weights (each pixel to many neurons)
- CNNs cut parameters using local receptive fields and weight sharing
	- Parameter Sharing = one filter (kernel) slides over the image reusing the same weights across spatial locations)

#### Structure Sensitivity
- Dense DNNs: pixel order can be permuted with little effect (weights permute correspondingly)
- CNNs: rely on spatial locality/hierarchy; randomly pixel shuffling destroys performance
	- CNNs are translation-equivalent (shift in input -> shifted feature map) and pooling/striding introduce approximate translation invariance

### Pre-2012 vision pipelines
- heavy manual feature engineering (Gabor filters, co-occurrence matrices) to craft, edges, texture, shapes

### Post-2012 paradigm
- CNNs learn features automatically from data, reducing manual engineering and improving accuracy across tasks (classification and detection)

### Core CNN layers
- Convolutional Layer
	- Learns filters over small neighborhoods (kernels) to detect patterns; parameters are learned via back propagation
- Pooling Layer
	- Downsampling (eg, max, average) to lower dimensionality and improve invariance 

### Design Knobs in convolutions
- kernel size, stride, padding, no. filters, determine receptive field all 

#### Activations and normalization
- modern CNNs typically use ReLU activations and batch normalization to stabilize training and allow deeper networks

#### Regularization
- Dropout, Weight Decay (L2) and data augmentation combat overfitting in CNNs

#### Head Layers for classification
- After Conv/Pool stacks, fully connected dense layers (or global average pooling ) map features to class logits

#### Beyond Images
- CNNs also work for audio, time-series, and signals, exploiting local correlations along time/frequency axes

#### Notable Architectures after AlexNet: Inception
- Multi-scale filter per stage
- faster ResNet (Residual/Skip) connections enable very deep networks

#### Receptive Field Growth
- Stacking conv/pool (or dilated convs) increase the effective receptive field letting deeper capture global context

#### Trade-offs of pooling
- Reduces computation and overfitting but discards spatial precision


#### Training at scale
- Large datasets and GPU/TPU are critical for deep CNNs to generalize well



## Understanding Convolutions

### What is a Convolution
- Combines 2 functions:
	- Input (image) 
	- Weight matrix (kernel/filter) 
	- to produce feature map

- kernel slides over neighboring pixels 
	- at each position it will multiply-and-sum pixels with kernel weights
	- same kernel weights are used at all locations (Weights sharing)

### 1D vs 2D vs 3D CNNs
- 1D CNNs
	- sequences time, audio, text
- 2D CNNs
	- images 
- 3D CNNs
	- volumetric/ video data
	- eg, MRI/CT, videos
- nD CNN
	- n  spatial dimensions (independent on channels)

### Tensor Shapes (Inputs)
- Grayscale: H x W x 1
- Color (RGB): H x W x 3
- 3D image volume: D x H x W x C

### Kernels/ Filters
- kernel has its own learnable weights
- each kernel produces 1 channel of output
	- with K kernels u get K output depth
- eg, RGB input 300x300x3 with 2 kernels
	- output (spatially smaller) x 2 cahnnels
	- 1 stride and no padding
	- Hout = Hin - K +1 (so 5x5 kernel give 300 > 296)

### Why output shrinks (no padding)
- with 5x5 and 3x3 kernel, output is 3x3 because 5 - 3 +1 =3 (reduce of 2 on each side)
- General rule (square kernel, stride 1, "valid") : size_out = size_in - kernel +1 per diemnsion

### What different kernels detect
- Horizontal Edge Detector (top row positive, bottom row negative) fires where row changes sharply
- Vertical Edge Detector is same but rotated 90 degrees (positive left, negative right)
- Center Heavy Kernel (High weight center, lower around )  highlights bright spots relative to neighbors (local maxima)

### From Edges to Shapes
- Stacking many learned filters let CNN combine low-level edges -> mid-level parts - > high-level objects


### Kernel Sizes in practice
- Early models like AlexNet used larger kernels (3x3 up to 11x11)
- Modern Architectures mostly use 3x3 kernels repeated in depth

### Hardware note
- GPUs and TPUs speed up CNNs by computing many kernel positions in parallel

## CNN Model Parameters
### What are parameters
- Model Params are learned weights (and biases) that transform inputs to outputs
- More complex CNNs = more trainable parameters (more filters, deeper stacks, larger dense layers)

### Tensor Shapes
- Keras Conv2D expects 4D tensors: (batch, height, width, channels)
- eg, RGB image: `[16, 256, 256, 3]`

### Conv2D key arguments (Keras)
- filters: no. output channels (one per learned kernel)
- kernel_size: eg, 3 ( 3x3) or (3x5 rectangular). Modern CNNs favor small kernels (3x3) stacked deeply
- strides: step of sliding window (default 1) Large stride = fewer outputs
- Padding:
	- "valid" -> no padding, spatial size shrinks
	- "same" - > pads to keep output size  ≈ input size (for stride 1)
- activation: usually ReLu for conv layers
- input_shape: only for first layer

### Output size formulas
- No padding ("valid")
$$
H_{out} = \left\lfloor \frac{H_{in} - K_h}{S_h} \right\rfloor + 1
$$

$$
W_{out} = \left\lfloor \frac{W_{in} - K_w}{S_w} \right\rfloor + 1
$$

- Same padding (Keras)
$$
H_{out} = \left\lceil \frac{H_{in}}{S_h} \right\rceil,  W_{out} = \left\lceil \frac{W_{in}}{S_w} \right\rceil
$$
- for stride 1, output height/width equals input

- How much padding per side (odd square kernel k, stride 1)
$$
p = (k -1 )/2
$$

Note that +1 in output size formula is not bias; bias affect parameter count not actual spatial size

### Parameter-count formulas
- Convolution Layer
$$
params = (K_{h} * K_{w} * C_{in} +1) * C_{out}
$$
- +1 is bias per filter
- Cout = no. filters

- Pooling layer
	- No learnable parameters = 0

- Full connected (dense0 layer)
$$
params = (P+1) * C
$$
 - P = units in previous layer, C = units in current layer, +1 = bias per neuron

### Worked Examples
#### AlexNet first Conv 
- Input : 227 x 227 x 3
- Filters : 96 
- kernel : 11 x 11
- stride often 4 in classic AlexNet
- Output Channel = 96
- Spatial size with valid , stride 4:
	- (227-11)/4 + 1 = 55 -> 55 x 55 x 96
- Params : (11 * 11 * 3 +1) * 96 = (363 +1) * 96 = 344944
- Stride Halving
	- 256 x 256 input, stride = 2 (square kernel, valid) : output ≈ 128 x 128

### What kernels detect
- Edge detectors (sobel-like): horizontal/vertical edges
- Center-Heavy kernels: bright spots
- Stacking layers let networks combine edges -> parts -> objects

### Practical Tips
- prefer small kernels (3x3) and deeper stacks over large single kernels (eg 3x3 layers with 18 weights vs 1 9x9 with 81 weights)
- use padding="same" to keep spatial sizes stable across layers for easier design
- Start with strides 1 in conv; use pooling or stride 2 sparing to down sample


## Working with Pooling Layers
### Why Pooling?
- CNNs can have millions or billions of parameters - > heavy compute and memory
- Pooling reduces spatial size of feature maps -> fewer activations to pass forward, lower compute, no extra learnable weights

### Types of pooling
- Max pooling: 
	- takes max in each window
	- common for keeping strongest activation
	- adds some translation invariance
	- eg, 2x2 window, stride 2 on 4x4 map -> 2x2 output (halves H and W)
- Average pooling:
	- takes mean in each window
	- smoother, less extreme than max
- Global pooling:
	- collapses each channel into a single value
	- Global Max Pooling
	- Global Average Pooling
	- handy before classification to replace large Dense layers

### Key properties
- pooling layers have 0 trainable params
- usually places after conv layers
- Stride controls down sampling:
	- stride 2 halves spatial size
	- stride 1 keeps size (acts more as smoothing)

### Why Conv > Dense first
- Far fewer weights -> faster training, less memory, less overfitting
- Conv uses local receptive fields + weight sharing
- Dense connects every pixel to every neuron

### MNIST comparison (28x28 grayscale -> 784 inputs)
- Dense first layer:
	- needs 1 weight per input per neuron
	- 300 neusons -> 784x300 = ~235k weights just for 1 layer
- Conv first layer:
	- 5x5 kernel, 4 filters
	- 5x5x1x5 = 100 weights (plus a few biases)

### Typical MNIST CNN front end
1. Conv2D (same padding) - preserves 28x28 size while learning edge/texture filters
2. (Optional) more Conv2D + Pooling - progressively compress spatial dims, enrich features
3. Flatten - turn feature maps into a vector
4. Dense - Softmax(10) for digits 0-9

### Key Conv2D parameters to remember
- filters = output channels (one per kernel)
- kernel_size = eg,3 or (5,5)
- padding: "same" (keeps size), "valid" (shrinks)
- strides: usually 1; :>1 down samples
- activation: usually ReLu

### Pooling's Role
- no trainable params
- reduces spatial size
- keeps strongest/average signals
- adds invariance

# Dealing with Image Data

## Preprocessing the Image Data

### 1. Build dataset
- Collect
- Validate
- Annotate

### 2. Store efficiently
- Avoid per-row CSV + JPG paths for large jobs (slow IO)
- use TFRecord:
	- Compact, splitable into many files
	- Fast parallel reads, ideal for GPUs/TPUs and multi-host training

### 3. Read with performant pipelines
- Use tf.data.TFRecordDataset and tf.data API
	- dataset = tf.data.TFRecordDataset(files).map(parse_fn, num_parallel_calls=AUTOTUNE).shuffle(...).batch(...).prefetch(AUTOTUNE)
	- Enables distributed file reads, random augmentations, batching, prefetch

### 4. Preprocess Images
- Resize
- Color space convert, crop, flip, rotate/transpose
- Task-specific segmentation, compression tweaks (Task specific)

#### Resizing Specifics
- tf.image.resize(img,size) - may distort if aspect ratio changes
- use tf.image.resize_with_pad to preserve aspect ratio (pads borders)
- choose method via tf.image.ResizeMethod (bilinear, nearest, etc)
- for best accuract in some tasks, consider, learned resizers (research result)

#### Other handy tf.image tools
- adjust brightness/contrast, bounding boxes, color conversions, decode/encode

### 5. Keras preprocessing layers (recommended)
- Plug preprocessing into the models graph so it runs in training and inference
	- tf.keras.layers.Resizing(H,W)
	- tf.keras.layers.Rescaling(1./255)
	- plus augmentation layers like RandomFlip, RandomRotation, etc
- Benefit: export a single SavedModel with preprocessing included; no special handing at predict time


## Model Params and Data Scarcity Problem

### Why data becomes a bottleneck
- CNNs are data-hungry:
	- more layers/filters -> more trainable params -> need more labelled data
- Training starts from (near) random weights:
	- more parameters -> more samples needed to estimate them

### Param counts -- MNIST examples  (28x28, 10 classes)
#### Linear (softmax) Model
- Weights: H x W x nClasses = 28x28x10 = 7840
- Biases: nClasses = 10
- Total: 7850

#### DNN (3 dense layers: first hidden has 200 units)
- First hidden layer params (28x28) x 300 +300 = 235500
- Whole DN = ~270k parmas 

#### CNN front end
- First Conv layer (10 filters of 3x3 stride 1)
- Params per filter = 3x3xCin+1 (grayscale : 9 +1= 10)
- Total 10 filters x 10 = 100
- ENtrie CNN has = ~300k params
- but 90% in final dense layers; conv layers are parameter efficient

### When Labeled data is scarce
#### 1. Data augmentation 
- Make more data
- Apply label-preserving transforms to training images to increase diversity:
	- random flips/rotations
	- crops
	- translations
	- zoom
	- color jitter (brightness/contrast/saturation)
	- noise
	- cutout/mixup/cutmix
- Helps reduce overfitting and improves generalization

#### 2. Transfer Learning
- Start with pretrained CNN (eg, on ImageNet)
- Freeze early layers (generic features), fine tune later layers and the classifier head on ur dataset
- needs far fewer labels than training from scratch and converges faster


## Data Augmentation