# What Do Consumers Value in a Used Car?
In the given dataset and the question asked, "What do consumers value in a used car?" can be reinterpreted as "What asking price should a used car dealer set for the cars on their lot?"

This interpretation makes more sense from a dealer’s perspective. A bigger question for a dealer would be to determine two key price points:

The purchase price – How much should I pay for a car at an auction?
The asking price – What price should I set when selling the car?
Since the dataset contains only one price column, and it is not explicitly defined as either the purchase price or the asking price, I will focus on answering the latter question.

Please find the code here: https://github.com/MRiDeb/Vehicles/blob/main/prompt_II.ipynb


Your text conveys the steps well but has multiple spelling and grammar issues. Here's a corrected version with improved readability and accuracy:

## According to the CRISP-DM process, the first step is to understand the business.

Business Understanding:

From the data overview, it is clear that the business deals with purchasing used cars and needs to determine the asking price for selling them.

Data Understanding:

By examining a few rows and the dataset information, we see that the dataset consists of over 400,000 records from various car manufacturers, including different models, their condition, year of manufacture, and car specifications such as color, engine type, and location of the car. I assume that this location represents where the car is currently situated for sale. The data also contains two identifier columns.

Exploratory Data Analysis:
![image](https://github.com/user-attachments/assets/d0c6f39a-b0d1-42d5-a778-2d63312c2064)

1. Create charts for numerical columns.
2. Check how many unique values exist in each categorical column.
3. Since the price data is skewed to one side, we will take log values of price to predict. Taking the logarithm (log) of price data that is skewed to one side is a common practice to normalize the distribution and improve the accuracy of predictions in a model
![image](https://github.com/user-attachments/assets/9ac683f3-50c0-4184-88d7-3a6e6cbae401)

Data Preparation:

To build a price prediction model, the dataset needs to be cleaned, as it contains many null values, unwanted columns, and incorrect data types. The following steps will be performed to clean the data:

1. Remove columns that are not useful.
2. Remove columns with more than 50% null values.
3. Remove rows with empty target values, manufacturer, or model type, as these three fields seem to be highly relevant.
4. Replace empty values: Forward fill will be used to replace empty values after sorting the data by manufacturer and model. The idea is that the same manufacturer and model should have similar values.
5. Split the dataset into training and testing datasets.
![image](https://github.com/user-attachments/assets/9232a0f1-e6a8-4c5f-9854-9504ece5cfd4)

Modeling:
1. Transform categorical columns into numerical columns using James-Stein encoding.
2. Apply PolynomialFeatures for feature expansion.
3. Use SequentialFeatureSelector to select three important features.
4. Set up a linear regression model using a pipeline.
5. Calculate the Mean Squared Error (MSE) between the training and test datasets.

Evaluation:
1. Using few data points, predit the price of the car. 
