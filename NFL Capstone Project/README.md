# NFL Sabermetrics

This holds all of my work for my first Springboard Capstone Project, *NFL Sabermetrics*. In here you can find all of my code, reports and presentation. The source of my data is the [Stattleship API](https://www.stattleship.com/), which contains detailed statistics for all of the major American sports including the NFL.

The purpose of this project is to find what statistics best help an NFL team win. I look through three seasons of the NFL, from 2015 - 2018, and go game-by-game to get the statistics for each team. My goal is to see the trends and patterns that best help an NFL team's chance of winning, how coaches may want to approach the sport as well as create a predictive model.

My Project Proposal is [here](https://github.com/SportsReiter12/Data-Science/blob/master/NFL%20Capstone%20Project/NFL%20Capstone%20Project%20Proposal.pdf).

My Final Report is [here](https://github.com/SportsReiter12/Data-Science/blob/master/NFL%20Capstone%20Project/NFL%20Capstone%20Final%20Report.pdf).

My Presentation is [here](https://github.com/SportsReiter12/Data-Science/blob/master/NFL%20Capstone%20Project/NFL%20Capstone%20Presentation.pptx).

Packages used include: numpy, pandas, stattleship, itertools, matplotlib, seaborn, scipy, scikit-learn.

## Data Wrangling

After installing stattlepy on my system, I was able to query NFL statistics with filters like season, team, game and player. One of the issues, however, was that the API limits how many results you receive so I could not just query a full season normally.

Instead I worked on multiple ways to create the queries I wanted and looped through them. These methods include:
  - A function to change game names to game slugs
  - A For Loop that creates each combination of season and team
  - List comprehension to get the name for each game
  - A function that gets the names of the winning, losing and possibly tying teams
  - A For Loop that takes all of these to get statistics from each game
  
Luckily this API had most statistics I wanted so I could easily extract what I wanted from each query. The important distinction is whether the team is away or home. 

Overall, there was not much missing data or at least any that needed cleaning. Events that did not occur usually received a zero and are still important for this project because they help illustrate importance.

My Data Wrangling Code is [here](https://github.com/SportsReiter12/Data-Science/blob/master/NFL%20Capstone%20Project/Data%20Wrangling/NFL%20Capstone%20Project%20Data%20Wrangling.ipynb) and the Data Wrangling Report is [here](https://github.com/SportsReiter12/Data-Science/blob/master/NFL%20Capstone%20Project/Data%20Wrangling/NFL%20Capstone%20Data%20Wrangling%20Report.pdf).

## Data Story

While there were many interesting plots from this data, I decided to focus on some of the most profound ones. For instance, Road Passing Attempts vs. Home Win was very surprising as this actually helped the opposing team win.

![alt text](/Users/dwreiter/Desktop/Work/Springboard/NFL Capstone Project/Data Storytelling/Road Passing Atts vs Home Win.png)

Another interesting visualization is how much of an increase win percentage there was in Home INT TDs vs. Home Win.

![alt text](/Users/dwreiter/Desktop/Work/Springboard/NFL Capstone Project/Data Storytelling/Home INT TDs vs Home Win.png)

The other top plots include:
   - Road Rushing Attempts vs. Road Win
   - Road Time of Possession vs. Road Win
   - Road Passing First Downs vs. Road Win
   - Road Sacks Given Up vs. Home Win
   - Home Goal To Go Successes vs. Home Win
   - Road Fourth Down Successes vs. Home Win
   
 The Data Story is [here](https://github.com/SportsReiter12/Data-Science/blob/master/NFL%20Capstone%20Project/Data%20Storytelling/NFL%20Capstone%20Data%20Story.ipynb).
 
 And if you are wondering how some of the above statistics impact the opposite team or any other statistic that I obtained while wrangling the data, click [here](https://github.com/SportsReiter12/Data-Science/blob/master/NFL%20Capstone%20Project/Data%20Storytelling/NFL%20Capstone%20EDA%20-%20Plots.ipynb).
 
 ## Inferential Statistical Analysis
 
 Using the plots from above as well as other popular statistics, I ran some t-tests, chi-squared tests and Pearson correlation tests to see how significant these stats were towards winning.
 
 Some of the most interesting ones include:
   - Rushing Yards and Total Yards (for either team) is statistically significant.
   - Passing Yards (for either team) is **not** statistically significant.
   - The relationship between Road and Home INTs Given Up is statistically significant
   
 To see all of the tests I ran, the code is [here](https://github.com/SportsReiter12/Data-Science/blob/master/NFL%20Capstone%20Project/Inferential%20Statistics/NFL%20Capstone%20EDA%20-%20Inferential%20Statistics.ipynb) and the Inferential Statistical Analysis is [here](https://github.com/SportsReiter12/Data-Science/blob/master/NFL%20Capstone%20Project/Inferential%20Statistics/NFL%20Capstone%20Inferential%20Statistical%20Analysis.pdf).
 
 ## Machine Learning
 
 When it came to predictive modeling, I started with a Logistic Regression model split between road and home teams since teams either win or lose. I used the standard train-test split as well as GridSearchCV to help with any overfitting issues. Afterwards, I fit the training data and predicted on the testing data with some very accurate scores.
 
 The Road Team model was around 96% accurate while the Home Team model was about 91% accurate. When it came to feature importance, the more impactful ones included scoring plays and turnovers while yards and time of possession were near the bottom.
 
 However, both models had high log losses. Because of this, I also made another model of each using Random Forests.
 
 For that, the Road Team model was about 92% accurate with the Home Team model being around 86% accurate. Once again, the model for the away team was stronger but both were weaker than Logistic Regression.
 
 Feature importance was a little different here as statistics like kickoffs, rushing attempts and time of possession were high while infrequent scoring plays and actions on special teams were low.
 
 Yet again, the log losses were high meaning you would be punished for being confident and wrong. However, the point of this project was more about accuracy and that is what these models succeed in. If one inputs all the stats from a game, they can tell you whether a team won or not.
 
 The code is [here](https://github.com/SportsReiter12/Data-Science/blob/master/NFL%20Capstone%20Project/Machine%20Learning/NFL%20Capstone%20Machine%20Learning.ipynb) and the Machine Learning Analysis is [here](https://github.com/SportsReiter12/Data-Science/blob/master/NFL%20Capstone%20Project/Machine%20Learning/NFL%20Capstone%20Machine%20Learning%20Analysis.pdf).
 
 ## Conclusion
 
 What became apparent throughout this project is how unimportant passing yards are in the NFL. Although the NFL is more seen as a passing league, statistically it does not help you. And as seen in many of the above analyses, there is a mix of what plays really impact a team's chance of wining.
 
 That said, there are ways this project can be furthered including:
  - Being more team-specific because of personnel
  - Using more seasons (I did have an issue with the expect number of games I received from the API)
  - More situational decisions instead of a general view
  - Find more statistics to utilize
  
With all that said, this project gained some major insight about what really helps a team win in the NFL and I hope you enjoy seeing my rendition of NFL Sabermetrics.
