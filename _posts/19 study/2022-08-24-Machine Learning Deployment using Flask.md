---
title: Machine Learning Deployment using Flask
author: JUNG YoungKyun
date: 2022-08-24
category: 19 study
layout: post
---

# 8주차 : Machine Learning Deployment using Flask
1. **Study: REST API with Flask**
    - Please read and try to understand about flask REST API (e.g.., how to create rest api with flask, how to call the api, etc.)
        - References:
            [article1](https://www.sqlshack.com/create-rest-apis-in-python-using-flask/),
            [article2](https://pythonbasics.org/flask-rest-api/),
            [article3](https://justkode.kr/python/flask-restapi-1)
    - Create a **simple project** on how to implement flask rest api !

2. **Deploying a Machine Learning Model with REST API Flask (모델 배포)**
    - Please read this following article: 
        [link](https://hackernoon.com/machine-learning-w22g322x)
    - Deploy a machine learning model using flask (with rest api)
        - Please follow the steps in the above-mentioned article and run on your local computer !
    - Additional Task:
        - On the article, they used **RandomForestRegressor** as classifier, **please change it with another type of classifier !**
            - You can choose the classifiers freely, e.g., linear model, decision tree, support vector machine, etc.
        - (optional) **Please make a simple UI** for this project (similar with the last week task)
            ```python
            # creating model
            from sklearn.ensemble import RandomForestRegressor
            classifier = RandomForestRegressor()
            classifier.fit(X_train, y_train)
            ```
3. **Deploying the project on the server**
    - Instead run the project on your local computer, **you can deploy the project on server** so other members can access your work
    - You might choose the server based on your preferences (e.g., Heroku, etc)  **give us any recommendations !**
    - Share your works with others ^^

4. **Try with other projects**
    - You can try with other problems/projects
    - For your references (choose one of them):
        - [https://wikidocs.net/143898](https://wikidocs.net/143898)
        - [https://niceman.tistory.com/192](https://niceman.tistory.com/192) 
        - [https://github.com/akashdeepjassal/mnist-flask](https://github.com/akashdeepjassal/mnist-flask)
        - Digital covid detection: 
            [link](https://blogs.sap.com/2020/06/28/digital-covid-19-detection-kit-based-on-chest-x-ray-using-machine-learning-and-sap-conversational-ai/) 


---

requirements.txt

```
Flask
numpy
scikit-learn
pandas
```

Dockerfile

```
FROM python:3.8-slim

WORKDIR /app

COPY . .

RUN pip install --no-cache-dir -r requirements.txt

EXPOSE 5000

CMD ["python", "./app.py"]
```

app.py

```python
import model # Import the python file containing the ML model
from flask import Flask, request, render_template,jsonify # Import flask libraries

# Initialize the flask class and specify the templates directory
app = Flask(__name__,template_folder="templates")

# Default route set as 'home'
@app.route('/home')
def home():
    return render_template('home.html') # Render home.html

# Route 'classify' accepts GET request
@app.route('/classify',methods=['POST','GET'])
def classify_type():
    try:
        sepal_len = request.args.get('slen') # Get parameters for sepal length
        sepal_wid = request.args.get('swid') # Get parameters for sepal width
        petal_len = request.args.get('plen') # Get parameters for petal length
        petal_wid = request.args.get('pwid') # Get parameters for petal width

        # Get the output from the classification model
        variety = model.classify(sepal_len, sepal_wid, petal_len, petal_wid)

        # Render the output in new HTML page
        return render_template('output.html', variety=variety)
    except:
        return 'Error'

# Run the Flask server
if(__name__=='__main__'):
    app.run(host='0.0.0.0', port=5000)
```

model.py

```python
# Importing necessary libraries
import pandas as pd
import numpy as np
from sklearn.linear_model import LogisticRegression

# Importing the dataset
data = pd.read_csv('iris.csv')

# Dictionary containing the mapping
variety_mappings = {0: 'Setosa', 1: 'Versicolor', 2: 'Virginica'}

# Encoding the target variables to integers
data = data.replace(['Setosa', 'Versicolor' , 'Virginica'],[0, 1, 2])

X = data.iloc[:, 0:-1] # Extracting the independent variables
y = data.iloc[:, -1] # Extracting the target/dependent variable

logreg = LogisticRegression() # Initializing the Logistic Regression model
logreg.fit(X, y) # Fitting the model

# Function for classification based on inputs
def classify(a, b, c, d):
    arr = np.array([a, b, c, d]) # Convert to numpy array
    arr = arr.astype(np.float64) # Change the data type to float
    query = arr.reshape(1, -1) # Reshape the array
    prediction = variety_mappings[logreg.predict(query)[0]] # Retrieve from dictionary
    return prediction # Return the prediction
```

templates/home.html

```html
<!DOCTYPE html>
<html>
<head>
	<meta charset="utf-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<title>Flower Variety</title>
	<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/bulma/0.9.0/css/bulma.min.css">
	<link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">
    <style>
        html{
            overflow: hidden;
        }

        body{
            position: absolute;
            width: 100%;
            height: 100%;
            margin: 0;
            padding: 0;
        }

        #login-form-container{
            position: absolute;
            width: 100%;
            height: 100%;
            display: flex;
            align-items: center;
            justify-content: center;
        }
    </style>
</head>	
<body>
    <div id="login-form-container">
        <form action="classify" method="GET">
            <div class="card" style="width: 400px">
            <div class="card-content">
                <div class="media">
                <div class="is-size-4 has-text-centered">Flower Variety Classification</div>
                </div>
                <div class="content">

                <div class="field">
                    <p class="control">
                    Sepal Length: <input class="input" type="number" value='0.00' step='0.01' name="slen" id="slen">
                    </p>
                </div>

                <div class="field">
                    <p class="control">
                    Sepal Width: <input class="input" type="number" value='0.00' step='0.01' name="swid" id="swid">
                    </p>
                </div>

                <div class="field">
                    <p class="control">
                    Petal Length: <input class="input" type="number" value='0.00' step='0.01' name="plen" id="plen">
                    </p>
                </div>

                <div class="field">
                    <p class="control">
                    Petal Width: <input class="input" type="number" value='0.00' step='0.01' name="pwid" id="pwid">
                    </p>
                </div>
                
                <div class="field">
                    <button class="button is-fullwidth is-rounded is-success">Submit</button>
                </div>
                </div>
            </div>
        </form>
    </div>
</body>
</html>
```

templates/output.html

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Flower Variety</title>
        <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/bulma/0.9.0/css/bulma.min.css">
        <link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">
        <style>
            html{
                overflow: hidden;
            }

            body{
                position: absolute;
                width: 100%;
                height: 100%;
                margin: 0;
                padding: 0;
            }

            #login-form-container{
                position: absolute;
                width: 100%;
                height: 100%;
                display: flex;
                align-items: center;
                justify-content: center;
            }
        </style>
    </head>	
    <body>
        <div id="login-form-container">
            <div class="card" style="width: 400px">
                <div class="card-content">
                    <div class="media">
                        <div class="is-size-4 has-text-centered">{{ variety }}</div>
                    </div>
                    <form action="home">
                        <div class="field">
                            <button class="button is-fullwidth is-rounded is-success">Retry</button>
                        </div>
                    </form>
                </div>
            </div>
        </div>
    </body>
</html>
```

[배포 된 app](http://20.214.141.2:5000/home)