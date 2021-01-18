# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Data Science: Capstone Project - Analysis and predictions for the top 5 leagues

**Why this project?**

Since the start of the course I knew my capstone would have to be inspired on what I'm passionate about the most ... **Football!**

I've always felt that although performances and results depend on many factors, there is so much that stats can explain and insights to be found that can be extremely useful and used to add value to a team. I've decided to collect as much detailed data as possible from each player so that I could have as many insights as possible and make the most accurate predictions.

( for full pdf presentation - [presentation](https://github.com/rodmarialvas/Capstone-Rodolfo/blob/main/Capstone%20Data%20Science%20-%20Rodolfo.pdf) )

( for full code - [code](https://github.com/rodmarialvas/Capstone-Rodolfo/blob/main/Capstone%20Rodolfo.ipynb) )


### **Capstone Part 1: Goals**

1. Provide valuable insights that can be useful to agents, investors, betting companies, managers, scouts and football professionals in general.
2. Predict season average ratings and most important stats for each position with regression models. 
3. Predict level of season performance with classification models. 
4. Find the best performing young stars. (in Tableau) 

### **Capstone Part 2: Dataset + Data Collection**

1. **Data Source - Football Api**

![Data Source](https://github.com/rodmarialvas/Capstone-Rodolfo/blob/main/archi-beta.jpg)

I soon realized that collecting and cleaning the data would turn out to be the most challenging side of the project, this was due to the amount of nested dictionaries and lists and how the data was structured within the api.

![Text](https://github.com/rodmarialvas/Capstone-Rodolfo/blob/main/jsontext.png) 

2. **Selecting the data and creating final dataframe.**

Once I was able to clean all the data and collect all the information from the top 5 leagues, I've realized that the last 3 seasons were the ones where the data was accurate and complete. I've then decided I would be using just these seasons for the purpose of this project.


### **Capstone Part 3: EDA + Preliminary Analysis**

1. **Heatmap, pair plot, histograms and correlations.**

Initially, my idea was to only predict the average rating players get at the end of each season but after analysing the correlations via the heatmap, I was surprised that for some of the features the correlation was not as high as I expected. This led me to decide I would try and predict others variables as well, due to the nature of the sport I've selected the most important stats for each position (goals_scored for attackers and midfielders, assists for midfielders, duels_won for the defenders and goals_conceded for the goalkeepers). As the full heatmap is harder to read, I've created specific heatmaps to analyse each of the target variables and their correlations.


### **Capstone Part 4: Modeling with regressors**

Models used : Linear regression, LassoCV, RidgeCV, ElasticnetCV, Knn Regressor, Decision Tree Regressor ( shown below only some of the best results )

- **Predicting rating**:

1. **Linear Regression** 

| -------------------------- | ------------------ |
|Mean cross validation score | 0.2169554443734551 |

2. **DecisionTreeRegressor**(max_depth=8)

Mean cross validation score: 0.3432106216819707

- **Predicting goals_scored for attackers**:

1. **LassoCV**

Mean cross-validated training score: 0.8804026621170709

- **Predicting duels_won for defenders**:

1. **LassoCV**

Mean cross validation score: 0.9895123559099694

As score was very high I've also tried the model without the most correlated feature (total_duels).

Mean cross-validated training score: 0.7430688883066259

- **Predicting assists for midfielders**:

1. **LassoCV**

Mean cross-validated training score: 0.6845306409517158

- **Predicting goals_scored for midfielders**:

1. **LassoCV**

Mean cross-validated training score: 0.7438977475673354 (not as high as for the attackers)

- **Predicting goals_conceded for goalkeepers**:

1. **LassoCV**

Mean cross-validated training score: 0.92422246095634348


### **Capstone Part 5: Modeling with classifiers**

Models used : Logistic regression and Gridsearch (L1 & L2 penalties), Knn Classifier, Decision Tree Classifier, Random Forrest Classifier ( shown below only some of the best results )

- **Predicting top performing players with classifiers**

count    17077.000000

mean         6.874672

std          0.381241

min          3.000000

25%          6.680000

50%          6.850000

75%          7.062500

max          9.400000

As mean rating is 6.87, I've decided to create a binary variable where 'top performers' are all players performing above threshold of 7.0. 

0 = 'normal performers'

1 = 'top performers'

**Proportion of the classes**

0    0.703636

1    0.296364

baseline = 0.7036364701059905

**Due to unbalanced classes 'classweight = balanced' was used**


1. **GridsearchCV** ( penalty = l2, classweight = balanced, scoring = accuracy )

Best estimator mean cross validated training score:
0.7774645869511476

To reduce the amount of false positives ( these meant that the model was predicting players to be top performers when they weren't ) I've changed the scoring to 'precision'.

2. **GridsearchCV** ( penalty = l2, classweight = balanced, scoring = precision )

Best estimator mean cross validated training score:
0.9418300653594771


### **Capstone Part 6: Analysing the leagues and the top young stars in Tableau**

1. Comparison of discipline, offensive and defensive stats between leagues.
2. Understanding where do goalscorers come from to be able to determine which nationalities have more scoring talent and adapt better to each league.
3. Analysing the young stars that have been performing at a top level.

[Tableau link](https://github.com/rodmarialvas/Capstone-Rodolfo/blob/main/Capstone.twb)

*Created a dataframe just with under 23 players.

*Filtered the dataframe to have only players who performed above average and played more than 9 matches.

[Under 23 data](https://github.com/rodmarialvas/Capstone-Rodolfo/blob/main/Future%20Stars.ipynb)

(Tableau screenshots below)

![Tableau screenshots](https://github.com/rodmarialvas/Capstone-Rodolfo/blob/main/League%20stats.png)

![Tableau screenshots](https://github.com/rodmarialvas/Capstone-Rodolfo/blob/main/World%20Goals.png)

![Tableau screenshots](https://github.com/rodmarialvas/Capstone-Rodolfo/blob/main/Goals%20per%20nationality%20and%20league.png)

![Tableau screenshots](https://github.com/rodmarialvas/Capstone-Rodolfo/blob/main/Goal%20Scorers.png)

![Tableau screenshots](https://github.com/rodmarialvas/Capstone-Rodolfo/blob/main/Screenshot%202020-12-14%20at%2010.47.58.png)
