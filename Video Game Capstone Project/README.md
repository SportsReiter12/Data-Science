# The Name of the Game

This holds all of my work for my second Springboard Capstone Project, *The Name of the Game*. In here you can find all of my code, reports and presentation. The source of my data includes a [kaggle dataset](https://www.kaggle.com/rush4ratio/video-game-sales-with-ratings), which contains the best-selling video games ever from 1985-2017, another [kaggle dataset](https://www.kaggle.com/dahlia25/metacritic-video-game-comments#metacritic_game_user_comments.csv) that includes thousands of Metacritic reviews of video games and a dataset from the [University of Portsmouth](https://researchportal.port.ac.uk/portal/en/datasets/video-games-dataset(d4fe28cd-1e44-4d2f-9db6-85b347bf761e).html) with U.S. Sales info from 2004 to 2010.

The purpose of this project is to find what types of video games sell best. I dive into the Global Sales as well as the three main regions (North America, Europe and Japan) to see what types of games do the best as well as the different preferences for each area. I also utilized natural language processing to find many common words in reviews to help break down their impact. My goal is to see the trends and patterns that best impact video game sales as well as create a predictive model.

My Project Proposal is [here](https://github.com/SportsReiter12/Data-Science/blob/master/Video%20Game%20Capstone%20Project/Video%20Game%20Capstone%20Project%20Proposal.pdf).

My Final Report is [here](https://github.com/SportsReiter12/Data-Science/blob/master/Video%20Game%20Capstone%20Project/Video%20Game%20Capstone%20Final%20Report.pdf).

My Presentation is [here](https://github.com/SportsReiter12/Data-Science/blob/master/Video%20Game%20Capstone%20Project/Video%20Game%20Capstone%20Presentation.pptx).

Packages used include: numpy, pandas, re, nltk, langdetect, collections, matplotlib, seaborn, scipy, scikit-learn.

## Data Wrangling

For the first dataset, there was not too much cleaning needed. The games that had missing data tended to be older games when the Internet was not around. Those games were dropped and other features (like Genre and Platform) were also changed into binary columns.

The second dataset took the most work mainly because of all the preprocessing steps needed before I could start natural language processing on the many different reviews.

Some of the processes used include:
  - A function to remove non-letters and extra white space.
  - Using langdetect to make sure the reviews are in English.
  - Taking a sample of 10,000 reviews to use as a base.
  - A function that tokenizes the words, stems them and then counts how many times they appeared in a review.
  - Making a DataFrame with all of these tokens and putting them through a TF-IDF Transformer.
  - Filtering the words based on their mean.
  - Putting the whole dataset through the same natural language processing, as long as they included the sample words from earlier.
  
While a very complex process, this led to a robust DataFrame that included the features from the first dataset as well as the average of how often a word appeared in a review for each game.

The last dataset was already clean and included binary columns so no work was needed.

My code is [here](https://github.com/SportsReiter12/Data-Science/blob/master/Video%20Game%20Capstone%20Project/Data%20Wrangling/Video%20Game%20Capstone%20Project%20Data%20Wrangling.ipynb) and the Data Wrangling Report is [here](https://github.com/SportsReiter12/Data-Science/blob/master/Video%20Game%20Capstone%20Project/Data%20Wrangling/Video%20Game%20Capstone%20Data%20Wrangling%20Report.pdf).

## Data Story

After going through many different plots, there were some that really stood out due to their impact on video game sales. For example, the relationship between Global and North American sales was very strong.

![Fraction of Sales Between Global and North America](https://user-images.githubusercontent.com/37318222/54299426-160f3c00-4578-11e9-836f-95deab6d0815.jpeg)

The same could be said for the relationship between Global and European sales.

![Fraction of Sales Between Global and Europe](https://user-images.githubusercontent.com/37318222/54299507-4656da80-4578-11e9-910a-31ae5b2c4d53.jpeg)

Yet the relationship between Global and Japanese sales was not as strong as the other major regions.

![Fraction of Sales Between Global and Japan](https://user-images.githubusercontent.com/37318222/54299537-566eba00-4578-11e9-967a-9e545ec9761e.jpeg)

When it came to the type of game vs. sales, the spectrum had a surprise or two.

![Genre vs Regional Sales](https://user-images.githubusercontent.com/37318222/54300379-f8db6d00-4579-11e9-8c69-d4feb6bf71a3.jpeg)

So why do Shooters, which are big now, only sit in the middle? Maybe Japan can explain.

![Shooting Games vs  Japanese Sales](https://user-images.githubusercontent.com/37318222/54300661-8e76fc80-457a-11e9-97ae-f8d94d4022db.png)

And when it comes to the platforms the games come from, Nintendo leads the way.

![Platform vs  Regional Sales](https://user-images.githubusercontent.com/37318222/54300493-38a25480-457a-11e9-9efb-f8b51b48ad49.jpeg)

There are plenty of other important plots I found including the sale of Xbox 360 games in the major regions as well as Critic and User scores vs. Regional Sales. For more information, the Data Story can be found [here](https://github.com/SportsReiter12/Data-Science/blob/master/Video%20Game%20Capstone%20Project/Data%20Storytelling/Video%20Game%20Capstone%20Data%20Story.ipynb).
 
And if you want to see all of the plots I made during the exploratory data analysis, click [here](https://github.com/SportsReiter12/Data-Science/blob/master/Video%20Game%20Capstone%20Project/Data%20Storytelling/Video%20Game%20Capstone%20EDA%20-%20Plots.ipynb).
 
## Inferential Statistical Analysis
 
Using the plots from above along with some of the other features, I ran t-tests, chi-squared tests and Pearson correlation tests to see how significant certain aspects of games are to sales as well as their relationships with each other.
 
Some of the most interesting results include:
   - Shooters, Sports and Action games sold worse in Japan while RPGs sold better.
   - Xbox 360 games sold better Globally as well as in North America and Europe but sold worse in Japan.
   - The relationships between Global Sales and North American as well as European sales were over 0.9.
   - All regions had positive relationships with Critic and User scores but were weak.
   
To see all of the tests I ran, the code is [here](https://github.com/SportsReiter12/Data-Science/blob/master/Video%20Game%20Capstone%20Project/Inferential%20Statistics/Video%20Game%20Capstone%20EDA%20-%20Inferential%20Statistics.ipynb) and the Inferential Statistical Analysis is [here](https://github.com/SportsReiter12/Data-Science/blob/master/Video%20Game%20Capstone%20Project/Inferential%20Statistics/Video%20Game%20Capstone%20Inferential%20Statistical%20Analysis.pdf).

## Machine Learning

After trying out multiple different models, I decided to stick with Random Forest because it had the best results for each of the major types of sales. For preprocessing, I split each type into Training and Testing sets as well as used GridSearchCV. Also, sometimes extra parameters were used to help improve R^2 and the Root Mean Squared Error (but not by too much). Lastly, other than just using the model on overall sales, I also tried the model on the major types of sales for values greater than or equal to their median.

For Global Sales, R^2 was around 0.43 with an RMSE close to 2.72. As seen below, there was a fair amount of difference between the true and predicted data.

<img src="https://user-images.githubusercontent.com/37318222/54483925-36a9f100-4819-11e9-92ce-7b6de55c9dfd.png" height="700" width="780">

This slope was essentially the same for all of the overall types of sales.

When filtered by the median, R^2 improved to about 0.45 while the RMSE raised to around 2.85. However, this model shows more of a slope when it comes to the difference between the true and predicted data.

<img src="https://user-images.githubusercontent.com/37318222/54483929-475a6700-4819-11e9-954c-3a6f8776dfc7.png" height="700" width="780">

The model for North American Sales was similar with R^2 around 0.43 and a Root Mean Squared Error at about 1.33. When it came to important features, this model was also very similar to that of Global Sales.

<img src="https://user-images.githubusercontent.com/37318222/54468760-6a1f4980-474d-11e9-9fef-f1951a83b4d7.png" height="700" width="780">

While I do not know how the features impact the model (positively or negatively), the ones that stand out the most include Critic Score, Critic Count and User Count as well as the words "mw," "super" and "mario."

After being filtered by the median, the model for North American Sales did far worse with R^2 close to 0.16 and RMSE around 1.51. The Relative Error plot below gives a clearer picture of how far off the test and prediction data could be.

<img src="https://user-images.githubusercontent.com/37318222/54468849-2416b580-474e-11e9-9e9d-24949604e747.png" height="700" width="780">

So what feature makes such a big difference? It might be the extreme values in User Count.

<img src="https://user-images.githubusercontent.com/37318222/54468890-735ce600-474e-11e9-9df8-2e40b1c9c62e.png" height="700" width="780">

Having games with such massive differences in User Count was a consistent issue for most of these models when it came to test vs. prediction.

For European Sales, R^2 was around 0.38 with an RMSE close to 0.93 and similar important features compared to the previous models.

<img src="https://user-images.githubusercontent.com/37318222/54469119-23335300-4751-11e9-8444-f7f2a39c3c26.png" height="700" width="780">

Once again, User Count was very significant along with key words such as "fifa" and "mw." Words that are sticking out tend to be a name or acronym of a major video game franchise. After filtering European Sales by the median, R^2 and the RMSE minimally changed to about 0.33 and 0.85 respectively.

To wrap up this dataset, Japanese Sales actually had the same results when run through a Random Forest, whether the model was used on overall sales or subsetted by the median. R^2 was close to 0.37 while the Root Mean Squared Error was around 0.46. To make this region even more unique, the most important features included more of the companies that made the games.

<img src="https://user-images.githubusercontent.com/37318222/54469182-0b100380-4752-11e9-9965-2ac4c95f3121.png" height="700" width="780">

In Japan, publishers as well as developers like Nintendo and SquareSoft have a major impact on video game sales.

While R^2 and the RMSE tended to get lower for each type of sale from this DataFrame, the data from University of Portsmouth led to a strong Random Forest model as R^2 was about 0.86 and the Root Mean Squared Error was around 0.41 for overall U.S. Sales. When looking at the difference between the true and predicted data, there is a much steeper slope.

<img src="https://user-images.githubusercontent.com/37318222/54483933-648f3580-4819-11e9-966f-cf8df5a4d624.png" height="700" width="780">

Now this data did not include any natural language processing so some of the features were different. Yet, much like the other models, Genre and Platform were not that important.

<img src="https://user-images.githubusercontent.com/37318222/54469278-39421300-4753-11e9-94ed-901155182d8e.png" height="700" width="780">

Instead the most important features were the blocks of the year that games come out in with the holidays being the most critical. And those stayed important when filtered by the median (despite a few changes) along with an R^2 around 0.92 and RMSE close to 0.42.

With these different datasets, we get a clearer idea of what features truly have a big impact on video game sales when put through a predictive model.

The code can be found [here](https://github.com/SportsReiter12/Data-Science/blob/master/Video%20Game%20Capstone%20Project/Machine%20Learning/Video%20Game%20Capstone%20Machine%20Learning.ipynb) while the Machine Learning Analysis can be found [here](https://github.com/SportsReiter12/Data-Science/blob/master/Video%20Game%20Capstone%20Project/Machine%20Learning/Video%20Game%20Capstone%20Machine%20Learning%20Analysis.pdf).

## Conclusion
 
While there is plenty more to break down in this project, what stands out is how key factors like brand names, the amount of users who review games as well as release dates become critical for video game sales. Despite rushed deadlines being seen as major contributors for disappointing games, there is a reason why companies want their biggest products coming out in the busy seasons.
 
Yet, as informative as these results may be, there are a few ways to dig deeper:
 - Include games for older consoles to help see the impact of retro games and systems.
 - Along with video games, include console sales as well.
 - Utilize more reviews including the words used by critics.
  
To that end, I hope you enjoy the layered narrative of video game sales and truly understand why The Name is the Game.
