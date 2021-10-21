# Analysis-of-Dropout-Phenomenon-in-Deep-Neural-Networks
The following project deals with the Analysis of the effects of dropouts on different parameters of Feed-Forward and Convolutional Neural Networks and derived relations between them. Proposed relation between Accuracy, Dropout rate, and Explainability of models using surrogate models.

**Effects of Dropouts on Neural Networks**

The main goal of the project is to study the effects of dropouts on the two specific fields of Deep Learning i.e Image Classification and Text Classification in order to achieve this goal we focus on the two main areas of a Neural Network namely “Effects on Model Parameters”, and “Effects on Feature Learning”. Model Parameters include the parameters based on which the performance of the model is judged here we have included six model features in our study namely Accuracy, Loss, Precision, Recall, ROC-AUC, and Learning Curve. 	In order to study the effects on feature learning, we use the concept of LIME(Locally Interpretable Model Agnostic Explanations). LIME in essence tells for a trained model that given a prediction made by the model what were the reasons for it to reach a particular decision, it treats any model fed to it as a black-box and for a given data sample it tweaks the parameters of the model to record the effects on the prediction made by the model and hence tries to predict which parameters for a given sample were most important in giving a prediction. 

For Image Classification, we used MNIST and CIFAR-10 datasets which are Grayscale and RGB datasets respectively. And for Text Classification, we have used the IMDB Review dataset. Various experimental setups were created in order to study the above-mentioned effects but in the big picture following were the steps taken to conduct the studies:

   1. Create the model pertaining to the dataset and whose features on which effects are to be studied i.e Feed-Forward or Convolutional Neural Networks
   2. Models created range from the dropout rates 0.0 to 0.9
   3. Models are trained on the needed dataset and its effects on the Learning curve are recorded
   4. During Test-Time analysis other model parameters are recorded to study effects on them
   5. LIME is used if needed to study the features most effective in the predictions made and draw relations between interpretability and dropout rates.

**Results and Discussions**
      
After conducting the above experiments following are the results on which we reach:

1. **For Convolutional Networks:**	

   **CIFAR - 10:** 

   The most suitable dropout rate to use in this case is p = 0.3, since it gave the best    value for model parameters in comparison to the rest of the rates in the given range of 0.0 to 0.9
	
   **MNIST:** 

   The most suitable dropout rate to use in this case is p = 0.4, since it gave the best value for a majority of model parameters including accuracy, precision, and ROC-AUC. According to the learning curve the best fit was of the model with p = 0.6.

2. **For Feed-Forward Networks:**

   **MNIST:** 
   
   The most suitable dropout rate in this case is p = 0.2 as it gave the best fit according to the learning curve and also the least loss. Other model parameters had variable optimum dropout rates but always remained in the range of 0.1 to 0.3.

3. When the models are trained with and without dropout for the same number of steps but with a varying batch size and epochs adjusted according to it, even though the accuracy in case of models with dropout is lower than the other, it is observed that the jump in the accuracy with increase in batch size is greater in the case of models with dropout.

Accuracy for LENET - 5 architecture without Dropout for varying Batch Sizes

![bs1](https://user-images.githubusercontent.com/48019495/116078450-3ea11400-a6b4-11eb-9c60-c82334ca4dce.png)

Accuracy for LENET - 5 architecture with 0.3 Dropout Rate for varying Batch Sizes

![bs2](https://user-images.githubusercontent.com/48019495/116078470-4660b880-a6b4-11eb-9463-ee9ad6ff3b61.png)


4. In case of Text Classification it was observed that the model was very complex for the dataset chosen and therefore without dropout the model was overfitting the dataset and gave the best accuracy and the fit when most of the neurons were lost at very high dropout rates. In such cases applying dropouts might not be a remedy towards over fitting as the model should be made less complex in terms of its architecture according to the dataset.

5. On studying the effects on feature learning it was observed that given a model adheres to our assumptions it was evident from the explanations of the surrogate models that as the dropouts were increasing the interpretability of the model was increasing in the case of both CIFAR-10 and MNIST.

  Mathematical Presentation: 
  
 ![Capture321](https://user-images.githubusercontent.com/48019495/116080118-4cf02f80-a6b6-11eb-8722-2facf53a7f67.PNG)



