
# Real Estate Price Prediction of California

Using Real Estate dataset of houses in california predict prices of single family houses

Goal of this Project is to predict the price of single family hosues in california. We will train using various regression models. Some analysis done to forecast the best prices and give some recommendation.

### Data used
https://www.kaggle.com/datasets/yellowj4acket/real-estate-california/data
This dataset shows real estate listing for California (US)

### Data Understanding, Data Analysis, Data Cleaning

Data Understanding, Data Analysis, Data Cleaning are done on collected data. 
More details of the analysis can be found in file:

### Feature Engineering

First 'description' field was mined using NLTK to look for specific keywords (for Features like 'hardwood floors', 'solar panels' or for Property Styles like 'victorian', 'contemporary' or for Property Conditions like 'renovated') that might help identify features of single family homes that are not captured in the individual columns. 

Keywords searched were:
- "Features": ['master', 'detached', 'waterfront', 'bonus room', 'solar panel', 'office', 'guest house', 'in law', 'granite', 'new roof', 'custom landscape', 'custom closet', 'backyard', 'back yard'],
- "Property_Condition": ['remodeled', 'renovated', 'designer', 'fixer upper', 'TLC', 'handyman special', 'model home'],
- "Location_Neighborhood": ['safe', 'cul de sac', 'gated', 'freeway', 'highway', 'golf course', 'beach', 'school', 'view', 'acre', 'secure', 'airport', 'train'],
- "Property_Style_Layout": ['ranch', 'colonial', 'victorian', 'mediterranean', 'contemporary', 'modern', 'tuscan', 'farmhouse'],
- "Amenities": ['pet', 'bar', 'pergola', 'furnished', 'community pool', 'gym', 'fireplace', 'deck'],
- "Terms": ['short sale', 'foreclosure', 'owner financing', 'seller financing', 'seller credit', 'cash offer', 'deed', 'association fee', 'motivated']

These keywords were added as columns to the DataFrame after stemming and lemmatizing and each occurence of a keyword in the 'description' field incremented the value in that column for that row.

Next derived Features from existing data:
- Age of the House: Calculate the age of the house by subtracting the year built from the current year (or a reference year=2021). Drop the ‘yearBuilt’ column since‘AgeOfHouse’ now represents the year built information.
- Living Area per Room: Divide the living area by the number of rooms to get a measure of space per room.
- Bath to Bedroom Ratio: bathrooms / bedrooms
- Garage to Bedroom Ratio: garageSpaces / bedrooms

Droped few columns that could likely to increase collinearity:
- yearBuilt - used in age of the house
- livingAreaValue - used in living area per room

Encode categorical columns using One Hot Encoding

## Models Used are
GridSearchCV was used to perform hyperparameter tuning across:
1. Linear Regression with polynomail factors up to a degree=4
1. Ridge Regression
1. Lasso Regression
1. Gradient Descent
1. Neural network with 3 hidden layers

Best Model: Lasso
Best Test RMSE: 213311.1284

## Next Steps
For improving the model further, a few of the below steps can be taken:
- Home prices are also impacted by a few other factors that are not available in the dataset available.
- Using the listing date, identify if it is a buyer's market or seller’s market. - Economic conditions may dictate influence on prices too.
- Adding other such details in the mix will likely reduce the RMSE further down making it a better model in predicting house prices with higher confidence.
- Use Latitude and Longitude to identify additional location-based details such as: Crime rate, proximity to good schools, proximity to airports/train tracks, highways, shopping centers, etc.
- Using street address, identify additional property related records – perhaps using government records - for property tax, association fees, number of acres of the land, specials fees/assessments, etc. that can play a significant portion in deciding the cost of house.
- It's important to remember that these findings are based on the data and model used, and they might vary depending on the dataset and the model's parameters.