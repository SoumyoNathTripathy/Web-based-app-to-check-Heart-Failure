# Web-based-app-to-check-Heart-Failure
## Heart-Failure-Prediction-and-Deployment-with-Flask-and-Heroku

![image](https://user-images.githubusercontent.com/85414445/185736615-94df6113-3863-4581-80f2-d9371cfc106f.png)
Cardiovascular diseases (which often leads to heart failures) are the number 1 cause of death globally, taking an estimated 17.9 million lives each year, which accounts for 31% of global deaths.

### Introductiom
Most cardiovascular diseases can be prevented by addressing behavioral risk factors such as tobacco use, unhealthy diet and obesity, physical inactivity, and harmful use of alcohol using population-wide strategies. However, people with cardiovascular disease or who are at high cardiovascular risk (due to the presence of one or more risk factors such as hypertension, diabetes, hyperlipidemia, or already established disease) need early detection and management wherein a machine learning model can be of great help.

### Abstract
This machine learning model could help in estimating the probability of deaths caused by heart failure by taking in important features from the dataset and making predictions based on these features.

The dataset consists of 12 variables/features, and 1 output variable/target variable. Let us examine the role of each feature in determining if a person is likely to have heart failure or not:

### Interface looks like this:
![image](https://user-images.githubusercontent.com/85414445/216848472-3ebaa128-c897-445b-9af0-61532c1c131e.png)


1.Age: This variable shows the patient’s age
2.Anemia: is the decrease in red blood cells or hemoglobin
3.Creatinine_phosphokinase: is the level of creatine kinase in the blood. This enzyme is important for muscle function.
4.Diabetes: is a chronic disease that causes high blood sugar
5.Ejection fraction: is the percentage of blood leaving the heart at each contraction
6.High blood pressure: is blood pressure that is higher than normal
7.Platelets: are tiny blood cells that help your body form clots to stop bleeding
8.Serum creatinine: is the level of serum creatinine in the blood
9.Serum sodium: is the level of serum sodium in the blood
10.Sex: gender of the patient
11.Time: This captures the time of the event
12.Death event: which is the predictor variable.

### Stepwise explanation of each feature:

Step 1: Import Libraries


Step 2: Import the Dataset

The Dataset used in building this model was downloaded as a CSV file to my PC from Kaggle.
Step 3: Data Cleaning and EDA

This data was pretty much clean, so I didn’t have to do any more cleaning. However, some important pieces of information can still be explored.


Next, I use Matplotlib to visualize the distribution of the target variable (Death_event). From the visualization, we can see that a greater percentage of the patients had a failed heart.


I also visualized the Distribution of each feature to investigate how they are related to the target variable. Some important features are discussed:


First, I explored the importance of the Age feature in determining If a patient is likely to have a heart failure or not. From the above, we can see that as the age increases, the probability of a death event also increases (i.e the older a patient is, the more likely he is to have a heart failure). Also, since the increase in one variable results in an increase in the other variable, we can deduce that these two variables are positively correlated. However, a correlation matrix will still be plotted for confirmation.


In general, the normal creatinine levels range from 0.9–1.3, and from the distribution of serum_creatinine against Death_event visualized above, we can see that the chances of survival are higher within this range.


The reference range for serum sodium is between 135–147 mmol/L. From the visualization above, the survival rate only starts to increase at this range. This feature also has a considerable correlation with Death_Event

To further evaluate the relationship between each input variable and the target variable, I use a heatmap, which gives a graphical representation of the relationship between the variables.


Step 4: Splitting the Train and Test Data


Step 5: Data Preprocessing

This brings the data to a state that the model can parse easily. For the purpose of this project, the Standard Scaler is used, which standardizes the features by subtracting the mean and then scaling to unit variance.


Step 6: Model Selection

The support vector machine (SVM), a supervised machine learning model that uses classification algorithms for two-group classification problems is used. After giving the SVM model sets of the preprocessed training data for each category, they’re able to categorize new output.


The classification report shows an accuracy of 75%.

Since this model will be deployed, it is saved into a pickle file (model.pkl) created by pickle, and this file will reflect in your project folder.

Pickle is a python module that enables python objects to be written to files on the disk and read back into the python program runtime.


Step 7: Deploying with Flask and Heroku

Deploying a machine learning model means making the model available for end-users to make use of.

Create the Webpage

Here we will create a CSS webpage that has text boxes to take in input from users. The CSS file was named index.html and can be found here.

Several templates for creating a CSS webpage can be found online.

Deploy the model on the webpage using Flask

In deploying this heart failure prediction model into production, a web application framework called Flask is used. Flask makes it easy to write applications, and also gives a variety of choices for developing web applications.

To make use of this web application framework in deploying this model, we install Flask by running the following command:


Next, a Flask environment with an API endpoint that takes in the model and enables it to receive input from users, and return output is setup.

After this, a python file app.py is created, and the required libraries imported


Create the Flask App


Load the pickle


Create an app route to render the HTML template as the home page


Create an API that gets input from the user and computes a predicted value based on the model.


Now, call the run function to start the Flask server.


This should return an output that shows that your app is running. Simply copy the URL and paste it into your browser to test the app.

Deploy the Flask APP to Heroku

Heroku is a multi-language application platform that allows developers to deploy, and manage their applications. It is flexible and easy to use, offering developers the simplest path to getting their apps to market.

The first thing to do in deploying the Flask app to Heroku is to Sign up and Log In to Heroku. After which you can create a Procfile and requirement.txt file, which handles the configuration part in order to deploy the model into the Heroku server.

web: gunicorn is the fixed command for the Procfile.


The requirements file consists of the project dependencies and can be installed with a single command:


Next, you commit your code to Github and connect Github to Heroku.



Link to the medium article i refered for README: https://towardsdatascience.com/deploying-a-heart-failure-prediction-model-using-flask-and-heroku-55fdf51ee18e










# Author- Soumyo Nath Tripathy
