# Deep Learning Challenge - Alphabet Soup
## Background
The nonprofit foundation Alphabet Soup wants a tool that can help it select the applicants for funding with the best chance of success in their ventures. With your knowledge of machine learning and neural networks, you’ll use the features in the provided dataset to create a binary classifier that can predict whether applicants will be successful if funded by Alphabet Soup.
## Overview
The purpose of this model is to allow the non-profit organization, Alphabet Soup, a way to efficiently scan through applications for funding in mass, approving those based on the likelihood that it will produce successful results. This model predicts success based on the parameter that the funding was used sucessfully. Measured by our target variable `IS_SUCCESSFUL`, the model returns a `0` for passing applications (*funding was used effectively*) and `1` for failing applications (*funding was not used effectively*). This allows non-profit's to quickly evaluate an application's worthiness of funding and likelihood of success, based on the method that money and funding is being spent effectively by the applicant.

## Results

### Data Preprocessing

##### **Target Variable:** 
 `IS_SUCESSFUL`

##### **Features:**
`APPLICATION_TYPE`
`AFFILIATION`
`CLASSIFICATION`
`USE_CASE`
`ORGANIZATION`
`STATUS`
`INCOME_AMT`
`SPECIAL_CONSIDERATIONS`
`ASK_AMT`

##### **Variables to Remove:**
`EIN`
`NAME`

### Compiling, Training, and Evaluating the Model
#### Neural Network Structure
##### **Original Model**
* **Input Features:** 45
* **Layer 1:** 
    * **40** Neurons
    * **Activation Function:** `ReLu`
* **Layer 2:** 
    * **20** Neurons
    * **Activation Function:** `ReLu`
* **Output Layer:**
    * **1** Neuron
    * **Activation Function:** `Sigmoid`

**Loss: 56.43%** 
**Accuracy: 72.28%**

##### **Final Optimized Model**
* **Input Features:** 44
* **Layer 1:** 
    * **90** Neurons
    * **Activation Function:** `ReLu`
* **Layer 2:** 
    * **40** Neurons
    * **Activation Function:** `ReLu`
* **Output Layer:**
    * **1** Neuron
    * **Activation Function:** `Sigmoid`

**Loss: 56.47%** 
**Accuracy: 73.10%**

#### Activation Function Selection:
**Rectified Linear Unit (ReLU)**
Not all data are positive, especially when normalized
→ Ideal for modeling positive, nonlinear input data for classification or regression
**Sigmoid Function**
Values are normalized to a probability between 0 and 1
→ Ideal for a binary classification dataset

-------

#### Optimization/Improving Model Accuracy

##### Steps Taken to Improve Model Accuracy
**Starting Accuracy:** 72.28%
1. The first step taken to optimize the original model (72.28% accuracy) was adjusting the **cut-off value** for our classification grouping (*increasing from 500 to 800*) and lowering the **random state** (*from 44 to 8*). This slightly increased our original model's accuracy *by 0.69%* (72.97% accuracy), however not significant enough and will require further optimization. 
    * **Hidden Layer 1:** 40 Neurons
    * **Hidden Layer 2:** 20 Neurons
    * **Accuracy Following Change:** 72.97%
2. Our next step in optimizing the model, was to **increase the number of neurons/nodes** applied to both hidden layers. The original model contained 40 neurons in our first layer and 20 in the second, we increased the amount of neurons for both hidden layers. While still returning higher accuracy than the original model, a slight drop in accuracy following initial optimization provided reason to believe alternative measures are needed in order to prove successful (parameters need further adjustment).
    * **Hidden Layer 1:** 60 Neurons
    * **Hidden Layer 2:** 30 Neurons
    * **Accuracy Following Change:** 72.94%

3. After noticing slight drops in accuracy following the increase of neurons in our [2] hidden layers, an **additional (third) layer was added** in attempt to further improve model accuracy. While this adjustment to the model improved overall accuracy, further optimization is still required to achieve target accuracy.
    * **Hidden Layer 1:** 60 Neurons
    * **Hidden Layer 2:** 30 Neurons
    * **Hidden Layer 3:** 5 Neurons
    * **Accuracy Following Change:** 72.98%

4. While the previous step in optimization was promising in noticing improvements in accuracy, altering the amount of **neurons distributed** across each hidden layer seemed to greatly effect our resulting model accuracy.
    * **Hidden Layer 1:** 30 Neurons
    * **Hidden Layer 2:** 20 Neurons
    * **Hidden Layer 3:** 5 Neurons
    * **Accuracy Following Change:** 73.00%

5. Finally, running a test with only **2 hidden layers** and normalizing the distribution of layer parameters (*increased amount of nodes, monitoring shift in Param #*) the model reurns an increased accuracy.
    * **Hidden Layer 1:** 90 Neurons
    * **Hidden Layer 2:** 40 Neurons
    * **Accuracy Following Change:** 73.10%


#### Were you able to achieve the target model performance?
No, the highest accuracy the model received was **73.10%**


## Summary
**Highest Model Accuracy Returned:** `73.10%` 
**Target Accuracy:** `75%`

While our model did not achieve the target accuracy (75%), further testing and optimization to our test model's cut-off values, random state, hidden layers and nodes can help to further improve overall model accuracy. I found myself utilizing a trial and error method when selecting the amount of nodes/hidden layers to assign my model. I was able to reach an accuracy of 73% with the addition of a third hidden layer, only after decreasing the node count for each layer. Finally, running a test with only **2 hidden layers** and normalizing the distribution of hyperparameters (*done through increasing hidden layer node counts*) the model reurns a final accuracy of **73.10%**. 

Throughout testing, different amounts of **epochs** were used to adjust the training regimen, landing on 80 to receive the best return with the most consistent results (*Tested with the following number of epochs: 30, 40, 50, 60, 80, 100*). The **activations functions** were purposefully selected for each layer, with `ReLu` representing our hidden layers with efficiency, and `Sigmoid` assigned to our output layer for binary classifation. These variables remained consistent throughout the optimization of our model. The amount of **epochs** can be further experimented with to achieve target accuracy.

More tests need to be conducted in order to achieve target model accuracy and improve consistency of acceptable performance. Next steps to further improve this model include further segmenting the data studied by our model and adjusting for rare occurences or outliers. Creating new features to target with the available data can provide further insight into whether or not funding will be 'successful.' My first thought would be to further filter by `income classification` vs. `ask amount`, removing any outliers in which we can say with high certainty will not result in successful funding prior to providing our model with data. Additionally, further testing of cutt-off threshholds, random states and hidden layers with various node counts can provide additional insight into producing a consistently accurate model. Given more time and additional optimization trials, the optimal amount of hidden layers and neurons can be more confidently selected, providing more accurate results from the model.

### Recommendations
To solve this classification problem, we can attempt creating alternative models:
* **K-Nearest Neighbors:** This model could be used to further improve our model accuracy by adding weight to more significant/similar values, decreasing the importance of outliers.
 * **Random Forest:** Further categorize and sample the data for our model by filtering out rows that don't meet our list of categorical requirements in preprocessing.


## Resources
* [Convert Categorical Variable to Numeric](https://www.geeksforgeeks.org/how-to-convert-categorical-variable-to-numeric-in-pandas/)
* [Selecting Number of Epochs to Train Neural Network in Keras](https://www.geeksforgeeks.org/choose-optimal-number-of-epochs-to-train-a-neural-network-in-keras/)
* [Choosing Activation Functions for Deep Learning](https://machinelearningmastery.com/choose-an-activation-function-for-deep-learning/)
* [RELU and SIGMOID Activation Functions in a Neural Network](https://www.shiksha.com/online-courses/articles/relu-and-sigmoid-activation-function/#Sigmoid-vs-ReLU-Activation-Function:)
* [Introduction to Activation Functions in Neural Networks](https://www.datacamp.com/tutorial/introduction-to-activation-functions-in-neural-networks)
* [Choose Number of Hidden Layers and Nodes](https://stats.stackexchange.com/questions/181/how-to-choose-the-number-of-hidden-layers-and-nodes-in-a-feedforward-neural-netw)
* [Stackoverflow - Number of Hidden Layers and Nodes](https://stackoverflow.com/questions/55760636/decide-how-many-layers-and-neurons-to-set-in-an-ann)