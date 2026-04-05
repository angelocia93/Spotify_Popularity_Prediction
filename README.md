Spotify Popularity Prediction 
Project Overview

The goal of this project is to predict the popularity of Spotify tracks using a set of audio features and categorical attributes describing each song. Spotify provides several numerical indicators that capture different musical characteristics of a track, such as rhythm, energy, mood, and structure.

The dataset includes features such as danceability, energy, loudness, acousticness, instrumentalness, valence, tempo, key, mode, time signature, and genre. These variables aim to describe different musical dimensions. For example, danceability measures how suitable a track is for dancing, while energy reflects its intensity and loudness. Other variables, such as valence, capture the emotional tone of the music.

The project follows a standard data science workflow, starting with an initial understanding of the data, followed by exploratory analysis, data preparation, model training, and evaluation.

Exploratory Data Analysis

The exploratory analysis focused on understanding how different musical attributes relate to track popularity.

In particular, statistical tests were used to evaluate the relationship between categorical variables and the popularity score. The results show that genre has the strongest association with popularity, while structural musical features such as key, mode, and time signature have a much smaller effect.

This finding suggests that stylistic and cultural aspects of music may influence popularity more than purely technical musical characteristics.

Additionally, the relationships between categorical variables were analyzed using measures of association. The results revealed mostly weak to moderate relationships, indicating that these musical features capture different aspects of a track and provide complementary information.

Data Preparation

Before training the models, several preprocessing steps were applied to the dataset.

Non-informative variables such as track name and artist name were removed because they do not provide useful predictive information and could introduce noise into the model. The categorical variable genre was encoded using one-hot encoding, allowing it to be used by machine learning algorithms.

The dataset was then split into training and test sets to evaluate model performance on unseen data. Feature selection was also guided by the insights obtained during the exploratory analysis.

To evaluate the predictive performance, two different models were trained and compared.

Models
Random Forest Regressor

The first model used in this project is a Random Forest Regressor, which is a tree-based ensemble method capable of capturing complex and non-linear relationships between variables.

The model was optimized using RandomizedSearchCV, which performs hyperparameter tuning through cross-validation by sampling different combinations of parameters. The tuning process focused on parameters such as the number of trees, tree depth, minimum number of samples required for splitting nodes, and the number of features considered at each split.

The best set of hyperparameters found was:

n_estimators: 250
min_samples_split: 2
min_samples_leaf: 8
max_features: 0.5
max_depth: None

The resulting performance of the Random Forest model was:

Metric	Train	Test
RMSE	7.11	9.26
MAE	5.26	7.02
R²	0.8468	0.7425

On the test set, the model is able to explain approximately 74% of the variance in track popularity. However, the difference between training and test performance suggests the presence of moderate overfitting, which is common in flexible models such as Random Forests.

Linear Regression (Baseline Model)

To better understand whether the additional complexity of the Random Forest model provides a meaningful advantage, a Linear Regression model was also trained as a baseline.

This simpler model assumes a linear relationship between the audio features and track popularity. The performance of the linear regression model was:

Metric	Train	Test
RMSE	9.59	9.61
MAE	7.25	7.27
R²	0.7218	0.7228
Model Comparison

Comparing the two models shows that the Random Forest model performs better than the linear regression baseline, although the improvement is moderate.

The Random Forest achieves a lower prediction error and a slightly higher R² score. This indicates that non-linear models are better able to capture the complex relationships between musical features and popularity.

However, the relatively small improvement also suggests that audio features alone cannot fully explain why a song becomes popular.

Key Insights

Several insights emerge from the analysis:

Genre plays a significant role in determining track popularity.
Musical attributes such as energy, danceability, and valence contribute to predicting popularity.
The relationship between audio features and popularity is not purely linear.
Tree-based models like Random Forest are better suited for this type of data.

At the same time, the results indicate that many important factors influencing popularity are not captured in the dataset.

Conclusion

This project demonstrates how machine learning techniques can be applied to predict the popularity of songs based on their audio characteristics.

The results show that Random Forest models outperform simpler linear approaches, although the improvement is relatively modest. This highlights an important aspect of music popularity: while audio features provide useful signals, they are only part of the story.

Popularity is also influenced by external factors such as artist reputation, marketing strategies, playlist placements, and cultural trends, which are not included in the dataset.

Future improvements to this project could include incorporating artist-level information, experimenting with more advanced models such as Gradient Boosting or XGBoost, and applying additional feature engineering techniques to better capture musical characteristics.
