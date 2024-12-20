# Learning in Public

This repository serves as a record of my learning journey, where I track and outline the resources I've used. My focus is on Machine Learning (including MLOps and ML Engineering), Data Science, Data Engineering, and Programming. 
I try to learn by implementing in code.  

| | Resource | Type | Personal Notes/Projects | Status of Completion |
| - | :-: | :-: | :-: | :-: |
| 1 | [**DataTalksClub Data Engineering Zoomcamp**](https://github.com/DataTalksClub/data-engineering-zoomcamp) | Course |  [**Data Engineering Zoomcamp**](https://github.com/kemaldahha/data-engineering-course/) | Paused until January |
| 2 | [**DataTalksClub Machine Learning Zoomcamp**](https://github.com/DataTalksClub/machine-learning-zoomcamp) | Course |  [**Machine Learning Zoomcamp**](https://github.com/kemaldahha/machine-learning-course/) | Ongoing |
| 3 | **Fundamentals of Data Engineering** | Book |  |  |
| 4 | [**Introduction to Data Engineering**](https://www.coursera.org/learn/intro-to-data-engineering) | Course |  |  |
| 5 | **Build a Large Language Model from Scratch** | Book |  |  |
| 6 | **Machine Learning with PyTorch and Scikit-Learn** | Book |  |  |
| 7 | **MIT Strang Linear Algebra** | Course |  |  |
| 8 | **Linear Algebra and Its Applications, 4th edition (Gilbert Strang)** | Book |  |  |
| 9 | **[Pablo Insente - Intro to Linear Algebra](https://pabloinsente.github.io/intro-linear-algebra)** | Website |  |  |
| 10 | **[300Days__MachineLearningDeepLearning](https://github.com/ThinamXx/300Days__MachineLearningDeepLearning)** | Website | Learn in Public Log - check out for good ML/DL resources |  |
| 11 | **[https://ivanstudyblog.github.io/](https://ivanstudyblog.github.io/)** | Website | Learn in Public Log - check out for good ML/DL/DE resources |  |


## Day 0

Over the past month I have been going through the Data Engineering Zoomcamp by DataTalksClub. Here is a summary of what I covered so far.
- **Docker** is a platform that uses containers to create, deploy, and run applications. It's self-contained, so whatever you 'Dockerize' on a particular system (e.g. Windows), will run on any other machine (e.g. Linux) with Docker. Docker images are files which contain everything to run a piece of software (e.g. Postgres). You can download them from Docker Hub or make them yourself. The creation of Docker images can be automated using a Dockerfile. You can provide it arguments and instructions (e.g. to upload a file from your current working directory to a certain location in the image before running the software). When you run a Docker image, a container (instance of an image) is created. You can run multiple containers that communicate with each other. Containers are _ephemeral_, meaning that their state is not saved unless _volumes_ are used for persistence. Networks can be used to allow multiple containers to communicate with each other.
- I used a **Postgres** database. To inspect the data in postgres, I used both pgcli (command-line interface) as well as pgAdmin (browser interface).
- I did a refresher on **SQL**. It's been a while since I did SQL, because these days I use Pandas. But I will put some SQL practice on my roadmap down the line.
- **Terraform** was completely new to me. It's an Infrastructure-as-Code application which allows for convenient setup of Cloud resources. It's an easy to use abstraction layer on top of Cloud platforms such as GCP, Azure, AWS, and many others. Terraform commands are pretty straightforward: init, plan, apply, destroy. You can use variables in your Terraform .tf files.
- During this month, I used **Linux** extensively and learned about **SSH** and **port forwarding**.  

![Image](./images/day0a.png)
![Image](./images/day0b.png)

Resources:
- [My week 1 notes](https://github.com/kemaldahha/data-engineering-course/blob/main/week_1_notes.md) for [DataTalksClub Data Engineering Zoomcamp](https://github.com/DataTalksClub/data-engineering-zoomcamp)

## Day 1

**Workflow orchestration** tools such as Apache Airflow enable Data Engineers to organize and manage data pipelines/workflows. For example, consider a pipeline that involves downloading CSV data from the internet, reading the data, and storing it in a database. Executing these steps sequentially using a simple bash script, can be error-prone - if one step fails, the entire pipeline fails. Although you could circumvent this by writing code to retry upon failure, this approach becomes unwieldy as workflows grow in complexity. Workflow Orchestration address these challenges by simplifying retries, enabling parametrization of steps in the workflow, handling parallel execution, and providing tools to inspect logs and track execution history.

Resources:
- [My week 2 notes](https://github.com/kemaldahha/data-engineering-course/blob/main/week_2_notes.md) for [DataTalksClub Data Engineering Zoomcamp](https://github.com/DataTalksClub/data-engineering-zoomcamp)

## Day 2

Today I set up **Airflow** using Docker. I took a docker-compose.yaml file from the [Apache Airflow documentation](https://airflow.apache.org/docs/apache-airflow/stable/howto/docker-compose/index.html) and made adjustments to it to make it work with GCP. Running into an issue which I'll troubleshoot tomorrow. 
![Error with airflow](./images/day2.png)


Resources:
- [My week 2 notes](https://github.com/kemaldahha/data-engineering-course/blob/main/week_2_notes.md) for [DataTalksClub Data Engineering Zoomcamp](https://github.com/DataTalksClub/data-engineering-zoomcamp)

## Day 3

I started today with troubleshooting yesterday's issue. Read more about it in [my notes](https://github.com/kemaldahha/data-engineering-course/blob/main/week_2_notes.md) and on the Stack Overflow answer I posted [here](https://stackoverflow.com/a/78877992/11486502). After fixing it, everything worked! In summary, I finalized the Airflow with Docker and Docker Compose setup by:
- creating the appropriate folder structure for Airflow
- setting the Airflow user id in a .env file 
- downloaded the docker-compose.yaml file from Airflow's documentation abd updated it to point to the course's Dockerfile which, on top of the Airflow Docker image, installs some dependencies specified in a requirements.txt and installs Google Cloud SDK.
- troubleshot an issue along the way

![command line](images/day3a.png)
![airflow web service](images/day3b.png)

Resources:
- [My week 2 notes](https://github.com/kemaldahha/data-engineering-course/blob/main/week_2_notes.md) for [DataTalksClub Data Engineering Zoomcamp](https://github.com/DataTalksClub/data-engineering-zoomcamp)

## Day 4

Today I learned more about DAGs (Directed Acyclic Graph) in Airflow. A **DAG** is used to define the order in which tasks should be executed in a workflow. It specifies dependencies between tasks, has an explicit execution order, and has a beginning and an end. A **task** is a defined unit of work. It could be to fetch some data, run an analysis, trigger other systems, listen for events, etc. Airflow DAGs are defined in Python. There are various ways to declare one, such as with a context manager, a constructor, or a decorator.
Now that the Airflow environment has been set up, the next step will be to write an ingestion pipeline to ingest raw data into a GCP Cloud Storage Bucket. 

Resources:
- [My week 2 notes](https://github.com/kemaldahha/data-engineering-course/blob/main/week_2_notes.md) for [DataTalksClub Data Engineering Zoomcamp](https://github.com/DataTalksClub/data-engineering-zoomcamp)

## Day 5

Today I put what I learned into practice. 
Using **Terraform** I set up the Google Cloud infrastructure: **Bucket** for raw data storage and a **BigQuery Table** for the extracted, structured data from the Bucket.
Then, using **Airflow** within a **Docker container**, I executed a **DAG** which downloads a CSV dataset, **parquetizes** it, uploads it to the Google Cloud **Bucket**, and subsequently stores it in the **BigQuery** table, where it can be easily queried. Using **Airflow** I can ensure the **tasks** are run in order, when I want, under the conditions I want, and I can easily inspect and visualize what has happened.
I am starting to see the big picture and how the different tools work together as a system.

![airflow-dag](./images/day5a.png)
![dag-status](./images/day5b.png)
![dag](./images/day5c.png)
Resources:
- [My week 2 notes](https://github.com/kemaldahha/data-engineering-course/blob/main/week_2_notes.md) for [DataTalksClub Data Engineering Zoomcamp](https://github.com/DataTalksClub/data-engineering-zoomcamp)


## Day 6

More practice with Airflow by converting the data ingestion script from week 1 into a DAG and setting up Airflow. Running into errors due to conflicting Airflow/Postgres database setups. Trying to figure things out still. On holiday for the next 10 days, so I'll pick back up after.

![airflow](images/day6.png)

Resources:
- [My week 2 notes](https://github.com/kemaldahha/data-engineering-course/blob/main/week_2_notes.md) for [DataTalksClub Data Engineering Zoomcamp](https://github.com/DataTalksClub/data-engineering-zoomcamp)

## Day 7

Back from holiday. With the [DataTalksClub Machine Learning Zoomcamp](https://github.com/DataTalksClub/machine-learning-zoomcamp) course starting in a week, I decided to pause my self-paced study of the [Data Engineering Zoomcamp](https://github.com/DataTalksClub/data-engineering-zoomcamp) and follow along with ML Zoomcamp. My priority is to do the project work and build my portfolio. Following along will facilitate that better. After finishing the ML Zoomcamp, I will pick up the DE Zoomcamp again which starts in January.

Today I reviewed the fundamentals of ML, such as features, target variables, training/fitting a model, supervised ML, regression, classification (binary and multi-class), ranking. Also I learned how ML systems differ from rule-based systems. With ML the model decides which rules are important and which ones aren't. This helps to avoid building rule-based systems with a myriad of rules and conditions that become impossible to maintain over time.

Resources:
- [My week 1 notes](https://github.com/kemaldahha/machine-learning-course/blob/main/week_1_notes.md) for [DataTalksClub Machine Learning Zoomcamp](https://github.com/DataTalksClub/machine-learning-zoomcamp)

## Day 8

Today I continued with the week 1 videos from ML Zoomcamp. I learned about CRISP-DM which is a methodology for Data Science projects. I set up my environment in WSL2 using Anaconda and learned about ML model selection using train-validation-test splits and why it is important to avoid models 'getting lucky' due to their probabilistic nature (Multiple Comparison Problem). Finally, I went through a Numpy refresher.

Resources:
- [My week 1 notes](https://github.com/kemaldahha/machine-learning-course/blob/main/week_1_notes.md) for [DataTalksClub Machine Learning Zoomcamp](https://github.com/DataTalksClub/machine-learning-zoomcamp)

## Day 9

Halfway through the linear algebra refresher in week 1 of ML Zoomcamp. Covered vectors, matrices, and dot products.

![dotproductexplanation](images/day9a.png)
![dotproductcode](images/day9b.png)

Resources:
- [My week 1 notes](https://github.com/kemaldahha/machine-learning-course/blob/main/week_1_notes.md) for [DataTalksClub Machine Learning Zoomcamp](https://github.com/DataTalksClub/machine-learning-zoomcamp)

## Day 10

I finished the linear algebra refresher in which I dot product, matrix-vector multiplication, matrix-matrix multiplication, the identity matrix, and the matrix inverse. Implemented it in Numpy. Next up: Pandas refresher. 

![notes](images/day9a.png)
![numpymatrixinverse](images/day9b.png)

Resources:
- [My week 1 notes](https://github.com/kemaldahha/machine-learning-course/blob/main/week_1_notes.md) for [DataTalksClub Machine Learning Zoomcamp](https://github.com/DataTalksClub/machine-learning-zoomcamp)

## Day 11

Today I studied an intro to Pandas. Pandas is a powerful data analysis library in Python to analyze tabular data. There are two Pandas datatypes: DataFrame and Series. A DataFrame's is like a table, its columns consist of Series. I reviewed all the basic operations on DataFrames, such as accessing elements, filtering with masks, groupby. 

![pandas1](images/day10a.png)
![pandas2](images/day10b.png)

Resources:
- [My week 1 notes](https://github.com/kemaldahha/machine-learning-course/blob/main/week_1_notes.md) for [DataTalksClub Machine Learning Zoomcamp](https://github.com/DataTalksClub/machine-learning-zoomcamp)


## Day 12

The second week goes through the entire lifecycle of setting up a regression ML model for a car price prediction dataset.  I learned about data preparation/cleaning, EDA, and model validation. Ensuring training/validation/testing are representative is crucial.

![datacleaning](images/day12a.png)
![logtransformplot](images/day12b.png)

Resources:
- [My week 2 notes](https://github.com/kemaldahha/machine-learning-course/blob/main/week_2_notebook.ipynb) for [DataTalksClub Machine Learning Zoomcamp](https://github.com/DataTalksClub/machine-learning-zoomcamp)


## Day 13

In linear regression models, feature values are multiplied with weights. The sum of these products yield a prediction of the target variable. This is done for each sample (i.e. row) in the training set. If a certain feature has a high weight, it means that that feature is very important for predicting the target variable. I set up a function for linear regression for a single sample. Then I extended it to the entire training set and wrote it in terms of a matrix-vector multiplication. 

![naivelinearmodel](images/day13a.png)
![interpretinglinearmodel](images/day13b.png)
![vectorform](images/day13c.png)

Resources:
- [My week 2 notes](https://github.com/kemaldahha/machine-learning-course/blob/main/week_2_notes.ipynb) for [DataTalksClub Machine Learning Zoomcamp](https://github.com/DataTalksClub/machine-learning-zoomcamp)


## Day 14

The Normal Equation solves for the weights in a linear regression problem such that the sum of squared errors is minimized between the data and the model.

![normalequation](images/day14.png)

Resources:
- [My week 2 notes](https://github.com/kemaldahha/machine-learning-course/blob/main/week_2_notes.ipynb) for [DataTalksClub Machine Learning Zoomcamp](https://github.com/DataTalksClub/machine-learning-zoomcamp)


## Day 15

I created a baseline model for the car price prediction dataset. This was done by selecting numeric features only, filling nans with 0, splitting the data into train/validation/test, and using the Normal equation on on the train data. I visualized the results below. Also I calculated the Root Mean Square Error (RMSE), which is a common metric for evaluating regression models.

![datapreparation](images/day15a.png)
![distribution](images/day15b.png)
![correlation](images/day15c.png)
![rmse](images/day15d.png)

Resources:
- [My week 2 notes](https://github.com/kemaldahha/machine-learning-course/blob/main/week_2_notes.ipynb) for [DataTalksClub Machine Learning Zoomcamp](https://github.com/DataTalksClub/machine-learning-zoomcamp)


## Day 16

Feature engineering is used to transform the data you have into new features. For instance the cars dataset I am looking at has a 'year' feature. I changed this into 'age', which improved the car price prediction. Categorical columns can be converted into binary columns for each category. However if you have too many features, your RMSE will go up and so will your weights. A way to deal with this is regularization.

![code](images/day16.png)

Resources:
- [My week 2 notes](https://github.com/kemaldahha/machine-learning-course/blob/main/week_2_notes.ipynb) for [DataTalksClub Machine Learning Zoomcamp](https://github.com/DataTalksClub/machine-learning-zoomcamp)

## Day 17

Learned about what happens when there are linearly dependent columns in the feature matrix X. In that case, X^T X in the Normal Equation becomes rank deficient and cannot be inverted. Or, if the columns are near linear dependent, it leads to numerical instability and very large weights. Regularization (Ridge/L2) can counter this. We add a small number to the diagnotal of X^T X which makes it invertible. The amount of regularization we apply is a hyperparameter that needs to be optimized. Besides this, I started writing a blog post about linear regression.

![residualplot](images/day17a.png)
![normalequation](images/day17b.png)

Resources:
- [My week 2 notes](https://github.com/kemaldahha/machine-learning-course/blob/main/week_2_notes.ipynb) for [DataTalksClub Machine Learning Zoomcamp](https://github.com/DataTalksClub/machine-learning-zoomcamp)
- [On Linear Regression (WIP)](https://github.com/kemaldahha/machine-learning-course/blob/main/linear_regression_article.ipynb)

## Day 18

Continued blog post on Linear Regression. Finalized formal derivation of Normal Equation. Next, explain why Numpy and sklearn (and LAPACK under the hood) use SVD/QR decomposition instead. Also started putting notes on fundamentals online.

![normalequation](images/day18a.png)
![fundamentals](images/day18b.png)

Resources:
- [My week 2 notes](https://github.com/kemaldahha/machine-learning-course/blob/main/week_2_notes.ipynb) for [DataTalksClub Machine Learning Zoomcamp](https://github.com/DataTalksClub/machine-learning-zoomcamp)
- [On Linear Regression (WIP)](https://github.com/kemaldahha/machine-learning-course/blob/main/linear_regression_article.ipynb)
- [Linear Algebra Fundamentals](https://kemaldahha.github.io/fundamentals/linear_algebra)

## Day 19

Last 4 days I didn't update my progress, so I'll mention it under 'day 19':
- Finalized my [blog post on Linear Regression](https://medium.com/@kemaldahha/understanding-linear-regression-by-deriving-the-normal-equation-364d9295be1b).
- Started working on my midterm project idea for ML Zoomcamp. I'm scraping data from a real estate website and plan to make an ML model for predicting a price. 
- Halfway through week 2 homework.

![homework2](images/day19.png)

# Day 20

Submitted week 2 homework assignment: a linear regression model for laptop price prediction. Also made progress with my project to scrape Dutch real estate data. I have downloaded all the data I need (about 5000 properties), next step is to clean it.

![data](images/day20.png)

# Day 21

Started going through week 3 videos which covers classification problems in ML. During the EDA section, it was explained how class imbalance may skew predictions. Also we started to use scikit-learn instead of implementing from scratch using numpy.

![churnprediction](images/day21a.png)
![sklearn](images/day21b.png)

# Day 22

In classification, feature importance can be analyzed by comparing the rate of a binary target variable across different feature groups relative to the global rate. Alternatively, mutual information measures how much knowing a feature reduces uncertainty about the target, capturing both linear and non-linear dependencies.

![comparerates](images/day22a.png)

![MI](images/day22b.png)

# Day 23

Day 23 of #LearnInPublic #mlzoomcamp

Today covered lessons 3.6/7 on Correlation Coefficient for numeric features and One-Hot Encoding for categorical features. Next up Logistic Regression.

![correlationchurnrate](images/day23a.png)
![onehot](images/day23b.png)


# Day 24

Day 24 of #LearnInPublic #mlzoomcamp

Today I covered Logistic Regression, which is closely related to Linear Regression. It basically takes the linear combination from linear regression and plug it into sigmoid + set decision boundary to make prediction.

![logreg](images/day24a.png)
![logreg2](images/day24b.png)


# Day 25

Day 25 of #LearnInPublic #mlzoomcamp

DictVectorizer converts a DataFrame into a list of dicts, one-hot encoding categorical columns while leaving numeric ones unchanged. It can also handle new observations in JSON format, preparing them for model prediction.

![dv](images/day25.png)

# Day 26

Day 26 of #LearnInPublic #mlzoomcamp

Finished week 3 homework. Next up: week 4 which is about Evaluation Metrics for Classification and cross-validation.

![wk3](images/day26.png)

# Day 27

Accuracy of a classification model when there is class imbalance, is misleading. Predicting the majority class would already give a higher score than a random prediction. Instead look at: confusion table, precision/recall

![threshold](images/day27a.png)
![lr](images/day27b.png)
![dummy](images/day27c.png)

# Day 28

Confusion matrices divdide classifications into 4 categories: true/false positives/negatives. This says more about the performance of a classification model than purely looking at accuracy which can be a misleading metric when there is class imbalance. Tomorrow I will further dive into evaluation metrics for classification such as Precision and Recall. 

![confusionmatrix](images/day28.png)

# Day 29

When evaluating a classification model, if you care mostly about avoiding false positives, look at Precision. However, if you care about avoiding false negatives, look at recall.

![precisionrecall](images/day29.png)

# Day 30

The ROC curve is used to evaluate binary classification models. By visualizing the false positive rate and true positive rate against the threshold we get a sense how well the model performs at various thresholds. Moreover, we can evaluate it against an ideal model and random model and evaluate our model against it.

![fprtpr](images/day30a.png)
![randomroc](images/day30b.png)
![roc](images/day30c.png)
![fprtpr](images/day30d.png)

# Day 31

ROC AUC is the area under the ROC curve. It's a way to quantify how well a binary classification model is close to the ideal. It's equivalent to the probability that a randomly selected negative sample has a lower score than a randomly selected positive sample. For an ideal classifier, AUC=1. For a random classifier, AUC=0.

![auc](images/day31.png)

# Day 32

Today I completed week 4 of ML Zoomcamp. So far the focus was on modeling data for regression and classification problems. Week 5 shifts gears and is about deploying ML models. The combination between (a sufficient amount of) theory and application/deployment is what drew me to ML Zoomcamp in particular as well as other courses by DataTalksClub. During my ML and programming learning journey, I've never struggled so much with the learning part, but I've always struggled with putting what I learned into practice and building a portfolio. Ultimately my goal is to start working in this domain, so this is key. DataTalksClub's courses are designed to put learnings into practice and share your work. I think this is what distinguishes it from other, more famous or rigorous courses.

# Day 33

All the code from the previous weeks was written in Jupyter notebooks. This week is about deploying the code. I transferred all the code into separate .py files for training and prediction. In train.py, a model can be trained and it is saved using the pickle module. In predict.py, this model can be used in conjunction with customer data sent in json format to make a prediction on whether they will churn or not. I did an intro into using Flask and currently am busy building a web service for churn prediction with Flask.

![flask](images/day33a.png)
![train](images/day33b.png)
![predict](images/day33c.png)

# Day 34

I took yesterday's churn prediction file and made a Flask app for it. When running the file, a post request can be sent to it with customer data in json format, and a prediction is sent back. Although a development server is used during developing, which autoreloads upon changes and provides error messages, during production a production server such as uvicorn should be used.

Since we will have multiple services running side by side, it helps to create separate virtual environments for them. This is where pipenv comes into play. When using pipenv, all dependencies are automatically registered in Pipfile and Pipfile.lock, including the exact versions of their sub-dependencies. The environment can then easily be set up on a new computer with `pipenv install`. We can run commands from this environment like `pipenv run gunicorn --bind 0.0.0.0:9696 predict:app`


![predictflask](images/day34a.png)
![pipenv](images/day34b.png)

# Day 35

Virtual environment managers such as pipenv help to isolate python dependencies. However, Docker goes a step further and isolates an application entirely from the system. For instance we can run multiple Docker containers from the same computer, where the containers have different OS versions from each other and from the host computer. Also using Docker makes it easy to deploy applications to the cloud.

![docker](images/day35.png)

# Day 36

Today I deployed the docker image I built yesterday, to the cloud using AWS Elastic Beanstalk. It was pretty straightforward, first I downloaded awsebcli using pipenv, via pipenv shell, I initialized the service, I ran it locally with eb to verify it works, then I deployed it using eb create. I didn't figure it'd be this straightforward. After that I did the homework for this week, which concludes week 5. Next week is on decision trees, random forrest, and XGBoost.

![dockerfile](images/day36.png)

# Day 37

Week 6 is on decision tree algorithms. The first lesson introduced the credit risk prediction problem. It's a similar binary classification problem as the customer churn prediction problem of the last 2 weeks. I followed the same data preparation steps, such as standardizing column names, mapping numeric codes to descriptive categories, handling missing values, and splitting the data into train/validation/test sets. 

![preprocessing](images/day37a.png)
![splitting](images/day37b.png)

# Day 38

Decision trees are a type of machine learning algorithm used for classification and regression tasks. They break down complex decisions into a series of simpler, sequential questions. At each step, or node, the data is split based on a specific feature and condition (e.g., "Is income greater than $50,000?"). This process continues until the data reaches a final decision, represented by a leaf node. The tree structure allows for easy interpretation, as it can be visualized as a flowchart of if-then-else conditions that guide the data to a result. They can be prone to overfitting. One way of mitigating this, is by setting the maximum depth of decision trees.

![alt text](images/day38a.png)
![alt text](images/day38b.png)
![alt text](images/day38c.png)

# Day 39

Today, I switched gears and worked on a miniproject using the OpenAI API. I downloaded transcripts from a YouTube channel focused on stock investing and created a script to feed each transcript to ChatGPT to extract stock recommendations, saving them as CSV entries with tickers, valuations, and relevant quotes from the transcript. However, ChatGPT's output didn't consistently adhere to CSV format. I tried tweaking the temperature and prompt engineering with few-shot examples, but no luck. I learned about using structured output with Pydantic, which I’ll try later. But for now, back to ML Zoomcamp!"

![chatgpt](images/day39.png)

# Day 40

Dove deeper into decision trees and explored parameter tuning. By training the model for different `max_depth` and `min_samples_leaf`, I found the combination which maximizes AUC score. After that I did the lesson on Random Forest in which multiple decision trees are trained on different, random subsets of features and their predictions are averages. Then I did parameter tuning on that. I checked at which  number of decision trees (`n_learners`), the model score no longer improves. Then I optimized `max_depth` and `min_samples_leaf`. Finally, I looked into XGBoost. Where Random Forest trains multiple models, independent from each other, XGBoost uses boosting, which is a technique in which a model is trained, its error determined, then another model is trained based on it with the purpose of reducing the error. This is done for many iterations. 

![heatmap](images/day40a.png)
![rftuning](images/day40b.png)
![xgb](images/day40c.png)

# Day 41

Today I continued with my XGBoost model and did a manual hyperparameter optimization/tuning. Out of the 3 models XGBoost was the best performing one with an AUC score of 83% vs 82% for RF and 78% for DT. I went ahead with XGBoost and used the combined training and validation data to train the model and evaluate it on the test set. This also gave an AUC score of 83%, which means the model generalizes well to unseen data. I completed the homework as well, concluding week 6. Next I will start working on my midterm project. I intend to use this in my portfolio, so I want to make sure it is of high quality. More to follow..

![xgbtuning](images/day41a.png)
![xgbtest](images/day41b.png)

# Day 42

I haven't shared my progress in 2 weeks, though I have worked on the ML Zoomcamp midterm project. Today's sharing covers the work done during past 2 weeks. I created a script which can download listings from Funda, the Dutch Zillow. The data needs a lot of wrangling though to get it in shape for modeling. I'm ending up with a lot of columns due to one-hot encodig, which I think may pose a problem later on due to multicollinearity. After preparing the data, I will do EDA, modeling, and then deploy it using AWS Elastic Beanstalk. The deadline is 26th of November. 

![datawrangling](images/day42.png)

# Day 43

Today I finished the data preparation for the ML Zoomcamp midterm project. I ran the first model to predict house prices in Rotterdam using linear regression. I managed to get an RMSE on the validation set of 158.321, which is not bad, but tomorrow I will try and improve it through feature engineering.  

![linreg](images/day43.png)

# Day 44

Spent quite a bit more time today on data cleaning and preparation. A lot of the features are correlated with each other and have outliers which need to be dealt with. Planning to evaluate how linear regression, decision tree, random forest, XGBoost and see how they stack up against each other. My goal is to finish the assignment tomorrow, but let's see how that goes.

![corrplot](images/day44a.png)
![dataprep](images/day44b.png)

# Day 45

Today I made a start with week 8, which is about deep learning. The example assignment is about image classification of fashion items. I set up an environment in Saturn Cloud, a GPU provider and used a bit of Tensorflow and Keras.

![tfkeras](images/day45.png)

# Day 46

Convolutional Neural Networks (CNNs) use convolutional layers to detect features in images and dense layers to make predictions. Convolutional layers act as filters, comparing small image segments to the input to create feature maps. These maps capture patterns like lines and shapes in early layers and more complex features in deeper layers. Dense layers use the resulting vector to calculate predictions, such as binary or multi-class classifications. In transfer learning, the convolutional layers of a pretrained CNN remain unchanged, as they are general-purpose, while dense layers are retrained for the specific problem, reducing data needs and training time.

![cnn](images/day46a.png)
![training](images/day46b.png)

# Day 47

Learning Rate
Learning rate is one of the most important hyperparameters for neural network training. If learning rate is too high, training will be relatively faster, but you'll likely overfit and perform poorly on validation. if it is too low, model training will be too slow. You'll likely underfit and perform poorly on validation. If you balance the learning rate well, the model training will not take too long and perform well on the validation data.

Checkpointing
During model training, images are processed in batches. When all training images have been used, it constitutes one cycle, which is called epoch. Checkpointing is a way of storing intermediate models. For example, each epoch's model can be stored, or only the ones that improved in terms of a specified metric (e.g. validation accuracy). Otherwise we would just be stuck with the last epoch's model, which is arbitrary compared to choosing a model based on performance.

Dropout
When a neural network trains and it sees the same dataset for multiple epochs, it may end up learning idiosynchrasies of the data. Imagine a certain t-shirt has a logo. The neural network may end up memorizing the logo and associate it with t-shirts. If another clothing item has that logo, it will mistakenly think it's a t-shirt. We want the neural network to learn more general characteristics, such as the overall shape of a t-shirt, the fact that it has a collar, and so on. Per epoch, dropout will randomly freeze certain neurons in an inner layer by removing connections between that inner layer and the vector representation.  

Data Augmentation
With dropout, we regularize our neural network. With data augmentation, we create more data out of our existing data. So we generate more images out of existing ones. For example, we can transform our image by flipping, rotating, shifting, shearing, etc. These can be combined. Data augmentation should be representative for the variety in data we get in production. So, if for example, all objects in an object recognition model would be oriented in one way, there's no point in augmenting the training data by changing the orientation. Also, we should only apply data augmentation to training and not to validation, as that will make it impossible to compare validation metrics across epochs.

![lr](images/day47a.png)
![checkpointing](images/day47b.png)