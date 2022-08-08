---
title: Python Modularity2
author: JUNG YoungKyun
date: 2022-08-03
category: 19 study
layout: post
---

# 8주차 : Python Modularity
1. Understanding the Python Modularity Script
    - Please download the new titanic data on the Teams channel, there are two data, **train.csv** and **test.csv**
    - Please find the python script for 7th week, **week7-problem.py**
    - Open the file and please understand for each sections/steps
    - Run the script on your local computer
    - Ge some insights !

2. Change the script !
    - Previously, you already learn about python main function: **if __name__ == ‘__main__’**
    - Your task is to change the script by adding a main function ! (see on the next page)
    - Please save your work with different filename

```python
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
import os

... 

# Importing the dataset
train = pd.read_csv("D:/FURANZU/CODE/dataset/train.csv")
test = pd.read_csv("D:/FURANZU/CODE/dataset/test.csv")

# Age categories.
def process_age(df, cut_points, label_names):
    df["Age"] = df["Age"].fillna(-0.5)
    df["AgeCategory"] = pd.cut(df["Age"], cut_points, labels=label_name)

    return df

cut_points = [-1, 0, 5, 12, 18, 35, 60, 100]
label_names = ["Missing", "Infant", "Child", "Teenager", "YoungAdult", "Adult", "Senior"]

train = process_age(train, cut_points, label_names)
test = process_age(test, cut_points, label_names)

...
...

pickle.dump(
    best_model[1],
    open(f"{best_model[0].lower().replace(' ', '_')}_classifier.model",
    "wb"))

(no main function)

```

Change to ⬇

```python
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
import os

... 

# Importing the dataset
train = pd.read_csv("D:/FURANZU/CODE/dataset/train.csv")
test = pd.read_csv("D:/FURANZU/CODE/dataset/test.csv")

# Age categories.
def process_age(df, cut_points, label_names):
    df["Age"] = df["Age"].fillna(-0.5)
    df["AgeCategory"] = pd.cut(df["Age"], cut_points, labels=label_name)

    return df

cut_points = [-1, 0, 5, 12, 18, 35, 60, 100]
label_names = ["Missing", "Infant", "Child", "Teenager", "YoungAdult", "Adult", "Senior"]

train = process_age(train, cut_points, label_names)
test = process_age(test, cut_points, label_names)

...
...

pickle.dump(
    best_model[1],
    open(f"{best_model[0].lower().replace(' ', '_')}_classifier.model",
    "wb"))

if __name__ == ‘__main__’:
   (your code here !)

```

Task: 
    
>In the current script, you MAY NOT found **if __name__ == ‘__main__’** function.
Please add main function on the script (HINT: you may change some parts into the main function, so the structure of the code will be changed)
Please refer to this [page](https://github.com/tamanna18/Titanic-Survival-prediction/tree/01a8ae07e5e64da11e7188734fda2645d662dff9) as your reference.

# 풀이

```python
# -*- coding: utf-8 -*-
"""
Created on Fri Jul 22 18:42:56 2022

@author: franz
"""

import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
import os

from sklearn.metrics import accuracy_score
from sklearn.metrics import confusion_matrix
from sklearn.model_selection import cross_val_score

import pickle
from sklearn.linear_model import LogisticRegression
from sklearn.neighbors import KNeighborsClassifier
from sklearn.svm import SVC
from sklearn.naive_bayes import GaussianNB
from sklearn.tree import DecisionTreeClassifier
from sklearn.ensemble import RandomForestClassifier, GradientBoostingClassifier

class Model:
    classifier_type = [ "Logistic Regression", "KNN", "SVM", "Kernel SVM", "Gaussian Naive Bayes", "Decision Tree",
            "Random Forest", "Gradient Boost" ]

    best_accuracy = 0
    best_model = None

    # 나이에 따라 분류
    def process_age(self, df, cut_points, label_names):
        # fillna 는 결측값을 채우는 함수 입니다.
        # 나이를 -0.5 로 채우고 있는것 같아 보임;
        df["Age"] = df["Age"].fillna(-0.5)

        # cut 은 분류를 해주는 것, 가령 나이에 따라 young, old 등으로
        df["AgeCategory"] = pd.cut(df["Age"], cut_points, labels=label_names)

        return df

    # 리스트 안에 title 명 이 있는지 없는지 구분
    def titles_in_name(self, name: str, titles: list):
        for title in titles:
            if title in name:
                return title
        return np.nan

    # title 명에 따라 Mr, Mrs, Miss 분류
    def categorize_titles(self, person):
        title = person["Title"]

        if title in ["Don", "Major", "Capt", "Jonkheer", "Rev", "Col"]:
            return "Mr"
        elif title in ["Countess", "Mme"]:
            return "Mrs"
        elif title in ["Mlle", "Ms"]:
            return "Miss"
        elif title in ["Dr"]:
            if person["Sex"] == "Male":
                return "Mr"
            else:
                return "Mrs"
        else:
            return title

    def add_encoded_columns(self, df, column):
        # get_dummies 는 전처리 함수 입니다.
        dummies = pd.get_dummies(df[column], prefix = column)
        # 동일한 데이터 속성? 구조? 인 경우 합쳐줍니다. sql 에서 union 느낌인거 같습니다.
        df = pd.concat([df, dummies], axis = 1)

        return df

    #########################################################################################################

    def __init__(self):
        cut_points = [-1, 0, 5, 12, 18, 35, 60, 100]
        label_names = ["Missing", "Infant", "Child", "Teenager", "YoungAdult", "Adult", "Senior"]
        train = pd.read_csv("./data/train.csv")
        test = pd.read_csv("./data/test.csv")

        self.train = self.process_age(train, cut_points, label_names)
        self.test = self.process_age(test, cut_points, label_names)
        self.title_list = ["Mrs", "Mr", "Master", "Miss", "Major", "Rev",
                        "Dr", "Ms", "Mlle","Col", "Capt", "Mme", "Countess",
                        "Don", "Jonkheer"]
        self.categorical_features = ["AgeCategory", "Sex", "Embarked", "Pclass", "Title"]
        self.columns = ["Fare", "AgeCategory_Infant", "AgeCategory_Child", "AgeCategory_Teenager", "AgeCategory_YoungAdult", "AgeCategory_Adult", "AgeCategory_Senior", "Sex_female", "Sex_male", "Embarked_C", "Embarked_Q", "Embarked_S", "Pclass_1", "Pclass_2", "Pclass_3", "FamilySize", "Title_Mr", "Title_Mrs", "Title_Miss", "Title_Master"]
        self.classifiers = {
            "Logistic Regression": LogisticRegression(random_state = 0, solver="lbfgs", max_iter = 10000),
            "KNN": KNeighborsClassifier(n_neighbors = 5, metric = "minkowski", p = 2),
            "SVM": SVC(kernel = "linear", random_state = 0),
            "Kernel SVM": SVC(kernel = "rbf", random_state = 0),
            "Gaussian Naive Bayes": GaussianNB(),
            "Decision Tree": DecisionTreeClassifier(criterion = "entropy", random_state = 0),
            "Random Forest": RandomForestClassifier(criterion = "entropy", n_estimators = 100, random_state = 0),
            "Gradient Boost": GradientBoostingClassifier()
        }

    def feature_engineering(self):
        self.train["FamilySize"] = self.train["SibSp"] + self.train["Parch"] + 1
        self.test["FamilySize"] = self.test["SibSp"] + self.test["Parch"] + 1
    
    def title(self):
        self.train["Title"] = self.train["Name"].map(lambda x: self.titles_in_name(x, self.title_list))
        self.test["Title"] = self.test["Name"].map(lambda x: self.titles_in_name(x, self.title_list))

        self.train["Title"] = self.train.apply(self.categorize_titles, axis=1)
        self.test["Title"] = self.test.apply(self.categorize_titles, axis=1)

    def encode(self):
        for feature in self.categorical_features:
            self.train = self.add_encoded_columns(self.train, feature)
            self.test = self.add_encoded_columns(self.test, feature)

    def fillna(self):
        self.train["Fare"] = self.train["Fare"].fillna((self.train["Fare"].mean()))
        self.test["Fare"] = self.test["Fare"].fillna((self.test["Fare"].mean()))

    def export_csv(self, prediction, type = "Logistic Regression"):
        holdout = self.test
        holdout_ids = holdout["PassengerId"]
        submission_df = {"PassengerId": holdout_ids,
                        "Survived": prediction}

        submission = pd.DataFrame(submission_df)
            
        # export prediction results to csv
        outname = f'titanic_{type}.csv'
        outdir = './prediction'
        filename = os.path.join(outdir, outname)
        
        if not os.path.exists(outdir):
            os.mkdir(outdir)
        
        submission.to_csv(filename, index=False)

    def prepare_set(self):
        columns = ["Fare", "AgeCategory_Infant", "AgeCategory_Child", "AgeCategory_Teenager", "AgeCategory_YoungAdult", "AgeCategory_Adult", "AgeCategory_Senior", "Sex_female", "Sex_male", "Embarked_C", "Embarked_Q", "Embarked_S", "Pclass_1", "Pclass_2", "Pclass_3", "FamilySize", "Title_Mr", "Title_Mrs", "Title_Miss", "Title_Master"]
        self.X_all = self.train[columns]
        self.y_all = self.train["Survived"]

    def predict(self, type = "Logistic Regression"):
        columns = ["Fare", "AgeCategory_Infant", "AgeCategory_Child", "AgeCategory_Teenager", "AgeCategory_YoungAdult", "AgeCategory_Adult", "AgeCategory_Senior", "Sex_female", "Sex_male", "Embarked_C", "Embarked_Q", "Embarked_S", "Pclass_1", "Pclass_2", "Pclass_3", "FamilySize", "Title_Mr", "Title_Mrs", "Title_Miss", "Title_Master"]
        holdout = self.test

        classifier = self.classifiers[type]

        print(f"\n--- {type} ---")
        scores = cross_val_score(classifier, self.X_all, self.y_all, cv = 10)
        accuracy = np.mean(scores)
        min = np.min(scores)
        max = np.max(scores)

        if accuracy > Model.best_accuracy:
            Model.best_accuracy = accuracy
            Model.best_model = (type, classifier)

        print(f"\nAccuracy: {accuracy}\nMin: {min}\nMax: {max}\n")
        print("Fitting on all data, predicting test data...\n")
        
        # train and predict
        classifier.fit(self.X_all, self.y_all)
        return classifier.predict(holdout[columns])

# main function
if __name__ == '__main__':
    model_instance = Model()

    # train model
    model_instance.feature_engineering()
    model_instance.title()
    model_instance.encode()
    model_instance.fillna()
    model_instance.prepare_set()

    for classifier_type in Model.classifier_type:
        prediction = model_instance.predict(classifier_type)
        model_instance.export_csv(prediction, classifier_type)

    print('best_model : ')
    print(Model.best_model)


    print('best_accuracy : ')
    print(Model.best_accuracy)
```

사실 문제 의도 파악이 되지 않았습니다.
일단 main function 에서 모듈을 호출하여 예측하도록만 변경했는데, 의도와 맞는지는 잘 모르겠네요.