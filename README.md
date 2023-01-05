# Phase_4_Project
DS Phase 4 Recommendation System project
#### Overview

This project uses the data made available by the 'MovieLens' dataset, which contains 4 CSV files where information such as movie titles, ratings and users are stored. The goal of this project is to create a recommendation system for a new online movie streaming company. We will import the CSV files, inspect and clean the data, perform EDA and then build our models. 
### Business Understanding

Our stakeholder is a new start-up company who are attempting to build their own movie streaming service. I have been tasked with creating a recommendation system based off a collection of user movie reviews. Another aspect that will need to be addresses is how to recommend movies for a new user, something that is often call the 'cold-start' problem. 
I believe after the completion of the models our stakeholder will be able to properly suggest appropriate movies to their customers.


### Data Understanding
The 'MovieLens' dataset is provided by the GroupLens research lab at the university of Minnesota. As stated it is well documented dataset that contains everything from movie titles and ID's, user ID's and ratings, and movie genres. It is a great asset to companies in our position and should have the information we need to build our models. 

We begin by importing the libraries we will need in this project along with the MovieLens CSV files.

##### Movies by Year
A visual to represent year distribution:

![movie_year](https://user-images.githubusercontent.com/93612651/210814334-261a92ac-d927-4262-a0ff-3ff8e9272195.png)


##### Movies by Genre
![genre](https://user-images.githubusercontent.com/93612651/210814685-e90e96a8-93ce-4616-b134-903caaffbbb1.png)


##### Movies by Rating

![ratings](https://user-images.githubusercontent.com/93612651/210814789-1b67f96c-4e17-467e-8094-f23c04f805eb.png)




#### Colloborative Filtering with User-Item Matrix
I created several tables that can be used for a matrix. This is used in our recommendation system to represent the interactions between users and items, for example where each row is a userId and each column is an item, which in our case is a movie. 


****

### First Models

To begin, in the context of the Surprise library, the 'build_full_trainset' function is used to create a Trainset object from a Dataset object. A Trainset object is a special type of dataset object that is used to train a recommendation model in the Surprise library. It contains the ratings data, as well as additional information such as the indices of the users and items, the rating scale, and the number of ratings. And from the Trainset we can create the Testset and therefore are able to train the model and make predictions in the user-item matrix.

### The 2 Machine Learning algorithms being used are SVD and KNN

***
### SVD

Singular value decomposition (SVD) is a matrix factorization technique that can be used to decompose a matrix into its constituent parts. In the context of recommendation systems, SVD can be used to decompose a user-item matrix into the product of three matrices: a user matrix, a diagonal matrix of singular values, and an item matrix. These matrices can then be used to make recommendations to users.

***
### KNN
In addition to using SVD, we will also run and compare some KNN algo's.  In a recommendation system, KNN works by finding the K nearest neighbors of a user or item, and using these neighbors to make recommendations.

### Some Information On the Metrics...
#### RMSE
The root mean squared error (RMSE) is a measure of the accuracy of a prediction model. 

In a recommendation system, the RMSE score is calculated by taking the square root of the mean squared error between the predicted ratings and the actual ratings in the test set. The mean squared error is calculated by taking the sum of the squared differences between the predicted and actual ratings, and dividing by the number of ratings in the test set.

A lower RMSE score indicates that the model is making more accurate predictions, while a higher RMSE score indicates that the model is making less accurate predictions.

#### MAE

In a recommendation system, the MAE is calculated by taking the absolute value of the difference between the predicted ratings and the actual ratings in the test set, and averaging these differences over the number of ratings in the test set.

Like the root mean squared error (RMSE), the MAE is a measure of the average error of the model's predictions. However, unlike the RMSE, the MAE does not square the errors before averaging them, which means that it is less sensitive to large errors and may be more appropriate for data with a large number of outliers. And again,the lower the score the better.


### Algorithm Results

<img width="392" alt="Screen Shot 2023-01-05 at 2 53 43 PM" src="https://user-images.githubusercontent.com/93612651/210878059-f1fbfe35-1f1c-4171-8c8b-47cc3c1f1a08.png">


After the running and fitting the algorithms we ended up with respectable RSME and MAE scores. These metrics can be used to measure the difference between our models predicted rating and the actual rating.


### Predictions 
After we fine tuned the KNN and SVD algorithms I will use the .fit attribute and then plug them into the 'get_top_n' function provided in the Surprise library documentation. This will return the top 5 items with the highest rating prediction for each user. We will try this on both our algorithms, starting with KNN.

### Results:

Both models performed well, with the KNN returning movies that looked more practical and similar in genre

### Cold Start Problem

While the prediction and functions are producing some good results, there is one issue it does not address. It is something known as the 'cold-start' problem, where our model can not predict movies for a new user since it has not gathered any data from that person yet. 
To solve this problem we created a function that makes a new matrix for new users and makes predictions with that from the SVD algo we used previously.

### Conclusion:

We began by inspecting and cleaning the data and then proceeded to train our algorithms.
We got some very good results, especially with our KNN based model. Our 'cold-start' model is a work in progress but very promising. 

### Final Evaluation For our Stakeholder:

-  Use the KNN model to launch
-  Continue to test and re-run the models every few months
-  Continue to use the Cold-Start engine to gain better insight into recommendation for the customers
- Consider weighting movies based on genre or year released, several of these movies being returned are classics, but quite old



### Repository Structure:

## ---Project Models Notebook
## ---Project Notebook PDF
## ---README
## ---MovieLens Data ZipFile
## ---Project Presentation PDF
