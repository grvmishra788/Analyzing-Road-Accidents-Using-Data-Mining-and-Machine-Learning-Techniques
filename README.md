## Road Accident Analysis


### Motivation
- UK police forces collect data on every vehicle collision in the UK on a form called Stats19. [Kaggle Dataset Link](https://www.kaggle.com/silicon99/dft-accident-data)
- The dataset used in this project provides detailed road safety data about the circumstances of personal injury road accidents in GB from 1979, the types (including Make and Model) of vehicles involved and the consequential casualties.
- Such a dataset can be used to obtain behavioural patterns based on certain rules. From these rules, some conclusions can be extracted which can help to develop suitable prevention policies to reduce number of casualties in cases of such accidents.


### Objective
- The goal of this work is to analyze the main factors that could be the possible causes of road accidents in UK as per the dataset provided.

### Dataset
- Download the dataset from this [Google Drive link](https://drive.google.com/file/d/1TSbV13ftvywhoH7H9GfzDqIsAL-jQDsE/view?usp=sharing), unzip and cut-paste the three csv files to input folder

### Proposed work
- A selection of accident data is made, taking into account its relevance in our study, in order to work with a reasonable data source. The variable Number_Of_Casualties, chosen a priori, serves as output attribute.
- To remove the curse of dimensionality, feature selection tools and techniques were applied in a unique way to find best 18 predictor variables for the output variable Number_Of_Casualties.
- Various data mining models (like k-nn classifier, naive bayes classifier, decision tree etc) trained and tested on the dataset.
- A ranking of the most important predictors for the output variable Number_Of_Casualties is established based on these models.
- Association rules from decision trees for the predictor variables are obtained. These association rules allow the most relevant factors to be extracted to enable the output variable to be evaluated.


#### Step 1 : Selection & Pre-processing of accident data 
- There are 3 CSVs in the dataset useds. Accidents is the primary one and has references by Accident_Index to the casualties and vehicles tables. 
- After merging the three tables the given dataset had 961906 samples with around 67 variables in each sample.
- To start with pre-processing, the attributes having a lot of null entries were removed.  Dataset now had only 62 variables.
- Out of these 62, the variable Number_Of_Casualties measured the gravity of the accidents and hence it was chosen as the response or output variable.

#### Step 2 : Applying feature selection techniques
- 961906 samples with around 61 variables in each sample were left in the dataset, which was a lot to process.
- Hence to remove the curse of dimensionality, feature selection tools and techniques were applied in a unique way to find best 18 predictor variables.<br/>
<p align="center">
  <img width="460" height="300" src="https://github.com/grvmishra788/Analyzing-Road-Accidents-Using-Data-Mining-and-Machine-Learning-Techniques/blob/master/images/feature_selection.png">
</p>

#### Step 3 : Applying ML models
- The dataset was then divided into training and test sets in the ratio 9:1.
- After this a variety of classifiers which can handle a large number of samples were applied on the dataset and following results were obtained.
- Decision Tree classifier seemed to produce the best results on the given dataset achieving an accuracy of 99.68% on training set and 93.71% on test set.
<p align="center">
  <img width="750" height="150" src="https://github.com/grvmishra788/Analyzing-Road-Accidents-Using-Data-Mining-and-Machine-Learning-Techniques/blob/master/images/table_accuracy.PNG">
</p>
 
 #### Step 4: Ranking of the predictor variables 
- Since Decision Tree classifier is the best performing classifier in this case, a ranking of the predictor variables was generated using it.
<p align="center">
  <img width="750" height="600" src="https://github.com/grvmishra788/Analyzing-Road-Accidents-Using-Data-Mining-and-Machine-Learning-Techniques/blob/master/images/features_ranking.png">
</p>

#### Step 5: Generating Decision Rules
- Since Decision Tree classifier is the best performing classifier in this case, obtaining a set of decision rules from the classifier could help in getting relevant insights about what factors actually resulted in severe accidents. This can then help in generating accident prevention policies in future (outside the course of this project).
- For instance, one of the three variable decision rule obtained was - <br/>
&nbsp;&nbsp;&nbsp;&nbsp; if <b> (Casualty_Reference <= 1.5 && Casualty_Type <= 6.5 && Number_of_Vehicles <= 2.5 )</b> => <b>(Number_Of_Casualties <= 1)</b> with 94.78% confidence </b> 
- In it's core essence, the above rule implies that if in an accident, Casuality_Reference was 1, the casuality involved two wheeleres i.e. Pedestrians, Cyclist or MotorCyclist and Number Of Vehicles involved were 2 or less then Total Number of Casualities that resulted from it were either 0 or 1. This claim was valid in 94.78% of the total accidents recorded.
- With the above insight, policies can be made to make more accident cases fall in this category i.e. <i> (Casualty_Reference <= 1.5 && Casualty_Type <= 6.5 && Number_of_Vehicles <= 2.5 )</i> so that Number Of Casualities are minimized. However, actual extraction of such policies is beyond the scope of this project.

### Conclusion
- With the objective to identify the main factors causing road accidents in UK and by using data mining techniques, nearly 900000 instances of road accidents recorded in the UK were analyzed. The study shows that the variables Casuality_Reference, Latitude, Longitude, Location_Northing_OSGR,  Location_Easting_OSGR, Road_Class , Number_Of_Vehicles and Speed_limit are in the genesis of most accidents. 
- This work, in future, could help in the establishment of improvement polices in order to minimize the rate of road accidents in the UK, which can be developed based upon the Decision Rules obtained.
