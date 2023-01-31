# deep-learning-challenge

# Overview 

The nonprofit foundation Alphabet Soup wants a tool that can help it select the applicants for funding with the best chance of success in their ventures. The purpose of this project, was to build a tool that can predict whether applicants will be successful if funded by Alphabet Soup using machine learning and neural networks.

# 1 -Data preprocessing

- EIN and NAME columns were removed from the data because they are neither targets nor features.

![image](https://user-images.githubusercontent.com/109463488/215876309-096adb64-8f15-4145-b16e-8fab5701cb74.png)

- I picked a cutoff point to bin "rare" categorical variables together in a new value.

![image](https://user-images.githubusercontent.com/109463488/215877179-6daf3381-461d-4da1-9bac-80c58a44d3cc.png)

![image](https://user-images.githubusercontent.com/109463488/215877243-64f8a96e-c8dc-4802-8004-d2a425e4f5b9.png)

- I converted categorical data to numeric with `pd.get_dummies`

![image](https://user-images.githubusercontent.com/109463488/215877502-88ec0efc-9f6a-433e-98fe-5e0c3b3547a1.png)

- I splitted the preprocessed data into features and target arrays, then splitted them into training and tesing datasets.

![image](https://user-images.githubusercontent.com/109463488/215877873-67fe17da-18f0-4aed-9b0d-2ce951f46c1e.png)

# 2 - Compiling, Training and Evaluating the Model

- I initially chose two hidden layers, with eight neurons in each layer, and a Relu function in each case.

![image](https://user-images.githubusercontent.com/109463488/215878230-29fe7f48-ad5d-412d-8149-b6bf79f208be.png)

** The model only achieved 72.5% accuracy, not reaching the 75% target.

![image](https://user-images.githubusercontent.com/109463488/215878723-a5c2f2eb-a833-4f82-8ca4-bb1ef48f57c8.png)

# 3- Optimisation

As I hadn't achieved the 75% accuracy target, I adopted several strategies:

## 3.1 Reducing the noise by dropping the outliers.

![image](https://user-images.githubusercontent.com/109463488/215879714-5fac279b-d714-4f3b-a63a-4a7d5f4d89f0.png)

![image](https://user-images.githubusercontent.com/109463488/215879772-b9e94efb-1f0e-4de0-831f-6fecb3834935.png)

I didn't change anything else from my model, and the accurary resulted in 71.5%, worse than before. So I decided that was not a good strategy.

## 3.2 Increasing the number of layers

Without dropping the outliers, I increased the number of layers and neurons.

![image](https://user-images.githubusercontent.com/109463488/215886326-b5b9450d-2a6f-44fb-a1ab-d425c9ee31b1.png)

Still not reaching the target accuracy.

## 3.3 Automated Neural Network optimisation

I decided to use an automated model optimizer to get the most accurate model possible by creating method that creates a keras Sequential model using the keras-tuner library with hyperparametes options.

![image](https://user-images.githubusercontent.com/109463488/215886743-144ad423-a490-454e-a8ee-6011d5c042ce.png)

But I still not reached the target

## 3.4 Going back to the raw data, and keeping column NAME.

Keeping the column NAME and letting keras-tuner decide activation function, number of layers and number of neurons.

![image](https://user-images.githubusercontent.com/109463488/215887311-852e3608-0cb3-456d-85f8-59f050c6b513.png)

I achieved 79.5% accuracy.

# Summary

The final automatically optimized neural network trained model from the keras tuner method achieved 79.5% prediction accuracy with a 0.452 loss, using a sigmoid activation function and 5 hidden layerss. Keeping the Name column was essential to achieve the target.



