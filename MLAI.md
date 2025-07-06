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
