# Important considerations
Some participants will have data from all questionnaires, while others will only have data from one questionnaire. It is crucial to be aware of this when interpreting missing values. The data set “SV_INFO” includes a unique identifier for each woman called ‘M_ID_XX’. This variable can be used to identify women who participate with more than one pregnancy and hence identify siblings.


We urge you to consider how the specific question may be interpreted by the respondent. If a respondent has answered “No” to a question, he/she may not have answered the follow-up questions and the corresponding variable(s) will have a missing value. Some respondents may also have answered inconsistently, e.g. answered “No” when asked “Have you ever smoked?” and answered “Daily” when asked “Do you smoke now?”. Therefore, it is important to check for inconsistency.

For twins and triplets, the mother fills out one questionnaire for each child after birth (i.e. questionnaire 6 months, 18 months, 3 years, 5 years, 7 years and 8 years). The mothers are told to fill in the section “About yourself” for the first child only. MoBa have not duplicated this information to the other sibling(s). These variables are usually missing for one of the twins or two of the triplets.


### A note on missing data

Not everyone participates in all questionnaires.

Missing values may therefore mean:
- the question was not asked  
- the questionnaire version did not include it  
- the participant did not respond  


### Things worth checking

- skip patterns (missing values after “No” answers)  
- inconsistent answers  
- version differences  

Example:  
Someone can answer “No” to smoking history but still report current smoking.


## Final tips

Before starting an analysis, it is usually worth:

- checking which questionnaire versions you are using  
- verifying coding for key variables  
- looking at missingness patterns  
- making sure merges behave as expected  



#### If you have questions or comments about the data files or suspect that something can be incorrect in labels or other documentation, please contact us at MorBarnData@fhi.no.
