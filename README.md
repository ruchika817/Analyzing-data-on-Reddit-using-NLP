
# Are Dairy Farms in Trouble?



## Problem Statement
According to the Dairy Farmers of America(DFA), sales of milk dropped by over 9% last year. The reasons for this could be rising awareness of global issues, animal rights, environmental impact of milk, dairy intolerance etc.

I am a dairy farmer, who is seeing profits going down and wants to make a decision about switching to the production of plant based milk. To do this I need insights about whether people who predominantly eat plant based food (Vegetarians) are switching from dairy milk to plant based milk alternatives like almond milk, oat milk etc.

I will be looking at reddit posts from the subreddit forums of Vegetarians and Vegans so I can target the Vegetarians for my research.I find that both the categories of people post freely in both subreddits and I would need to do some processing of the posts to figure out who to target. I will be running a few regression models on the words of the texts that I have to find where each post belongs. The Regression models that I think will work the best are the CountVectorized Logistic Regression, the CountVectorized Multinomial Bayes Model, the TF-IDF Vectorized Logistic Model and the TF-IDF Vectorized SVM (Support Vector Machine) Model. I will be using the metric of the Cross Validated Accuracy Score to compare my models to choose the best one.

## Resources

- Reddit
- Libraries used
-- Numpy
-- sklearn
-- matplotlib
-- pandas





## Executive Summary


In order to begin the process of building the model, I first had to scrape data using the Reddit Pushshift API. The API allows for only 30 days at a time. So I had to create a loop so that we could get data from the last 150 days, from both the subreddit forms, r/Vegetarian and r/Vegan.

Data Cleaning : The data was cleaned in a few ways. The simplest was dropping unnecessary columns as well as converting the date_posted column into an actual datetime data type. Next I removed HTML characters as well as all other characters and numbers and the [removed] datapoint, which I think were images.I also combined the 'title' column with the 'selftext' column so that I would have a larger amount of text to work with. Since I had less than 5000 rows, it made sense to get the largest amount of text that I could get.   

Preprocessing and Modeling: After cleaning the data, I decided to Lemmatize the data and add stopwords to the existing stopword dictionary. This was done to avoid words that frequently appeared in posts because that would give us false positives in my model. I attempted to use and fit CountVectorizer and TF-IDF Transformers and various classifiers including logistical regression, Support Vector Machine and multinomial naive bayes. We complemented these classifiers with some necessary hyperparameters in order to select the best classifier, based on accuracy.

## Conclusions

The problem that we had set out to solve was to identify the Vegetarians from the posts that were posted to the two groups Vegetarian and Vegan because we want to start producing plant based milk as against dairy milk. We used Pushshift's API to collect data from two of the subreddits 'Vegetarian' and 'Vegan'so that we can identify the posts that are being posted by Vegetarians. After doing the initial cleanup of the data, I concatenated the dataframes to be used for training the model.

While doing the EDA, we found the days of the week that were the post popular for postings so that we were able to get a larger amount of posts to use in our training data.

The best model to predict whether a post belongs to the Vegetarian or the Vegan subreddit was the Logistic Regression with TFIDF Vectorization. It had an Accuracy Score of 82% and a Cross Val Score of 83%. It also had the ROC accuracy score of 91%. It was clearly the better model compared to the baseline as well as all the other models that I tested.

I was surprised that the SVM did not perform as well. Though its Cross Val score was 0.81, not much different from the Logistic model, it had a very high variance implying that it was very overfitted. Since SVM fits a hyperplane to classify data, that is understandable.

Using this model, I would get reasonably good results in identifying which posts belonged to the Vegetarians in the group and which would belong to the Vegans. I would then be able to target my surveys at the people in the Vegetarian group and find out if they would want to drink plant based milk.

##  Next Steps
For next steps there is plenty of scope to better the model and find out if there is another one. Some of the models to try are Decision Trees or Random Forest models

I would like to be able to get more posts to run the regressions with a larger dataset.

Run regressions with other reddit groups included.. Like the meat eaters..to see if they would like to have plant based products as well
