# Marathon-Predictions
Machine learning models that predict the finishing times of marathon runners. 

## Inspiration
While watching the Berlin Marathon, I saw thousands of people of all ages from all around the world competing to run 42 kilometers as fast as they could. The top finishers were mostly Kenyans and Ethiopians in their 20s and 30s. At the back of the pack, finishing a few hours later, were older men and women, mostly from Europe. I started to wonder just how closely you could predict the finishing time of a runner just by knowing their age, gender, and country, so later that week I decided to take a look at the data.

## Raw Data
The data comes from the results page of the official Berlin Marathon website: https://www.bmw-berlin-marathon.com/en/impressions/statistics-and-history/results-archive/. I used BeautifulSoup to scrape the data and then pandas to get it into usable form.

## Hypothesis
I expected that for certain countries, it would be quite easy to predict the finishing times of runners. For example, there are very few amateur runners from Kenya or Ethiopia, so once you know their gender, you can narrow in on the range pretty closley 
For countries like Germany, however, it would be a lot harder. There are runners of all ages and genders who are serious runners, but also lots who are running their first marathon and will be towards the back of the pack. There are also a lot more runners from Germany, so they will have a much greater influence on the average error.
While looking at the data, I quickly found another feature that was easily availabe in the data and likely to correlate quite well with the finishing times: the amount of time after the gun that the runner crossed the starting line. In big races like this with tens of thousands of runners, it takes some runners almost an hour to cross the starting line! The organizers don't put the people in line randomly: the faster runners go to the front so they don't have to be passing people the entire time.

## Tools
I used scikit-learn to create some machine learning models that would predict the finishing time based on the four features I mentioned earlier
- gender
- age
- country
- start time

## Results
First, I used a dummy regressor so I could get a baseline for my predictions - it just predicted the mean finishing time from the training data for everyone. It led to a mean absolute error of 36.6 minutes.
Then I used GridSearchCV to find the best hyperparameters for a Ridge Regression, which led to a mean absolute error of 23.1 minutes when applied to the test set.
Finally, I found a Random Forest Regression (again, using GridSearchCV to tune the hyperparameters) that had a mean absolute error of 22.5 minutes.

Here's a Jupyter Notebook with the code and more detailed analysis: https://github.com/NickVance/Marathon-Predictions/blob/master/Berlin%20Marathon%20Predictions.ipynb

## Future Projects
I've thought of some possible future projects using these models as the basis:
- see how the models work at predicting the results of the 2018 Berlin Marathon
- add more historical data and create models that predic the results of the 2019 Berlin Marathon
- extend the models to work on other marathons: ones that I have the complete results on (at least for a couple of years) and ones that I have limited data on (for example, only the winning time or average finishing time)

