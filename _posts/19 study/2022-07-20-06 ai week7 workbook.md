---
title: Python Modularity
author: JUNG YoungKyun
date: 2022-07-20
category: 19 study
layout: post
---

# 7주차 : Python Modularity
1. For your personal practice​
    - Please try to understand the flow on how to make a machine learning model (from data loading until model testing)​
    - Change some parts on your code using python function (if possible) to make it modular​
2. Python class introduction​
    - Find the new dataset on the Teams folder ‘weatherHistory.csv’​
    - Find the example code on the Teams folder ‘week6-problem.py’​
    - Open the code on your local computer. In this time, you can use the IDE​
        - Suggested: Spyder, Visual Studio Code, Notepad++ ​
    - Try to understand the flow first ​
3. Running the Python script (running the .py file)​
    - Please run the code and get the result. ​
    - Try to run with the following options:​
        - Option 1: please run the code from directly your IDE (references: vscode, spyder)​
        - Option 2: please run the code using command line (references: article, article, article)​

4. Update the script: Data Loading​
    - Currently, the data is defined by static (i.e., /data/filename.csv)​
    - Please change the data loading section with more flexibility:​
        - User define the path (e.g., file directory address), and​
        - User define the filename (e.g., mydata.csv)​
        
    ![Data Loading](../images/19 study/06/04 Data Loading​.png)
    *Hint: data loading part*
    
5. Update the script: Add more classifiers​
    - Add one more classifiers on the script​
    - Please add DecisionTreeRegressor as an additional classifier. So, we will have 3 classifiers in total !​
    
    ![Add more classifiers](../images/19 study/06/05 Add more classifiers​.png)
    *Hint: classifiers part*
    
6. Update the script: Number of features​
    - Currently, the number of features is limited to 3 features (i.e., humidity, )​
    - Try to add one or two more features on the features​
    - Run, and see the difference with the previous result (i.e., with 2 features) !​
    
    ![Number of features​​](../images/19 study/06/06 Number of features​.png)
    *Hint: features part*
    
​7. Update the script: Add data preprocessing or feature engineering
- Previously, you learned about data preprocessing, such as:​
    - Data imputation (i.e., fill the missing value)​
    - Data filtering​
    - Feature extraction (i.e., create a new feature)​
    - Feature encoding ​
    - Feature transformation (i.e., data standardization, normalization)​
- In the existing python script, there is no any data preprocessing or feature engineering steps​
- Please add any the data preprocessing or feature engineering steps on the script​
    - You should add two processes at least, for example: fill the missing value and data standardization​
- Then, run the code and get the result​
    - The ultimate goal for this step is to increase the accuracy score
    
8. 기타
    - [1분 파이썬 강좌](https://www.youtube.com/watch?v=sj4vexbygKA&list=PLMsa_0kAjjrcxiSJnHNfzBN71D3zpYtkX&ab_channel=%EB%82%98%EB%8F%84%EC%BD%94%EB%94%A9)