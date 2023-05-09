# MaybeYouLike
## Authors: Tai Ta - Ryan Power

## 1. Introduction

For this project we had the goal of using the Spotify API to get songs, and predict whether the user would like these songs based on their listening history and preferences. We basically wanted to create a recommendation app, but instead of recommending new songs, we would give songs to the model and the model would output whether we will like that song or not. 

## 2. Methods / Case Study

To start out, we picked a dataset and decided what we wanted to do with it. In our case, we picked a dataset of songs from Spotify that were labeled “like” or “dislike”. Then, we wanted to create a model to predict, given a new song, whether it would be labeled “like” or “dislike”, based on the other songs that had been labeled. Each song had a variety of attributes which the model could assign weights to in order to predict which songs would be liked. Some of these attributes were things like danceability, energy, instrumentalness, loudness, and duration. So we wanted to create a model which could predict whether the user would like the song; for example, if the user tends to like to dance, then songs with higher danceability would have a higher chance of being a “like” by the user. 

Once we had fetched our data from the Spotify API, we decided to start out by testing a few different models using default parameters. Some of the popular algorithms for this type of problem are neural networks, KNN, Content-Based filtering, and decision trees or Random Forest. We decided to try out a few of these and pick the ones that performed better. We used the default parameters on a few algorithms included in the Sklearn library and fit them to our dataset to see the initial accuracy. We were evaluating the models on two datasets, one which we got from Kaggle and one which we made in the same format as the Kaggle database but with our own songs that we liked or disliked. We decided to add this second dataset for three reasons: 1) to have more data to train models on 2) so we could input new songs that we liked or disliked to test our model on 3) to see if different models would work better for different datasets.
