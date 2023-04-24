# Thyroid Disease Detection
  Thyroid disease is a very common problem in India, more than one crore people are suffering with the disease every year. Thyroid disorder can speed up or slow down     the metabolism of the body.

  The main objective of this project is to predict if a person is having compensated hypothyroid, primary hypothyroid, secondary hypothyroid or negative (no thyroid)     with the help of Machine Learning. Classification algorithms such as Random Forest, XGBoost and KNN Model have been trained on the thyroid dataset, UCI Machine         Learning repository. After hyperparameter tuning XGBoost model has performed well with better accuracy, precision and recall. Application has deployed on Heroku with   the help of flask framework
  
Application url:


Dataset url:
[Dataset](https://archive.ics.uci.edu/ml/datasets/thyroid+disease)

# Quickstart/Demo
  

https://user-images.githubusercontent.com/77872928/233975494-66d070cc-94d5-45a6-893a-25d5ec61fa19.mp4



# Table of Contents

- [Thyroid Disease Detection](#thyroid-disease-detection)
- [Quickstart/Demo](#quickstartdemo)
- [Table of Contents](#table-of-contents)
- [Data Discription](#data-discription)
- [Technical Aspects](#technical-aspects)
- [Architecture](#architecture)
- [Project WorkFlow](#project-workflow)
- [Development](#development)

# Data Discription
[(Back to top)](#table-of-contents)

The client will send data in multiple files in batches to a given location. Data will contain different classes of thyroid and 30 columns of different values. "Class" column will have four unique values “negative,compensated_hypothyroid, primary_hypothyroid, secondary_hypothyroid”.

we also require a "schema" file from the client, which contains all the relevant information about the training files such as: Name of the files, Length of Date stamp in FileName, Length of Time stamp in FileName, Number of Columns, Name of the Columns, and their datatypes.

# Technical Aspects
[(Back to top)](#table-of-contents)

1.Python
2.scikit-learn
3.Flask

# Architecture
[(Back to top)](#table-of-contents)

The process outline that we will follow in the project is as follows-

![image](https://user-images.githubusercontent.com/88799249/159979820-fc6c54a7-53ee-46a1-847c-75678dc2f3df.png)

# Project WorkFlow
[(Back to top)](#table-of-contents)

* Data Validation:-
We validate the name of the files based on the given name in the schema file. We have created a regex expression as per the name given in the schema file to use it for our validation. After validating the pattern in the name, we check the length of date in the file name & length of time in the file name. If all the values are as per the schema file, we move these files to "Good_Data Folder" else we move such files to "Bad_Data Folder."

* Data Preprocessing
converts all the columns with string data type so that each value for that column is enclosed in quotes.
1. Data Insertion in Database
2. Database Creation and Connection 
3. Table creation in the database 
4. Create a Table with name 
5. Insertion of files into the table -

* Clustering - KMeans algorithm is used to create clusters in the pre-processed data. Select the number of clusters by using "KneeLocator" function. Now, the Kmeans model is trained and the model is saved for the further use during prediction.

* Model Selection - After clusters are created, we find the best model for each cluster. Here, we are using two algorithms, "Random Forest" and "KNN". For each cluster, both the algorithms are passed with the best parameters derived from GridSearch. We calculate the AUC scores for both models and select the model with the best score. All the models for each cluster are saved for using them during prediction.
* Prediction Data Description:-
Based on the cluster number, the respective model is loaded and is used to predict the data for that cluster.
Once the predictions are made for all the clusters, the predictions along with the original names before label encoder are saved in a CSV file to a given location and the location is returned to the client.

-Author
Afaf Ahmed: https://www.linkedin.com/in/AfafAhmed/
(Supported by Ineuron.ai Mentors)

