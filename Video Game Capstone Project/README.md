# The Name of the Game

This holds all of my work for my second Springboard Capstone Project, *The Name of the Game*. In here you can find all of my code, reports and presentation. The source of my data includes a [kaggle dataset](https://www.kaggle.com/rush4ratio/video-game-sales-with-ratings), which contains the best-selling video games ever from 1985-2017, another [kaggle dataset](https://www.kaggle.com/dahlia25/metacritic-video-game-comments#metacritic_game_user_comments.csv) that includes thousands of reviews of video games and a dataset from the [University of Portsmouth](https://researchportal.port.ac.uk/portal/en/datasets/video-games-dataset(d4fe28cd-1e44-4d2f-9db6-85b347bf761e).html) with U.S. Sales info from 2004 to 2010.

The purpose of this project is to find what types of video games sell best. I dive into the Global Sales as well as the three main regions (North America, Europe and Japan) to see what types of games do the best as well as the different preferences for the key areas. I also utilized natural language processing to find many common words in reviews to help break down their impact. My goal is to see the trends and patterns that best impact video game sales as well as create a predictive model.

My Project Proposal is [here](https://github.com/SportsReiter12/Data-Science/blob/master/Video%20Game%20Capstone%20Project/Video%20Game%20Capstone%20Project%20Proposal.pdf).

Packages used include: numpy, pandas, re, nltk, langdetect, collections, matplotlib, seaborn, scipy, scikit-learn.

## Data Wrangling

For the first dataset, there was not too much cleaning needed. The games that had missing data tended to be older games when the Internet was not around. Those games were dropped and other features (like Genre and Platform) were also changed into binary columns.

The second dataset took the most work mainly because of all the preprocessing steps needed before I could start natural language processing on the many different reviews.

Some of the processes used include:
  - A function to remove non-letters and extra white space.
  - Using langdetect to make sure the reviews are in English.
  - Taking a sample of 10,000 to use as a base.
  - A function that tokenizes the words, stems them and then counts how many times they appeared in a review.
  - Making a DataFrame with all of these tokens and putting them through a TF-IDF Transformer.
  - Filtering the words based on their mean.
  - Putting the whole dataset through the same natural language processing, as long as they included the sample words from earlier.
  
While a very complex process, this led to a robust DataFrame that included the features from the first dataset as well as the average of how often a word appeared in a review for each game.

The last dataset was already clean and included binary columns so no work was needed.

My code is [here](https://github.com/SportsReiter12/Data-Science/blob/master/Video%20Game%20Capstone%20Project/Data%20Wrangling/Video%20Game%20Capstone%20Project%20Data%20Wrangling.ipynb) and the Data Wrangling Report is [here](https://github.com/SportsReiter12/Data-Science/blob/master/Video%20Game%20Capstone%20Project/Data%20Wrangling/Video%20Game%20Capstone%20Data%20Wrangling%20Report.pdf).

## Data Story

After going through many different plots, there were some that really stood out due to their impact on video game sales. For example, the relationship between Global and North American Sales was very strong.

![Fraction of Sales Between Global and North America](https://user-images.githubusercontent.com/37318222/54299426-160f3c00-4578-11e9-836f-95deab6d0815.jpeg)

The same could be said for the relationship between Global and European Sales.

![Fraction of Sales Between Global and Europe](https://user-images.githubusercontent.com/37318222/54299507-4656da80-4578-11e9-910a-31ae5b2c4d53.jpeg)

Yet the relationship between Global and Japanese Sales was not as strong as the other major regions.

![Fraction of Sales Between Global and Japan](https://user-images.githubusercontent.com/37318222/54299537-566eba00-4578-11e9-967a-9e545ec9761e.jpeg)

When it came to the type of game vs. sales, the spectrum had a surprise or two.

![Genre vs Regional Sales](https://user-images.githubusercontent.com/37318222/54300379-f8db6d00-4579-11e9-8c69-d4feb6bf71a3.jpeg)

So why do Shooters, which are big now, only sit in the middle? Maybe Japan can explain.

![Shooting Games vs  Japanese Sales](https://user-images.githubusercontent.com/37318222/54300661-8e76fc80-457a-11e9-97ae-f8d94d4022db.png)

And when it comes to the platforms the games come from, Nintendo leads the way.

![Platform vs  Regional Sales](https://user-images.githubusercontent.com/37318222/54300493-38a25480-457a-11e9-9efb-f8b51b48ad49.jpeg)

There are plenty of other important plots I found including the sale of Xbox 360 games in the major regions as well as Critic and User Scores vs. Regional Sales. For more information, the Data Story can be found [here](https://github.com/SportsReiter12/Data-Science/blob/master/Video%20Game%20Capstone%20Project/Data%20Storytelling/Video%20Game%20Capstone%20Data%20Story.ipynb).
 
And if you want to see all of the plots I made during the exploratory data analysis, click [here](https://github.com/SportsReiter12/Data-Science/blob/master/Video%20Game%20Capstone%20Project/Data%20Storytelling/Video%20Game%20Capstone%20EDA%20-%20Plots.ipynb).
 
## Inferential Statistical Analysis
 
Using the plots from above along with some of the other features, I ran t-tests, chi-squared tests and Pearson correlation tests to see how significant certain aspects of games are to sales as well as their relationships with each other.
 
Some of the most interesting results include:
   - Shooters, Sports and Action games sold worse in Japan while RPGs sold better.
   - Xbox 360 games sold better Globally as well as in North America and Europe but sold worse in Japan.
   - The relationships between Global Sales and North American as well as European Sales were over 0.9.
   - All regions had positive relationships with Critic and User Scores but were weak.
   
To see all of the tests I ran, the code is [here](https://github.com/SportsReiter12/Data-Science/blob/master/Video%20Game%20Capstone%20Project/Inferential%20Statistics/Video%20Game%20Capstone%20EDA%20-%20Inferential%20Statistics.ipynb) and the Inferential Statistical Analysis is [here](https://github.com/SportsReiter12/Data-Science/blob/master/Video%20Game%20Capstone%20Project/Inferential%20Statistics/Video%20Game%20Capstone%20Inferential%20Statistical%20Analysis.pdf).
