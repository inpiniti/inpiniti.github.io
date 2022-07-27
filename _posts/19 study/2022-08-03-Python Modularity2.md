---
title: Python Modularity2
author: JUNG YoungKyun
date: 2022-07-20
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