Results and Interpretations from Comprehensive Attacking Soccer Players Analysis
 
# Introduction

This document presents a comprehensive analysis of data primarily sourced from Transfermarkt.com, focusing on attacking players in professional soccer. The dataset was meticulously scraped from the website, ensuring a rich collection of relevant data.
The initial phase involved cleaning and processing the data using SQL, a step crucial for ensuring accuracy and reliability in the subsequent stages of analysis. This process streamlined the dataset, making it more conducive for detailed examination. I further preprocessed the data using Python. This stage involved refining the dataset, preparing it for more sophisticated analytical techniques.
To enhance my understanding and to present the data in an easily interpretable format, I utilized Tableau for visualization. This allowed me to transform complex data sets into clear, insightful visual representations, making the analysis more accessible.
Advanced statistical methods were employed, including the construction of confidence intervals and hypothesis testing. These techniques provided a robust framework for evaluating the data and drawing statistically significant conclusions.
Two predictive models were developed:
1. Logistic Regression Model: This model achieved an accuracy of 0.80 and was designed to predict whether a player is likely to win an individual title in their lifetime. The high accuracy of this model underlines its potential utility for player assessment in professional soccer.
2. Random Forest Model:  With an R-square value of 0.5, this model aimed at predicting the performances of players in next years. The model's moderate predictive power demonstrates its value in forecasting player performances. Once the model has been created and trained using the 2022 goals dataset, the next step is to utilize it for predicting the 2023 goals. Subsequently, we can identify the highest-scoring player in 2023 based on the predictions generated by our model.
The key variables include:

Name: The player's name.
Sub-Position: Specific playing position.
Country: Player's country of origin.
Matches: Total matches played.
Goals: Total goals scored.
CurrentValue(M): The current market value of the player in millions.
Progress: The player's performance progress over the last three years.
Age: The age of the player.
Minutes: Total minutes played by the player.
Injury_Sum: Total Matches missed by player due to injury.
Achievements: Career achievements.
Assist Per Season: Average assists per season.
League, Team: Current playing league and team.
Goals by Year (2020, 2021, 2022): Goals scored in specific years.
League_Code: League representation code.
Cups: Number of cups won.
Position: Numerical code for playing position.

# Confidence Intervals

Case Introduction: 
Imagine a scenario where one of the prominent Manchester football clubs faces a sudden setback as their star striker sustains a season-ending injury. With their key player sidelined, the club urgently seeks to bolster their squad by acquiring a top-tier attacking player to maintain their competitive edge in the upcoming season. To ensure they make an informed and confident decision, they turn to us (data analyst) with a crucial question: How much can they expect to pay for a young & quality attacking player while asked to being highly confident (95%) in the estimated price?
     Analysis:
My analysis commences by delving into the dataset, focusing on soccer players' values, with a particular emphasis on a variable known as "Currentvalue(M)," representing the market value of players in millions. This variable plays a pivotal role in deciphering various facets of player dynamics, including performance, popularity, and market demand.
In light of the specific scenario where a Manchester club seeks a replacement striker, we will continue with a selected subgroup of players. This subgroup consists of young attacking players aged between 22 to 28 years and those deemed "good" based on their ContributionPermin, which falls below 140. This meticulous filtering mirrors the practical need to identify high-potential attacking talents. 
Our methodology for estimating the market value of these sought-after young and high-performing attacking players in 2023 involves the utilization of the sampling concept. I utilize the Central Limit Theorem (CLT) in our analysis because performing t-statistic tests on non-normally distributed data can be problematic. By applying CLT, I transform the player values within this specific subset into smaller, manageable samples. Within each of these samples, we calculate the average market value. This approach allows analysis to provide valuable insights into the typical market value exhibited by players meeting these stringent criteria while addressing the challenges posed by non-normal data distributions.
Final dataset after CLT implementation:

<img width="648" alt="Screenshot 2023-11-18 at 3 35 25 PM" src="https://github.com/aliiyevali/Soccer-Player-Analysis/assets/147966223/03573c14-1c3f-4564-a02b-66e8ef01a26f">

To provide the Manchester club with a highly confident (95%) estimate of how much acquiring such a player might cost in 2023, we employ statistical techniques to determine confidence intervals around the sample means. These intervals offer an estimate of the likely range in which the true average market value of these players resides, given our sample data. The use of a specific multiplier in the calculation assures a 95% level of confidence, demonstrating our commitment to precision. Based on our rigorous analysis, we estimate that the market value for these promising young attacking players in 2023 falls within the range of $26 million to $42 million, thus empowering the Manchester club to make a well-informed and confident decision in their pursuit of a replacement striker.

# Hypothesis Testing

Some experts suggest that left-footed players have more abilities in playmaking, such as providing assists, while right-footed players are often associated with having better finishing skills when it comes to scoring goals. This raises the question of whether these notions are grounded or if they are merely myths in the world of soccer. To shed light on this topic and investigate whether there is a substantial difference in playmaking abilities between left-footed and right-footed players, I will conduct an analysis using statistical methods to determine the validity of these claims.
Non-Normal distributions of Goals by Right, Left footed players:

<img width="959" alt="Screenshot 2023-11-18 at 3 57 35 PM" src="https://github.com/aliiyevali/Soccer-Player-Analysis/assets/147966223/c2729efb-2d0d-4994-a058-05967ec81f39">

I conducted a hypothesis test to examine whether there is a significant difference in playmaking skills, as indicated by the number of assists, between left-footed and right-footed attacking players. To perform this analysis, I used the Mann-Whitney U test, which is appropriate for comparing non-normally distributed data.
The null hypothesis in this test is that there is no significant difference in assist production between left-footed and right-footed attackers. To determine whether I can reject the null hypothesis, I compare the calculated p-value to a predetermined significance level (alpha), which in this case is set at 0.10.
- The U-statistic provides a measure of the rank-based difference between the two groups. In this case, the U-statistic is 45358.5.
- The p-value, which is 0.4039, represents the probability of obtaining results as extreme as the ones observed in our data, assuming that the null hypothesis is true.
Given that the p-value (0.4039) is greater than the significance level (alpha = 0.10), I do not have sufficient evidence to reject the null hypothesis. Therefore, I conclude that there is no significant difference in final passing ability, as measured by assists, between left-footed and right-footed attacking players based on the data analyzed.
As a result, there is no strong statistical evidence to support the idea that left-footed attackers provide significantly more assists than right-footed players in the dataset.
In the second phase of analysis, I conducted a hypothesis test to explore whether there is a significant difference in goal-scoring abilities between right-footed and left-footed players. To perform this analysis, I utilized the Mann-Whitney U test again, which is particularly suitable for comparing non-normally distributed data.
In this context, the null hypothesis posits that there is no significant difference in goal-scoring abilities between right-footed and left-footed players. To ascertain whether I can reject the null hypothesis, I compared the calculated p-value to a predetermined significance level (alpha), which in this analysis was set at 0.10.
- The U-statistic represents a measure of the rank-based difference between the two groups. In this case, the U-statistic is 52398.0.The p-value, which is approximately 0.0297, signifies the probability of observing results as extreme as those in our data, assuming that the null hypothesis holds true.
- Given that the p-value (0.0297) is less than the significance level (alpha = 0.10), I have sufficient statistical evidence to reject the null hypothesis. This implies that there is indeed a significant difference in goal-scoring abilities between right-footed and left-footed players, based on the most-recent data including more than 700 records.
In simpler terms, the results suggest that right-footed players tend to have superior goal-scoring abilities compared to their left-footed counterparts in the dataset. This finding provides support for the assumption that right-footed players excel in terms of goal scoring.
Our analysis offers insights into football player performance in the year 2023, but it's important to consider that expert opinions may have been formed based on data and observations from previous years. The world of football is dynamic, with tactics, strategies, and player roles evolving rapidly over time. What held true in the past may not necessarily hold in the present. Expert viewpoints often reflect insights gathered during different football eras.
In essence, football performance is a complex interplay of factors, including individual skills, team strategies, opponent tactics, and coaching philosophies. Our findings shed light on player performance specific to 2023, but they should be viewed within the broader context of an ever-changing sport, where tactics and strategies continue to evolve in response to contemporary demands and trends.
In conclusion, these findings emphasize the complexity of soccer player abilities, which are influenced by various factors beyond just their dominant foot. In my opinion, every individual attacking player has unique skills and generalizing players by only their foot preference is not logical at this point. 

# Tableau Dashboard and Results

![Soccer TSA Dashboard](https://github.com/aliiyevali/Decoding-Soccers-Data-Secrets/assets/147966223/93e8832c-862d-4cd2-9efb-f23f93931d9f) 

Radial Bar Chart:
The top-left corner of the display features a radial bar chart showcasing the leading players with the highest number of stats between attacking football players. Each bar symbolizes a different top player, with its length indicating the total number of goals scored by particular attacking player —the longer the bar, the higher number of goals scored. Beside each player's name, the actual total number of goals is indicated numerically. Haaland, Mbappe, and Pedro are notable leaders in this chart, with Kane, Benzema, and Lewandowski also securing spots in the top 10.

The Progress Map
The "Progress Map" graph uses color intensity to indicate the progress of attacking players' market values in European countries over the last three years. Darker shades on the map represent countries with significant improvement or higher performance levels of attacking players, while lighter shades indicate less progress. This visualization allows for a quick comparative analysis of which countries have seen more substantial advancements in the values of their attacking football players in last 3 years.
We can divide Europe to 2 parts, While Western Europe continue to improve in soccer, Eastern Europe shows relatively less improvement. It also means trend will not stop and we will see Western Europe’s dominance in next years as in previous years. The Scandinavian countries have defied expectations with a significant improvement that can be considered most unexpected outcome from this graph.

Donut Charts
The donut charts on the dashboard represent the distribution of goals scored, assists made and counts of players categorized by their preferred foot: right-footed, left-footed, and both-footed. The "Goal Distribution by Foot" chart illustrates the average goals scored by each category, providing insights into the goal-scoring tendencies according to the players' foot dominance. The "Assist Distribution by Foot" chart, on the other hand, details the assists associated with players of each foot preference, highlighting the performance metric for right-footed, left-footed, and ambidextrous players within the football market. These visualizations help to analyze the performance and respective counts of different footed players. 
Left footed players are fewer than right-footed ones. Some sources, believe left-footed players are more valuable due to that reason. Our analysis almost resonates that with 5 million value difference between these 2 groups. In every economic situation, less can often hold more value. In the context of goals, it is evident that right-footed players tend to score relatively more, which aligns with the results of our hypothesis testing.

Time series Charts
The initial graph illustrates the goal-scoring trends across various leagues. The X-axis corresponds to league codes, while the Y-axis represents the total number of goals scored. Notably, some leagues exhibit a propensity for high-scoring matches, resulting in a significant goal tally. Conversely, certain leagues and their dedicated fan bases favor intense, pressure-packed gameplay, leading to elevated goal counts, as observed in the case of UK leagues. Moreover, leagues such as the Austrian and German leagues also register substantial goal figures, a phenomenon attributed to the tactical emphasis on offensive strategies, in contrast to the defensive orientation often seen in Italian leagues. Consequently, these leagues consistently produce a greater number of goals.
When assessing various player positions, it becomes clear that center forwards tend to excel in scoring. Furthermore, left-wing players have demonstrated superior scoring abilities compared to their counterparts on the right wing. This observation aligns with the findings of my hypothesis testing, which indicates that right-footed players, who predominantly occupy left-wing positions, have been responsible for a greater number of goals in the year 2023.
Analyzing the goal differences between years reveals a consistent upward trend, indicating a steady increase in the number of goals scored annually. This phenomenon can likely be attributed to the growing number of games played each year, which naturally results in a higher overall goal tally.

The Bar Chart
The bar chart labeled "Country-wise Goals and Injuries Comparison Chart" provides a visual comparison between the number of goals scored and the injuries sustained by football players from various countries. Each country is represented by a bar with size of goals and the color indicating the injuries. The bars reflect the total goals scored by players from that nation, while the injury colors indicate the frequency of injuries sustained over a specific period. 
As a result, it is evident that high-performing countries exhibit higher injury rates among their players. This contrast can provide valuable insights for discussions regarding the delicate balance between aggressive play and player safety within international teams, as well as the effectiveness of training and medical support across various footballing nations.
Furthermore, it's important to consider that the top three countries, namely England, France, and Spain, produce a substantial number of talented players. However, it's worth noting that two of these countries boast the best leagues globally, while the French league is often regarded as one of the most physically demanding. The Premier League, in particular, features the highest number of games in a calendar year compared to other leagues, which could explain the higher incidence of injuries. This serves as a reminder that more games can lead to the development of exceptional players but also expose them to a higher risk of injuries and physical strain.

# Value Calculator

In the world of football (soccer), determining the value of a player can be a complex and sometimes biased process. Factors such as market trends and personal opinions can skew valuations. However, to bring some objectivity into the equation, I've created a function that calculates a player's value based on concrete metrics, free from any emotional bias.
Key Metrics Considered:
	Performance Score: I start by evaluating a player's offensive performance, which is a combination of the number of goals they've scored and the number of assists they've provided to their team.
Age: Age plays a crucial role in assessing a player's value. Different age groups are given different weightings to reflect their career stage.
Injury Duration: I take into account the total duration of injuries a player has suffered, which can impact their availability to their team.
Awards: The number of achievements a player has earned is factored in to recognize their excellence in the sport.
Output:
The function returns a calculated player value, providing an objective estimate of their worth.

<img width="825" alt="Screenshot 2023-11-19 at 1 13 26 AM" src="https://github.com/aliiyevali/Soccer-Player-Analysis/assets/147966223/d0c3996a-9683-4110-a4b3-47669ad187b2">

Although our function may not offer a flawless representation of a player's value, it presents a structured and data-driven approach to the evaluation process. This approach can help mitigate the biases often linked to player valuations. To further enhance the function, we could consider assigning more weight to recent goals and introducing an additional factor that accounts for a player's experience by taking into consideration the various leagues they have played in. However, our dataset doesn’t contain that much information, it seems prudent to retain the function in its current form.

# Logistic Regression

First, I conducted an analysis to determine whether a player received an individual award. The primary objective of the logistic model was to predict whether a player would win an individual award during their career. 
Upon examining a heatmap, I decided to include the following columns in the model: 'Dummy Position,' 'Goals Per Season,' 'Assists Per Season,' 'Recent Progress,' and 'Injury Sum.' The 'Dummy Position' column was created based on the 'Position' column, assigning numerical values to indicate player positions. Additionally, I preprocessed the data to create new columns representing the average number of goals and assists per season for each player. ('Goals Per Season,' 'Assists Per Season,)
To ensure the model's accuracy, I performed VIF (Variance Inflation Factor) calculations and found that 'Assists Per Season' exhibited high multicollinearity with 'Goals Per Season.' Consequently, I chose to drop the 'Assists Per Season' column from the model.
Final Features passed Multicollinearity assumption:

<img width="191" alt="Screenshot 2023-11-19 at 1 17 45 AM" src="https://github.com/aliiyevali/Soccer-Player-Analysis/assets/147966223/96d00bdb-e9e0-49c4-840c-49aa4460acb9">

After creating and fine-tuning the model through multiple iterations, I concluded that the 'Injury' and 'Position' columns did not significantly contribute to the model's predictive power. It is worth noting that while players may experience injuries, these injuries typically do not have a substantial impact on their ability to earn individual awards over a career spanning 25-30 years. Additionally, the 'Recent Progress' column was found to be of limited value, as it only reflects a player's recent performance and only accounts for awards received prior to that limited period. Consequently, I decided to exclude these columns from the final model.
The Receiver Operating Characteristic (ROC) curve depicted below serves as a visual representation of the model's diagnostic capabilities. This curve illustrates the relationship between the true positive rate (sensitivity) and the false positive rate (1-specificity) across various threshold settings. In essence, when the blue line closely hugs the y-axis, it signifies superior performance. Our curve covers 81%, indicating a fairly strong performance.

<img width="729" alt="Screenshot 2023-11-19 at 1 19 55 AM" src="https://github.com/aliiyevali/Soccer-Player-Analysis/assets/147966223/e1b1870c-9eb9-40f1-8652-b68b4814bfde">

The model demonstrates an accuracy of 77.78%, signifying its capacity to correctly identify award winners approximately 77.78% of the time. This accuracy score underscores the model's overall predictive prowess. 
The precision score of 58.66% reveals that among all the players predicted to receive awards, approximately 58.66% of them actually do. This precision metric highlights the model's ability to make accurate positive predictions.
The recall score of 48.21% signifies the model's capability to identify genuine award winners. Although it captures less than half of the true award winners, it strikes a balance with other performance metrics.
The F1 score, standing at 52.94%, holds particular significance in scenarios where equal importance is assigned to precision and recall. The F1 score suggests a moderate equilibrium between precision and recall in our model's performance.
With an AUC (Area Under the Curve, can be viewed better in graph) of 0.8125, the model achieves a substantial level of discrimination between individuals who received awards and those who did not. An AUC of 0.8125 reflects strong model performance, indicating a high degree of separation between the positive and negative classes.
In summary, the model's predictive variables were narrowed down to 'Position' and 'Goals Per Season.' As a result of this refinement, the model achieved an impressive accuracy level of 80% as indicated by the confusion matrix, which is a highly satisfactory outcome.

# Machine Learning: SARIMAX

The initial modeling attempt utilized a SARIMAX model to forecast goal statistics. Time series analysis necessitates a different data format compared to conventional machine learning models. A second attempt involved reshaping the data to fit the SARIMAX model better, which yielded improved results. The reconfigured SARIMAX model, with transposed data, emerged as highly-accurate, achieving a Mean Absolute Error (MAE) of 3.3 and a Root Mean Squared Error (RMSE) of 4.6. The third trial included an ensemble and stacking of three models: an LSTM model to predict 2022 goals based on historical performance data, an XGBoost model leveraging players' exogenous data for the same year, and a linear regression model that synthesized outputs from the other models to forecast actual goals. 
Prior to modeling, the stationarity of the time series data was ascertained using the Augmented Dickey-Fuller (ADF) test, confirming the data's suitability for time series analysis. The accompanying graph illustrates the SARIMAX model's initial results, with an MAE of 6.4, which is anticipated to be halved through subsequent model optimization strategies.

![basladiq](https://github.com/aliiyevali/Decoding-Soccers-Data-Secrets/assets/147966223/7c7ba678-019d-4124-8736-18f52e04a030)

Following a thorough multicollinearity examination, I implemented both logarithmic and Box-Cox transformations on the target variable to mitigate any issues of heteroscedasticity. The results of these transformations exhibited a slight improvement over the use of the original target variable. Additionally, scaling was applied, which yielded marginal enhancements.
Further attempts at feature selection and hyperparameter tuning were made, experimenting with various combinations and settings. However, these efforts did not result in substantial gains.
The results of final model of my first try with 95% confidence intervals, From the graph, it's clear that while the model does follow the trend of the actual values to some degree, there is considerable volatility, and many of the predictions are not very close to the actual values (indicated by the vertical distance between the blue and orange lines). The confidence intervals are also quite wide for many of the predictions, which suggests that the model is not very certain about its forecast:

![basladiq2](https://github.com/aliiyevali/Decoding-Soccers-Data-Secrets/assets/147966223/966205f5-fec6-4918-886d-530c0f05ba8a)

Optimizing the model to achieve a Mean Absolute Error (MAE) of 5.9 has been a step in the model refinement process, but it falls short of the targeted performance goals. In the quest for further optimization, various strategies have been considered and tested.
Initially, the inclusion of team data was hypothesized to enhance model performance, under the assumption that team dynamics could be a significant predictor of individual player goal-scoring potential. However, this proved counterproductive, as the variability in goal-scoring across players from different teams year-on-year introduced more noise than predictive value.
Subsequently, a transformation of the dataset was applied, transposing the data to make it more amenable to the SARIMAX model, which improved the model's performance. The application of smoothing techniques directed the model to weigh recent years more heavily than older ones, leading to a better fit with a training MAE of 3.4 and a Test MAE of 5.2.
Given the impracticality of evaluating every possible feature combination due to time and resource constraints, my strategy has pivoted to assess features based on their causal relationships and associated coefficients. This phase led me to discard the 'minutes played' variable. My rationale was that the 'age' variable already serves as an indicator of a player's experience, rendering the 'minutes' data somewhat redundant. The subsequent results affirmed my hypothesis; excising the 'minutes' feature improved the model's performance, culminating in a training MAE of 3.38 and a test MAE of 4.69.
To contextualize, MAE—Mean Absolute Error—is a metric for gauging the proximity of the model's predictions to the actual outcomes. A lower MAE is synonymous with greater predictive accuracy. In the context of the training data, an MAE of 3.38 suggests that the model's predictions deviate from the actual goal count by an average of 3.38 goals. Similarly, an MAE of 4.69 for the test set denotes a slight uptick in the average error to 4.69 goals for data the model hasn't previously encountered, which is an expected phenomenon as models generally exhibit a dip in performance when confronted with new data.
Refined model results:

![basladiq3](https://github.com/aliiyevali/Decoding-Soccers-Data-Secrets/assets/147966223/ba67c27d-12ed-4101-810b-5477a49b9288)
![basladiq4](https://github.com/aliiyevali/Decoding-Soccers-Data-Secrets/assets/147966223/454a41bd-78fa-4177-9984-a348434f2139)

The plot above suggests that the SARIMAX model is capturing the patterns in the data effectively, and the errors it makes are seemingly random, which is what you aim for in a well-fitting time series model.

![basladiq5](https://github.com/aliiyevali/Decoding-Soccers-Data-Secrets/assets/147966223/0e2eec5a-fb08-4122-80ca-b925f8fed3c3)

The peak of the density plot is around 0, which is a good sign. It suggests that most predictions are close to the actual values.
The distribution appears somewhat normal but slightly right skewed, indicating that there are more instances of under-prediction (predicting fewer goals than actually scored) than over-prediction. I took into account the injury summaries of players; that's why the model is so good at handling overprediction. But for the underprediction problem, there is no merit in measuring these players. Reasons can differ in such a complex sport named football. 
There are a few large errors towards the right, which could represent outliers where the model has significantly under-predicted the number of goals. This is quite reasonable when you consider that some players unexpectedly score more goals in a single year, which is common in football. Experts even have a name for this kind of player: 'one-season wonder.' They peak in their career for a season and then return to their old numbers the next season.

![basladiq6](https://github.com/aliiyevali/Decoding-Soccers-Data-Secrets/assets/147966223/fc68e164-c429-41e5-ae75-e4f5c68b7282)

There is a visible spread between the actual and predicted values, which is expected in any predictive modeling task. The confidence intervals are quite wide, especially for higher values, indicating more significant uncertainty in the predictions for players with a large number of goals. The model seems to capture the general trend, but there are noticeable discrepancies, particularly for players with very high or very low goal counts. 

![basladiq7](https://github.com/aliiyevali/Decoding-Soccers-Data-Secrets/assets/147966223/86c63b9e-ccf5-4b15-9428-7cb4d0ea0546)

At lag 0, autocorrelation is always 1 because it's comparing each data point with itself. At higher lags, the autocorrelation values are hovering around zero. This suggests that there is little to no autocorrelation in the residuals at these lags, which is a good sign. It implies that the residuals (the errors made by the model) are random and don't follow a particular pattern over time.
Considering the entire range (0 to 60) of the target variable, an MAE of 3 or 4 can be seen as relatively good. The standard deviation of my target column is 7.1. A training MAE of 3 means that the average prediction error on the training set is less than half the standard deviation. This indicates that the model has a good level of accuracy on the training data.
A test MAE of 4, while higher than the training MAE, is still slightly over half the standard deviation. It signifies that the model is reasonably accurate on unseen data. The model is somewhat hindered by the high variability of the target variable. 
The next phase involves exploring more sophisticated modeling techniques by ensemble learning and stacking three distinct models, potentially capturing the complex relationships within the data more effectively. This ensemble approach could provide a pathway to achieving the desired prediction accuracy.

# Results from SARIMAX model:

As I mentioned, residuals don't have a pattern. The model captured patterns well, and there are no overfitting or underfitting problems. We can see it from the close numbers between the test and train MAE and RMSEs. The only concern can be some outliers in the data with so many goals. In football, coaches change one's approach by implementing attacking football, which leads to more goals, while others prefer defending and consider scoring only one goal to be enough for them. Coaches also affect players' performances, not only by their tactics but also by the relationships between them. The personal lives of players are another thing that can't be predicted. The luck in soccer is another unpredictable dimension. There is so much unpredictability when it comes to goals, and I consider a MAE of 3 and 4 very well in such circumstances.

# Leveraging the Ensemble and Stacking Techniques

The integration of LSTM and XGBoost models aims to augment the predictive robustness by harnessing their distinct capabilities. The LSTM model is configured to analyze sequential data, specifically the goal records from preceding years. In contrast, the XGBoost model focuses on a diverse array of player-specific features, offering predictions that account for the multifaceted nature of player performance. This strategic combination is designed to enhance the overall complexity and predictive accuracy of the system.![image]

![basladiq8](https://github.com/aliiyevali/Decoding-Soccers-Data-Secrets/assets/147966223/866cb318-eb87-43c3-b5e1-4f4bd3e35471)

The graph provides a clear depiction of the model's learning trajectory over numerous epochs. The training loss undergoes a steep decline, denoting a rapid adaptation by the model to the training dataset. The concurrent descent of the validation loss is indicative of the model's ability to generalize, as it implies that improvements in the model's predictions are not merely the result of memorizing the training data but also extend to previously unseen data. This is a positive sign that the model is learning patterns that are applicable to both the training and the validation datasets.

![basladiq9](https://github.com/aliiyevali/Decoding-Soccers-Data-Secrets/assets/147966223/00f9cd7a-2c57-4f1a-9563-a82656264f1d)

In examining the scatter plot, it's evident that for numerous data points, particularly at the lower end of the target value spectrum, the predicted values are in close proximity to the actual values, suggesting a reasonable degree of accuracy in the predictions. However, discrepancies become more pronounced with higher target values, signaling potential outliers previously discussed.
The model's predictions do not perfectly mirror the actual values, implying that overfitting is unlikely, and indicating a certain level of generalizability. The distribution of predicted values around the actual ones offers a visual gauge of the error margin, which stands at a Test Mean Absolute Error (MAE) of 4.65, similar to the result of the SARIMAX model.
The coefficient of determination, or R-squared value, hovers around 0.35 for both the LSTM and the XGBoost models. Efforts are being directed toward refining the R-squared value while also diminishing the error margins. The XGBoost model has a similar Test MAE of 4.72.
An ensemble approach, combining Long Short-Term Memory (LSTM) networks with XGBoost models, was employed to generate predictions based on their mean, which resulted in a slight uptick in the R-squared value to 0.39. However, it is hypothesized that stacking linear regression into this ensemble method could potentially enhance the model's performance further.
After implementing Linear Regression, the results are as follows:
•	R-Squared ~ 0.5
•	Test MAE ~ 4.2
•	Test RMSE ~ 5.6
These results indicate that the Linear Regression model has performed better than the individual LSTM and XGBoost models. It suggests that the model stacking approach effectively combines the strengths of both the XGBoost and LSTM models, resulting in more accurate and reliable predictions for the number of goals scored.
The Linear Regression model seems to address some of the weaknesses present in the XGBoost and LSTM models when used individually. As a result, the composite model created through model stacking outperforms any single model on its own. Below graph represents results of 4 models:

![basladiq10](https://github.com/aliiyevali/Decoding-Soccers-Data-Secrets/assets/147966223/11907f79-b1be-4f40-a32f-e6a1c59339ad)

The XGBoost, Linear Regression, and LSTM models exhibit differing levels of accuracy in their predictions when compared to the actual values. There are instances where one model surpasses the others, highlighting the unique strengths of each model depending on the specific data point in question. It's worth noting that the actual values themselves display substantial variability, and all the models are striving to make predictions in the face of this inherent unpredictability.
Furthermore, the normality of errors plays a crucial role in enhancing the models' predictive capabilities. It signifies that the models are effectively capturing the underlying patterns and tendencies within the data. The models are accounting for the random fluctuations and noise in the data, which can lead to more reliable and robust predictions.

![basladiq11](https://github.com/aliiyevali/Decoding-Soccers-Data-Secrets/assets/147966223/9208e9df-f476-4f9a-ab2e-0bf78e7d5acd)

# Conclusion:

As a consequence, I observed that as I introduced greater complexity, the model's performance consistently improved. As I've consistently emphasized, the essence of machine learning extends beyond mere performance enhancement; it entails striking a delicate equilibrium between complexity and performance. In my specific case, the optimal performing model featured a fusion of model ensembling and stacking techniques. It achieved a Test MAE score of 4. When assessing the intricacies of soccer, my target column’s standard deviation of 7 and a goal range spanning from 0 to 60, achieving a Test MAE of 4 is indeed an impeccable outcome. Key assumptions such as stationarity, multicollinearity, normality, homoscedasticity, and others validated throughout all processes. Soccer is renowned for its inherent complexity, with the number of goals susceptible to fluctuations due to factors such as player transfers, coaching tactics, injuries, luck, personal circumstances, and more. Despite these formidable challenges, the models performed admirably under these dynamic conditions.

# References:

https://www.simplilearn.com/tutorials/statistics-tutorial/central-limit-theorem#:~:text=and%20its%20applications.-,What%20is%20the%20Central%20Limit%20Theorem%3F,equal%20to%20the%20population%20mean.

https://www.udemy.com/course/the-data-science-course-complete-data-science-bootcamp/learn/lecture/10777190#content

Povak, N. A., Hessburg, P. F., McDonnell, T. C., Reynolds, K. M., Sullivan, T. J., Salter, R. B., & Cosby, B. J. (2014). Machine learning and linear regression models to predict catchment-level base cation weathering rates across the southern Appalachian Mountain region, USA. Water Resources Research, 50(4), 2798–2814. https://doi.org/10.1002/2013WR014203

https://towardsdatascience.com/ensemble-methods-in-machine-learning-what-are-they-and-why-use-them-68ec3f9fef5f







