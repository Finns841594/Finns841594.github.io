---
layout: post
title:  "Questionnaire 04"
date:   2022-06-28 20:00:00 +0200
categories: Deep Learning
---


#### 1. How is a grayscale image represented on a computer? How about a color image?  
A grayscale image is stored as a matrix with same columns and rows as the resolution size. Each number in this matrix is ranged within 0~255, which represents the darkness of the pixel. A color image has three matrix which stored the information of the image by three channels: red, green, blue.

#### 2. How are the files and folders in the 'MNIST_SAMPLE' dataset structured? Why?  
The 'MNIST' datasets follows a common layout for machine learning datasets: seperate folders for the trainning set and the validation set(and/or test set).

#### 3. Explain how the "pixel similarity" approach to classifying digits works.  
Based on the matrix we mentioned for the question one. We assume that the image of a number should have similar gray pixel distribution as other images of the same number. So we caculate the average number of the matrix which presents the images of a number as a 'standard', when we classifying a test image, we compare the piexel number of it to our 'standard', and give the inference result based on the similarity.

#### 4. What is a list comprehension? Create one now that selects odd numbers from a list and doubles them.  
Its a very useful feature of Python. It is well explained as follow:
    'List and dictionary comprehensions are a wonderful feature of Python. Many Python programmers use them every day, including the authors of this book—they are part of "idiomatic Python." But programmers coming from other languages may have never seen them before. There are a lot of great tutorials just a web search away, so we won't spend a long time discussing them now. Here is a quick explanation and example to get you started. A list comprehension looks like this: new_list = [f(o) for o in a_list if o>0]. This will return every element of a_list that is greater than 0, after passing it to the function f. There are three parts here: the collection you are iterating over (a_list), an optional filter (if o>0), and something to do to each element (f(o)). It's not only shorter to write but way faster than the alternative ways of creating the same list with a loop.'

#### 5. What is a "rank-3 tensor"?  
A 3 dimensional tensor.

#### 6. What is the difference between tensor rank and shape? How do you get the rank from the shape?  
The rank shows how many dimension this tensor has. While the shape tells you the length of each dimension or axis. If a tensor has shape of 128*128*30, we say its a rank 3 tensor.

#### 7. What are RMSE and L1 norm?  
RMSE, root mean squared error, which is also called as L2 norm, take the mean of the square of differences and then take the square root: sqrt((value - mean)**2)
L1 norm, mean absolute difference, take the mean of the absolute value of difference.


