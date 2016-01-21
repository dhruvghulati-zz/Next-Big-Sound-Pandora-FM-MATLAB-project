# Next-Big-Sound-Pandora-FM-MATLAB-project

A data science user retention analysis project, to try and classify what features make a user within Next Big Sound active or not.

# Background

Next Big Sound ("NBS") is a music data platform that provides artists, bands, music labels and publishers to track musicians and get data on where they are playing, what their "signal" is within the music industry on a realtime basis, and also allow labels to sign new and upcoming artists in a data-driven manner. 

The aim of the project was to use Intercom attributes data to try and figure out what attributes were most important in converting a user of the NBS platform to being inactive or not (classification problem).

Active is defined as being above the 95th percentile of web sessions per month across all users.

# Results

Using a balanced dataset using manual under-sampling, a target random forest model achieves a 72.1% predictive accuracy rate, vs 50% for a dumb prediction. Using a decision tree, the is_premier feature was the only relevant feature in determining if a user would be active or not.

Using a lasso/elastic net, artists_paying_for and bookmarks were the two most important features, with weights of 25% and 15% respectively.

# Learnings

* I got one of the top grades in my class but because the course was more about investigation of a problem, different approaches, explaining what you did. 
* In full honesty I really wanted to build something that categorically says “this is the answer” but I have realised I was just scratching the surface - these things take time and lots of iterations, and gradual improvements! It isn't as easy as I thought :)
* I learnt that machine learning models are very black box - with a random forest model I know I can predict a user will be active or not with a 72% accuracy rate, but these models don't tell me what features were used most in this prediction.  Systematic feature selection is very hard. 
* Regression problems are the best at figuring out what is going on, because you can interpret them feature by feature. However when you have lots of categorical binary variables, regression functions do not work very well with this. With models like SVM or random forest you have to first pick the features then apply the model, then test again. So this is definitely an art not a science, which was definitely a key learning for me.
* Being purely applied and being able to write MATLAB functions is not the best way to really understand what is going on behind the scene.
* The aspects I would implement as next steps in terms of really adding value to Next Big Sound's user retention drive would be:
  * Add the huge amount of features that can come from event counts per user - I wrote a PHP script to get this from the Intercom API after a lot of wrangling from the team. Reimplement the models with these new features.
  * Verify accuracy of the model implementations
  * Improve prediction accuracy
  * Build a data cleaning pipeline
  * Implement stepwise logistic regression in the dataset and interpret results, as this should have been the most basic model. However, again there are issues with the fact there are so many categorical features.
  * Try different methods to balance the dataset beyond manual under-sampling
  * Ensure the models are fully cross validated (I used a simple 30/70 training split, but 10 fold cross validation would be next)

