# Happiness_Index_EDA
 EDA of World Happiness Index

## Objective
Find, clean, and analyze data thorugh exploratory data analysis (EDA) investigating the World Happiness Index and determining if weather has any impact on happiness. 

## Techologies Used 
* Pandas
* Jupyter Notebook
* Matplotlib
* Seaborn

## Insipriation and Motivation
Due to the events that transpired in 2020, we wanted to see how the World Happiness Report measured happiness and what features impacted a countries happiness score the most. We also wanted to see if any outside factors such as weather has any impact on a countries happiness score. 

## Data 
* Kaggle: https://www.kaggle.com/unsdsn/world-happiness
* OpenWeather API:  https://openweathermap.org/api
* Google Maps API:  https://developers.google.com/maps

## Hypothesis
* Happiness has increased over time. 
* Weather positively affects happiness. 
* We predict happiness will decrease next year. (2020)

## Data Cleaning and Analysis 
We imported the each CSV for the years 2015-2020. Cleaned each year's data by formatting annd remaing columns for consistnnecy. We then merged all of these dataframes to create one CSV for comparison over time. 
<br>
We frist wanted to know which country is the most happy. We created a cholorpleth map that visulizes each countries Happiness Score from 2015-2020.  
<br>
![Choropleth-HappinessScore](Happiness/Images/Heatmaps/choropleth.png)
<br>
After analyzing who was happy, we analyzed the Happiness Score over time. The histogram shows a normal distribution of these scores over the 2015-2020 timeframe highlighted by the overlay. The violin plot of the Happiness Score goes on to emphasize this distribution for each year in addition to showing the slight increase in scores.
<br>
![Happiness-Overtime](Happiness/Images/Histograms/Histogram_of_Happiness_Score_Over_Time.png)
<br>
![Violin-HappinessScore](Happiness/Images/Violin_Plots/Violin_Plot_of_Happiness_Score_Over_Time.png)
<br>
ANOVA: Economy (GDP per Capita) After investigating the ANOVA for overall Happiness Score, we ran it with all of the different variables that made up the Happiness Score. All of the variables were statistically significant. It is important to note that for the variable Economy, the statistically significant result was fragile. By looking at the series of means in figure 4, the year 2015 is a very slight outlier compared to the rest of the years. Despite how inconsequential this may appear, we found that after removing this year from the test, there was no longer overall statistical significance for Economy.
<br>
![Violin-Economy](Happiness/Images/Violin_Plots/Violin_Plot_of_Economy(GDP_per_Capita)Over_Time.png)
<br>
![Table-Significance](Happiness/Images/Tables/variable_significance.png)
<br>
ANOVA: Health Life Expectancy Through ANOVA testing we found that another significant factor of overall happiness was the Health Life Expectancy variable. We also tried manipulating the test by removing the year 2017, as it was the outlier for this variable, to see if it would cause the same result as the Economy test. Once it was removed, the data was still statistically significant.
<br>
![Violin-LifeExpectancy](Happiness/Images/Violin_Plots/Violin_Plot_of_Health_Life_Expectancy_Over_Time.png)
<br>
Top & Bottom Countries After investigating the difference between different variables across the years, the countries that were repeatedly in the top and bottom 10% of the total countries based on their Happiness Score were investigated. The top three countries were Denmark, Norway and Iceland. The bottom three countries were Rwanda, Afghanistan, and Tanzania.
All three of the top countries' Health and Life Expectancy dropped from 2019 to 2020 whereas the bottom three countries have risen from 2019 to 2020. It is also worth noting that these values are quickly approaching each other, yet the bottom three countries remained in the bottom 10% and the top three countries remained in the top 10% based on Happiness Rank.
As the years go on, the top three countries are slowly decreasing whereas the bottom three continue to rise. This analysis of how the top and bottom countries changed over time lead us to dig deeper into our data to see what variable correlated most with Happiness Score.
<br>
![LineChart-HappinessScore](Happiness/Images/Line_Charts/Top_and_Bottom_Countries_Happiness_Score_over_the_Years.png)
<br>
T-tests T-tests were performed comparing the top 10 countries Happiness Score of 2015 to 2020, and then ran the same test for the bottom 10 countries. When looking at Happiness Score, both tests produced p-values greater than .05. Therefore the changes over time are not statistically significant, and we rejected the alternative hypothesis, accepting the null.
When running the test for Economy and Health, these tests all produced p-values less than .05. Therefore the changes were statistically significant, rejecting the null hypothesis and accepting the alternative.
<br>
![Ttest-Happiness](Happiness/Images/Tables/t_tests.png)
<br>
Correlations Economy and Health Life Expectancy have the strongest correlations. The strengths of these correlations were also investigated by creating scatterplots and running stats models. Since both r-values were above .5, they have a strong positive correlation.
Stats models were also run on the other variables. All of them had a positive r-value that was below .5 and therefore have a weak correlation with Happiness Score.
<br>
![Correlation-Heatmap](Happiness/Images/Heatmaps/Happiness_Correlation_Heat_Map.png)
![Table-Economy](Happiness/Images/Tables/happiness_v_economy.png)
![Table-LifeExpectancy](Happiness/Images/Tables/happiness_v_life_expenctancy.png)
<br>
### Correlations with Weather 

There are not very many strong correlations between any of the weather variables and the World Happiness Report variables. There is a slight positive correlation between Latitude and Happiness Score and a slight negative correlation between Temperature and Happiness Score.
After reviewing each R-value it became apparent none of the weather variables had a strong correlation with Happiness Score. There is a weak relationship between Happiness Score and Temperature. The calculated r-values for the simple linregress is 0.44 which shows that there is a weak positive correlation between Happiness Score and Latitude. 
![Correlation-Weather](Happiness/Images/Heatmaps/Correlation_Heat_Map_Weather.png)
![Regression-Temperature](Happiness/Images/Regressions/Regression_Happiness_Score_vs_Latitude.png)

Similarly, the relationship between Happiness Score vs Latitude shows a slight negative correlation. The calculated r-values for the simple linregress is -0.35 which shows that there is a weak negative correlation between Happiness Score and Temperature.

## Prediction Model
Stats models was run on all the variables from the World Happiness Report versus Happiness Score to create a prediction model. This provided an Adjusted R-squared of .714. As mentioned before, the Happiness Score is a sum of all of the variables, so it was expected that the r-squared would be high. The p-values for each variable were all at zero, or very close to it. Therefore, none of the variables are having a negative effect on correlation

![Table-Predictions](Happiness/Images/Tables/prediction.png)

## Prediction with Weather
Based on the correlation heat map, a multivariate regression prediction model was used to investigate if multiple weather variables (Latitude, Humidity, Cloudiness) could predict Happiness Score. The adjusted R-squared value decreased when any other variables were used.
Overall, the prediction model including weather variables holds a 21% accuracy rating, which indicates that our regression model is not the best.

It is apparent that the predictions do not cluster around the actual values (pink line) and there is a large discrepancy between the two values. This is also visualized where the residual values do not cluster around the 0 value, further proving that our regression model cannot be validated.
![Prediction-Weather](Happiness/Images/Tables/prediction_weather.png)

## Conclusions 
For our hypotheses we can now conclude that we were correct that happiness has increased over time, weather does not positively affect happiness, and that our ability to predict happiness is questionable because it is dependent upon the variables.

## Limitations 
There were a few limitations that we came across in our exploration of this dataset. These were in part due to our own lack of mastery over the method, but also due to the data itself. The dataset was limited because it was trying to quantify a feeling that everyone defines differently. While it may at first seem like the responses to the questions given were prone to subjectivity, we instead believe that the questions asked were. The dataset was also not uniform across all 6 years. Some countries were only reported for one year, and we didn???t use the raw dataset for this reason.

## Future Work
In the future we would like to expand our weather data by accumulating it over the same 2015-2020 time period and see if there really is any correlation between weather and happiness.. We would also bring in other factors such as education, housing, etc. to see if there is any connection between them and Happiness Scores.

## Contact
*Alex Arnold
*Sophie Knight
*Samantha Lane: slane700@gmail.com
*Rachel Podemski





