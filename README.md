# Metabolic Syndrome Prediction

*Christina Brockway*

## Business Understanding

**Stakeholder Needs:** To look at common risk factors and use a machine learning model to predict the likelihood of someone having metabolic syndrome.
 
**Metabolic Syndrome**
- *Other Names:* Syndrome X, Insulin Resistance Syndrome, Dysmetabolic Syndrome
- *Definition:*  A cluster of conditions that cause and increased risk for heart disease, stroke, and diabetes

According to the Mayo Clinic, metabolic syndrome will  cause an increase in the risk of heart disease, stroke, and type 2 diabetes.  This syndrome is caused by the presence of multiple risk factors such as body mass index, waist circumference, cholesterol levels, age,  and other various factors.  The National Heart, Lung, and Blood Institue says the syndrome is found in about 1 in 3 adults making it farily common. A diagnosis of metabolic syndrome, although eye opening, doesn't mean patients are definitively getting diabetes or having a stroke. With the right diet and healthy lifestyle changes, metabolic syndrome is preventable, thus showing the importantance of identifying it. 

The goal of this projest is to use a series of risk factors, and create a model that can predict the likihood of metabolic syndrome in patients. The dataset provided came from the NHANES initiative.  It contains variables including: waist circumference, triglyerades, cholesterol levels, race, income, uric acid levels, age, gender, marital status, body mass index, urine albumin grades and rates, and blood glucose levels.

The target for this dataset is the metabolic syndrome feature.  SEQN will be set as the index as it is a unique identifier.  There are 2401 records representing a person and their attributes of which there are 13. There are some columns that have null values needing to be imputed. The feature 'UrAlbCr' was not defined and and assumption was made as to what is being represented based on the NIH and Cleavland Clinic websites. Aside from "UrAlbCr" not being defined, there don't appear to be any chanllenges with the dataset that would interfere with modeling.

--------
**Using the dataset found on Dataworld:** 
https://data.world/informatics-edu/metabolic-syndrome-prediction
---------
<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-0pky{border-color:inherit;text-align:left;vertical-align:top}
</style>
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
### Explanatory Analysis:

The model found that BMI and waist size were reliably able to predict Metabolic Syndrome.  The 













-----------------------
The following sources were used to research the dataset and create this dictionary. The only issue was the 'UrAlbCre' feature. After researching the various tests done for metabolic syndrome and the values provided, it is assumed that 'UrAlbCr' is UACR. UACR is a measure of the ratio of albumin to creatin in urine, and is used to detect kidney disease.

Images: https://www.ncbi.nlm.nih.gov/pmc/articles/PMC9479724/

https://www.urmc.rochester.edu/encyclopedia/

https://www.nhlbi.nih.gov/health/metabolic-syndrome/diagnosis

https://my.clevelandclinic.org/health/diseases/10783-metabolic-syndrome

https://www.kidney.org/content/kidney-failure-risk-factor-urine-albumin-to-creatinine-ration-uacr