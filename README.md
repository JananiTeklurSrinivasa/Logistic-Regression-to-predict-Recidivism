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

---

## Results

This analysis evaluated how individual-level criminal justice variables and county-level socioeconomic conditions jointly influence two-year recidivism outcomes in Wisconsin. The final dataset consisting of 266,677 criminal cases from Wisconsin (restricted to years 2008–2012) was trained on three different models, namely a Basic model consisting of predictors selected by LASSO, an interaction model consisting of a term that combines education index, Poverty rate and Unemployment rate and a reduced interaction model with a minimal number of predictors compared to the interaction model.

There were several predictors that were statistically significant at the 0.05 level. As the sample size is large, the inflated p-value issue was addressed by using the sub-sampling approach using a 20\% and 30\% subset of the training data.The basic model was re-estimated across these subsamples and some variables edu\_index, case\_Type, unemployment and poverty sometimes showed lower statistical significance. Other variables seem to consistently show lower p-values. This could be due to the fact that these variables are correlated with median household income and Urban Influence codes. Although the VIF value suggests the absence of multicollinearity in the basic model, the EDA suggested medium to strong correlations between Unemployment and poverty (0.41), Education and Unemployment (-0.47). Thus, two interaction models were built to account for the compounding effects with some of these variables removed and combining the socioeconomic variables as an interaction term.

The reduced interaction model demonstrated the strongest predictive performance (AUC = 0.687, Accuracy = 0.659), outperforming both the baseline model without interactions (AUC = 0.672) and the full interaction model (AUC = 0.672). The Sensitivity and Specificity of the reduced model were 0.334 and 0.869 respectively.

Although individual level variables have a stronger contribution to change in odds of recidivism, there was a small but significant contribution by socioeconomic variables towards recidivism after inclusion of the interaction terms. Although the primary goal of the analysis is to understand the effects of socioeconomic factors and not maximize predictive power, model performance metrics indicate that incorporating interaction effects between unemployment, poverty, and educational attainment not only provides deeper insight into contextual contributors to recidivism, but also slightly improves predictive accuracy. 
