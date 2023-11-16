# deep-learning-challenge

The purpose of the Alphabet Soup analysis is to utilize a neural network to develop a deep learning model that will be used to predict which applicants that have applied for funding from the Alphabet Soup nonprofit foundation will successfully use the funds. The model is then evaluated for its accuracy based on training and testing data from 34,000 organizations that have previously been granted funding by Alphabet Soup.

## Results

* Data Preprocessing
  * The target variable for the model is the IS_SUCCESSFUL variable, indicating whether or not the organization successfully utilized the funding.
  * The feature variables for the model are APPLICATION_TYPE, AFFILIATION (sector of industry), CLASSIFICATION (Government organization classification), USE_CASE, ORGANIZATION (organization type), STATUS, INCOME_AMT, SPECIAL_CONSIDERATIONS, and ASK_AMT (requested funding amount).
  * The EIN and NAME identification columns were removed as they have no impact on whether or not the funding was used successfully.
* Compiling, Training, and Evaluating the Model
  * How many neurons, layers, and activation functions did I select and why? Initally, the following was used to train the model:
    * Layer 1 - 129 neurons (# of input features * 3), activation function: ReLU
    * Layer 2 - 86 neurons (# of input features * 2), activation function: ReLU
    * Output Layer - activation function: Tanh
    * The number of layers was selected to create a simple model to work from. The number of neurons are multiples of the number of input features, selected to balance resource usage and accuracy. ReLU was selected for the hidden layers as none of the input data was negative. Tanh was selected for the output layer as it is slightly simpler than ReLU.
  * The inital model had an accuracy of 72.35%, which was under the target accuracy of 75%.
  * The first round of optimization involved increasing the number of hidden layers from two to three in order to increase the number of calculations thus enabling the model to consider more interactions between variables. This resulted in an accuracy of 72.54%.
  * The second round of optimization kept the previous changes and changed output activation function to sigmoid, as the target variable only has values of 0 or 1. This resulted in an accuracy of 72.62%.
  * The third round of optimization kept the previous changes and increased the number of nodes in the third hidden layer from 86 to 129 in order to help reduce training loss and improve accuracy. This resulted in an accuracy of 72.63%.
  * For the fourth round of optimizaton, Keras tuner was used to optimize the model. However, Google Colab kept timing out before tuning was completed so the number of nodes and layers used for trainig the model were the best values produced by the tuner prior to timeout. Six layers were used (# of neurons were 129, 86, 43, 129, 86, 43). The ReLU activation function was used in every hidden layer, sigmoid was used in the output layer. This resulted in an accuracy of 72.54%.

## Summary

The best performance achieved by the model was 72.63% accuracy, well below the target of 75%. The lack of performance increase after adjusting the number of neurons, layers, and activation functions indicates that better preprocessing of the data is required to improve accuracy. A supervised logistic regression model could be implemented as well, utilizing the same feature and target variables, as the features are already labeled and the desired training outcome is a binary classification - whether the funded organization successfully used the funds or not. 
