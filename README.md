# Disaster Response Pipeline NLP Project

## About the Project
This is Data Science project which classifies the disater messages from various sources into relavant categories. 
Here I'vd applied the data engineering to create an API that classifies disaster messages from sources like Twitter, text messages into 36 categories. Trained a model with predefined lables and applied supervised machine learning to classify the outcome.
In simple words, when a message is given, the alogrothim predicts the category of the given messages. 
ie. what is the message related to: water, food, shelter, money etc.?
ex: Please, we need tents and water. We are in Silo, Thank you!
Predection : Water and Tents Request.

The reason is that when disaster happens, there are millions of messages sent and tweeted to inform about it. However, disasters are taken care of different organizations. Food provision might be offered by a certain organization, while putting down fires would be taken care of a different organization. Hence,the utility of this application would be to categorize these messages into various types so that it can be understood what type of aid is necessary for a specific disaster.

## Structure 
There are three parts of the project:

1. ETL Pipeline
To Extract, transform and load the data in to a Database, here I've loaded two data set, processed and merged as single dataset and loaded into a SQLite database. This dataset is used to generate the model in the ML pipeline

2. ML Pipeline
The Machine Learing pipeline converts the dataset into a model, that can be used to predict the data. The first step is to load the data from dataset, text processing the data using  the nltk (Natural Language Tool Kit) then applying the RandomForest Classifier with GridSearchCV to select the best parameters. Followed by evaluating the model and finally loading the trained model in format of pickel file.

3. Flask Web App
A webinterface or a front end application, where users can give a message to predict the classification.

## Important Files
`data\process_data`, ETL Pipeline
`models\train_calssifier`, ML Pipeline
`app\run.py`, Flask application which loads the model and predict the classification for the given text
`app\templates\master.html`, HTML5 webpage for user interface to enter the message
`app\templates\go.html`, HTML5 webpage to display the prediction results

## To Run The APP
Run the following commands in the project's root directory to set up your database and model.

1. To run ETL pipeline that cleans data and stores in database `python data/process_data.py data/disaster_messages.csv data/disaster_categories.csv data/DisasterResponse.db`
To run ML pipeline that trains classifier and saves `python models/train_classifier.py data/DisasterResponse.db models/classifier.pkl`
2. Run the following command in the app's directory to run your web app. `python app/run.py`
3. Go to http://0.0.0.0:3001/