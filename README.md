# econ3916-lab15-bias-variance
# The Bias-Variance Tradeoff: Choosing How Flexible a Model Should Be

## Objective

I wanted to see how changing the degree of a polynomial affects how well it predicts new data.

## Methodology

- I used a simulation with a known true curve to estimate bias squared and variance from 200 fresh samples at each of six polynomial degrees.
- I fit polynomials of degrees 1 through 15 and compared their training error with their error on 2,000 new points.
- I used 5-fold cross-validation to choose a degree and looked at how much the errors varied across folds.
- I used nested cross-validation to estimate prediction error on folds that were kept separate from the degree selection.
- I wrote a function called `kfold_mse()` to average the test errors across folds for a given degree and number of folds, then used it to compare degrees 4 and 5 with 10 folds.

## Key Findings

- I found that variance increased from 0.0180 at degree 5 to 0.0994 at degree 15. Training error kept falling as I increased the degree, but held-out error was lowest at degree 5.
- With 5-fold cross-validation, I picked degree 4 because it had the lowest mean squared error (MSE) at 0.1401. Degrees 4 and 5 also had the most consistent errors across folds.
- My nested cross-validation estimate was 0.2070. It was higher than the lowest 5-fold CV error, which makes sense because I used the 5-fold scores to pick the degree in the first place.
- With 10-fold cross-validation, I got an MSE of 0.1409 for degree 4 and 0.1457 for degree 5, so degree 4 still had the lower error.
