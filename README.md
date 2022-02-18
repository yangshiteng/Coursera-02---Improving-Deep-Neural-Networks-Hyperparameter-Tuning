# Week 1

- Bias is the model performance among the training dataset, if the error is large, then, we say large bias, if error is small, then, we say it is low bias
- Variance is the model performance difference in training and testing dataset, if the difference is large, we say it is high variance, if the difference is small, we say it is low variance
- Training a bigger network almost never hurt, and the main cost of training a neural network that is too big is just computational time
- Regularization is a very useful technique for reducing variance (remedy overfitting), there is a little bit of a bias-variance tradeoff when you use regularization
- We often use L2-norm to perform the regularization
- The regularization term in Neural Network is called 'Frobenius Norm'
![image](https://user-images.githubusercontent.com/60442877/151812156-0fdbe91a-152b-4b23-a37c-3d04e1ea4b22.png)
- Regularization: Just add penalty term in the cost function
- If you take a very large value for lambda in Frobenius Norm, then, the weights will be closed to 0, and this will raise higher bias 
- L2-Regularization: Frobenius Norm
- Dropout Regularization: Randomly knock out units in the network
- Data Augmentation (prevent overfitting)
![image](https://user-images.githubusercontent.com/60442877/154621348-fcfae5c6-a417-4335-afad-47807968bcdf.png)
- Early Stopping (prevent overfitting)
![image](https://user-images.githubusercontent.com/60442877/154622313-b2e0e16c-bb33-40dc-9a37-650abbd57d9a.png)
- Normalization of training sets: when training a neural network, one of the techniques to speed up your training is if you normalize your inputs
![image](https://user-images.githubusercontent.com/60442877/154623244-2d761e2f-2c61-4392-90bf-93fa92319f90.png)
- Vanishing or Exploding Gradients problem (the gradient can be either very small or very high), usually for the very deep neural networks
- A partial solution to this Vanishing or Exploding Gradients problem is the more careful choice of the random initialization 
![image](https://user-images.githubusercontent.com/60442877/154625895-cd3e771b-9839-495e-91a9-d7f618cc1bbb.png)

