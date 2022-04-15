# MechaCar_Statistical_Analysis
Mod 15: Statistics and R
# Project Overview
In this project, statistics and hypothesis testing is used to analyze a series of datasets from AutosRUs’ and their competition using the R programming language. Below are some of the specific statistical tests that we will be running:
•	Perform multiple linear regression analysis to identify which variables in the dataset predict the mpg of MechaCar prototypes
•	Collect summary statistics on the pounds per square inch (PSI) of the suspension coils from the manufacturing lots
•	Run t-tests to determine if the manufacturing lots are statistically different from the mean population
•	Design a statistical study to compare vehicle performance of the MechaCar vehicles against vehicles from other manufacturers. For each statistical analysis, you’ll write a summary interpretation of the findings.

## Linear Regression to Predict MPG
 
Which variables/coefficients provided a non-random amount of variance to the MPG values in the dataset?
Using linear regression lm() function in R, I passed in all six variables and added in the DataFrame that I created. The equation looked like this:
mecha_car_regression <- lm(mpg ~ vehicle_length + vehicle_weight + spoiler_angle + ground_clearance + AWD, data=mecha_car) #generate multiple linear regression model

Reviewing the output in R, the variables with the most non-random (or fixed) amount of variance were vehicle_length and ground_clearance, as noted in the above image in yellow highlights. A linear regression model run on these variables against the values for MPG generated p-values of 2.60e-12 and 5.21e-08, respectively. 

Is the slope of the linear model considered to be zero? Why or why not?
The slope of the linear model is not considered to be zero, since the p-value is 5.35e-11 (also written as 0.0000000000535), as shown above in green, which is much lower than one would consider for the level of significance. The p-value for each term tests the null hypothesis that the coefficient is equal to zero (no effect). A low p-value (< 0.05, which this clearly is) indicates that we can reject the null hypothesis. This means that the relationship between our variables and the MPG is subject to more than random chance and changes in the predictor’s value are more related to changes in the response variable.

Does this linear model predict mpg of MechaCar prototypes effectively? Why or why not?
Yes, sort of. The Multiple R-Squared value above (in Cayan blue) is sitting roughly at 71%, so there is confidence in suggesting that the linear model does predict mpg for the MechaCar…at least so far as one is willing to invest in the confidence level of something at 71%. Short story is that we can certainly do better.

## Summary Statistics on Suspension Coil

The design specifications for the MechaCar suspension coils dictate that the variance of the suspension coils must not exceed 100 pounds per square inch. Does the current manufacturing data meet this design specification for all manufacturing lots in total and each lot individually? Why or why not?

![Total Summary](https://user-images.githubusercontent.com/96449605/163629683-8c83ad82-c9b5-47e1-8054-d585cdffca0d.png)

 
A review of the results of the T-test for the suspension coils across all manufacturing lots shows that they are not statistically different from the population mean, and the p-value = 0.0603 is not low enough for us to reject the null hypothesis.

 ![Lot Summary](https://user-images.githubusercontent.com/96449605/163629643-03d4a7be-d6eb-4d33-a466-d689b602c7ad.png)


1.	Lot 1. Reviewing the output for Lot 1 and its associated p-value = 1, we can see that it is not statistically significant and so therefore can confidently reject the null hypothesis.
2.	Lot 2. Reviewing the output for Lot 2 and its associated p-value = 0.6072, we can see that it is not statistically significant and so therefore can confidently reject the null hypothesis.
3.	Lot 3. Reviewing the output for Lot 3 and its associated p-value = 0.04168, we can see that it is statistically significant and so therefore can confidently reject the null hypothesis.



Deliverable 4

## Study Design: MechaCar vs Competition

To further aid AutosRU in refining their MechaCar prototype that advances its performance capabilities against the competition, we will design a study in order to get more comparative data against the industry competition. In this design study, the MechaCar data will be further analyzed against comparable data from the market’s competition to highlight metrics that may be of interest to potential consumers, as well as AutosRU's leadership.

Metric to test

With global warming and green energy being on everyone’s mind these days, economy and fuel efficiency is becoming more and more of a driving factor in consumer automotive purchases. With that being the case, we will design a study surrounding fuel efficiency (mpg) and compare that against industry competition.

Null and Alternative Hypothesis

•	Null Hypothesis = there is no difference in statistical significance between the MechaCar and its competition and so are equal. 
•	Alternative Hypothesis = there is a difference in statistical significance between the MechaCar and its competition and so are not equal.

Statistical Test Used

Since we’re determining statistical significance, we will use the one-way ANOVA test because it checks the impact of one or more factors (mpg in this case) by comparing the means of different samples between two groups. If we use a t-test instead of ANOVA test, it won’t be as reliable since the number of samples are more than two and will result in an error.

What data is needed

To perform this ANOVA test, we would need:
•	A dependent variable that is continuous and numerical variable. In this case, we are testing MPG, which would satisfy that requirement. 

•	An independent variable when using ANOVA that compare against vehicles of the same class using multiple categorical variables. This would be the different vehicles for comparison, the MechaCar prototype included. 

•	Sufficiently large (at least 30) sample sizes of each group. We would also operate under the assumption that the dependent variable (mpg) is normally distributed and that the variance among each group is similar.
