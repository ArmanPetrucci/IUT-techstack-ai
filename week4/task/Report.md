## Using HOG features to train ML models that recognize if an image contains a dog or a cat

1. I implemented function 'extract_hog_features' which uses skimage built-in method for calculating HOG
   and stored features. also stored visualizations if visualization=True
2. I then implemented 'split_and_save_dataset' which uses sklearn train_test_split to split the data and saved images based on their labels in the given directories
3. because I wanted to keep the indices of train and test data I had to add an index column to my data.
4. then I added labels column and used train_test_split and returned features (X), indices and target values (y)
5. decided to go with Random Forest instead of Decision Tree because it is a better model overall
6. then used GridSearchCV from sklearn for hyper parameter tuning
7. after finding them I commented the hyper parameter tuning because it takes more time to complete but I used the best parameters found to train my current model
8. at last I implemented function 'evaluate_model' which first predicts labels and then uses sklearn's accuracy_score to find the accuracy
9. I did the same thing but this time used SVM but hyper parameter tuning took much longer to complete so I didn't include that part
10. I only used the best parameters that was found and trained an SVC model in the last cell

## conclusion

1. when I used decision trees the accuracy was less than 92 percent almost all the time
2. random forest had the best accuracy out if the models I found
3. SVC also performed decently well
4. I also tried XGboost but maybe because the dataset was not that big it didn't do any better than random forest and it did as good as random forest
