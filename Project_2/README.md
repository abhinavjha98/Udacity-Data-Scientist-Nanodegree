# Disaster Response Pipeline Project
---

## Prerequisites
### Libraries
To be able to run this project, you need to install the required libraries in the `requirements.txt`. Run the command below.
```
pip install -r requirements.txt
```
### Model
You can build your own model using `train_classifier.py`.

---

## Introduction
In this project, we are going to built a web app to do Machine Learning task, which is classifying a message. If we breakdown, there are three major steps in this project.

### 1. ETL Process
We merge the dataset in the `data` folder (`disaster_messages.csv` and `disaster_categories.csv`), then do some preprocessing to get the clean data. We store the clean data in sqlite database `Disaster_db.db`.

### 2. Training Model
Using scikit-learn, then we train the classifier to be able to get a model which can classify a message, save the model in the `models` folder with the name `model.pkl`.

### 3. Run the Web App
Using flask, we can run our model and deploy in the website so that people can manually type the message and see its category. 

---

## Files

#### `data/disaster_categories.csv` , `data/disaster_messages.csv`

The dataset we use in this project, `disaster_messages.csv` contains the message (translated and original) and genre of the message. `disaster_categories.csv` contains the categories of each message.

#### `data/process_data.py`

This file is used for the ETL process, where we merge the `disaster_messages.csv` and `disaster_categories.csv` then store it in sqlite database.

#### `models/train_classifier.py`

This is where we train our model to obtain the classfier. We load the data from the sqlite database, do some text preprocessing using Count Vectorizer and TF-IDF, train the model, and save the model as a pickle object.

#### `app/run.py`

The flask application that being used to run the web app. You can modify the web page in the `app/templates/master.html` and `app/templates/go.html`.

---

## Instructions
1. Run the following commands in the project's root directory to set up your database and model.

    - To run ETL pipeline that cleans data and stores in database
        ```
        python data/process_data.py data/disaster_messages.csv data/disaster_categories.csv data/Disaster_db.db
        ```
    - To run ML pipeline that trains classifier and saves
        ```
        python models/train_classifier.py data/DisasterResponse.db models/model.pkl
        ```

2. Run the following command in the app's directory to run your web app. 
```
python run.py
```

3. Go to http://0.0.0.0:3001/
