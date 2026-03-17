# Food Deserts and Swamps - DATASCI 112 Final Project
## File Documentation
### Preliminary Work
`dataset_genearation (1).ipynb`: Our data collection and cleaning. We begin with three relatively large datasets, select relevant rows (related to food accessibility, the number of stores in a county and health outcomes), and merge on county `fips` values.

`prelim_analysis.ipynb`: First analysis on individual `x` and `y` values. We analyzed relationships between each independent and dependent 
variable, hoping to find some initial correlation to guide future investigation. Initially, we weren't quite sure what to investigate, so we observed relationships between health outcomes and potential "independent" variables. We know that `income` is the most strongly related to health outcomes; upon confirming this using a linear regression and its $R^2$ value, we decide to use it as a baseline.

### Figures
`chloropleth_generation (1).ipynb`: We create chloropleths based on `Average Household Income`, `RFEI`, `Cumulative Disease Burden`, and `SNAP Stores`. An important note is that we flipped the color scales in accordance with the relative socioeconomic status that each value represents; for instance, counties with a higher average income tend to correlate with less SNAP stores and a lower disease burden, so those color schemes are opposite. We also put `income` in thousands for better readability, we included these on our final poster.

`correlation_heatmap.ipynb`: Initially, we wanted to observe the relationships betwee variables. The lack of correlation between `RFEI` and health outcomes definitely stood out to us; additionally, we noticed strong correlation between `SNAP Stores` and all health outcomes.

`figure_creation.ipynb`: This is where we created the machine learning-based figures on our poster. The one that we did not present was the $R^2$ comparison; although it clearly shows that other models were stronger in this area than `RFEI`, this only displays a lack of *fit* for the model, not accuracy. We felt that `CV_RMSE` (RMSE through cross validation) better highlights our findings. The final two figures are comparisons between `SNAP` and non-`SNAP` models, which will be further elaborated on in our `model_data` section.

### Analysis
`model_creation_analysis.ipynb`: We fit nearly every combination of variables possible in linear regressions, then saved the model results. We specifically kept track of model parameters, $R^2$, and `CV_RMSE`. Additionally, we were concerned about multicollinearity, so we did test some principle component analysis for `store` and `access`-related variables. However, the `raw` variables by themselves tended to perform better. We also ran some `SNAP`-specific regressions, which will be further elaborated on in our `model_data` section.

### Model Data
`full_model_results.csv`: The results of the model we ran in `model_creation_analysis.ipynb`.

`only_snap.csv`: We ran linear regressions using `SNAP` and `RFEI` as the only independent variables and compared the relative `CV_RMSE` values (in additon to the $R^2$'s, though those weren't plotted. We found that `SNAP` tended to outperform `RFEI` for all outcomes.

`store_snap.csv`: Because `RFEI` is a metric based on all the store variables except for `SNAP`, we wanted to see if `SNAP` was causing the `stores_only` regression to perform so well. We ran two regressions, one with all the `store` variables, and one with all of them except for `SNAP`. We observed that the regression with `SNAP` performed better for the outcomes of `diabetes` and `cancer`; however, it had a slightly larger error value for `obesity`. We weren't quite sure what to do with this metric, since the difference between models seems to be almost negligibly small; additionally, we are aware that `obesity` is the strongest health outcome correlated with all variables. We cautiously chose to conclude that both models performed about the same for this category, though this could serve as a topic of future investigation.

## Conclusions and Future Actions
Overall, we came to the conclusion that access-related variables may be more strongly correlated with health outcomes than the metrics used to calculate `RFEI`. This means that the food environment-centered scientific sphere might benefit not from removing `RFEI` entirely, but also including access-based metrics in their analyses. Additionally, local governments might want to improve food access for citizens, instead of building more outlets, if they wish to best address food-related health issues.

Our final poster can be accessed [here](https://docs.google.com/presentation/d/1Ybx248KbEbiH9A1uNEYZSV2dav6PkV4nBK3WsO4P0zA/edit?usp=sharing).
