---
title: 05 ai week6 workbook
author: JUNG YoungKyun
date: 2022-07-13
category: 19 study
layout: post
---

# 6주차 : Data Splitting & Model Loading
1. Data splitting: Split the data into training and test dataset
    1. Please [read](https://towardsdatascience.com/understanding-train-test-split-scikit-learn-python-ea676d5e3d1) on what is the training set and testing set in advance (e.g., what is feature, what is target label)
    1. Split the preprocessed dataset into training set (80%) and testing set (20%) (hint: use train_test_split)
        1. output: X_train, X_test, y_train, y_test
1. ML model: Create a classifier (machine learning model)
    1. Let’s try to make a simple Decision Tree classifier for our problem (hint: use DecisionTreeClassifier)
    1. Define your Decision Tree Classifier ([read](https://towardsdatascience.com/understanding-train-test-split-scikit-learn-python-ea676d5e3d1) here)
1. ML model: Train and test the classifier
    1. Train the classifier using the training data ! (hint: use “fit”)
    1. Test the classifier by creating predictions using the testing data (hint: use “predict”)  output: a list of prediction (e.g., y_pred)
    1. Show the accuracy score between y_test and y_pred
1. ML model: Load pre-trained model
    1. Find the pre-trained model (i.e., [dt_model_220707.pkl](./dt_model_220707.pkl)) on Teams folder
    1. Upload that model into your Jupyter Hub directory, place it in folder “model” (please make it first !)
    1. Load that model and create predictions using that model 
    1. Show the accuracy score ! (hint: use accuracy_score)
1. Watch and get insights from online lecture video 
    1. Please watch the lecture video until next Tuesday (2022.07.12)
    1. Get some idea or insights from the video
    1. Share with others on the next seminar session if you found some interesting parts from the video 
    1. Link: 
        1. [YouTube : 93. 머신러닝 파이프라인의 이해 (Annotation AI 이광희 CTO)](https://www.youtube.com/watch?v=hRqmBFd0juw&ab_channel=AI%ED%94%84%EB%A0%8C%EC%A6%88)
        1. [머신러닝 파이프라인의 이해.pdf](../images\15.02 ai traning\05\머신러닝 파이프라인의 이해_2021215.pdf){:target="_blank"}
1. Share any cool tips 꿀팁 to others !
    1. Found one or more cool tips to make other members can enjoy when study, or to finish their work/job, etc.
    1. You can share any cool tips ! 
    1. Only cool tips related to study or work-life are allowed, not for holiday or SNS 
