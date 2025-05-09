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