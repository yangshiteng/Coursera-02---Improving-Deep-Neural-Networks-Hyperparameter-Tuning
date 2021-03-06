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
- Gradient Approximation 
![image](https://user-images.githubusercontent.com/60442877/154787217-1a7d2688-05b4-4f93-ac98-1bbb023d9217.png)
- Two side approximation is more accurate than one side approximation
- For gradient checking, we rather use two side approximation for its accuracy
- Gradient Checking is a technique that can  be used to help people save tons of time and help people find bugs in implementations of back-propagation, it is implemented by compare the approximated gradient (two side approximation) with the calculated gradient by the following formula:
![image](https://user-images.githubusercontent.com/60442877/154817590-ec2d092b-9144-4822-919f-b3321a4630dc.png)
- Don't use gradient checking in training, only to debug
- If algorithm fails gradient checking, look at components in gradient vector to try to identify bug
- If you use regularization, don't forget it
- Gradient checking doesn't work with dropout regularization
- Run at random initialization
![image](https://user-images.githubusercontent.com/60442877/154818037-3f162df1-010c-48ec-90dc-cfdd6ea81f82.png)
![image](https://user-images.githubusercontent.com/60442877/154818968-a45d569c-e45f-4859-986c-9965530d4f17.png)
![image](https://user-images.githubusercontent.com/60442877/154820442-9392724e-c226-4afb-b2bb-2486da49423b.png)
![image](https://user-images.githubusercontent.com/60442877/154822540-6e7ea439-adb1-4ed8-b83d-c447480dfa18.png)
![image](https://user-images.githubusercontent.com/60442877/154825473-0891bdd7-4bc7-4d66-9124-0642b4c72f98.png)


# Week 2 - Optimization Algorithms

- Optimization Algorithms enable you to train your Neural Network much faster
- Deep Learning tends to work best in the regime of big data and training on a large dataset is just slow. Having fast optimization algorithms can really speed up the efficiency of your project

## Week 2 - Mini-batch Gradient Descent

- split up your big training dataset into smaller little baby training datasets and these baby training datasets are called mini-batches
- When you have large training dataset, Mini-batch Gradient Descent runs much faster than batch gradient descent (just vectorization implementation for whole dataset)
![image](https://user-images.githubusercontent.com/60442877/154870804-16ce94ba-5f0c-4184-9cad-0dbc105cc6bb.png)
- epoch is a word that means a single pass through the training dataset
- With batch gradient descent, a single pass through the training dataset allows you to take only one gradient descent update step
- With mini-batch gradient descent, a single pass through the training dataset, that is one epoch, allows you to take 5000 gradient descent update steps
- If you want to take multiple passes through the tranining dataset, just add another for loop 
- Cost function curve comparison between Batch Gradient Descnet and Mini-batch gradient Descent
![image](https://user-images.githubusercontent.com/60442877/154870996-040b046e-8ccd-4aae-988b-13ef71f678a1.png)
- If mini-batch size = m (the number of observations), then, its just batch gradient descent
- If mini-batch size = 1, then, it is Stochastic Gradient Descnet (never converge), every observation is a mini-batch
![image](https://user-images.githubusercontent.com/60442877/154871701-faa454b0-5654-4354-bd4a-343f4e7343d7.png)

## Week 2 - Exponentially Weighted Moving Averages

![image](https://user-images.githubusercontent.com/60442877/154874603-c1d27ee4-a367-4c30-916d-e7f040312743.png)
- Bias Correction
![image](https://user-images.githubusercontent.com/60442877/154883316-82cd436a-dccc-4b30-b4e4-c5c8457b6dfd.png)

## Week 2 - Gradient Descent with Momentum

- always works faster than the stardard gradient descent algorithm
- the basic idea is to compute an exponentially weighted moving average of your gradients, and then use that gradient to update your weights instead
![image](https://user-images.githubusercontent.com/60442877/154883250-8654bd3e-1d32-4361-b0da-c62fe9516ffc.png)

## Week 2 - RMSprop (Root Mean Square prop)

- Speed up gradient descnet
![image](https://user-images.githubusercontent.com/60442877/154987314-9bd79825-ca32-4261-b84c-fc5eebb8b8c9.png)

## Week 2 -  Adam Optimization Algorithm

- the combination of Momentum and RMSprop 
- Adam stands for Adaptive moment estimation
![image](https://user-images.githubusercontent.com/60442877/154989783-ac9bdbb6-7539-454c-bea7-9e0021cf65de.png)
![image](https://user-images.githubusercontent.com/60442877/154995244-3ca72825-6b51-4deb-b061-9afaad0748a3.png)

## Week 2 - Learning Rate Decay

- speed up your leanring algorithm by slowly reducing your leanring rate overtime
- 1 epoch = 1 pass through the data
- Mainly used for min-batch gradient descent, cause it will not converge. 
![image](https://user-images.githubusercontent.com/60442877/155000185-fd8ac073-b1e8-4699-a33f-f150e5c81031.png)
![image](https://user-images.githubusercontent.com/60442877/155000251-cca6f540-95cb-4602-9438-23ac121298e8.png)
![image](https://user-images.githubusercontent.com/60442877/155000312-b5d4930b-563b-4197-a50b-5de3e4e28e51.png)
- Don't worry about the local optima problem in Neural Network
- Momentum can help us reduce the oscillation of mini-batch gradient descent 
![image](https://user-images.githubusercontent.com/60442877/155270703-ca4033da-f1b1-4000-9ffb-4981ddcb56fe.png)
![image](https://user-images.githubusercontent.com/60442877/155272050-5a7b6c8a-369e-4037-b52b-173bc10d0520.png)
![image](https://user-images.githubusercontent.com/60442877/155272862-b2a89539-0973-400b-87d7-1e0aebedb203.png)

# Week 3 

## Hyperparameter Tuning

Hyperparameter tune:
1. learning rate
2. momentum beta
3. adam, momentum beta, RMSprop beta, epsilon in denominator to prevent 0
4. number of layers
5. number of hidden units
6. learning rate decay
7. mini-batch size
![image](https://user-images.githubusercontent.com/60442877/155861003-8356d7fb-6f03-4782-b439-a9e5385a8d4f.png)

Coarse to fine scheme:
1. Firstly find some points that work really wel
2. Then, zoom in to a smaller region that include these points
3. Then, try more points in this region
![image](https://user-images.githubusercontent.com/60442877/155861419-67eebeb7-5997-4b4b-8271-f215791139e6.png)

- Use random sampling, not grid search
- consider implementing the coarse to fine search process

![image](https://user-images.githubusercontent.com/60442877/155863069-bcb50b63-093f-4a81-8bac-fa8b7ffe1fdf.png)

## Batch Normalization

- make your hyperparameter search much easier
- make your Neural Network more robust
- very easy to train very deep Neural Network
- Normalize the input features can speed up the learning algorithm
![image](https://user-images.githubusercontent.com/60442877/155865601-15ab7bad-13b4-414a-89da-18fbe7b9eff7.png)
- gamma and beta are learnable parameters which means they can be optimized in gradient descent like W and b
![image](https://user-images.githubusercontent.com/60442877/155865955-b132486a-45e7-484c-81a3-e4334c27f283.png)
- When you are using the Batch Norm, there is no point to have bias term since this bias will be cancelled out during the normalization
![image](https://user-images.githubusercontent.com/60442877/155866396-993902c5-ceb8-42cf-a9bd-8e5ba0ca82c0.png)
![image](https://user-images.githubusercontent.com/60442877/155866603-57a40437-c505-4972-977d-aa69da98b794.png)


## Multi-class Classification

![image](https://user-images.githubusercontent.com/60442877/155870041-22f696a0-05f8-4c86-8b55-97492975204f.png)
The loss function of Multi-class Classification is: the negative of log of the predicted probability being the true label
![image](https://user-images.githubusercontent.com/60442877/155871603-d0df4756-150a-4d76-b9bf-137530dd91d9.png)

![image](https://user-images.githubusercontent.com/60442877/155871434-85a67df4-baf1-4756-8540-8013314d1290.png)

## Deep Learning Frameworks

![image](https://user-images.githubusercontent.com/60442877/155872553-1cb57c55-5353-4f37-86f5-41a0bc1e1090.png)





