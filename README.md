# ML-MODEL-DEPLOYMENT-USING-FLASK
Flower classification is a very important, simple, and basic project for any machine learning student. Every machine learning student should be thorough with the iris flowers dataset. This classification can be done by many classification algorithms in machine learning, we used logistic regression. Mainly by focusing on Logistic Regression
Iris Flowers dataset and performed a logistic regression algorithm
Finally, it classified flowers into their species.
And got an accuracy of 97.37%, which shows that the model we built is very accurate.
Classification of iris flowers is perhaps the best-known example of machine learning.
The aim is to classify iris flowers among three species (Setosa, Versicolor, or Virginica) from sepals' and petals' length and width measurements.
The iris data set contains fifty instances of each of the three species.
The central goal is to design a model that makes proper classifications for new flowers. In other words, one which exhibits good generalization.

# Contents:
Application type.
Data set.
Neural network.
Training strategy.
Model selection.
Testing analysis.
Model deployment.

This example is solved with Neural Designer. To follow it step by step, you can use the free trial.

# 1. Application type
This is a classification project. Indeed, the variable to be predicted is categorical (setosa, versicolor, or virginica).

The goal is to model class membership probabilities conditioned on the flower features.

# 2. Data set
The first step is to prepare the data set. This is the source of information for the classification problem. For that, we need to configure the following concepts:

Data source.
Variables.
Instances.
The data source is the file iris_flowers.csv. It contains the data for this example in comma-separated values (CSV) format. The number of columns is 5, and the number of rows is 150.

The variables are:

sepal_length: Sepal length, in centimeters, used as input.
sepal_width: Sepal width, in centimeters, used as input.
petal_length: Petal length, in centimeters, used as input.
petal_width: Petal width, in centimeters, used as input.
class: Iris Setosa, Versicolor, or Virginica, used as the target.
Note that neural networks work with numbers. In this regard, the categorical variable "class" is transformed into three numerical variables as follows:
iris_setosa: 1 0 0.
iris_versicolor: 0 1 0.
iris_virginica: 0 0 1.
The instances are divided into training, selection, and testing subsets. They represent 60% (90), 20% (30), and 20% (30) of the original instances, respectively, and are randomly split.
As we can see, the target is well-distributed. Indeed, there is the same number of Virginica, Setosa, and Versicolor samples.

# 3. Neural network
The second step is to choose a neural network. For classification problems it is usually composed by:

A scaling layer.
Two perceptron layers.
A probabilistic layer.
The neural network must have four inputs since the data set has four input variables (sepal length, sepal width, petal length, and petal width).
The scaling layer normalizes the input values. As all input variables have normal distributions, we use the mean and standard deviation scaling method.
Here we use 2 perceptron layers:

The first layer has 4 inputs, 3 neurons, and a logistic activation function.
The second layer has 3 inputs, 3 neurons, and a logistic activation function.
The probabilistic layer allows to interpret the outputs as probabilities. In this regard, all outputs are between 0 and 1, and their sum is 1. The softmax probabilistic method is used here.
The neural network has three outputs since the target variable contains three classes (Setosa, Versicolor, and Virginica).

# 4. Training strategy
The fourth step is to set the training strategy, which is composed of:

Loss index.
Optimization algorithm.
The loss index chosen for this application is the normalized squared error with L2 regularization.
The error term fits the neural network to the training instances of the data set. The regularization term makes the model more stable and improves generalization.
The optimization algorithm searches for the neural network parameters which minimize the loss index. The quasi-Newton method is chosen here.
The following chart shows how the training and selection errors decrease with the epochs during training. The final values are training error = 0.005 NSE (blue), and selection error = 0.195 NSE (orange).


# 5. Model selection
The objective of model selection is to find the network architecture with the best generalization properties. That is, that which minimizes the error on the selected instances of the data set.
We want to find a neural network with a selection error of less than 0.195 NSE, which is the value we have achieved so far.
Order selection algorithms train several network architectures with a different number of neurons and select that with the smallest selection error.
The incremental order method starts with a small number of neurons and increases the complexity at each iteration. The following chart shows the training error (blue) and the selection error (orange) as a function of the number of neurons. The neural network with two neurons in the first perceptron layer.


# 6. Testing analysis
The purpose of the testing analysis is to validate the generalization performance of the model. Here we compare the neural network outputs to the corresponding targets in the testing instances of the data set.
In the confusion matrix, the rows represent the targets (or real values) and the columns the corresponding outputs (or predictive values). The diagonal cells show the correctly classified samples. The off-diagonal cells show the misclassified samples.
Predicted setosa	Predicted versicolor	Predicted virginica
Real setosa	10 (33.3%)	0	0
Real versicolor	0	11 (36.7%)	0
Real virginica	0	1 (3.33%)	8 (26.7%)
Here we can see that all testing instances are well classified, but one. In particular, the neural network has classified one flower as Virginica being Versicolor. Note that the confusion matrix depends on the particular testing instances .
The confusion matrix allows us to calculate the model's accuracy and error:

Classification accuracy: 96.67%.
Error rate: 3.33%.

# 7. Model deployment
The neural network is now ready to predict outputs for inputs that it has never seen. This process is called model deployment.
To classify a given iris flower, we calculate the neural network outputs from the lengths and withs of its sepals and petals. For instance:

Sepal length (cm):	
5.8
Sepal width (cm):	
3
Petal length (cm):	
3.8
Petal width (cm):	
1.2
Probability of Iris Setosa:	21.85%
Probability of Iris Versicolor:	56.72%
Probability of Iris Virginica:	21.42%
For this particular case, the neural network would classify that flower as being of the versicolor species since it has the highest probability.
