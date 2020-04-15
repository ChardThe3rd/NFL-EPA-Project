# NFL EPA Project

![](Images/champions.jpg)

## Objective - Field (Goals)
* Can we train a model to intake data points from previous season NFL team stats?
* Based on the stats, how accurately can it predict the winner?
* Can we run multiple models selecting data we think should be more valuable to prediction.
* Can we used the train model to predict future games?
* Can we incorporate betting indicators on these results?

## Definitions - The Playbook
* EPA - Expected Points Added
* The value of a football play has traditionally been measured in yards gained.  But this is now considered a flawed measurement because not all yards are equal. 
* A 4-yard gain on 3rd down and 3 is much more valuable than a 4-yard gain on 3rd and 8. Any measure of success must consider the down and distance situation.
* Field position is also an important consideration. Yards gained near the goal line are tougher to come by and are more valuable than yards gained at midfield. Yards lost near one’s own goal line can be more costly as well.
* EPA is a method of assigning relational value to these different type of plays.

## Data and Munging - The Playing Field (SQL)
* Original dataset is listed by play, grouped by game_id
* Needed to remove non-plays (time-outs, penalties)
* Narrowed down to two lines per game_id for each team. Separated by home and away
* Creating a moving average of 3 previous games to populate in the rows of data. 

![](Images/SQL.PNG)

*Merging and appending in Pandas*
![](Images/pandas.PNG)

## Model - Trusting The Process
* Used a Deep Learning Sequential model with a dense layers, 
* We began our model with a near perfect accuracy of 99%. Quickly determined what our issue was
* Removed score of both teams, used results of the games the model was predicting. 
* Want the model to be trained based on what data it is going to use when predicting  

## Most Effective Model - EPA, Air Yards
200 epochs - 5 Runs: 
* Run 1: 58.6%
* Run 2: 58.6%
* Run 3: 56%
* Run 4: 56.8%
* Run 5: 57.7%
* AVG: 58%
![](Images/effmodel.PNG)

## Team Total EPA for the Season per Each Model Ran
![](Images/teamtotalEPA.PNG)

## Model Outcomes and Acknowledgements
* What are our insights from the various model runs?  All data was too much noise?  
* Turnovers are too unpredictable
* Models WITH EPA provided a higher accuracy result
* We have no ‘soft factors’ accounted for such as weather, home field advantage, etc.

## NFL Teams Total EPA Highlighted by Playoff Team or Not
![](Images/AllTeamsEPA.PNG)

## Chiefs EPA By Game
![](Images/ChiefsEPAByGame.PNG)

## Lessons Learned - Overtime
Challenges:
* Began with different data than what we would use to predict games
* Started out only using 2019 data but then incorporated 2018 to increase sample size

Opportunities:
* Coaches and General Managers
* Fantasy Sports (Isolate EPA by Player)
* Gambling Applications

## Conclusion
Publicly available data can help us better commentate, project, and analyze the game of football. It can be useful when making decisions in fantasy sports or when wagering on games, but it doesn't replace X's and O's
![](Images/TurningPoint.PNG)

