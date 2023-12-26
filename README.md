Screen Time Analysis lets you know how much time you spend on what kind of applications and websites using your device. And screen time analysis gives a visual report of the same. So, in this project, I am more focused on analysing screen time. <p>

# Screen Time Analysis
Screen Time Analysis is the task of analyzing and creating a report on which applications and websites are used by the user for how much time. Apple devices have one of the best ways of creating a screen time report.<p>

For the task of screen time analysis, I found an ideal dataset that contains data about: <p>

1. Date  <p>
2. Usage of Applications  <p>
3. Number of Notifications from Applications  <p>
4. Number of times apps opened <p>

# Screen Time Analysis using Python
Let’s start the task of screen time analysis by importing the necessary Python libraries and the dataset: <p>

import pandas as pd <p>
import numpy as np <p>
import plotly.express as px <p>
import plotly.graph_objects as go <p>

data = pd.read_csv("Screentime_App_Details.csv") <p>
print(data.head()) <p>

Now let’s have a look if the dataset has any null values or not: <p>

data.isnull().sum() <p>

The dataset doesn’t have any null values. Now let’s have a look at the descriptive statistics of the data: <p>
print(data.describe()) <p>

Now let’s start with analyzing the screen time of the user. I will first look at the amount of usage of the apps: <p>
 
figure = px.bar(data_frame=data,  <p>
                x = "Date",  <p>
                y = "Usage",  <p>
                color="App",  <p>
                title="Usage") <p>
figure.show() <p>

Now let’s have a look at the number of notifications from the apps: <p>

figure = px.bar(data_frame=data,  <p>
                x = "Date",  <p>
                y = "Notifications",  <p>
                color="App",  <p>
                title="Notifications") <p>
figure.show() <p>

Now let’s have a look at the number of times the apps opened:  <p>

figure = px.bar(data_frame=data,    <p>
                x = "Date",  <p>
                y = "Times opened",  <p>
                color="App", <p>
                title="Times Opened") <p>
figure.show() <p>

We generally use our smartphones when we get notified by any app. So let’s have a look at the relationship between the number of notifications and the amount of usage: <p>

figure = px.scatter(data_frame = data,  <p>
                    x="Notifications", <p>
                    y="Usage",   <p>
                    size="Notifications",  <p>
                    trendline="ols",  <p>
                    title = "Relationship Between Number of Notifications and Usage") <p>
figure.show() <p>

There’s a linear relationship between the number of notifications and the amount of usage. It means that more notifications result in more use of smartphones. <p>

