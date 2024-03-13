# Metabolic Syndrome Prediction

*Christina Brockway*

## Business Understanding

**Stakeholder Needs:** To look at common risk factors and use a machine learning model to predict the likelihood of someone having metabolic syndrome.
 
**Metabolic Syndrome**
- *Other Names:* Syndrome X, Insulin Resistance Syndrome, Dysmetabolic Syndrome
- *Definition:*  A cluster of conditions that cause and increased risk for heart disease, stroke, and diabetes

According to the Mayo Clinic, metabolic syndrome will  cause an increase in the risk of heart disease, stroke, and type 2 diabetes.  This syndrome is caused by the presence of multiple risk factors such as body mass index, waist circumference, cholesterol levels, age,  and other various factors.  The National Heart, Lung, and Blood Institue says the syndrome is found in about 1 in 3 adults making it farily common. A diagnosis of metabolic syndrome, although eye opening, doesn't mean patients are definitively getting diabetes or having a stroke. With the right diet and healthy lifestyle changes, metabolic syndrome is preventable, thus showing the importantance of identifying it. 

The goal of this projest is to use a series of risk factors, and create a model that can predict the likihood of metabolic syndrome in patients. The dataset provided came from the NHANES initiative.  It contains variables including: waist circumference, triglyerades, cholesterol levels, race, income, uric acid levels, age, gender, marital status, body mass index, urine albumin grades and rates, and blood glucose levels.

The target for this dataset is the metabolic syndrome feature.  SEQN will be set as the index as it is a unique identifier.  There are 2401 records representing a person and their attributes of which there are 13. There are some columns that have null values needing to be imputed. The feature 'UrAlbCr' was not defined and and assumption was made as to what is being represented based on the NIH and Cleavland Clinic websites. Aside from "UrAlbCr" not being defined, there don't appear to be any challenges with the dataset that interfere with modeling.

--------

*Using the dataset found on Dataworld:* https://data.world/informatics-edu/metabolic-syndrome-prediction

---------

<table class="tg">
<thead>
  <tr>
    <th class="tg-0pky" colspan="5"><span style="font-weight:bold;font-style:italic">Data Dictionary for Metabolic Syndrome Dataset </span></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0pky"><span style="font-weight:bold">Feature</span></td>
    <td class="tg-0pky"><span style="font-weight:bold">dtype</span></td>
    <td class="tg-0pky"><span style="font-weight:bold">Expected Range</span></td>
    <td class="tg-0pky"><span style="font-weight:bold">Definition</span></td>
    <td class="tg-0pky"><span style="font-weight:bold;font-style:italic">cat, num, ord</span></td>
  </tr>
  <tr>
    <td class="tg-0pky"><span style="font-weight:bold;font-style:italic">seqn</span></td>
    <td class="tg-0pky">int</td>
    <td class="tg-0pky">#</td>
    <td class="tg-0pky">sequential identification number</td>
    <td class="tg-0pky"><span style="font-weight:bold;font-style:italic">Index?</span></td>
  </tr>
  <tr>
    <td class="tg-0pky">Age</td>
    <td class="tg-0pky">int</td>
    <td class="tg-0pky">20-80</td>
    <td class="tg-0pky">age of individual<br></td>
    <td class="tg-0pky">num</td>
  </tr>
  <tr>
    <td class="tg-0pky">Sex</td>
    <td class="tg-0pky">str</td>
    <td class="tg-0pky">Male<br>Female</td>
    <td class="tg-0pky">gender of individual</td>
    <td class="tg-0pky">cat</td>
  </tr>
  <tr>
    <td class="tg-0pky">Marital</td>
    <td class="tg-0pky">str</td>
    <td class="tg-0pky">Married<br>Single<br>Divorced<br>Widowed<br>Separated</td>
    <td class="tg-0pky">marital status</td>
    <td class="tg-0pky">cat</td>
  </tr>
  <tr>
    <td class="tg-0pky">Income</td>
    <td class="tg-0pky">int</td>
    <td class="tg-0pky">#</td>
    <td class="tg-0pky">income information</td>
    <td class="tg-0pky">num</td>
  </tr>
  <tr>
    <td class="tg-0pky">Race</td>
    <td class="tg-0pky">str</td>
    <td class="tg-0pky">Other<br>MexAmerican<br>Hispanic<br>Asian<br>Black<br>White</td>
    <td class="tg-0pky">race of individual</td>
    <td class="tg-0pky">cat</td>
  </tr>
  <tr>
    <td class="tg-0pky">WaistCirc</td>
    <td class="tg-0pky">float</td>
    <td class="tg-0pky">risk factor(cm): Men, Women<br>low: &lt; 94m,&nbsp;&nbsp;80w<br>high: 94-102m, 80-88w<br>very high: &gt; 102m, 88w</td>
    <td class="tg-0pky">Circumference of the waist</td>
    <td class="tg-0pky">num</td>
  </tr>
  <tr>
    <td class="tg-0pky">BMI</td>
    <td class="tg-0pky">float</td>
    <td class="tg-0pky">Underweight:&lt; 18.5<br>Normal:18.5-24.9<br>Overweight: 25-29.9<br>Obese: &gt; 30<br></td>
    <td class="tg-0pky">body mass index, a measurement of body composition using height and weight </td>
    <td class="tg-0pky">num</td>
  </tr>
  <tr>
    <td class="tg-0pky">Albuminuria</td>
    <td class="tg-0pky">int</td>
    <td class="tg-0pky">0<br>1<br>2</td>
    <td class="tg-0pky">aka proteinuria<br>a scale grading levels of albumin in urine<br><span style="font-weight:bold">A1: &lt;10-30 Normal or mildly elevated </span><br><span style="font-weight:bold">A2:  30-300 moderately elevated</span><br><span style="font-weight:bold">A3:  &gt;300 albuminuria</span></td>
    <td class="tg-0pky">ord<br></td>
  </tr>
  <tr>
    <td class="tg-0pky">UrAlbCr</td>
    <td class="tg-0pky">float</td>
    <td class="tg-0pky">A1: &lt;30 Normal or mildly elevated <br>A2:  30-300 moderately elevated<br>A3:  &gt;300 albuminuria<br></td>
    <td class="tg-0pky">UACR - ratio of the levels of albumin and creatin in urine</td>
    <td class="tg-0pky">num</td>
  </tr>
  <tr>
    <td class="tg-0pky">UricAcid</td>
    <td class="tg-0pky">float</td>
    <td class="tg-0pky">Normal female: &gt;6mg/dL<br>Normal male: &gt;7 mg/dL</td>
    <td class="tg-0pky">measures amount of uric acid in blood<br>Uric acid is a normal body waste product<br>too high may mean kidneys are not working properly</td>
    <td class="tg-0pky">num</td>
  </tr>
  <tr>
    <td class="tg-0pky">BloodGlucose</td>
    <td class="tg-0pky">int</td>
    <td class="tg-0pky">Normal 80-130mg/dL</td>
    <td class="tg-0pky">Level of glucose in blood<br>too low or too high indicated blood sugar control issues</td>
    <td class="tg-0pky">num</td>
  </tr>
  <tr>
    <td class="tg-0pky">HDL</td>
    <td class="tg-0pky">int</td>
    <td class="tg-0pky">Normal male:  &lt; 40mg/dL <br>Normal female: &lt;50mg/dL</td>
    <td class="tg-0pky">"good" cholesterol levels in blood<br>a lower HDL means higher risk for heart attack</td>
    <td class="tg-0pky">num</td>
  </tr>
  <tr>
    <td class="tg-0pky">Triglycerides</td>
    <td class="tg-0pky">int</td>
    <td class="tg-0pky">150-199 mg/dL borderline<br>200-499 mg/dL high<br>&gt;500 mg/dL very high</td>
    <td class="tg-0pky">amount of triglycerides in blood<br>high levels means risk for stroke or heart attack</td>
    <td class="tg-0pky">num</td>
  </tr>
  <tr>
    <td class="tg-0pky"><span style="font-weight:bold;font-style:italic">MetabolicSyndrome</span></td>
    <td class="tg-0pky">str</td>
    <td class="tg-0pky">No MetSyn<br>MetSyn</td>
    <td class="tg-0pky">does the individual have metabolic syndrome</td>
    <td class="tg-0pky"><span style="font-weight:bold;font-style:italic">target</span></td>
  </tr>
</tbody>
</table>

-----

**For this project the following technolgy was used:**
-  Pandas
-  Matplotlib
-  Numpy
-  Seaborn
-  SciKit Learn
-  TensorFlow
-  KMeans for clustering
-  Neural Network modeling

----------

### Exploratory Analysis:
After cleaning the data Matplolib, NumPy, and Seaborn were used to explore the data and find correlations between the features.  

![countplots](https://github.com/SeeBee8/Metabolic-Syndrome-Prediction/assets/141530991/448a98c4-096d-4de5-9d72-4d9f06ffa41c)

These countplots show the distribution of each feature. There are a number of features such as race, waist size, BMI, and marital status to name a few. The countplot shows how each of these features are distributed. For example, the first plot shows males and females are almost evenly distributed among those tested. The MetS plot shows the patients who have MetS represent about 1/3 of the total number of paitents.  

![heatmap](https://github.com/SeeBee8/Metabolic-Syndrome-Prediction/assets/141530991/dcd7e883-2bad-4c76-8d6b-ef78e3aa5768)

The heatmap shows a correlation between features, the darker the color the higher the correlation. Waist size and BMI have a very high positive correlation, and HDL and triglyceride levels have a high negative correlation. Thus the larger the waist the higher the BMI, and the higher the triglyceride levels, the lower the HDL.

### Feature Engineering:
In order for the model to identify Metabolic Syndrome, there were a few approaches taken to eliminate features that were not as predictive.  Permutation importance was one way features were reduced to the 10 most likely features that effect the identification of Metabolic Syndrome.  These features were then reduced using a threshold of 0.02.  

![image](https://github.com/SeeBee8/Metabolic-Syndrome-Prediction/assets/141530991/e2e19e6a-94b3-4aeb-8a89-823b06b41adb)

-----
### Explanatory Analysis:

The model found that blood glucose levels and triglyceride levels were reliably able to predict Metabolic Syndrome.  However, using multiple features together decreased the liklihood of false positives.

![Screenshot 2023-12-28 121048](https://github.com/SeeBee8/Metabolic-Syndrome-Prediction/assets/141530991/a389f5db-e406-47c2-8af1-e014317f8d07)

This plot shows the relationship between Glucose and Metabolic Syndrome.  As blood glucose levels increase the liklihood of having metabolic syndrome is increased.  

The following plot shows a similar relationship between triglyceride levels and metabolic syndrome.  Both of these features are good predictors of metabolic syndrome. When triglyceride levels and glucose levels are used togther the more precise the prediction of metabolic syndrome.

![Screenshot 2023-12-28 121027](https://github.com/SeeBee8/Metabolic-Syndrome-Prediction/assets/141530991/bf764406-fb5e-4032-b3d8-142df521b62a)


------------------------------------------------------------------------------------
#### Neural Network:

A neural network model was built to try and improve results.  This was a dense neural network using Tensorflow and Keras.  

![RNN-default](https://github.com/SeeBee8/Metabolic-Syndrome-Prediction/assets/141530991/5dd9f5da-3388-45e7-bd96-6e75af1077f4)

Looking at these plots, the loss of the training data and the loss of the validation data should approach each other closely as possible.  The neural network perfomed well, however it does show some overfitting, and it didn't have better results than the Kmeans model. 

---------------------------------------------------------------------------------------


--------

### Final Evaluation:

The best model for this dataset was the DecisionTree Classifier model using KMeans Clustering.  This model will perform with an 87% accuracy at identifying Metabolic Syndrome.  The output of this model can be used to aid in diagnosis along with other medical tests with a precision of 91% No Metabolic Syndrome and 81% Metabolic Syndrome.  

![Screenshot 2024-03-13 142325](https://github.com/SeeBee8/Metabolic-Syndrome-Prediction/assets/141530991/51412d9a-216a-4ff6-94df-6ee1290061e2)

Based on the analysis of the model's performance and the feature importance, it has been observed that high triglyceride and high glucose levels are the most effective predictors of Metabolic Syndrome.  It is noteworthy that utilizing fewer than top 8 features did not improve the models performance. These features are the following:
-  low HDL levels
-  elevated waist sizes
-  higher BMIs
-  high urinary albumin to creatin ratio
-  higher uric acid levels
-  age


-----------------------
The following sources were used to research the dataset and create the dictionary. 

Images: https://www.ncbi.nlm.nih.gov/pmc/articles/PMC9479724/

https://www.urmc.rochester.edu/encyclopedia/

https://www.nhlbi.nih.gov/health/metabolic-syndrome/diagnosis

https://my.clevelandclinic.org/health/diseases/10783-metabolic-syndrome

https://www.kidney.org/content/kidney-failure-risk-factor-urine-albumin-to-creatinine-ration-uacr
