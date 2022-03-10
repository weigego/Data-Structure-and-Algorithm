# Decision Tree
Two types of popular trees are:
- classification trees: Tree models where the target variable takes a discrete set of values. leaves represent class labels and branches represent conjunctions of features that lead to those class labels. 
- regression trees: Tree models where the target variable takes continuous values (typically real numbers)


# Random Forest
Random forests or random decision forests is an **ensembl learninge** method for classification, regression by constructing a multitude of decision trees at training time.

For classification tasks, the output of the random forest is the class selected by most trees. For regression tasks, the output is the mean or average prediction of the individual trees. 

Overfitting to training set won't happen in DT. Random forests generally outperform decision trees, but their accuracy is lower than gradient boosted trees.

Random forests are "blackbox" models, as they generate reasonable predictions across a wide range of data while requiring little configuration.
