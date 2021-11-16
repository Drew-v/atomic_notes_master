Hyperparameter tuning can increase model performance, but also decrease it if overturned to a specific test set. This is mitigated by using a holdout set, or a [[Machine learning - validation set | validation set]]. The hyperparameter tuning adjustments are measured against performance on the validation set instead of a particular test set. 

Select model with the best validation performance, then train this best model on the full training data set and test against the unseen test set to get a generalization error estimate.

This might not give expected performance if validation sets are too small. But if not enough data is used on training set, model performance comparisons may not be equivalent, as each has a small picture of the whole dataset. The solution? **[[cross-validation]]**