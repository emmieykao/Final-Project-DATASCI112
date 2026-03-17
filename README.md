# Food Deserts and Swamps - DATASCI 112 Final Project
## File Documentation
### Preliminary Work
`dataset_genearation (1).ipynb`: Our data collection and cleaning. We begin with three relatively large datasets, select relevant rows (related to food accessibility, the number of stores in a county and health outcomes), and merge on county `fips` values.

`prelim_analysis.ipynb`: First analysis on individual `x` and `y` values. We analyzed relationships between each independent and dependent 
variable, hoping to find some initial correlation to guide future investigation. Initially, we weren't quite sure what to investigate, so we observed relationships between health outcomes and potential "independent" variables. We know that `income` is the most strongly related to health outcomes; upon confirming this using a linear regression and its $R^2$ value, we decide to use it as a baseline.
