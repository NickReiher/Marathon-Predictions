# Marathon-Predictions
Machine learning models that predict the finishing times of marathon runners. 

## Inspiration
In 2017, I watched thousands of runners competing in the Berlin Marathon. They varied widely in age and came from countries all over the world. While watching, it was easy to see that the frontrunners came mostly from Kenya and Ethiopia, and were in their 20s or 30s. A few hours later, you noticed that the final finishers tended to be older. But there were definitely exceptions, so I started to wonder just how closely you could predict the finishing time of a runner just by knowing their age, gender, and country. That's when I decided to take a look at the data.

## Raw Data
The data comes from the official Berlin Marathon website. I used BeautifulSoup to scrape it, and then pandas to get it into usable form.

## Hypothesis
I expected that for certain countries, it would be quite easy to predict the finishing times of runners. For example, there are very few amateur runners from Kenya or Ethiopia, so once you know their gender, you can narrow in on the range pretty narrowly. 
For countries like Germany, which have a lot of participants, it would be a lot harder. There are runners of all ages and genders who are serious runners, but also lots who are running their first marathon and will be towards the back of the pack.
While looking at the data, I saw that it was easy to find another feature that would likely correlate quite well with the finishing times: the amount of time after the gun that the runner crossed the starting line. In big races like this with tens of thousands of runners, it takes some runners almost an hour to cross the starting line! The organizers don't put the people in line randomly: the faster runners go to the front so they don't have to be passing people the entire time.

## Tools
I used scikit-learn to create some machine learning models that would predict the finishing time based on the four features I mentioned earlier
- gender
- age
- country
- start time

First I used a dummy regressor so I could get a baseline for my predictions - it just predicted the mean finishing time from the training data for everyone. It led to a mean absolute error of 36.6 minutes.
Then I used GridSearchCV to find the best hyperparameters for a Ridge Regression, which led to a mean absolute error of 23.1 minutes when applied to the test set.
Finally, I found a Random Forest Regression (again, using GridSearchCV to tune the hyperparameters) that had a mean absolute error of 22.5 minutes.

Here's a Jupyter Notebook with the code and more detailed analysis: https://github.com/NickVance/Marathon-Predictions/blob/master/Berlin%20Marathon%20Predictions.ipynb

## Future Projects
I've thought of some possible future projects using these models as the basis:
- see how the models work at predicting the results of the 2018 Berlin Marathon
- add more historical data and create models that predic the results of the 2019 Berlin Marathon
- extend the models to work on other marathons: ones that I have the complete results on (at least for a couple of years) and ones that I have limited data on (for example, only the winning time or average finishing time)

