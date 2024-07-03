# [House Sales in King Count USA](https://github.com/GBOL67/House_Sales_in_King_Count_USA/blob/main/House_Sales_in_King_Count_USA.ipynb)
The primary objective of this project is to develop a predictive model for estimating house prices in King County, USA, to assist a Real Estate Investment Trust (REIT) in making informed investment decisions in the residential real estate market. The model aims to identify key predictors of house prices and provide accurate price estimates, thereby enabling the REIT to assess property values and potential returns on investment effectively.

## Data Understanding
 King County house sales  for homes sold between May 2014 and May 2015.The dataset comprises  with 21 features. Key features include:
- `id`: House identifier
- `date`: Sale date
- `price`: Sale price (target variable)
- `bedrooms`, `bathrooms`, `sqft_living`, `sqft_lot`: House characteristics
- `floors`, `waterfront`, `view`, `condition`, `grade`: Quality and condition metrics
- `sqft_above`, `sqft_basement`: Square footage details
- `yr_built`, `yr_renovated`: Construction and renovation years
- `zipcode`, `lat`, `long`: Location information
- `sqft_living15`, `sqft_lot15`: Living and lot sizes in 2015, indicating potential renovations

## Data Preparation
**Input:** Raw King County house sales dataset.
**Process:**
1. **Import and Initial Cleaning**: Loaded the dataset into a Pandas DataFrame and identified missing values in the `bedrooms` and `bathrooms` columns.
2. **Feature Engineering**: Created new features, including sale day, month, duration since construction (`dur`), and a binary indicator for renovation status.
3. **Imputation**: Addressed missing values using appropriate imputation techniques to ensure data completeness.
**Ouput:** A cleaned dataset named `data` consisting of  23 variables.

## Data Analysis
**Input:** Dataset `data`.
**Process:**
1. **Correlation Analysis**: Analyzed the correlation between features and the target variable (`price`), The feature sqft_living had the highest positive correlation with price (0.702035), while dur had the highest negative correlation (-0.053951).
   
| Feature        | Coefficient |
|----------------|-------------|
| price          | -0.053951   |
| dur            | -0.053203   |
| zipcode        | -0.053203   |
| month          | -0.010081   |
| long           | 0.021626    |
| condition      | 0.036362    |
| sqft_lot15     | 0.082447    |
| sqft_lot       | 0.089661    |
| renovated      | 0.126092    |
| yr_renovated   | 0.126434    |
| floors         | 0.256794    |
| waterfront     | 0.266369    |
| lat            | 0.307003    |
| bedrooms       | 0.308797    |
| sqft_basement  | 0.323816    |
| view           | 0.397293    |
| bathrooms      | 0.525738    |
| sqft_living15  | 0.585379    |
| sqft_above     | 0.605567    |
| grade          | 0.667434    |
| sqft_living    | 0.702035    |


2. **Feature Categorization**: The price data was categorized into three levels: `low (<3.219500e+05)`, `medium (<4.500000e+05)`, and `high (<7.700000e+06)`. Histogram plots were used to compare the categorized price data with other features such as bathrooms, bedrooms, and square footage of living space. These features were also categorized to match the price data for better comparison.
<img src="https://github.com/GBOL67/House_Sales_in_King_Count_USA/blob/main/media/bathrooms.PNG" align="center" width="700" height="600" />
<img src="https://github.com/GBOL67/House_Sales_in_King_Count_USA/blob/main/media/bedrooms.PNG" align="center" width="700" height="600" />
<img src="https://github.com/GBOL67/House_Sales_in_King_Count_USA/blob/main/media/sqft_living_bins.PNG" align="center" width="700" height="600" /> 
**Output:** Histogram plots used to compare the categorized price data with other features such as bathrooms, bedrooms, and square footage of living space.   

## Model Development 
**Input:** Dataset `clean`. The dependent data (Y) consist of the price feature while the independent data (X) consist of all features except the price feature. 
1. **Data Splitting**: Divided the dataset into training and testing sets with various test sizes (10%, 25%, 75%).
2. **Polynomial Features**: Applied polynomial transformations (orders 1 to 3) to the independent variables to capture non-linear relationships.
3. **Linear Regression**: Built multiple linear regression models and evaluated their performance, achieving an initial R-squared value of 0.768 with a polynomial order of 2.
<img src="https://github.com/GBOL67/Taxi-Tip-Prediction/blob/main/media/r2_vs_order.PNG" align="center" width="700" height="600" /> 


**Output:** The test size of 10% and polynomial transformation of the 2nd order for model refinement.

## Model Refinement and Evaluation
**Input:** Dataset `clean`. The dependent data (Y) consist of the price feature while the independent data (X) consist of all features except the price feature. 
1. **Cross-Validation**: Refined the model using cross-validation with a test size of 10%, improving the R-squared value to 0.863.
2. **Ridge Regression**: Implemented Ridge regression with Grid Search to optimize the regularization parameter with the fold created with the cross-validation method, resulting in a cross-validated R-squared of 0.865 and a test set R-squared of 0.873.
<img src="https://github.com/GBOL67/House_Sales_in_King_Count_USA/blob/main/media/model%20refinement.PNG" align="center" width="700" height="600" /> 

**Output:** A density plot that shows the relationship between the predicted data and the actual data.

## CONCLUSION
A comprehensive analysis of house prices in King County was done leveraging various features to develop a predictive model. The model demonstrated that the square footage of living space is the most significant predictor of house prices, while the duration since construction had a negative impact. The refined model, using cross-validation, achieved an R-squared value of 0.86317220221015, indicating a good fit and reliability in predicting house prices.
