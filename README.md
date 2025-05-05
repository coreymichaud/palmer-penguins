# Predicting Penguin Species with Palmer Penguins

This is a notebook that I am using to try out different machine learning models and techniques. The data, Palmer Penguins, is very simple and small. This makes it easy to try things out fast.

## About the Data

This notebook uses the [Palmer Penguins Dataset](http://https://allisonhorst.github.io/palmerpenguins/). The data was collected and made available by Dr. Kristen Gorman and the Palmer Station, Antarctica LTER, a member of the Long Term Ecological Research Network. The dataset contains 3 penguin species.

## Goal

The goal is to predict the penguin species. In the future, I might try doing other things with the data (like maybe predicting the body mass).

## Thought Process

### Removing Missing Data

Some rows had missing data, and instead of trying to impute them to get mid results, I opted for dropping those rows entirely. There were only 11 rows with missing data, accounting for about 3.2% of the total data.

### Multicollinearity

When I checked for multicollinearity, I saw that flipper_length_mm and body_mass_g both had a high correlation of 0.87, which was the only correlation above 0.7. As a result, I decided to drop flipper_length_mm.

### Feature Selection

Besides getting rid of flipper_length_mm, the only other column I got rid of was year. This was because when I checked the percentage per species per year, they each had roughly the same percentage per species, meaning they're equally distributed, and all 3 years were the same. As a result, year wouldn't be that important in classifying species.

### One-Hot & Label Encoding + Scaling

To get the features to be "machine ready", I scaled the numerical features and did one-hot encoding to the categorical features, with the first column of each being dropped to prevent multicollinearity. I also applied label encoding to the target feature, species, because it would be interpretable for the model to predict.

### Cross-Validation

I only did one instance of stratified 5-fold cross validation, which was used for logistic regression, because I wanted to see how well my model was *actually* performing after I had already gotten all my results. Getting perfect accuract, f1, recall, etc is very good, so I wanted to see if it was just a perfect train/test split, and the cv score showed it was. It still had very high accuracy, 99.4%, but it showed that my model isn't *as* good as I thought it was.

### Metrics

My goal was to classify the penguin species, so I used classification metrics. I went with the classic accuracy, precision, recall, F1, and AUC. I used a range of metrics just to see how well each model was performing for certain conditions, but really all I needed was accuracy and F1.

## What I Learned

I learned that there are different weights you can use for the f1 score depending on class imbalances in the data.

## Future Endeavors

I would like to try out other ML models with the data. This dataset is very small and easy to work with, so it's nice to be able to quickly implement something and have it work.

# Kaggle!

Check out this notebook on [Kaggle](https://www.kaggle.com/code/coreymichaud/palmer-penguins).
