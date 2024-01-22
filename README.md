# Summary
This is an Open-ended project for PSTAT class.

This project is written in R. See *project.Rmd* for the full report as R Markdown file. It is also knitted as *project.html*.

## Research Purpose
By studying the H-1B applications throughout passing years, I want to provide a prediction on the case stautus of H-1B visas, which also revive possible preferences or discriminations among the immigrants.

## An Overview of Dataset
The dataset includes the information of H1B visa applications in from 2011 to 2016. The original dataset comes from [kaggle](https://www.kaggle.com/datasets/nsharan/h-1b-visa). It contains about 3 million observations, among which 87% of the record are certified. Majority of the predictors are categorical variables except for *Prevailing Wage*, which is numeric.

## Research Method
There are four status of visa: certified, certified-withdrawn, withdrawn, denied. Given the basic information about a H1B visa application, I want to predict its chance to be **certified**. Six predictors are used in this project: employer name, job title, full-time or part-time, prevailing wage, year, work site. To address this classification question, four models are fitted, which are KNN, logistic regression, elastic net, and random forest.

## Result
The four models are fitted and tunned. Although all four model has a very similar roc_auc of around 0.61, random forest does a slightly better prediction on 0.6127. The best random forest is fitted to the entire training set and has an outcome roc_auc = 0.7178 that is higher than its performance during cross validation.

## Discussion and Troubleshooting
The overall performance of all selected four model are not ideal, which may caused by following issues:
1. Insufficient Predictors
2. Unclear Boundary Between Case Status (Certified and Certified-Withdrawn)
3. Factual or political reason
The second guess was addressed and verified by the same dataset. Certified and Certified-Withdrawn are group together, and Withdrawn is completely dropped out. Denied is kept unchanged. In general, the updated data set that has 2 levels has a better performance than the original data with 4 levels. But its preformance on testing dataset is still poor. Therefore, having multiple levels on outcome variable is not the main reason that cause the model to preform poorly.

## Conclusion
Random forest model wins with a narrow margin. However, its performance on the testing set shows that it does not help much on determining the H-1B visa’s case status. The problems may involves with factual issues that is outside of the data. In order to improve model, a more detailed information about the applicants, such as gender and ethnicity, are require to build a better model.
