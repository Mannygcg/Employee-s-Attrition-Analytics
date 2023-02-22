# Employee's Attrition Analytics

## Introduction

The aim of this project is to provide analytical services to a company called 'Globex Pharma', in regards to their recent staff turnover - which it is suspected by the company due to dissatisfied employees looking for better opportunities in other companies.

Before the turnover, 'Globex Pharma' requested their employees to complete a survey that measures several attributes about their personal lives and jobs. The aim of this project is to use said dataset and provide any analytical insight and a predictive modelling that could help the company avoid a similar situation.

This data set will be split in two Sections: Data Exploration and Predictive Modelling.

## Data Exploration

Initially, the dataset obtained from 'Globex Pharma' did not include which employees left the company. The scope of this initial report is to explore three research questions about Globex Pharma and answer these questions by analysing the dataset given by Globex Pharma. Once the questions are answered, these will be further explored to see if there is a correlation between the results and the recent turnover.
The questions are:
1.	Are employees with a high level of education among the ones with the highest income?
2.	Is there a relationship between working overtime and promotions?
3.	How is the work environment perceived by the employees?

### Question 1 – Are employees with a high level of education among the ones with the highest income?

The purpose of this question is to explore the relationship between Globex Pharma employees’ educational attainment and their salaries. These were the observations gathered from the analytical study (Figure 1):
•	Employees with a higher level of education normally have a higher income.
•	Significant income jump from employees that have graduated from High School and employees with diplomas.
•	Negligible difference between employees with diplomas, bachelor, and master’s degrees in terms of the monthly income median. However, the bachelor’s degree seems to have the highest variability.

![Figure 1 - Level of education v Monthly Income](https://user-images.githubusercontent.com/111329092/220790025-7754355f-94cc-45ca-b413-c3e2968ebce1.png)

*Figure 1 - Level of education v Monthly Income* 

According to a study made by the Australian Government (Department of Education, 2022), educational attainment has an impact on employment and incomes – increasing educational attainment is normally associated with a higher income from wages and salaries.

With this information, we could assume that there is a high possibility that the turnover might be unrelated to employees with a higher level of education being underpaid to peers with a lower level of education.

Nevertheless, there is not enough data to further explore if employees with a certain level of education are being underpaid compared to other industries or companies. 

### Question 2 – Is there a relationship between working overtime and promotions?

The purpose of this question is to explore the relationship between Globex Pharma employees that work overtime and promotions within the company. These were the observations gathered from the analytical study (Figure 2):
•	The variance for employees that perform overtime seems to be smaller than for those that do not.
•	The median for both employees is identical (1 year).
•	The mean years since last promotion for employees that do not perform overtime is higher than those that do. However, the difference is of only 0.06 years.

![Figure 2 - Overtime v Years since last promotion](https://user-images.githubusercontent.com/111329092/220790376-bf83c948-e48d-437b-8188-7b44cbbb2ac5.png)

*Figure 2 - Overtime v Years since last promotion*

Many companies support overtime and even reward with promotions to their employees for it (Patel, 2019). However, studies have confirmed that working overtime can have detrimental effects on health  (Rabenu, 2017) (Nien-Chih Hu, 2016) and could potentially make employees quit (Tilo, 2022).

According to our analysis, Globex Pharma does not appear to have a culture that rewards those who overtime with promotions over those who do not. This would be a positive view for the company regarding career progression.

Nevertheless, further analysis showed that 26.8% of Globex Pharma employees do overtime Figure 3. Globex Pharma might need to address this issue since it could be a reason for the recent turnover.

![Figure 3 - Employees doing Overtime](https://user-images.githubusercontent.com/111329092/220790424-fb0a1749-1209-4f7a-bb95-72dea3b3ccab.png)

*Figure 3 - Employees doing Overtime*

### Question 3 – How is the work environment perceived by the employees?

The purpose of this question is to explore the work environment satisfaction of Globex Pharma employees according to different factors. These were the observations gathered from the analytical study (Figure 4, Figure 5):
•	Employees between 20 – 30 years with low tenure seem discontent with their work environment (low).
•	Employees with high tenure seem to have a higher work environment satisfaction.
•	Most of the employees (70%) have less than 8 years of tenure and a big group (40%) has less than 4 years of tenure.
•	Overall, most of the employees with low work environment satisfaction have less than 5 years of tenure.

![Figure 4 - Work environment satisfaction in terms of age and tenure](https://user-images.githubusercontent.com/111329092/220790486-a89dd49d-5222-4b9a-9235-b967182ebcae.png)

*Figure 4 - Work environment satisfaction in terms of age and tenure*

![Figure 5 - Employees distribution by tenure](https://user-images.githubusercontent.com/111329092/220790494-2173d595-1a3d-4096-a184-c82924e9c2a7.png)

*Figure 5 - Employees distribution by tenure*

According to studies (Raziq & Maulabakhsh, 2015) (Donley, 2021), working conditions are pivotal for an employee job satisfaction and including its efficiency, effectiveness and productivity whilst working. Furthermore, another review (Flowers & Hughes, 1973) claims that the two most relevant factors for someone to stay or leave a company are job satisfaction and work environment.

The fact that employees with low tenure (< 5 years) make up part of most of the company and this group is the one that has the most dissatisfaction towards the work environment, it could potentially explain a key plausible trigger for the recent turnover.

It is recommended for Globex Pharma further investigate this issue, find practical solutions for this situation to prevent further turnover.

## Predictive Modelling

### Model Selection, build and comparison.
The independent variable for this study is the ‘Attrition’ binary categorical variable, meaning it only has two plausible values (‘yes’ and ‘no’), the recommended models are the Decision Tree model and a Logistic Regression model, due to these models being better suited for binary classification.

#### Selecting and validating the relevant predictors
To determine the relevant predictors to the attrition variable we have used the forward stepwise selection (FSS) and the backward stepwise selection (BSS) methods (Further information in Appendix A. Selection Method) and then cross validated using a 10-fold cross validation method to identify any overfitting or underfitting in the model (Further information in Appendix B. Cross-validation).

#### Selection, validation, and modelling results
After running the models through the selection methods and a ten-fold cross validation, we have calculated the area under the curve (measures the efficiency of the model more info in Appendix C. Area Under the Curve (AUC) and Sensitivity) as a technique to compare the different methods. These were the results:

##### Logistic Regression model
-	Cross-validation score for FSS: 0.8330
-	Cross-validation score for BSS: 0.8329
These both had a similar score and the difference in predictor variables was for the FSS to have StockOptionLevel and YearsWithCurrentManager whilst BSS had PerformanceRating and Education (variables obtained are available in detail in Key Predictors section).

In this case, it is recommended to use the logistic regression model with the predictor variables selected from the FSS.  

##### Decision Tree model
-	Cross-validation score for FSS: 0.8327
-	Cross-validation score for BSS: 0.8222

These both had a similar score and the difference in predictor variables was for the FSS to have Department, Education, and StockOptionLevel whilst BSS had TotalWorkingYears, YearsAtCompany, and YearsWithCurrManager (variables obtained are available in detail in Key Predictors section).

Overall, both models had similar AUC scores but the Logistic Regression model was slighter better.

### Statistically Significant Variables and Sensitivity

#### Statistically Significant Variables
Despite the logistic regression and decision tree models had a similar AUC, we had to check if the variables used in the logistic regression model are statistically significant or not.

According to the summary of the logistic regression model, several variables are not statistically significant (>0.01 – further explained in Appendix E. Sensitivty) or at least partially. As an example, the variable ‘MaritalStatus’ is statistically significant if the employee is single, however when divorced or married it is not considered statistically significant.

Therefore, to further optimised the model we have removed the non-significant variables and added new ones to provide a model with statistically significant variables (variables can be inspected in the Key Predictors section) and ran the model using a 10-fold cross validation method. The results were:
•	Cross-validation AUC (Logistic Reg. – with FSS method variables): 0.8330
•	Cross-validation AUC (Logistic Reg. – with only statistically significant variables): 0.8335

In this scenario, not only all the variables are statistically significant, but the AUC score of the model further improved.

#### Sensitivity
For this model, sensitivity measures how correctly the model predicts if an employee is leaving the company (further explain in Appendix E. Sensitivity). The sensitivity results were:
•	Cross-validation Sensitivity (Logistic Reg. - with only statistically significant variables): 0.8089
•	Cross-validation Sensitivity (Decision Tree): 0.7737
•	Cross-validation AUC (Logistic Reg. - with only statistically significant variables): 0.8335
•	Cross-validation AUC (Decision Tree): 0.8176

The logistic regression model has a higher AUC score and sensitivity than the decision tree model, nevertheless they both provide a good sensitivity score.

### Key Predictors
Despite the decision tree (DR) and the logistic regression (LR) models having different AUC and sensitivity scores, they have similar predictor variables (Table 1)

<img width="348" alt="Table 1 - Key Predictor Variables for models" src="https://user-images.githubusercontent.com/111329092/220790563-0ce6f4f4-9983-4143-9deb-3003ce394209.png">

*Table 1 - Key Predictor Variables for models*

Out of the 25 predictor variables available, the LR model is using 15 whilst the DR model is using 19 – which includes all LR predictor variables.

However, one of the key differences between the predictor variables between the models is that the LR model also has some additional + customised variables such as MaritalStatus_Single in which despite the MaritalStatus has a low statistical significance to the model, the ‘Single’ value was significant and therefore a new variable was produced – this is repeated for BusinessTravel and JobRole.

#### Logistic Regression Key Predictor Variables
Looking at the results of the logistic model (Figure 6). In this section we will discuss the key predictor variables for Attrition and how they impact it – assuming all the other predictor variables are held constant.

<img width="283" alt="Figure 6 - Logistic Regression model summary (without non-statistically significant variables)" src="https://user-images.githubusercontent.com/111329092/220790602-5113e0ef-dea7-46e0-b07e-7110c5d7a76a.png">

*Figure 6 - Logistic Regression model summary (without non-statistically significant variables)*

The further away from 0 the bigger the impact the predictor has on attrition. Positive coefficients increases the probability of Attrition whilst negative ones decreases it. These were the key predictor variables for Attrition (in order of relevance):

Variables that Increase Attrition
•	Overtime (Yes) – Coefficient of 1.84.
•	Business Travel (Frequently and Rarely) - Coefficients of 1.83 and 1.10 respectively.
•	Job Role Sales (Sales Representative, Human Resources, Laboratory Technician, and Sales Executive) – Coefficients of 1.74, 1.57, 1.29 and 0.83 respectively.
•	Marital Status Single – Coefficient of 1.25.
•	Years Since Last Promotion – Coefficient of 0.19 
•	Number of Companies Worked – Coefficient of 0.16
•	Distance From Home – Coefficient of 0.04

Variables that Decrease Attrition
•	Work Life Balance – Coefficient of -0.47
•	Job Involvement – Coefficient of -0.45
•	Environment Satisfaction – Coefficient of -0.42
•	Relationship Satisfaction – Coefficient of -0.23
•	Years in current role – Coefficient of -0.16
•	Age – Coefficient of -0.05

#### Decision Tree Key Predictor Variables and Outcomes
Looking at the results of the decision tree model (Figure 7), these were the outcomes:
•	Employees have a 100% chance of leaving the company if:
o	They perform overtime, 
o	Have an income greater than $3,752, 
o	Live more than 13km from the office, 
o	Have a poor work environment satisfaction, and 
o	have worked at more than 5 companies. However, even if they have worked at less than 5 companies, these employees would have 43% chance of leaving the company

•	Employees have an 86% chance of leaving the company if they have: 
o	A poor Job Involvement (< 3 out of 5), 
o	One of the following job roles: 
	Healthcare Representative, 
	Human Resources, Manager, 
	Manufacturing Director, 
	Research Director, 
	Laboratory Technician, 
	Research Scientist, or 
	Sales Executive 
o	A poor life balance ( < 2 out of 5), and
o	An income higher than $1,452 (the company median is $4,837)

•	Employees have a 62% chance of leaving the company if:
o	They do not perform overtime, and 
o	Have a low income ($1,452, company median is $4,837).

•	Employees have 91% chance of leaving the company if:
o	They earn less than $3752 (the company median is $4,837), 
o	Are younger than 34 years, 
o	Are married or single, and
o	Are a Research Scientist, Human Resources, Lab technician or sales representative. Nevertheless, if an employee is not in one of those roles and live less than 11km from the office, they have an 81% chance of leaving the company.

<img width="452" alt="Figure 7 - Decision Tree Diagram" src="https://user-images.githubusercontent.com/111329092/220790673-88443478-bed1-49e0-9336-b902dd96299e.png">

*Figure 7 - Decision Tree Diagram*

### Model results differences
When examining the differences between the models, it can be seen that the logistic regression model provides a better and more accurate prediction than the decision tree model in terms of AUC and sensitivity.

However, the results of the decision tree model are easier to interpret than the logistic model. We do know which predictors from the logistic models have a greater impact on employees’ attrition to the others; however, to calculate by how much would attrition be affected is a complex calculation that would require additional time and resources.

The decision tree on the other hand, provides a result that is easier to interpret and despite not specifying how much is attrition affected by each predictor, it can communicate the likelihood of employees’ attrition according to the compliance of one or several predictors.

For this study, I believe both models provided relevant and important information about the key predictor variables of the ‘Attrition’ variable.

### Recommended Strategies
Now that the key predictor of employees’ attrition have been identifies, we will be giving our plausible solutions and recommendations to prevent any further attrition.

#### Overtime Policies
Several studies have shown that employees that work overtime can develop health related issues (Rabenu, 2017) (Nien-Chih Hu, 2016) and make employees to consider quitting their jobs (Tilo, 2022). Studies have shown that when an overtime policy is established it can decrease overtime by allowing a more controlled approval of overtimes and caps (Campbell, 2019) (Adobe, 2018)

#### Flexible Work Arrangements
Studies have shown that flexible work arrangements (including working from home) can have beneficial effects on employees in regards to work environment satisfaction and even those with long commutes (High distance from home) (Jacobson, 2022) (Adobe, 2018).

#### Leadership Training
Several studies have shown that leadership is the foundation of a positive employee experience at work, this would include opening up transparency and feedback at work (O.C.TANNER, 2019), encourage employee recognition (DeLeon, 2022), and awareness if their team has the right tools and resources  (Adobe, 2018). These skills and others can be developed to employees in leadership positions with training or courses.

#### One-On-One Meetings
It is highly recommended for employees and their supervisors/managers to have regular one on one meetings to discuss the current successes, challenges, goals and ways that the employee could be supported – these should cover well-being check in, review short term and long term goals, career development and request/provide feedback (Timms, 2020).

In these meetings, it is encouraged that when speaking to employees in positions with high business travel (Ex. Sales and Sales Representative) to express how their experience could be improved – As an example, this can be done by providing additional leave days for their travels or other benefits.

Nevertheless, it is highly recommended for the company to obtain further feedback from employees in the positions of Healthcare Representative, Human Resources, Manager, Manufacturing Directors, Research Directors, Laboratory Technician, Research Scientist, Sales Representative and Sales Executives including their respective supervisors/managers – Most of these roles are within the research, sales, directors and human resources departments, it is highly recommended to prioritise these departments.

#### Industry Salary Research
Besides giving the space for employees to discuss their salary expectations during the one-on-one meetings, it would also be beneficial for the company to perform end of year salary research. This can be done by a third part company to determine if current employees’ salaries are competitive within in the industry and role.

## Appendix

### Appendix A. Selection Method
To determine which variables would make the models perform best, we used the forward stepwise selection (FSS) and the backward stepwise selection (BSS) methods.

The FSS consists of the iteration of the model, starting with no independent variables, whilst adding independent variables to the model until the best set of independent variables is found – the best set is measured by the cross validation and area under the curve values. 

The BSS is similar to the stepwise but instead it starts with all of the available independent variables and instead of adding variables each iteration, it removes them.

It is likely that both methods could result with a different set of independent variables, the idea of running both is to then compare the results and determine which set would fit the model best.

### Appendix B. Cross-validation
To prevent any cases of overfitting or underfitting the model, we ran both models through both stepwise selection methods using a 10-fold cross validation. The idea of this is to split the dataset into ten identical groups, train the model using 9 of the groups and 1 as the test/validation group to validate the efficiency of the model. This was repeated 10 times and each time the test/validation group is different.

### Appendix C. Area Under the Curve (AUC)
Models and selection methods were compared using their respective AUC scores (the mean of the 10 folds). AUC measures the probability that the model will be able to correctly predict the independent variable using the given predictors.  Using the AUC is an effective method to compare the performance of two different models.

Results:

Logistic Regression
-	Cross-validation score (AUC) for FSS: 0.8330
-	Cross-validation score (AUC) for BSS: 0.8329

Decision Tree
-	Cross-validation score (AUC) for FSS: 0.8327
-	Cross-validation score (AUC) for BSS: 0.8222

Logistic Regression model with FSS predictors produced the highest AUC score and the Decision Tree model with FSS predictors produced a higher AUC score than BSS.

### Appendix D. Statistically Significant Variables
A statistically significant variable would be the likelihood that the relationship between variables is not explained by chance alone. Meaning that the relationship between a non-statistically significant predictor variable and the dependable variable could potentially be due to random chance.

This is normally expressed as the p-value, normally the p-value is 5%. However, in this report we have been conservative and made the limit to be 1%. Meaning that any predictor variable with more than 1% chance of having a relationship with the dependable variable due to random chance, would be removed from the logistic model.

In this report we compared the model using all of the predictor variables generated by the selection method and compared it against a model using only the statistically significant predictor variables from the selection method. 

Results:

-	Cross-validation AUC (Logistic Reg. – with FSS method variables): 0.8330
-	Cross-validation AUC (Logistic Reg. – with only statistically significant variables): 0.8335

The model with solely statistically significant predictor variables showed a better AUC.

### Appendix E. Sensitivity
To calculate sensitivity, the ‘best’ threshold of the ROC curve was found and with it, its sensitivity. Since the models will be using a 10-fold cross validation method, the sensitivity score for each of the models will be an average of all of their respective folds.
-	Cross-validation Sensitivity (Logistic Reg. - with only statistically significant variables): 0.8089
-	Cross-validation Sensitivity (Decision Tree): 0.7737

The logistic regression model provided a higher sensitivity than the decision tree.

References
Adobe, 2018. Adobe Business. [Online] 
Available at: https://business.adobe.com/blog/basics/6-productivity-tips-that-will-also-reduce-overtime
[Accessed 17 02 2023].

Campbell, S., 2019. https://wheniwork.com/blog/how-to-reduce-overtime. [Online] 
Available at: https://wheniwork.com/blog/how-to-reduce-overtime
[Accessed 17 02 2023].

DeLeon, H., 2022. USF Corporate Training and Professional Education Blog. [Online] 
Available at: https://corporatetraining.usf.edu/blog/how-to-increase-employee-job-satisfaction
[Accessed 17 02 2023].

Department of Education, 2022. Australian Government - Department of Education. [Online] 
Available at: https://www.education.gov.au/integrated-data-research/benefits-educational-attainment/income
[Accessed 23 01 2023].

Donley, J., 2021. The Impact of Work Environment on Job Satisfaction. National Library of Medicine, 19(6), pp. 585-589.
Flowers, V. S. & Hughes, C. L., 1973. Harvard Business Review - Why Employees Stay. [Online] 
Available at: https://hbr.org/1973/07/why-employees-stay
[Accessed 24 01 2023].

Flowers, V. S. & Hughes, C. L., 1973. Harvard Business Review - Why Employees Stay. [Online] 
Available at: https://hbr.org/1973/07/why-employees-stay
[Accessed 24 01 2023].

Jacobson, A., 2022. BuiltIn. [Online] 
Available at: https://builtin.com/people-management/work-life-balance
[Accessed 17 02 2023].

Nien-Chih Hu, J.-D. C. a. T.-J. C., 2016. The Associations Between Long Working Hours, Physical Inactivity, and Burnout. Journal of Occupational and Environmental Medicine, 58(5), pp. 514-518.

O.C.TANNER, 2019. Global Culture Report, s.l.: O.C. Tanner.

Patel, M., 2019. LinkedIn. [Online] 
Available at: https://www.linkedin.com/pulse/staying-overtime-office-might-lead-promotion-ugly-truth-meet-patel/
[Accessed 24 01 2023].

Rabenu, E., 2017. Understanding the Relationship between Overtime and Burnout. International Studies of Management & Organization, 47(4), pp. 324-335.

Tilo, D., 2022. https://www.hcamag.com/au/specialisation/corporate-wellness/the-rise-of-quiet-quitting-how-overtime-led-to-an-hr-crisis/417883. [Online] 
Available at: https://www.hcamag.com/au/specialisation/corporate-wellness/the-rise-of-quiet-quitting-how-overtime-led-to-an-hr-crisis/417883
[Accessed 24 01 2023].

Timms, M., 2020. Linkedin. [Online] 
Available at: https://www.linkedin.com/pulse/why-every-manager-should-hold-11-meetings-how-do-them-michael-timms/
[Accessed 16 02 2023].

