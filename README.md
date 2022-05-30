# DSE 230 Final Project: 
# Ocean Health: Important Indicators for Determining Healthy Marine Ecosystems
## Karina, Katie, Leslie's Final Project with the CalCOFI Bottle Database

#### Purpose of Project
The purpose of this project is to look at oceanographic measurements from the CalCofi Bottle Database to build a model to predict chlorophyll concentrations in a new ocean water sample from other oceanographic measurements. The CalCofi Bottle Dataset was created from ocean water samples taken off the coast of California. Each sample was analyzed and reported 30 unique environmental factor concentrations and quality ratings per measurement. The measurements were taken from 1949 to the present. 

We understand the importance of measuring phytoplankton levels to help monitor the ocean's overall health. Phytoplankton are important because they represent the base of the ocean's food web. A change in phytoplankton population can have detrimental effects on the environment around it. A rapid abundance of phytoplankton can cause a steep decrease of oxygen in the water, creating what is known as a dead zone, killing the marine species in surrounding areas. If phytoplankton are less abundant, the bottom of the food web is distorted, causing a ripple affect of food depletion cascading up the food web. Predicting phytoplankton early, when we can see the concentrations are rising or falling, can help scientists manage the surrounding environment effectively.

To determine phytoplankton concentration, we have chosen to analyze chlorophyll concentrations, 'R_CHLA'. With chlorophyll being an important chemical in photosynthesis, determining it's concentration would be symmetrical to the phytoplankton concentration. We chose to transform our chlorophyll concentrations into three categories, low, medium, and high levels. We chose to do this as categorizing them can produce a more interpretable result, instead of the concentration value. It provides scientists with immediate feedback of a change in population, going from medium concentration one day, to high the next. 

Ultimately, our project will produce a Logistic Regression and a Decision Tree model that will predict which concentration level the new sample is in. This will cut back on sampling cost and labor because a mass spectrometry analysis for chlorophyll will be unnecessary. 


## Notebook Outline

- Data Preperation
	- Cleaned Data
		- Removed unnecessary columns to our analysis
		- Removed rows with the Quality Codes labeled 8 (bad quality)
		- Removed features with high null values
	- Reduce Dimentionality without Reducing Variance	
		- Performed Lasso Regression to find feature coefficient contributing to the model (coefficient > 0)
		- Perform Feature Correlation to find highly correlated feature pairs and removed the column with less null values 
	- Resulted in 8 features for our model
- Analysis Preparation
	- Transformed Chlorophyll concentrations into low, medium, and high concentration categories. 
	- Split our dataset into train, test, and validation datasets
	- Scaled dataset using MinMaxScaler
	- Assured proportional distributions throughout each dataset to ensure each step was a good representation of the dataset. 
- Analysis
	- Performed Logistic Regression analysis
	- Performed Decision Tree analysis
	- Each reported an accuracy of 0.882
	- The most important features to chlorophyll predictions were: 
		- Phaeophytin
		- Dynamic Height
		- Temperature
		- Oxygen Saturation
		- Nitrite


## How To Run:
1. Download data "bottle.csv" from https://www.kaggle.com/datasets/sohier/calcofi
    
	Note: "cast.csv" is a supplemental dataset that we will not use
2. start jupyter lab
3. pip install pyspark
4. write data "bottle.csv" to HDFS 

	hadoop fs -copyFromLocal bottle.csv /
5. run jupyter notebook "FinalProject.ipynb"

