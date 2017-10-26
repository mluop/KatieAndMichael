> In the report, you should describe your data set in greater detail. Describe how you plan to avoid over (and under-)fitting, and how you will test the effectiveness of the models you develop. Include a few histograms or other descriptive statistics about the data. How many features and examples are present? How much data is missing or corrupted? How can you tell? You should also run a few preliminary analyses on the data, including perhaps some regressions or other supervised models, describing how you chose which features (and transformations) to use. Finally, explain what remains to be done, and how you plan to develop the project over the rest of the semester.

# Loan Default Prediction
Report to manager --

Here at Lendors "R" Us we have seen great success over the years, thanks to the autonomy and empowerment we provide to our loan agents. However, as recent events in our San Diego office have revealed, our new hires often don't have the intuition or experience to make optimal loan approval decisions. As we proposed in our last memo, **we are investigating and modeling what factors in loan applications best predict loan defaults**.

In this report, we provide a status update on our work. This includes:
1. Exploring, cleaning, and transforming our dataset.
2. Preliminary investigations into our dataset.
3. Plans for future development.

## Exploring, Cleaning, and Transforming our Dataset
Our dataset consists of features for all loans issued by Lending Club for an eight year span. This dataset contains information on **890k loans** during this period. For each loan, there are **75 variables**, including most importantly the current status of the loan (e.g. default, fully payed, etc.).

### Missing Data

A major roadblock for using this dataset is that many of the values are missing. The majority (40) of our features have at least some values missing. In fact, for some features the entries for almost *all* of the loans are missing. In the following graph, for each of the 75 features, we plot the proportion of loans that are missing data.

![](missing_data.jpg "Missing Data for each Feature")

From this graph we learn that, even though 40 features are missing data, only about 20 features seems to be missing data for a significant proportion of the loans. This is a promising result, as many features may still be usable, despite missing some data. This could be accomplished by keeping the features for which, say, 80% of the loans have data. The remaining 20% of the loans may simply receive the mean, median, or zero value -- standard imputation techniques for dealing with missing data.

### Dirty Labels

The next major hurdle for using this dataset is that the column we intend to use as a label -- `loan_status` -- is not a simple indicator variable for defaulted or not. Instead, the loan status can take on extraneous values (such as "In Grace Period") which do not necessarily indicate whether the loan will default. Below we graph the proportion of loans with each raw loan status.

![](raw_piechart.jpg "Distribution of Raw Loan Statuses")

From this chart it becomes immediately clear that approximately 0% of the loans have the label "Default" -- a huge concern for us! If we do not have any examples of defaulting loans, it would be massively difficult to predict which loans *would* default. Thankfully, once alerted to this issue, we learned that "Charged Off" is a stage strictly after "Default"; thus we can consolidate the two label values into a unified "Default" value.

Additionally, we note that the majority of loans in the dataset have a loan status of "Current" meaning that they are still in the process of being paid off. This label, allowing with the other "Current"-esque labels, do not tell us definitively whether a given loan results in a default. Thus in our preliminary analyses we drop the loans which have these intermediate statuses.

Altogether, our cleaned labels are "YES" (i.e. "Default" or "Charged Off") and "No" (i.e. "Fully Paid). This cleaned dataset still has 250k example loans, which is sufficiently large to build our models with. Even better, we note that the class-imbalance of default-to-nondefault loans is just 18:82. This is promising because we have plenty of examples from each class of loans, and we can effectively train to predict loan defaults.

![](final_piechart.jpg "Distribution of Cleaned Loan Statuses")

## Preliminary Investigations into our Dataset

## Plans for Future Development
