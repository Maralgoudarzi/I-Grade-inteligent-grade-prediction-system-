# I-Grade (inteligent grade prediction system)
Grade prediction system based on trend of the recorded data in database. User select its habit then get the grade closest to the final result.

# Requirments and prepration
This project is based on the following technology:
* Data
  + Pandas
  + Numpy
  
* Model
  + Sikit-learn
  
* Web side
  + Flask
  + Bootstrap

* visualisation
  + Chartjs

# App Structure
we can seprate this project (Flask framework) to several main part with different functionality.

App (I-grade):
  + static (folder)
    + css (folder)
      + bootstrap
    + datasets (folder)
      + dataset_main.csv // main dataset for making model
    + images (folder)
      + Logo.png 
      + ki.jpg
    + javascript (folder)
      + viz.js // main javascript file for making charts
  + template (folder)
    + index.html
    + prediction.html // page of showing the prediciton result
    + question_form.html // the form for getting user input
  + Convertor.py
  + Model_classification.py // clasifier model
  + plot.py // preparing data to use for plotting
  + server.py // application server backend part
  

# Step 1
### Data prepration (Model_classification.py)
for making our model and use it for the prediction we need to first prepare the data for process. we are dealing with data using "pandas", "numpy" , "sklearn"
so we need to import this library:

```
import pandas as pd
import numpy as np
from sklearn.preprocessing import LabelEncoder

```
and then we are reading the data and encoding the categorical data in order to give them to model in training process:

```
#read data
df = pd.read_csv("./static/datasets/dataset_main.csv", engine='python',sep=',')



# add new feature to use it for classification
grades = df['G3'].values
labels = []

for grade in grades:
    if grade >=17:
        labels.append('very good')
    elif grade < 17 and grade >= 15:
        labels.append('good')
    elif grade < 15 and grade >= 10:
        labels.append('average')
    elif grade < 10:
        labels.append('bad')

#encoding the data
enc = LabelEncoder()
for item in df:
    data_raw = df[item].values
    df[item] = enc.fit_transform(data_raw)

enc_labels = enc.fit_transform(labels)

print(df.head(4))
df = df.values
#print(df['item'].head())
#preparing test data
X_train, X_test, y_train, y_test = train_test_split(df[:,:16],enc_labels, stratify=enc_labels,random_state=0,test_size=0.20)

```

