# App Rating Prediction

## Overview

This project is designed to predict the rating of apps in the Google Play Store using various features associated with each app. The goal is to build a model that can help identify which apps are likely to receive high ratings based on other characteristics, such as reviews, size, price, and category. The project involves data cleaning, exploratory data analysis (EDA), feature engineering, and model building using linear regression.

## Problem Statement

The Google Play Store team aims to launch a new feature that boosts the visibility of apps with high potential, based on their ratings. These apps will be recommended more frequently in sections like "Similar apps," "You might also like," and "New and updated games," as well as appear higher in search results. This project focuses on predicting the rating of apps to help identify which apps should be promoted.

### Dataset

The dataset used is a CSV file containing the following fields:

- **App**: Application name
- **Category**: Category the app belongs to
- **Rating**: Overall user rating of the app
- **Reviews**: Number of reviews for the app
- **Size**: Size of the app
- **Installs**: Number of downloads/installs
- **Type**: Paid or Free
- **Price**: Price of the app
- **Content Rating**: Age group the app is targeted at (e.g., Children, Adult)
- **Genres**: Multiple genres that the app belongs to
- **Last Updated**: Date of last update on the Play Store
- **Current Ver**: Current version of the app
- **Android Ver**: Minimum Android version required

## Tasks Performed

### 1. Data Preprocessing

- **Loading the Data**: The dataset is loaded using Pandas for further analysis.
- **Handling Missing Values**: Null values are checked for each column and records with missing data are dropped.
- **Data Type Corrections**: Several fields are corrected for data type inconsistencies:
  - **Size**: Converted from string to numeric, considering units (KB or MB).
  - **Reviews**: Converted from string to numeric.
  - **Installs**: Converted from string to integer, handling special characters like commas and plus signs.
  - **Price**: Cleaned up by removing the dollar sign and converting to numeric.

### 2. Sanity Checks

- **Rating Range**: Ensured that ratings are within the allowed range of 1 to 5.
- **Reviews vs. Installs**: Verified that reviews are not greater than installs and removed any such records.
- **Free Apps**: Ensured that the price of free apps is not greater than 0.

### 3. Exploratory Data Analysis (EDA)

- **Univariate Analysis**:
  - **Boxplot for Price**: Identified outliers for app prices.
  - **Boxplot for Reviews**: Checked for apps with excessive reviews.
  - **Histogram for Rating and Size**: Analyzed the distribution of ratings and app sizes.
  
- **Outlier Treatment**:
  - **Price**: Apps with unusually high prices (e.g., > $200) were removed.
  - **Reviews**: Removed apps with over 2 million reviews, which are considered outliers.
  - **Installs**: Percentiles were computed to identify and remove apps with excessive installs.

### 4. Bivariate Analysis

- **Scatter Plots and Box Plots**:
  - **Rating vs. Price**: Analyzed the relationship between rating and price.
  - **Rating vs. Size**: Checked whether heavier apps tend to have better ratings.
  - **Rating vs. Reviews**: Investigated whether more reviews correlate with better ratings.
  - **Rating vs. Content Rating and Category**: Analyzed if certain content types or categories result in better ratings.

### 5. Data Preprocessing for Modeling

- Applied log transformation to the **Reviews** and **Installs** fields to reduce skewness.
- Dropped unnecessary columns: App, Last Updated, Current Ver, and Android Ver.
- Created dummy variables for categorical features like **Category**, **Genres**, and **Content Rating** to enable model training.

### 6. Model Building

- **Train-Test Split**: The dataset was split into training and test sets (70-30 split).
- **Model**: A linear regression model was built to predict the app ratings based on the prepared features.
- **Evaluation**: The model's performance was evaluated using the R² score on the training set and predictions on the test set.

## Results

- **R² Score**: The linear regression model achieved a good fit, with the R² score indicating the percentage of variance explained by the model on both the training and test datasets.

## Conclusion

This project successfully demonstrated how app features such as price, size, reviews, and category can be leveraged to predict app ratings on the Google Play Store. The model can help identify promising apps that could benefit from higher visibility, and further improvements can be made by exploring more advanced techniques or additional features.
