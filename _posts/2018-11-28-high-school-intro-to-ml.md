---
layout: post
title: Intro to Machine Learning For a High School Student
---

I've hosted high-school work experience students at 3 different companies where I've worked. At all companies so far, the ramp-up time to setup a dev environment, security concerns with exposing company IP and requisite level of coding skills have made contributing to the main product infeasible for students within a 1-2 week timeline. Instead I've setup small technical projects related to the same domain as the company's main product. I try to finding existing, well supported tutorials, courses or well-defined mini-projects that a student could pursue some what independently.

This year I had my student do a series of mini-projects to introduce Data Science and Machine Learning. She was a grade 12 student with some Python programming experience. Here is the sequence of projects that she did:

## Introductory videos and tutorials

I think she completed all

1. [VIDEO: Conceptual Introduction to Machine Learning](https://www.youtube.com/watch?v=z-EtmaFJieY)

2. [Machine Learning Intro in 2 hours](https://machinelearningmastery.com/machine-learning-in-python-step-by-step/) I like this tutorial because it has detailed instructions and lets you get some hands on practice with very little pre-requisite knowledge.

3. [Slightly more complex machine learning exercise](https://www.kaggle.com/niklasdonges/end-to-end-project-with-python). I think this is a great follow-up to the previous tutorial link. It re-enforces the same concepts with a more complex data set. Unlike the Iris dataset used in the previous tutorial, this dataset requires some cleaning. So this tutorial introduces the data cleanup/ pre-processing step.

## Coding Project - Data Explorer application
Build an application that will help a data scientist do some pre-liminary explorations of a dataset. The requirements for this project are broken into multiple parts to facilitate adding functionality through iterative improvements

### Requirements
There should be a file called data_explorer.py that can be run like this:
`python data_explorer.py  <file-path-or-url>`

### Part 1

1. When this file is run it should load the data specified at the file path/url input parameter and output the following basic information about the dataset:
  a.  how many rows and columns
  b.  statistical summary
  c.  top 20 rows of data
2. If the user does not specify a file path or url when running the file an error should be printed

Think about how you structure your python file. Divide up the logic you write into multiple functions. Use meaningful variable and function names. Add comments to each function to explain what it is supposed to do.

Try out the tool with a couple of different datasets, Iris, Titanic and few others of your choice.

### Part 2

Extend the above program to also so you also display the following:
1. univariate box plots for each feature
2. histograms for each feature
2. scatter matrix for dataset

Note: you will need to figure out how to have multiple matplotlib windows displayed at the same time in order to display all the above correctly.
Note2: the other big thing you will need to figure out is how to display information for different sizes for datasets. Some datasets may have 5 columns others may have 12 or 200.

### Part 3
Extend the above program to output additional information about the data including:
1. types of each feature (Eg: string, integer, float etc)
2. whether there is missing data? If yes, how many rows are missing data for each feature?

### After Part 3
Depending on how long the above parts take, we can make incremental improvements to our script to make it more polished. We can add more data to the output and we can polish the output so it is more stylish and easy to view.  We can discuss all the possible improvements and pick the next thing to improve once we get some starter version of the data explorer tool.

### Resources
* This python library will help you handle defining, using and validating the input argument [argparse](https://docs.python.org/2/howto/argparse.html)
* This matplotlib tutorial will cover how to display multiple figures. Scroll down till you find the appropriate bit of info
[matplotlib](https://matplotlib.org/users/pyplot_tutorial.html)
* [Seaborn](https://seaborn.pydata.org/)
* [D3JS](https://d3js.org/)
