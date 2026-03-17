# Logistic Regression to Predict Recidivism

This is a Repository containing the files related to the project **"Logistic Regression to predict Recisdivism"**. The approach used in this project is Logistic Regression on the County Level Education, Poverty and Unemployment to predict recidivism.

---

## Summary of the Approach

This approach utilized the U.S. Department of Agriculture (USDA) data on educational attainment and unemployment, and U.S. Census Bureau Small Area Income and Poverty Estimates (SAIPE) data, along with a curated large dataset of criminal cases compiled from Wisconsin circuit courts.

County level data on education, Poverty and Unemployment were merged with the individual level Wisconsin circuit courts data using FIPS code and an education index was added to combine 4 education related variables.

Logistic regression was the method chosen to analyze the importance of education, poverty, and Unemployment on recidivism due to its interpretability and because the response 'is_recid_new' is binary. The response variable reflects whether an individual recidivated within a two-year follow-up period.

A broad selection of demographic, prior criminal history and county level socio-economic variables were evaluated. A LASSO regularization model was employed to select the strongest predictors, thus helping with dimensionality reduction.

A basic model containing features chosen by LASSO was built. Previous studies have focused on individual level characteristics of offenders. However, there are not many studies that describe the effects of county or neighborhood characteristics on recidivism. To address this gap, individual level predictors such as history of crime, Jail time, case duration, Race, and type of case and county level socio-economic predictors such as unemployment rate, education index (an index that combines county education data at the high school and college level), percentage of individuals living below the poverty level and median household income were included in the basic model.

To further analyze the dependencies on the socio-economic predictors, an interaction model was built. A final model added the three-way interaction term (education × unemployment × poverty) that allow us to examine whether the effect of education on recidivism changes at different levels of unemployment or poverty, reflecting compounding structural disadvantage.

All models were trained on a sample size of data that included 266677 circuit court cases from Wisconsin.
