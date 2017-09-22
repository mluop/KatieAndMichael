# Loan Default Prediction
Memo to manager --

Here at Lenders "R" Us, we pride ourselves in giving our loan agents the autonomy to approve and reject loan applications using their own judgement. This fosters a culture of empowerment and trust, giving us a strong competitive advantage over other lending institutions. However, as recent events in our San Diego office have revealed, our new hires often don't have the intuition or experience to make optimal approval decisions. Last quarter's report shows our San Diego new hires have approved eventually-defaulting loans at a significantly higher rate than our veteran employees. This is cutting significantly into our bottom-line, and in order to stay solvent, we need to help our new hires learn what factors predict loan defaults.

We propose a data-driven project to model the factors that contribute to the risk of a loan defaulting. We will create a system which can predict the likelihood that a given loan will default, and predict the loss incurred from the default, based on information in the loan application. In essence, we hope to answer the question: **What factors predict which loans will default and the severity of the defaults?**

The dataset we will use for this project was found on Kaggle.com. The dataset contains all loans issued by Lending Club for an eight year span. This dataset contains information on 890k loans during this period. For each loan, there are 75 variables, including most importantly whether or not the loan defaulted. Possibly crucial predictive variables include:
- Lendee employment title
- Lendee home ownership
- Lendee income
- Lendee credit score
- Loan amount
- Loan term
- Loan interest rate

We believe there will be strong predictive value in these variables, all of which we have when considering a loan application. Intuitively, there should be some relationship between this information about the lendee and whether the loan defaults. We intend to tease out these relationships by building a predictive model based on the proposed dataset. Because the dataset is so large and fits our use-case so well, we believe we are likely to succeed in discovering what factors predict which loans will default and the severity of the defaults. 
