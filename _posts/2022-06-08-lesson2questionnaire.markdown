---
layout: post
title:  "Lesson 2 Questionnaire"
date:   2022-06-08 14:00:00 +0200
categories: Deep Learning
---

# 1. Provide an example of where the bear classification model might work poorly in production, due to structural or style differences in the training data.
If there have no black-and-white images of bears in the trainning data, the model might do poorly in classifier mission when we input a black-and-white bear image. So when we collecting the training data, we should take the type of data that would be used in practical mission into consideration.


# 2 Where do text models currently have a major deficiency?
Deep learning is currently not good at generating correct natural language responses.

# 3 What are possible negative societal implications of text generation models?
Auto generated text contents can be used to spread disinformation, create unrest, and encourage conflict, which will bring much bigger influence than before. Because the speed of generated such contents by machine learning model is thousands of times greater than any troll farm previously seen. 

# In situations where a model might make mistakes, and those mistakes could be harmful, what is a good alternative to automating a process?
Use this model as a tool for human for the specific task. Combineing the efficiency of a machine and the accuracy of a human.

# What kind of tabular data is deep learning particularly good at?
Natrual language and high-cardinality categorical columns(discrete numbers such as zip code or product ID).

# What's a key downside of directly using a deep learning model for recommendation systems?
It recommands based on the relativeness. So a deep learning model may recommend something highly relative which you already known.

# What are the steps of the Drivetrain Approach?
Define the Objective -> Actions can be taken(levers) -> Data can be used
After the logic line above is cleared, then decide which model to be used.

"We use data not just to generate more data (in the form of predictions), but to produce actionable outcomes."

# How do the steps of the Drivetrain Approach map to a recommendation system?
1.Define the Objective: recommending a book based on the book that a user has purchased;
2.Actions: train a model which output the data which describes the revelance of each books in our libarary.
3.Data: names of Books each user has bought;

Belows are from course:
The objective of a recommendation engine is to drive additional sales by surprising and delighting the customer with recommendations of items they would not have purchased without the recommendation.
The lever is the ranking of the recommendations.
New data must be collected to generate recommendations that will cause new sales.
Finally, you could build two models for purchase probabilities, conditional on seeing or not seeing a recommendation.

What I got:
Go deeper into the motivation. Recommending a book here is to sell it.

Create an image recognition model using data you curate, and deploy it on the web.
See my previous post:
https://finns841594.github.io/fengsblog/machine%20learning/2022/06/01/first-complete-practice.html

Deployed at here:
https://hub.gke2.mybinder.org/user/finns841594-dog_classifier-bu59zdrv/voila/render/Dog_Classifier.ipynb?token=saWa_1L4SZ2zaDWTk5Q1Dg

# What is DataLoaders?
A class that stores the dataloads that you passed to it. Usually used in following way:
dls = DataBlock.dataloaders(path)

# What four things do we need to tell fastai to create DataLoaders?
1, what kind of data
2, how to get the list of items
3, how to label these items
4, how to create the validation set

From where to get what data, in what way to label them and in what way to split validation set.

# What does the splitter parameter to DataBlock do?
To tell the DataBlock how much percentage of the all data should be used for validation.

# How do we ensure a random split always gives the same validation set?
Give the splitter same random seed.

# What letters are often used to signify the independent and dependent variables?
x for the independent variables while y for the dependent variables.

# What's the difference between the crop, pad, and squish resize approaches? When might you choose one over the others?
Cropping may lose pixels(informations), padding may add a lot of extra black pixels, squish resizing leads to unrealistic shapes. All three methonds have negative influence on model trainning. Usually we use random resize crop.

# What is data augmentation? Why is it needed?
It means to creating random variations of the data. The variations has same meaning(key information) of the data, but slightly different. It is needed because It can help trainning our model to caputre the essential part of the data instead of caring about less important details.

# 17 What is the difference between item_tfms and batch_tfms?

item_tfms applies on single item one by one, batch_tfms applies on the full batch at once.

# 18 What is a confusion matrix?

It is for us to evaluate the performence of model, and to anylise where are the errors. It is a matrix shows the coherence of the predict and the result.

# 19 What does export save?

It saved the parameters and the model together in fastai format.

# 20 What is it called when we use a model for getting predictions, instead of training?

inference

# 21 What are IPython widgets?

GUI components

# 22 When might you want to use CPU for deployment? When might GPU be better?

Use CPU when you don't need to deal with many identical works at the same time. Use GPU when you need that.

# 23 What are the downsides of deploying your app to a server, instead of to a client (or edge) device such as a phone or PC?

First, the framework which helps you achive that might not support the layer or function we are using for trainning the model. In addition, its time costing to adapt the application to the different version of os on different devices by small team(or alone).

# 24 What are three examples of problems that could occur when rolling out a bear warning system in practice?

Most of the problems occured because the quality of images for trainning are different from the images for inferencing in practice, which leads the desension of accuracy. For example, low quality for inferencing, video data instead of images, bears in the images are in rarely seen position, etc.

# 25 What is "out-of-domain data"?

Domain here means the range of data we used for trainning. Out-of-domain data thus means the type or the quality of data for inferencing is different from the data we used for the trainning.

# 26 What is "domain shift"?

data that our model sees changed with the time.

# 27 What are the three steps in the deployment process?

Manula process, to limited scope deployment, to gradual expansion.

