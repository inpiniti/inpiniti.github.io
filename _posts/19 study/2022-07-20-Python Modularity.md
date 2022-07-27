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

7. Update the script: Add data preprocessing or feature engineering
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
    - youtube[1분 파이썬 강좌](https://www.youtube.com/watch?v=sj4vexbygKA&list=PLMsa_0kAjjrcxiSJnHNfzBN71D3zpYtkX&ab_channel=%EB%82%98%EB%8F%84%EC%BD%94%EB%94%A9)

아래는 과제를 수행 하면서 나온 결과 코드입니다.

```python
from sklearn.ensemble import RandomForestRegressor
from sklearn.linear_model import LinearRegression
from sklearn.model_selection import train_test_split
from sklearn.tree import DecisionTreeRegressor
from sklearn.preprocessing import OrdinalEncoder

import pandas as pd
import numpy  as np

# Define a class
class Model:
    
    def __init__(self, path = 'data', datafile = 'weatherHistory.csv', model_type = None):
        # load the data
        self.df = pd.read_csv(path+'/'+datafile)
        
        # init the classifier
        if model_type == 'rf':
            self.user_defined_model = RandomForestRegressor()
        elif model_type == 'dt':
            self.user_defined_model = DecisionTreeRegressor()
        else:
            self.user_defined_model = LinearRegression()
            
    
    def split(self, test_size, features_type = None):
        '''
        Splitting the data into features (X) and label (y)
        Then, split training and testing data (numpy operation)
        '''
        X = np.array(self.df[['Humidity', 'Pressure (millibars)']])

        # Update the script: Number of features
        if features_type == 'ws':
            y = np.array(self.df['Wind Speed (km/h)'])
        elif features_type == 'wb':
            y = np.array(self.df['Wind Bearing (degrees)'])
        else:
            y = np.array(self.df['Temperature (C)'])

        
        self.X_train, self.X_test, self.y_train, self.y_test = train_test_split(X, y, 
                                                                                test_size= test_size, 
                                                                                random_state=40)
    
    def fit(self):
        '''
        Training the model using training dataset
        '''
        self.model = self.user_defined_model.fit(self.X_train, self.y_train)
    
    def predict(self, input_value):
        '''
        Making prediction using testing data or new data
        '''
        if input_value == None:
            result = self.user_defined_model.predict(self.X_test)
        else:
            result = self.user_defined_model.predict(np.array([input_value]))
        return result
    
    def isna(self):
        print(self.df.isna().sum())
    
    def fillna(self, value = ''):
        self.df.fillna(value, inplace=True)

    def filtering(self, column):
        self.df = self.df.drop([column], axis = 1)

    def extraction(self, new_column, column, fn):
        self.df[new_column] = self.df[column].apply(fn)

    def dataFrame(self):
        print(pd.DataFrame(self.df))

    def encoding(self, column):
        ord_enc = OrdinalEncoder()
        self.df[[column]] = ord_enc.fit_transform(self.df[[column]]).astype(int)

def cold_hot(passenger):
    if passenger < 10:
        return '차가움'
    elif (passenger >= 11) and (passenger < 30):
        return '미지근함'
    elif (passenger >= 31) and (passenger < 40):
        return '따뜻함'
    elif passenger > 41:
        return '뜨거움'
    else:
        return '불가능'

if __name__ == '__main__':
        
    # init model
    model_instance = Model()

    # train model
    model_instance.split(0.2, 'ws')
    model_instance.fit()
    
    # make prediction with new data: humidity and pressure
    print(model_instance.predict([.8, 1000]))
    
    # print the model performance with accuracy score
    print("Accuracy: ", model_instance.model.score(model_instance.X_test, model_instance.y_test))

    # 누락 확인
    model_instance.isna()
    # Precip Type 517

    # 누락 치환
    model_instance.fillna()

    # 누락 확인
    model_instance.isna()
    
    # 필터링
    model_instance.dataFrame()
    model_instance.filtering('Daily Summary')
    model_instance.dataFrame()

    # 특징 추출
    model_instance.extraction('abc', 'Temperature (C)', cold_hot)
    model_instance.dataFrame()

    # 인코딩
    model_instance.encoding('abc')
    model_instance.dataFrame()
```

terminal
```
[10.28327687]
Accuracy:  0.051332330496865475
Formatted Date                0
Summary                       0
Precip Type                 517
Temperature (C)               0
Apparent Temperature (C)      0
Humidity                      0
Wind Speed (km/h)             0
Wind Bearing (degrees)        0
Visibility (km)               0
Loud Cover                    0
Pressure (millibars)          0
Daily Summary                 0
dtype: int64
Formatted Date              0
Summary                     0
Precip Type                 0
Temperature (C)             0
Apparent Temperature (C)    0
Humidity                    0
Wind Speed (km/h)           0
Wind Bearing (degrees)      0
Visibility (km)             0
Loud Cover                  0
Pressure (millibars)        0
Daily Summary               0
dtype: int64
                      Formatted Date        Summary Precip Type  Temperature (C)  Apparent Temperature (C)  Humidity  Wind Speed (km/h)  Wind Bearing (degrees)  Visibility (km)  Loud Cover  Pressure (millibars)                           Daily Summary
0      2006-04-01 00:00:00.000 +0200  Partly Cloudy        rain         9.472222                  7.388889      0.89            14.1197                   251.0          15.8263         0.0               1015.13       Partly cloudy throughout the day.
1      2006-04-01 01:00:00.000 +0200  Partly Cloudy        rain         9.355556                  7.227778      0.86            14.2646                   259.0          15.8263         0.0               1015.63       Partly cloudy throughout the day.
2      2006-04-01 02:00:00.000 +0200  Mostly Cloudy        rain         9.377778                  9.377778      0.89             3.9284                   204.0          14.9569         0.0               1015.94       Partly cloudy throughout the day.
3      2006-04-01 03:00:00.000 +0200  Partly Cloudy        rain         8.288889                  5.944444      0.83            14.1036                   269.0          15.8263         0.0               1016.41       Partly cloudy throughout the day.
4      2006-04-01 04:00:00.000 +0200  Mostly Cloudy        rain         8.755556                  6.977778      0.83            11.0446                   259.0          15.8263         0.0               1016.51       Partly cloudy throughout the day.
...                              ...            ...         ...              ...                       ...       ...                ...                     ...              ...         ...                   ...                                     ...
96448  2016-09-09 19:00:00.000 +0200  Partly Cloudy        rain        26.016667                 26.016667      0.43            10.9963                    31.0          16.1000         0.0               1014.36  Partly cloudy starting in the morning.
96449  2016-09-09 20:00:00.000 +0200  Partly Cloudy        rain        24.583333                 24.583333      0.48            10.0947                    20.0          15.5526         0.0               1015.16  Partly cloudy starting in the morning.
96450  2016-09-09 21:00:00.000 +0200  Partly Cloudy        rain        22.038889                 22.038889      0.56             8.9838                    30.0          16.1000         0.0               1015.66  Partly cloudy starting in the morning.
96451  2016-09-09 22:00:00.000 +0200  Partly Cloudy        rain        21.522222                 21.522222      0.60            10.5294                    20.0          16.1000         0.0               1015.95  Partly cloudy starting in the morning.
96452  2016-09-09 23:00:00.000 +0200  Partly Cloudy        rain        20.438889                 20.438889      0.61             5.8765                    39.0          15.5204         0.0               1016.16  Partly cloudy starting in the morning.

[96453 rows x 12 columns]
                      Formatted Date        Summary Precip Type  Temperature (C)  Apparent Temperature (C)  Humidity  Wind Speed (km/h)  Wind Bearing (degrees)  Visibility (km)  Loud Cover  Pressure (millibars)
0      2006-04-01 00:00:00.000 +0200  Partly Cloudy        rain         9.472222                  7.388889      0.89            14.1197                   251.0          15.8263         0.0               1015.13
1      2006-04-01 01:00:00.000 +0200  Partly Cloudy        rain         9.355556                  7.227778      0.86            14.2646                   259.0          15.8263         0.0               1015.63
2      2006-04-01 02:00:00.000 +0200  Mostly Cloudy        rain         9.377778                  9.377778      0.89             3.9284                   204.0          14.9569         0.0               1015.94
3      2006-04-01 03:00:00.000 +0200  Partly Cloudy        rain         8.288889                  5.944444      0.83            14.1036                   269.0          15.8263         0.0               1016.41
4      2006-04-01 04:00:00.000 +0200  Mostly Cloudy        rain         8.755556                  6.977778      0.83            11.0446                   259.0          15.8263         0.0               1016.51
...                              ...            ...         ...              ...                       ...       ...                ...                     ...              ...         ...                   ...
96448  2016-09-09 19:00:00.000 +0200  Partly Cloudy        rain        26.016667                 26.016667      0.43            10.9963                    31.0          16.1000         0.0               1014.36
96449  2016-09-09 20:00:00.000 +0200  Partly Cloudy        rain        24.583333                 24.583333      0.48            10.0947                    20.0          15.5526         0.0               1015.16
96450  2016-09-09 21:00:00.000 +0200  Partly Cloudy        rain        22.038889                 22.038889      0.56             8.9838                    30.0          16.1000         0.0               1015.66
96451  2016-09-09 22:00:00.000 +0200  Partly Cloudy        rain        21.522222                 21.522222      0.60            10.5294                    20.0          16.1000         0.0               1015.95
96452  2016-09-09 23:00:00.000 +0200  Partly Cloudy        rain        20.438889                 20.438889      0.61             5.8765                    39.0          15.5204         0.0               1016.16

[96453 rows x 11 columns]
                      Formatted Date        Summary Precip Type  Temperature (C)  Apparent Temperature (C)  Humidity  Wind Speed (km/h)  Wind Bearing (degrees)  Visibility (km)  Loud Cover  Pressure (millibars)   abc
0      2006-04-01 00:00:00.000 +0200  Partly Cloudy        rain         9.472222                  7.388889      0.89            14.1197                   251.0          15.8263         0.0               1015.13   차가움
1      2006-04-01 01:00:00.000 +0200  Partly Cloudy        rain         9.355556                  7.227778      0.86            14.2646                   259.0          15.8263         0.0               1015.63   차가움
2      2006-04-01 02:00:00.000 +0200  Mostly Cloudy        rain         9.377778                  9.377778      0.89             3.9284                   204.0          14.9569         0.0               1015.94   차가움
3      2006-04-01 03:00:00.000 +0200  Partly Cloudy        rain         8.288889                  5.944444      0.83            14.1036                   269.0          15.8263         0.0               1016.41   차가움
4      2006-04-01 04:00:00.000 +0200  Mostly Cloudy        rain         8.755556                  6.977778      0.83            11.0446                   259.0          15.8263         0.0               1016.51   차가움
...                              ...            ...         ...              ...                       ...       ...                ...                     ...              ...         ...                   ...   ...
96448  2016-09-09 19:00:00.000 +0200  Partly Cloudy        rain        26.016667                 26.016667      0.43            10.9963                    31.0          16.1000         0.0               1014.36  미지근함
96449  2016-09-09 20:00:00.000 +0200  Partly Cloudy        rain        24.583333                 24.583333      0.48            10.0947                    20.0          15.5526         0.0               1015.16  미지근함
96450  2016-09-09 21:00:00.000 +0200  Partly Cloudy        rain        22.038889                 22.038889      0.56             8.9838                    30.0          16.1000         0.0               1015.66  미지근함
96451  2016-09-09 22:00:00.000 +0200  Partly Cloudy        rain        21.522222                 21.522222      0.60            10.5294                    20.0          16.1000         0.0               1015.95  미지근함
96452  2016-09-09 23:00:00.000 +0200  Partly Cloudy        rain        20.438889                 20.438889      0.61             5.8765                    39.0          15.5204         0.0               1016.16  미지근함

[96453 rows x 12 columns]
                      Formatted Date        Summary Precip Type  Temperature (C)  Apparent Temperature (C)  Humidity  Wind Speed (km/h)  Wind Bearing (degrees)  Visibility (km)  Loud Cover  Pressure (millibars)  abc
0      2006-04-01 00:00:00.000 +0200  Partly Cloudy        rain         9.472222                  7.388889      0.89            14.1197                   251.0          15.8263         0.0               1015.13    3
1      2006-04-01 01:00:00.000 +0200  Partly Cloudy        rain         9.355556                  7.227778      0.86            14.2646                   259.0          15.8263         0.0               1015.63    3
2      2006-04-01 02:00:00.000 +0200  Mostly Cloudy        rain         9.377778                  9.377778      0.89             3.9284                   204.0          14.9569         0.0               1015.94    3
3      2006-04-01 03:00:00.000 +0200  Partly Cloudy        rain         8.288889                  5.944444      0.83            14.1036                   269.0          15.8263         0.0               1016.41    3
4      2006-04-01 04:00:00.000 +0200  Mostly Cloudy        rain         8.755556                  6.977778      0.83            11.0446                   259.0          15.8263         0.0               1016.51    3
...                              ...            ...         ...              ...                       ...       ...                ...                     ...              ...         ...                   ...  ...
96448  2016-09-09 19:00:00.000 +0200  Partly Cloudy        rain        26.016667                 26.016667      0.43            10.9963                    31.0          16.1000         0.0               1014.36    1
96449  2016-09-09 20:00:00.000 +0200  Partly Cloudy        rain        24.583333                 24.583333      0.48            10.0947                    20.0          15.5526         0.0               1015.16    1
96450  2016-09-09 21:00:00.000 +0200  Partly Cloudy        rain        22.038889                 22.038889      0.56             8.9838                    30.0          16.1000         0.0               1015.66    1
96451  2016-09-09 22:00:00.000 +0200  Partly Cloudy        rain        21.522222                 21.522222      0.60            10.5294                    20.0          16.1000         0.0               1015.95    1
96452  2016-09-09 23:00:00.000 +0200  Partly Cloudy        rain        20.438889                 20.438889      0.61             5.8765                    39.0          15.5204         0.0               1016.16    1

[96453 rows x 12 columns]
```